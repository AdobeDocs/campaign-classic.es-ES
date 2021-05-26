---
solution: Campaign Classic
product: campaign
title: Configuración del servidor de Campaign
description: Configuración del servidor de Campaign
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 46c8ed46-0947-47fb-abda-6541b12b6f0c
source-git-commit: bce114f36d1ec4582fc79e750d48155ba0d7cd1f
workflow-type: tm+mt
source-wordcount: '1578'
ht-degree: 2%

---

# Introducción a la configuración del servidor de Campaign{#gs-campaign-server-config}

En este capítulo se detallan las configuraciones del lado del servidor que se pueden realizar para adaptarlas a sus necesidades y a las particularidades de su entorno.

## Restricciones

Estos procedimientos están restringidos a **implementaciones locales**/**híbridas** y requieren permisos de administración.

Para implementaciones **alojadas**, la configuración del lado del servidor solo se puede configurar mediante Adobe. Sin embargo, algunas configuraciones se pueden configurar dentro de [Panel de control de Campaign de campaña](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html), como administración de listas de permitidos IP o permisos de URL. [Más información](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html).

Para obtener más información, consulte estas secciones:

* [Documentación del Panel de control](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=es)
* [Modelos de alojamiento](../../installation/using/hosting-models.md)
* [Matriz de capacidades alojadas y locales del Campaign Classic](../../installation/using/capability-matrix.md)

## Archivos de configuración

Los archivos de configuración del Campaign Classic se almacenan en la carpeta **conf** de la carpeta de instalación de Adobe Campaign. La configuración se distribuye en dos archivos:

* **serverConf.xml**: configuración general para todas las instancias. Este archivo combina los parámetros técnicos del servidor Adobe Campaign: todas las instancias las comparten. A continuación se detalla la descripción de algunos de estos parámetros. Los diferentes nodos y parámetros y enumerados en esta [sección](../../installation/using/the-server-configuration-file.md).
* **config-`<instance>`.xml**  (donde  **** instance es el nombre de la instancia): configuración específica de la instancia. Si comparte el servidor entre varias instancias, introduzca los parámetros específicos de cada instancia en su archivo correspondiente.

## Ámbito de configuración

Configure o adapte el servidor de Campaign según sus necesidades y configuración. Puede:

* Asegurar el [identificador interno](#internal-identifier)
* Habilitar [Procesos de campaña](#enabling-processes)
* Configurar [Permisos de URL](url-permissions.md)
* Definir [Zonas de seguridad](security-zones.md)
* Configurar [configuración de Tomcat](configure-tomcat.md)
* Personalizar [Parámetros de envío](configure-delivery-settings.md)
* Definir [seguridad de página dinámica y relés](#dynamic-page-security-and-relays)
* Restringir la lista de [Comandos externos permitidos](#restricting-authorized-external-commands)
* Configurar [Seguimiento redundante](#redundant-tracking)
* Administrar [Afinidades de alta disponibilidad y flujo de trabajo](#high-availability-workflows-and-affinities)
* Configurar la administración de archivos: [Más información](file-res-management.md)
   * Limitar el formato de los archivos de carga
   * Habilitar el acceso a los recursos públicos
   * Configuración de la conexión proxy
* [Reinicio automático del proceso](#automatic-process-restart)


## Identificador interno {#internal-identifier}

El identificador **internal** es un inicio de sesión técnico que se utilizará con fines de instalación, administración y mantenimiento. Este inicio de sesión no está asociado a una instancia.

Los operadores conectados mediante este inicio de sesión tendrán todos los derechos en todas las instancias. Este inicio de sesión no tendrá contraseña en el caso de una nueva instalación. Debe definir manualmente esta contraseña.

Utilice el siguiente comando:

```
nlserver config -internalpassword
```

A continuación, se muestra la siguiente información. Introduzca y confirme la contraseña:

```
17:33:57 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
Enter the current password.
Password:
Enter the new password.
Password: XXXX
Confirmation: XXXX
17:34:02 >   Password successfully changed for account 'internal' (authentication mode 'nl')
```

## Habilitar procesos {#enabling-processes}

Los procesos de Adobe Campaign en el servidor están habilitados (y deshabilitados) a través de los archivos **config-default.xml** y **`config-<instance>.xml`** .

Para aplicar los cambios a estos archivos, si se inicia el servicio de Adobe Campaign, debe ejecutar el comando **nlserver config -reload**.

Existen dos tipos de procesos: instancia múltiple y instancia única.

* **varias instancias**: se inicia un solo proceso para todas las instancias. Este es el caso de los procesos **web**, **syslogd** y **trackinglogd**.

   La habilitación se puede configurar desde el archivo **config-default.xml**.

   Declaración de un servidor de Adobe Campaign para acceder a las consolas de cliente y para la redirección (seguimiento):

   ```
   vi nl6/conf/config-default.xml
   <web args="-tomcat" autoStart="true"/>  
   <!-- to start if the machine is also a redirection server -->  
   <trackinglogd autoStart="true"/>
   ```

   En este ejemplo, el archivo se edita mediante un comando **vi** en Linux. Se puede editar con cualquier editor **.txt** o **.xml**.

* **instancia** mono: se inicia un proceso para cada instancia (módulos:  **mta**,  **wfserver**,  **inMail**,  **** smand  **stat**).

   La habilitación se puede configurar utilizando el archivo de configuración de la instancia:

   ```
   config-<instance>.xml
   ```

   Declarar un servidor para su envío, ejecutar instancias de flujo de trabajo y recuperar el correo rechazado:

   ```
   <mta autoStart="true" statServerAddress="localhost"/>
   <wfserver autoStart="true"/>  
   <inMail autoStart="true"/>
   <stat autoStart="true"/>
   ```

**Almacenamiento de datos de Campaign**

Puede configurar el directorio de almacenamiento (directorio **var**) de datos de Adobe Campaign (registros, descargas, redirecciones, etc.). Para ello, utilice la variable del sistema **XTK_VAR_DIR**:

* En Windows, indique el siguiente valor en la variable de sistema **XTK_VAR_DIR**

   ```
   D:\log\AdobeCampaign
   ```

* En Linux, vaya al archivo **customer.sh** e indique: **exportar XTK_VAR_DIR=/app/log/AdobeCampaign**.

   Para obtener más información, consulte [Personalize parameters](../../installation/using/installing-packages-with-linux.md#personalizing-parameters).


## Seguridad y relevos dinámicos de la página {#dynamic-page-security-and-relays}

De forma predeterminada, todas las páginas dinámicas están relacionadas automáticamente con el servidor **local** Tomcat del equipo cuyo módulo web se ha iniciado. Esta configuración se introduce en la sección **`<url>`** de la configuración de la retransmisión de consulta para el archivo **ServerConf.xml**.

Puede retransmitir la ejecución de la página dinámica en un servidor **remoto**; si el módulo web no está activado en el equipo. Para ello, debe reemplazar el **localhost** con el nombre del equipo remoto para JSP y JSSP, aplicaciones web, informes y cadenas.

Para obtener más información sobre los distintos parámetros disponibles, consulte el archivo de configuración **serverConf.xml**.

Para las páginas JSP, la configuración predeterminada es:

```
<url relayHost="true" relayPath="true" targetUrl="http://localhost:8080" urlPath="*.jsp"/>
```

Adobe Campaign utiliza las siguientes páginas JSP:

* /nl/jsp/**soaprouter.jsp**: conexiones de consola de cliente y servicios web (API SOAP),
* /nl/jsp/**m.jsp**: páginas espejo,
* /nl/jsp/**logon.jsp**: Acceso basado en la web a los informes y a la implementación de la consola del cliente,
* /nl/jsp/**s.jsp** : Uso del marketing viral (patrocinio y redes sociales).

Los JSSP utilizados para el canal de aplicaciones móviles son los siguientes:

* nms/mobile/1/registerIOS.jssp
* nms/mobile/1/registerAndroid.jssp

**Ejemplo:**

Es posible evitar las conexiones del equipo cliente desde el exterior. Para ello, simplemente limite la ejecución de **soaprouter.jsp** y autorice la ejecución de páginas espejo, vínculos virales, formularios web y recursos públicos.

Los parámetros son los siguientes:

```
<url IPMask="<IP_addresses>" deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="*.jsp"/>
<url IPMask="<IP_addresses>" deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="*.jssp"/> 
<url IPMask=""               deny=""     hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080" timeout="" urlPath="m.jsp"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080" timeout="" urlPath="s.jsp"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080" timeout="" urlPath="webForm.jsp"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/webApp/pub*"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/jssp/pub*"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/strings/pub*"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/interaction/pub*"/>
<url IPMask=""               deny="true" hostMask="" relayHost="false" relayPath="false" targetUrl="http://localhost:8080" timeout="" urlPath="*.jsp"/>
<url IPMask=""               deny="true" hostMask="" relayHost="false" relayPath="false" targetUrl="http://localhost:8080" timeout="" urlPath="*.jssp"/>
```

En este ejemplo, el valor **`<IP_addresses>`** coincide con la lista de direcciones IP (separadas por comas) autorizadas para utilizar el módulo de transmisión para esta máscara.

>[!NOTE]
>
>Los valores se adaptarán según su configuración y sus limitaciones de red, especialmente si se han desarrollado configuraciones específicas para su instalación.

### Administrar encabezados HTTP {#managing-http-headers}

De forma predeterminada, todos los encabezados HTTP no se retransmiten. Puede añadir encabezados específicos en las respuestas enviadas por relé. Para ello:

1. Vaya al archivo **serverConf.xml**.
1. En el nodo **`<relay>`**, vaya a la lista de encabezados HTTP reenviados.
1. Agregue un elemento **`<responseheader>`** con los siguientes atributos:

   * **nombre**: nombre de encabezado
   * **valor**: nombre del valor.

   Por ejemplo:

   ```
   <responseHeader name="Strict-Transport-Security" value="max-age=16070400; includeSubDomains"/>
   ```

## Restringir comandos externos autorizados {#restricting-authorized-external-commands}

Desde la versión 8780, los administradores técnicos pueden restringir la lista de comandos externos autorizados que se pueden utilizar en Adobe Campaign.

Para ello, debe crear un archivo de texto con la lista de comandos que desee evitar utilizar, por ejemplo:

```
ln
dd
openssl
curl
wget
python
python3
perl
ruby
sh
```

>[!IMPORTANT]
>
>Esta lista no es exhaustiva.

En el nodo **exec** del archivo de configuración del servidor, debe hacer referencia al archivo creado anteriormente en el atributo **blacklistFile**.

**Solo** para Linux: en el archivo de configuración del servidor, se recomienda especificar un usuario dedicado a ejecutar comandos externos para mejorar la configuración de seguridad. Este usuario se establece en el nodo **exec** del archivo de configuración. Todos los parámetros disponibles en **serverConf.xml** se enumeran en esta [sección](../../installation/using/the-server-configuration-file.md).

>[!NOTE]
>
>Si no se especifica ningún usuario, todos los comandos se ejecutan en el contexto de usuario de la instancia de Adobe Campaign. El usuario debe ser diferente al usuario que ejecuta Adobe Campaign.

Por ejemplo:

```
<serverConf>
 <exec user="theUnixUser" blacklistFile="/pathtothefile/blacklist"/>
</serverConf>
```

Este usuario debe añadirse a la lista de usuarios del operador &quot;neolane&quot; Adobe Campaign.

>[!IMPORTANT]
>
>No debe utilizar un sudo personalizado. Se debe instalar un sudo estándar en el sistema.


## Seguimiento redundante {#redundant-tracking}

Cuando se utilizan varios servidores para la redirección, deben poder comunicarse entre sí a través de llamadas SOAP para compartir información de las direcciones URL a redirigir. En el momento del inicio del envío, es posible que no todos los servidores de redirección estén disponibles; por lo tanto, es posible que no tengan el mismo nivel de información.

>[!NOTE]
>
>Cuando se utiliza la arquitectura estándar o empresarial, se debe autorizar al servidor de aplicaciones principal para que cargue información de seguimiento en cada equipo.

Las direcciones URL de los servidores redundantes deben especificarse en la configuración de redirección, a través del archivo **serverConf.xml**.

**Ejemplo:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

La propiedad **enableIf** es opcional (vacía de forma predeterminada) y le permite habilitar la conexión solo si el resultado es true. Esto permite obtener una configuración idéntica en todos los servidores de redirección.

Para obtener el nombre de host del equipo, ejecute el siguiente comando: **hostname -s**.



## Flujos de trabajo y afinidades de alta disponibilidad {#high-availability-workflows-and-affinities}

Puede configurar varios servidores de flujo de trabajo (wfserver) y distribuirlos en dos o más equipos. Si elige este tipo de arquitectura, configure el modo de conexión de los equilibradores de carga según el acceso de Adobe Campaign.

Para acceder desde la web, seleccione el modo **equilibrador de carga** para limitar los tiempos de conexión.

Si accede a través de la consola de Adobe Campaign, elija el modo **hash** o **ip adhesiva**. Esto permite mantener la conexión entre el cliente enriquecido y el servidor e impedir que se interrumpa una sesión de usuario durante una operación de importación o exportación, por ejemplo.

Puede optar por forzar la ejecución de un flujo de trabajo o una actividad de flujo de trabajo en un equipo concreto. Para ello, debe definir una o más afinidades para el flujo de trabajo o la actividad correspondientes.

1. Cree las afinidades del flujo de trabajo o la actividad introduciéndolas en el campo **[!UICONTROL Affinity]** .

   Puede elegir cualquier nombre de afinidad, pero asegúrese de no utilizar espacios ni signos de puntuación. Si utiliza servidores diferentes, especifique nombres diferentes.

   ![](assets/s_ncs_install_server_wf_affinity01.png)

   ![](assets/s_ncs_install_server_wf_affinity02.png)

   La lista desplegable contiene afinidades que antes se usaban. Se completa con el tiempo con los diferentes valores introducidos.

1. Abra el archivo **nl6/conf/config-`<instance>.xml`**.
1. Modifique la línea que coincida con el módulo **[!UICONTROL wfserver]** de la siguiente manera:

   ```
   <wfserver autoStart="true" affinity="XXX,"/>
   ```

   Si define varias afinidades, deben separarse con comas sin espacios:

   ```
   <wfserver autoStart="true" affinity="XXX,YYY,"/>
   ```

   La coma que sigue al nombre de la afinidad es necesaria para la ejecución de flujos de trabajo para los que no se define ninguna afinidad.

   Si desea ejecutar solo flujos de trabajo para los que se define una afinidad, no agregue una coma al final de la lista de afinidades. Por ejemplo, modifique la línea de la siguiente manera:

   ```
   <wfserver autoStart="true" affinity="XXX"/>
   ```

## Reinicio automático {#automatic-process-restart}

De forma predeterminada, los diferentes procesos de Adobe Campaign se reinician automáticamente a las 6 a. m. (hora del servidor) todos los días.

Sin embargo, puede cambiar esta configuración.

Para ello, vaya al archivo **serverConf.xml**, ubicado en el repositorio **conf** de la instalación.

Cada proceso configurado en este archivo tiene un atributo **processRestartTime**. Puede modificar el valor de este atributo para adaptar el tiempo de reinicio de cada proceso según sus necesidades.

>[!IMPORTANT]
>
>No elimine este atributo. Todos los procesos deben reiniciarse todos los días.
