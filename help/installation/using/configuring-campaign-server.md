---
product: campaign
title: Configuración del servidor de Campaign
description: Configuración del servidor de Campaign
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Solo se aplica a Campaign Classic v7"
badge-v7-prem: label="on-premise e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 46c8ed46-0947-47fb-abda-6541b12b6f0c
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1603'
ht-degree: 4%

---

# Introducción a la configuración del servidor de Campaign{#gs-campaign-server-config}



En este capítulo se detallan las configuraciones del lado del servidor que se pueden realizar para adaptarse a sus necesidades y a las características específicas de su entorno.

## Restricciones

Estos procedimientos se limitan a **on-premise**/**híbrido** implementaciones de y requieren permisos de administración.

Para **alojado** En implementaciones, la configuración del lado del servidor solo se puede configurar mediante el Adobe. Sin embargo, algunos ajustes se pueden configurar en [Panel de control de Campaign de campaña](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=es), como la administración de listas de permitidos IP o los permisos de URL. [Más información](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html?lang=es).

Para obtener más información, consulte estas secciones:

* [Documentación del Panel de control](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=es)
* [Modelos de alojamiento](../../installation/using/hosting-models.md)
* [Campaign Classic Matriz de funciones locales y alojadas](../../installation/using/capability-matrix.md)

## Archivos de configuración

Los archivos de configuración del Campaign Classic se almacenan en **conf** de la carpeta de instalación de Adobe Campaign. La configuración se distribuye en dos archivos:

* **serverConf.xml**: configuración general para todas las instancias. Este archivo combina los parámetros técnicos del servidor de Adobe Campaign: todos los instancias los comparten. La descripción de algunos de estos parámetros se detalla a continuación. Los diferentes nodos y parámetros y enumerados en esta [sección](../../installation/using/the-server-configuration-file.md).
* **config-`<instance>`.xml** (donde **instancia** es el nombre de la instancia): configuración específica de la instancia. Si comparte el servidor entre varias instancias, introduzca los parámetros específicos de cada instancia en el archivo correspondiente.

## Ámbito de configuración

Configure o adapte el servidor de Campaign según sus necesidades y configuración. Puede hacer lo siguiente:

* Proteja el [Identificador interno](#internal-identifier)
* Activar [Procesos de Campaign](#enabling-processes)
* Configurar [Permisos de URL](url-permissions.md)
* Definir [Zonas de seguridad](security-zones.md)
* Configurar [Configuración de Tomcat](configure-tomcat.md)
* Personalizar [Parámetros de envío](configure-delivery-settings.md)
* Definir [Seguridad y transmisiones dinámicas de páginas](#dynamic-page-security-and-relays)
* Restringir la lista de [Comandos externos permitidos](#restricting-authorized-external-commands)
* Configuración de [Seguimiento redundante](#redundant-tracking)
* Administrar [Alta disponibilidad y afinidades del flujo de trabajo](#high-availability-workflows-and-affinities)
* Configuración de la administración de archivos - [Más información](file-res-management.md)
   * Limitar formato de archivos de carga
   * Habilitar el acceso a los recursos públicos
   * Configurar conexión proxy
* [Reinicio automático del proceso](#automatic-process-restart)


## Identificador interno {#internal-identifier}

El **interno** El identificador es un inicio de sesión técnico que se utiliza con fines de instalación, administración y mantenimiento. Este inicio de sesión no está asociado a ninguna instancia de.

Los operadores conectados mediante este inicio de sesión tendrán todos los derechos en todas las instancias. Este inicio de sesión no tendrá contraseña en el caso de una nueva instalación. Debe definir esta contraseña manualmente.

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

Los procesos de Adobe Campaign en el servidor están habilitados (y deshabilitados) mediante la variable **config-default.xml** y **`config-<instance>.xml`** archivos.

Para aplicar los cambios a estos archivos, si el servicio Adobe Campaign está iniciado, debe ejecutar el **nlserver config -reload** comando.

Existen dos tipos de procesos: instancia múltiple y instancia única.

* **de varias instancias**: se inicia un solo proceso para todas las instancias. Este es el caso de **web**, **syslogd** y **trackinglogd** procesos.

  La activación se puede configurar desde el **config-default.xml** archivo.

  Declarar un servidor de Adobe Campaign para acceder a las consolas de cliente y para redireccionarlas (seguimiento):

  ```
  vi nl6/conf/config-default.xml
  <web args="-tomcat" autoStart="true"/>  
  <!-- to start if the machine is also a redirection server -->  
  <trackinglogd autoStart="true"/>
  ```

  En este ejemplo, el archivo se edita mediante una **vi** en Linux. Se puede editar utilizando cualquier **.txt** o **.xml** editor.

* **monoinstancia**: se inicia un proceso para cada instancia (módulos: **mta**, **wfserver**, **inMail**, **sms** y **estadísticas**).

  La habilitación se puede configurar mediante el archivo de configuración de la instancia:

  ```
  config-<instance>.xml
  ```

  Declaración de un servidor para la entrega, ejecución de instancias de flujo de trabajo y recuperación del correo rechazado:

  ```
  <mta autoStart="true" statServerAddress="localhost"/>
  <wfserver autoStart="true"/>  
  <inMail autoStart="true"/>
  <stat autoStart="true"/>
  ```

**Almacenamiento de datos de Campaign**

Puede configurar el directorio de almacenamiento (**var** directorio) de datos de Adobe Campaign (registros, descargas, redirecciones, etc.). Para ello, utilice el **XTK_VAR_DIR** variable del sistema:

* En Windows, indique el siguiente valor en **XTK_VAR_DIR** variable del sistema

  ```
  D:\log\AdobeCampaign
  ```

* En Linux, vaya a **customer.sh** archivo e indicar: **export XTK_VAR_DIR=/app/log/AdobeCampaign**.

  Para obtener más información, consulte [Personalizar parámetros](../../installation/using/installing-packages-with-linux.md#personalizing-parameters).


## Seguridad y transmisiones dinámicas de páginas {#dynamic-page-security-and-relays}

De forma predeterminada, todas las páginas dinámicas se relacionan automáticamente con la variable **local** Servidor Tomcat del equipo cuyo módulo web se ha iniciado. Esta configuración se introduce en **`<url>`** de la configuración de retransmisión de consulta para **ServerConf.xml** archivo.

Puede retransmitir la ejecución de la página dinámica en un **remoto** servidor; si el módulo Web no está activado en el equipo. Para ello, debe reemplazar el **localhost** con el nombre del equipo remoto para JSP y JSSP, aplicaciones web, informes y cadenas.

Para obtener más información sobre los distintos parámetros disponibles, consulte la **serverConf.xml** archivo de configuración.

Para páginas JSP, la configuración predeterminada es:

```
<url relayHost="true" relayPath="true" targetUrl="http://localhost:8080" urlPath="*.jsp"/>
```

Adobe Campaign utiliza las siguientes páginas JSP:

* /nl/jsp/**soaprouter.jsp**: consola de cliente y conexiones de servicios web (API de SOAP),
* /nl/jsp/**m.jsp**: páginas espejo,
* /nl/jsp/**logon.jsp**: acceso basado en la web a los informes y a la implementación de la consola del cliente,
* /nl/jsp/**s.jsp** : Uso del marketing viral (patrocinio y redes sociales).

Los JSSP utilizados para el canal de aplicaciones móviles son los siguientes:

* nms/mobile/1/registerIOS.jssp
* nms/mobile/1/registerAndroid.jssp

**Ejemplo:**

Es posible evitar conexiones de equipos cliente desde el exterior. Para ello, simplemente limite la ejecución de **soaprouter.jsp** y solo autorizar la ejecución de páginas espejo, enlaces virales, formularios web y recursos públicos.

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

En este ejemplo, la variable **`<IP_addresses>`** El valor coincide con la lista de direcciones IP (separadas por comas) autorizadas a utilizar el módulo de retransmisión para esta máscara.

>[!NOTE]
>
>Los valores se adaptarán de acuerdo con su configuración y sus restricciones de red, especialmente si se han desarrollado configuraciones específicas para su instalación.

### Administrar encabezados HTTP {#managing-http-headers}

De forma predeterminada, no se retransmiten todos los encabezados HTTP. Puede agregar encabezados específicos en las respuestas enviadas por transmisión. Para ello, haga lo siguiente:

1. Vaya a la **serverConf.xml** archivo.
1. En el **`<relay>`** , vaya a la lista de encabezados HTTP retransmitidos.
1. Añadir un **`<responseheader>`** con los atributos siguientes:

   * **name**: nombre del encabezado
   * **valor**: nombre del valor.

   Por ejemplo:

   ```
   <responseHeader name="Strict-Transport-Security" value="max-age=16070400; includeSubDomains"/>
   ```

## Restringir comandos externos autorizados {#restricting-authorized-external-commands}

A partir de la versión 8780, los administradores técnicos pueden restringir la lista de comandos externos autorizados que se pueden utilizar en Adobe Campaign.

Para ello, debe crear un archivo de texto con la lista de comandos que desea evitar que utilice, por ejemplo:

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

En el **exec** del archivo de configuración del servidor, debe hacer referencia al archivo creado anteriormente en la **blacklistFile** atributo.

**Solo para Linux**: en el archivo de configuración del servidor, se recomienda especificar un usuario dedicado a ejecutar comandos externos para mejorar la configuración de seguridad. Este usuario se configura en la variable **exec** del archivo de configuración. Todos los parámetros disponibles en **serverConf.xml** se enumeran en esta [sección](../../installation/using/the-server-configuration-file.md).

>[!NOTE]
>
>Si no se especifica ningún usuario, todos los comandos se ejecutan en el contexto de usuario de la instancia de Adobe Campaign. El usuario debe ser diferente al usuario que ejecuta Adobe Campaign.

Por ejemplo:

```
<serverConf>
 <exec user="theUnixUser" blacklistFile="/pathtothefile/blacklist"/>
</serverConf>
```

Este usuario debe añadirse a la lista de usuarios del operador Adobe Campaign &quot;neolane&quot;.

>[!IMPORTANT]
>
>No debe utilizar un sudo personalizado. Es necesario instalar un sudo estándar en el sistema.


## Seguimiento redundante {#redundant-tracking}

Cuando se utilizan varios servidores para la redirección, deben poder comunicarse entre sí mediante llamadas SOAP para compartir información de las direcciones URL que se van a redirigir. En el momento del inicio de la entrega, es posible que no todos los servidores de redirección estén disponibles; por lo tanto, es posible que no tengan el mismo nivel de información.

>[!NOTE]
>
>Al utilizar la arquitectura estándar o empresarial, el servidor de aplicaciones principal debe estar autorizado para cargar la información de seguimiento en cada equipo.

Las direcciones URL de los servidores redundantes deben especificarse en la configuración de redirección a través de **serverConf.xml** archivo.

**Ejemplo:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

El **enableIf** La propiedad es opcional (vacía de forma predeterminada) y permite habilitar la conexión solo si el resultado es true. Esto permite obtener una configuración idéntica en todos los servidores de redirección.

Para obtener el nombre de host del equipo, ejecute el siguiente comando: **hostname -s**.



## Flujos de trabajo y afinidades de alta disponibilidad {#high-availability-workflows-and-affinities}

Puede configurar varios servidores de flujo de trabajo (wfserver) y distribuirlos en dos o más equipos. Si elige este tipo de arquitectura, configure el modo de conexión de los equilibradores de carga según el acceso de Adobe Campaign.

Para acceder desde la web, seleccione la **equilibrador de carga** para limitar los tiempos de conexión.

Si accede a a través de la consola de Adobe Campaign, elija **hash** o **ip adhesiva** modo. Esto permite mantener la conexión entre el cliente enriquecido y el servidor e impedir que una sesión de usuario se interrumpa durante una operación de importación o exportación, por ejemplo.

Puede optar por forzar la ejecución de un flujo de trabajo o una actividad de flujo de trabajo en un equipo concreto. Para ello, debe definir una o más afinidades para el flujo de trabajo o actividad correspondiente.

1. Cree las afinidades del flujo de trabajo o actividad introduciéndolas en la variable **[!UICONTROL Affinity]** field.

   Puede elegir cualquier nombre de afinidad, pero asegúrese de no utilizar espacios ni signos de puntuación. Si utiliza servidores diferentes, especifique nombres diferentes.

   ![](assets/s_ncs_install_server_wf_affinity01.png)

   ![](assets/s_ncs_install_server_wf_affinity02.png)

   La lista desplegable contiene las afinidades utilizadas anteriormente. Se completa con el tiempo con los diferentes valores introducidos.

1. Abra el **nl6/conf/config-`<instance>.xml`** archivo.
1. Modifique la línea que coincide con el **[!UICONTROL wfserver]** como sigue:

   ```
   <wfserver autoStart="true" affinity="XXX,"/>
   ```

   Si define varias afinidades, deben separarse con comas sin espacios:

   ```
   <wfserver autoStart="true" affinity="XXX,YYY,"/>
   ```

   La coma que sigue al nombre de la afinidad es necesaria para la ejecución de flujos de trabajo para los que no se define ninguna afinidad.

   Si desea ejecutar únicamente flujos de trabajo para los que se ha definido una afinidad, no añada una coma al final de la lista de afinidades. Por ejemplo, modifique la línea de la siguiente manera:

   ```
   <wfserver autoStart="true" affinity="XXX"/>
   ```

## Reinicio automático {#automatic-process-restart}

De forma predeterminada, los diferentes procesos de Adobe Campaign se reinician automáticamente a las 6 a. m. (hora del servidor) todos los días.

Sin embargo, puede cambiar esta configuración.

Para ello, vaya a la **serverConf.xml** , ubicado en el **conf** repositorio de la instalación.

Cada proceso configurado en este archivo tiene un **processRestartTime** atributo. Puede modificar el valor de este atributo para adaptar el tiempo de reinicio de cada proceso según sus necesidades.

>[!IMPORTANT]
>
>No elimine este atributo. Todos los procesos deben reiniciarse todos los días.
