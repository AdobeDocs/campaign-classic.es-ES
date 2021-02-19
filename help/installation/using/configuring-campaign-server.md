---
solution: Campaign Classic
product: campaign
title: Configuración del servidor de Campaign
description: Configuración del servidor de Campaign
audience: installation
content-type: reference
topic-tags: additional-configurations
translation-type: tm+mt
source-git-commit: 6d0ae3d597f9ee30515437d94901cb034d0ca3d5
workflow-type: tm+mt
source-wordcount: '3600'
ht-degree: 4%

---


# Configuración del servidor de Campaign{#configuring-campaign-server}

La sección siguiente detalla las configuraciones del lado del servidor que se pueden realizar para satisfacer sus necesidades y las características específicas de su entorno.

>[!IMPORTANT]
>
>Estas configuraciones deben ser realizadas por administradores y sólo para **modelos de alojamiento local**.
>
>Para implementaciones **alojadas**, la configuración del lado del servidor se puede configurar únicamente mediante Adobe. Sin embargo, algunos ajustes se pueden configurar dentro del Panel de control de Campaign (por ejemplo, administración de listas de permitidos IP o permisos de URL).

Para obtener más información, consulte estas secciones:

* [Documentación del Panel de control](https://docs.adobe.com/content/help/es-ES/control-panel/using/control-panel-home.html)
* [Modelos de alojamiento](../../installation/using/hosting-models.md)
* [Matriz de Campaign Classic in situ y capacidad alojada](../../installation/using/capability-matrix.md)
* [Pasos de configuración de modelos híbridos y alojados](../../installation/using/hosting-models.md)

Los archivos de configuración del Campaign Classic se almacenan en la carpeta **conf** de la carpeta de instalación de Adobe Campaign. La configuración se distribuye en dos archivos:

* **serverConf.xml**: configuración general para todas las instancias. Este archivo combina los parámetros técnicos del servidor de Adobe Campaign: todas las instancias las comparten. La descripción de algunos de estos parámetros se detalla a continuación. Los diferentes nodos y parámetros que se enumeran en esta [sección](../../installation/using/the-server-configuration-file.md).
* **config-`<instance>`.xml** (donde  **** instanceis es el nombre de la instancia): configuración específica de la instancia. Si comparte el servidor entre varias instancias, introduzca los parámetros específicos de cada instancia en el archivo correspondiente.

## Definición de zonas de seguridad {#defining-security-zones}

### Acerca de las zonas de seguridad {#about-security-zones}

Cada operador debe estar vinculado a una zona para iniciar sesión en una instancia y la IP del operador debe incluirse en las direcciones o conjuntos de direcciones definidos en la zona de seguridad. La configuración de la zona de seguridad se realiza en el archivo de configuración del servidor de Adobe Campaign.

Los operadores están vinculados a una zona de seguridad desde su perfil en el nodo de la consola ( **[!UICONTROL Administration > Access management > Operators]**). Descubra cómo vincular las zonas a los operadores de Campaña en [esta sección](#linking-a-security-zone-to-an-operator).

### Creación de zonas de seguridad {#creating-security-zones}

Una zona está definida por:

* uno o más intervalos de direcciones IP (IPv4 e IPv6)
* un nombre técnico vinculado a cada rango de direcciones IP

Las zonas de seguridad están interbloqueadas, lo que significa que la definición de una nueva zona dentro de otra zona reduce el número de operadores que pueden iniciar sesión en ella mientras aumentan los derechos asignados a cada operador.

Las zonas deben definirse durante la configuración del servidor, en el archivo **serverConf.xml**. Todos los parámetros disponibles en **serverConf.xml** se enumeran en esta [sección](../../installation/using/the-server-configuration-file.md).

Cada zona define derechos, como:

* Conexión HTTP en lugar de HTTPS
* Visualización de errores (errores de Java, JavaScript, C++, etc.)
* Previsualización de informes y aplicaciones web
* Autenticación mediante inicio de sesión y contraseña
* Modo de conexión no segura

>[!NOTE]
>
>**Cada operador debe estar vinculado a una zona**. Si la dirección IP del operador pertenece al rango definido por la zona, el operador puede iniciar sesión en la instancia.\
>La dirección IP del operador puede definirse en varias zonas. En este caso, el operador recibe el **conjunto** de derechos disponibles para cada zona.

El archivo predeterminado **serverConf.xml** incluye tres zonas: **public, VPN y LAN**.

>[!NOTE]
>
>**La configuración predeterminada es segura**. Sin embargo, antes de migrar desde una versión anterior de Adobe Campaign, puede que sea necesario reducir temporalmente la seguridad para migrar y aprobar las nuevas reglas.

Ejemplo de cómo definir una zona en el archivo **serverConf.xml**:

```
<securityZone allowDebug="false" allowHTTP="false" label="Public Network" name="public">
<subNetwork label="All addresses" mask="*" name="all"/>

<securityZone allowDebug="true" allowHTTP="false" label="Private Network (VPN)"
              name="vpn" showErrors="true">

  <securityZone allowDebug="true" allowEmptyPassword="true" allowHTTP="true"
                allowUserPassword="false" label="Private Network (LAN)" name="lan"
                sessionTokenOnly="true" showErrors="true">
    <subNetwork label="Lan 1" mask="192.168.0.0/16" name="lan1"/>
    <subNetwork label="Lan 2" mask="172.16.0.0/12" name="lan2"/>
    <subNetwork label="Lan 3" mask="10.0.0.0/8" name="lan3"/>
    <subNetwork label="Localhost" mask="127.0.0.1/16" name="locahost"/>
    <subNetwork label="Lan (IPv6)" mask="fc00::/7" name="lan6"/>
    <subNetwork label="Localhost (IPv6)" mask="::1/128" name="localhost6"/>
  </securityZone>

</securityZone>
</securityZone>
```

Todos los derechos que definen una zona son los siguientes:

* **allowDebug**: habilita la ejecución de una aplicación web en modo &quot;debug&quot;
* **allowEmptyPassword**: autoriza una conexión a una instancia sin contraseña
* **allowHTTP**: se puede crear una sesión sin utilizar el protocolo HTTPS
* **allowUserPassword**: el token de sesión puede tener el siguiente formulario &quot;`<login>/<password>`&quot;
* **sessionTokenOnly**: no se requiere el token de seguridad en la dirección URL de conexión
* **showErrors**: los errores del lado del servidor se reenvían y muestran

>[!IMPORTANT]
>
>En una definición de zona, cada atributo con el valor **true** reduce la seguridad.

Al utilizar el Centro de mensajes, si hay varias instancias de ejecución, debe crear una zona de seguridad adicional con el atributo **sessionTokenOnly** definido como **true**, donde sólo se añadirán las direcciones IP necesarias. Para obtener más información sobre la configuración de instancias, consulte [este documento](../../message-center/using/creating-a-shared-connection.md).

### Prácticas recomendadas para zonas de seguridad {#best-practices-for-security-zones}

En la definición de la zona de seguridad **lan**, es posible agregar una máscara de dirección IP que defina el acceso técnico. Este complemento habilitará el acceso a todas las instancias alojadas en el servidor.

```
<securityZone allowDebug="true" allowEmptyPassword="false" allowHTTP="true"
                    allowUserPassword="false" label="Private Network (LAN)" name="lan"
                    sessionTokenOnly="true" showErrors="true">
        <subNetwork label="Lan 1" mask="192.168.0.0/16" name="lan1"/>
        <subNetwork label="Lan 2" mask="172.16.0.0/12" name="lan2"/>
        <subNetwork label="Lan 3" mask="10.0.0.0/8" name="lan3"/>
        <subNetwork label="Localhost" mask="127.0.0.1/16" name="locahost"/>
        <subNetwork label="Lan (IPv6)" mask="fc00::/7" name="lan6"/>
        <subNetwork label="Localhost (IPv6)" mask="::1/128" name="localhost6"/>
  
        <!-- Customer internal IPs -->
        <subNetwork id="internalNetwork" mask="a.b.c.d/xx"/>

      </securityZone>
```

Se recomienda definir los intervalos de direcciones IP directamente en el archivo de configuración dedicado a la instancia para los operadores que solo acceden a una instancia específica.

En el archivo **`config-<instance>.xml`**:

```
  <securityZone name="public">
   ...
    <securityZone name="vpn">
      <subNetwork id="cus1" mask="a.b.c.d/xx"/>
```

### Subredes y proxies en una zona de seguridad {#sub-networks-and-proxies-in-a-security-zone}

El parámetro **proxy** se puede utilizar en un elemento **subNetwork** para especificar el uso del proxy en una zona de seguridad.

Cuando se hace referencia a un proxy y se introduce una conexión mediante este proxy (visible mediante el encabezado HTTP X-Forwarded-For), la zona verificada es la de los clientes del proxy y no la del proxy.

>[!IMPORTANT]
>
>Si se configura un proxy y es posible ignorarlo (o si no existe), la dirección IP que se probará será falsificada.
>
>Además, los relés ahora se generan como proxies. Por lo tanto, puede agregar la dirección IP 127.0.0.1 a la lista de proxies en la configuración de la zona de seguridad.
>
>Por ejemplo: &quot; `<subnetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" proxy="127.0.0.1,10.100.2.135" />`&quot;.

Pueden producirse varios casos:

* En la zona de seguridad se hace referencia directa a una subred y no se configura ningún proxy: los usuarios de la subred pueden conectarse directamente al servidor de Adobe Campaign.

   ![](assets/8101_proxy1.png)

* Se ha especificado un proxy para una subred en la zona de seguridad: los usuarios de esta subred pueden acceder al servidor de Adobe Campaign a través de este proxy.

   ![](assets/8101_proxy2.png)

* Un proxy se incluye en una subred de zona de seguridad: los usuarios que tengan acceso a través de este proxy, independientemente de su origen, pueden acceder al servidor de Adobe Campaign.

   ![](assets/8101_proxy3.png)

Las direcciones IP de los proxies que probablemente tengan acceso al servidor de Adobe Campaign deben ingresarse en la **`<subnetwork>`** red de  concernida y en la subred de primer nivel **`<subnetwork name="all"/>`**. Por ejemplo, aquí para un proxy cuya dirección IP es 10.131.146.102:

```
<securityZone allowDebug="false" allowHTTP="false" label="Public Network" 
                      name="public">
    <subNetwork label="All addresses" mask="*" name="all"
                      proxy="10.131.146.102,127.0.0.1, ::1"/>

    <securityZone allowDebug="true" allowHTTP="false" label="Private Network (VPN)" 
                      name="vpn" showErrors="true">
        <securityZone allowDebug="true" allowEmptyPassword="false" allowHTTP="true" 
                      allowUserPassword="false" label="Private Network (LAN)" 
                      name="lan" sessionTokenOnly="true" showErrors="true">
            <subNetwork label="Lan proxy" mask="10.131.193.182" name="lan3" 
                      proxy="10.131.146.102,127.0.0.1, ::1"/>
            <subNetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" 
                      proxy="127.0.0.1, ::1"/>

        </securityZone>
    </securityZone>
</securityZone>
```

### Vinculación de una zona de seguridad a un operador {#linking-a-security-zone-to-an-operator}

Una vez definidas las zonas, cada operador debe estar vinculado a uno de ellos para poder iniciar sesión en una instancia y la dirección IP del operador debe incluirse en las direcciones o el rango de direcciones a las que se hace referencia en la zona.

La configuración técnica de las zonas se realiza en el fichero de configuración del servidor de Campaña: **serverConf.xml**.

Antes de esto, debe configurar la lista desglosada predeterminada **[!UICONTROL Security zone]** para vincular una etiqueta al nombre interno de la zona definida en el archivo **serverConf.xml**.

Esta configuración se realiza en el explorador de Campañas:

1. Haga clic en el nodo **[!UICONTROL Administration > Platform > Enumerations]**.
1. Seleccione la lista desglosada del sistema **[!UICONTROL Security zone (securityZone)]**.

   ![](assets/enum_securityzone.png)

1. Para cada zona de seguridad definida en el archivo de configuración del servidor, haga clic en el botón **[!UICONTROL Add]**.
1. En el campo **[!UICONTROL Internal name]**, introduzca el nombre de la zona definida en el archivo **serverConf.xml**. Corresponde al atributo **@name** del elemento `<securityzone>`. Escriba la etiqueta vinculada al nombre interno en el campo **Etiqueta**.

   ![](assets/enum_addsecurityvalue.png)

1. Haga clic en Aceptar y guarde las modificaciones.

Una vez definidas las zonas y configurada la lista desglosada **[!UICONTROL Security zone]**, deberá vincular cada operador a una zona de seguridad:

1. Haga clic en el nodo **[!UICONTROL Administration > Access management > Operators]**.
1. Seleccione el operador al que desea vincular una zona de seguridad y haga clic en la ficha **[!UICONTROL Edit]**.
1. Vaya a la ficha **[!UICONTROL Access rights]** y haga clic en el vínculo **[!UICONTROL Edit access parameters...]**.

   ![](assets/zone_operator.png)

1. Seleccione una zona en la lista desplegable **[!UICONTROL Authorized connection zone]**

   ![](assets/zone_operator_selection.png)

1. Haga clic en **[!UICONTROL OK]** y guarde las modificaciones para aplicar estos cambios.

## Configuración de Tomcat {#configuring-tomcat}

### Puerto predeterminado para Tomcat {#default-port-for-tomcat}

Cuando el puerto de escucha 8080 del servidor Tomcat ya está ocupado con otra aplicación necesaria para la configuración, debe reemplazar el puerto 8080 por uno gratuito (por ejemplo, 8090). Para cambiarlo, edite el archivo **server.xml** guardado en el directorio **/tomcat-8/conf** de la carpeta de instalación de Adobe Campaign.

A continuación, modifique el puerto de las páginas de retransmisión JSP. Para ello, cambie el archivo **serverConf.xml** guardado en el directorio **/conf** del directorio de instalación de Adobe Campaign. Todos los parámetros disponibles en **serverConf.xml** se enumeran en esta [sección](../../installation/using/the-server-configuration-file.md).

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

### Asignación de una carpeta en Tomcat {#mapping-a-folder-in-tomcat}

Para definir la configuración específica del cliente, puede crear un archivo **user_contextos.xml** en la carpeta **/tomcat-8/conf**, que también contiene el archivo **contextos.xml**.

Este archivo contendrá el siguiente tipo de información:

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

Si es necesario, esta operación se puede reproducir en el servidor.

## Personalización de parámetros de envío {#personalizing-delivery-parameters}

Los parámetros de envío se definen en el archivo de configuración **serverConf.xml**. Todos los parámetros disponibles en **serverConf.xml** se enumeran en esta [sección](../../installation/using/the-server-configuration-file.md).

Los comandos y la configuración general del servidor se detallan en [configuración del servidor de Campaña](../../installation/using/campaign-server-configuration.md).

También puede realizar las siguientes configuraciones en función de sus necesidades y configuración.

### Relé SMTP {#smtp-relay}

El módulo MTA actúa como agente de transferencia de correo nativo para la retransmisión SMTP (puerto 25).

Sin embargo, es posible reemplazarlo por un servidor de retransmisión si su política de seguridad lo requiere. En ese caso, el rendimiento global será el de transmisión (siempre que el rendimiento del servidor de transmisión sea inferior al de Adobe Campaign).

En este caso, estos parámetros se establecen configurando el servidor SMTP en la sección **`<relay>`**. Debe especificar la dirección IP (o el host) del servidor SMTP utilizado para transferir el correo y su puerto asociado (25 de forma predeterminada).

```
<relay address="192.0.0.3" port="25"/>
```

>[!IMPORTANT]
>
>Este modo operativo implica serias limitaciones en los envíos, ya que puede reducir considerablemente el rendimiento debido a las prestaciones intrínsecas del servidor de transmisión (latencia, ancho de banda...). Además, la capacidad para calificar los errores de envío sincrónicos (detectados mediante el análisis del tráfico SMTP) será limitada y el envío no será posible si el servidor de retransmisión no está disponible.

### Procesos secundarios de MTA {#mta-child-processes}

Es posible controlar la población de procesos secundarios (maxSpareServers de forma predeterminada 2) para optimizar el rendimiento de difusión según la potencia de CPU de los servidores y los recursos de red disponibles. Esta configuración se debe realizar en la sección **`<master>`** de la configuración de MTA en cada equipo individual.

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

Consulte también [Optimización del envío de correo electrónico](../../installation/using/email-deliverability.md#email-sending-optimization).

### Administración del tráfico SMTP saliente con afinidades {#managing-outbound-smtp-traffic-with-affinities}

>[!IMPORTANT]
>
>La configuración de la afinidad debe ser coherente de un servidor a otro. Le recomendamos que se ponga en contacto con Adobe para la configuración de afinidad, ya que los cambios de configuración deben replicarse en todos los servidores de aplicaciones que ejecutan MTA.

Puede mejorar el tráfico SMTP saliente mediante afinidades con direcciones IP.

Para ello, siga los siguientes pasos:

1. Introduzca las afinidades en la sección **`<ipaffinity>`** del archivo **serverConf.xml**.

   Una afinidad puede tener varios nombres diferentes: para separarlos, utilice el carácter **;**.

   Ejemplo:

   ```
    IPAffinity name="mid.Server;WWserver;local.Server">
             <IP address="XX.XXX.XX.XX" heloHost="myserver.us.campaign.net" publicId="123" excludeDomains="neo.*" weight="5"/
   ```

   Para realizar la vista de los parámetros relevantes, consulte el archivo **serverConf.xml**.

1. Para habilitar la selección de afinidades en las listas desplegables, debe agregar los nombres de afinidades en la lista desglosada **IPAffinity**.

   ![](assets/ipaffinity_enum.png)

   >[!NOTE]
   >
   >Las listas desglosadas se detallan en [este documento](../../platform/using/managing-enumerations.md).

   A continuación, puede seleccionar la afinidad que se va a utilizar, como se muestra a continuación para las tipologías:

   ![](assets/ipaffinity_typology.png)

   >[!NOTE]
   >
   >También puede hacer referencia a [configuración del servidor de Envío](../../installation/using/email-deliverability.md#delivery-server-configuration).

## Permisos de URL {#url-permissions}

La lista predeterminada de direcciones URL a las que pueden llamar los códigos JavaScript (flujos de trabajo, etc.) a través de instancias de Campaign Classic es limitada. Son direcciones URL que permiten que las instancias funcionen correctamente.

De forma predeterminada, las instancias no pueden conectarse a direcciones URL externas. Sin embargo, es posible agregar algunas direcciones URL externas a la lista de direcciones URL autorizadas para que la instancia pueda conectarse a ellas. Esto le permite conectar las instancias de Campaign a sistemas externos como, por ejemplo, servidores SFTP o sitios web para habilitar la transferencia de datos o archivos.

Una vez añadida una URL, se hace referencia a ella en el archivo de configuración de la instancia (serverConf.xml).

La forma en que puede administrar los permisos de URL depende del modelo de alojamiento:

* **** Hibridor  **in situ**: agregue las direcciones URL para permitir en el  **archivo** serverConf.xml. La información detallada se encuentra disponible en la sección siguiente.
* **Alojado**: agregue las direcciones URL para permitir mediante el  **Panel de control de Campaign**. Para obtener más información, consulte la [documentación especializada](https://docs.adobe.com/content/help/es-ES/control-panel/using/instances-settings/url-permissions.html).

Con los modelos de alojamiento **híbridos** y **locales**, el administrador debe hacer referencia a un nuevo **urlPermission** en el archivo **serverConf.xml**. Todos los parámetros disponibles en **serverConf.xml** se enumeran en esta [sección](../../installation/using/the-server-configuration-file.md).

Existen tres modos de protección de conexión:

* **Bloqueo**: todas las direcciones URL que no pertenecen a la lista de permitidos están bloqueadas, con un mensaje de error. Es el modo predeterminado después de una posactualización.
* **Permiso**: se permiten todas las direcciones URL que no pertenecen a la lista de permitidos.
* **Advertencia**: se permiten todas las direcciones URL que no pertenecen a la lista de permitidos, pero el intérprete de JS emite una advertencia para que el administrador pueda recopilarlas. Este modo agrega mensajes de advertencia JST-310027.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!IMPORTANT]
>
>De forma predeterminada, el cliente de nuevos clientes utiliza el **modo de bloqueo**. Si necesitan permitir una nueva dirección URL, deben ponerse en contacto con el administrador para agregarla a la lista de permitidos.
>
>Los clientes existentes que provienen de una migración pueden utilizar el **modo de advertencia** durante un tiempo. Mientras tanto, deben analizar el tráfico saliente antes de autorizar las direcciones URL. Una vez definida la lista de las direcciones URL autorizadas, deben ponerse en contacto con el administrador para agregar las direcciones URL a la lista de permitidos y activar el **modo de bloqueo**.

## Seguridad de página dinámica y relevos {#dynamic-page-security-and-relays}

De forma predeterminada, todas las páginas dinámicas se relacionan automáticamente con el servidor **local** Tomcat del equipo cuyo módulo Web se ha iniciado. Esta configuración se introduce en la sección **`<url>`** de la configuración del relé de consulta para el archivo **ServerConf.xml**. Todos los parámetros disponibles en **serverConf.xml** se enumeran en esta [sección](../../installation/using/the-server-configuration-file.md).

Para retransmitir la ejecución de la página dinámica en un servidor **remoto**; si el módulo Web no está activado en el equipo. Para ello, debe reemplazar el **host local** por el nombre del equipo remoto para JSP y JSSP, Aplicaciones web, informes y cadenas.

Para obtener más información sobre los distintos parámetros disponibles, consulte el archivo de configuración **serverConf.xml**.

Para las páginas JSP, la configuración predeterminada es:

```
<url relayHost="true" relayPath="true" targetUrl="http://localhost:8080" urlPath="*.jsp"/>
```

Adobe Campaign utiliza las siguientes páginas JSP:

* /nl/jsp/**soaprouter.jsp**: conexiones de consola de cliente y servicios Web (API de SOAP),
* /nl/jsp/**m.jsp**: páginas espejo,
* /nl/jsp/**login.jsp**: Acceso basado en la Web a los informes y a la implementación de la consola del cliente,
* /nl/jsp/**s.jsp**: Usando mercadotecnia viral (patrocinio y redes sociales).

Los JSSP utilizados para el Canal de aplicaciones móviles son los siguientes:

* nms/mobile/1/registerIOS.jssp
* nms/mobile/1/registerAndroid.jssp

**Ejemplo:**

Es posible evitar las conexiones de equipos cliente desde el exterior. Para ello, simplemente restrinja la ejecución de **soaprouter.jsp** y autorice la ejecución de páginas espejo, enlaces virales, formularios Web y recursos públicos.

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

## Restricción de comandos externos autorizados {#restricting-authorized-external-commands}

>[!NOTE]
>
>La siguiente configuración sólo es necesaria para instalaciones in situ.

Desde la compilación 8780, los administradores técnicos pueden restringir la lista de comandos externos autorizados que se pueden utilizar en Adobe Campaign.

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

**Sólo** para Linux: en el archivo de configuración del servidor, le recomendamos que especifique un usuario dedicado a ejecutar comandos externos para mejorar la configuración de seguridad. Este usuario se establece en el nodo **exec** del archivo de configuración. Todos los parámetros disponibles en **serverConf.xml** se enumeran en esta [sección](../../installation/using/the-server-configuration-file.md).

>[!NOTE]
>
>Si no se especifica ningún usuario, todos los comandos se ejecutan en el contexto de usuario de la instancia de Adobe Campaign. El usuario debe ser distinto del usuario que ejecuta Adobe Campaign.

Por ejemplo:

```
<serverConf>
 <exec user="theUnixUser" blacklistFile="/pathtothefile/blacklist"/>
</serverConf>
```

Este usuario debe agregarse a la lista de superusuario del operador &quot;neolane&quot; de Adobe Campaign.

>[!IMPORTANT]
>
>No debe usar un sudo personalizado. Es necesario instalar un sudo estándar en el sistema.

## Administración de encabezados HTTP {#managing-http-headers}

De forma predeterminada, no se retransmiten todos los encabezados HTTP. Puede agregar encabezados específicos en las respuestas enviadas por retransmisión. Para ello:

1. Vaya al archivo **serverConf.xml**. Todos los parámetros disponibles en **serverConf.xml** se enumeran en esta [sección](../../installation/using/the-server-configuration-file.md).
1. En el nodo **`<relay>`**, vaya a la lista de encabezados HTTP reenviados.
1. Añada un elemento **`<responseheader>`** con los atributos siguientes:

   * **name**: nombre del encabezado
   * **value**: nombre del valor.

   Por ejemplo:

   ```
   <responseHeader name="Strict-Transport-Security" value="max-age=16070400; includeSubDomains"/>
   ```

## Seguimiento redundante {#redundant-tracking}

Cuando se utilizan varios servidores para la redirección, deben poder comunicarse entre sí a través de llamadas SOAP para compartir información de las direcciones URL que se van a redirigir. En el momento del inicio del envío, es posible que no todos los servidores de redirección estén disponibles; por lo tanto, es posible que no tengan el mismo nivel de información.

>[!NOTE]
>
>Cuando se utiliza la arquitectura estándar o empresarial, se debe autorizar al servidor de aplicaciones principal para que cargue información de seguimiento en cada equipo.

Las direcciones URL de los servidores redundantes deben especificarse en la configuración de redirección, mediante el archivo **serverConf.xml**. Todos los parámetros disponibles en **serverConf.xml** se enumeran en esta [sección](../../installation/using/the-server-configuration-file.md).

**Ejemplo:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

La propiedad **enableIf** es opcional (está vacía de forma predeterminada) y le permite habilitar la conexión sólo si el resultado es true; Esto le permite obtener una configuración idéntica en todos los servidores de redirección.

Para obtener el nombre de host del equipo, ejecute el siguiente comando: **hostname -s**.

## Administración de recursos públicos {#managing-public-resources}

Los recursos públicos se presentan en [Administración de recursos públicos](../../installation/using/deploying-an-instance.md#managing-public-resources).

Se almacenan en el directorio **/var/res/instance** del directorio de instalación de Adobe Campaign.

La dirección URL coincidente es: **http://server/res/instance** donde **instance** es el nombre de la instancia de seguimiento.

Puede especificar otro directorio agregando un nodo al archivo **conf-`<instance>`.xml** para configurar el almacenamiento en el servidor. Esto significa agregar las siguientes líneas:

```
<serverconf>
  <shared>
    <dataStore hosts="media*" lang="fra">
      <virtualDir name="images" path="/var/www/images"/>
     <virtualDir name="publicFileRes" path="$(XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)/"/>
    </dataStore>
  </shared>
</serverconf>
```

En este caso, la nueva dirección URL de los recursos públicos proporcionados en la parte superior de la ventana del asistente de implementación debe apuntar a esta carpeta.

## Flujos de trabajo y afinidades de alta disponibilidad {#high-availability-workflows-and-affinities}

Puede configurar varios servidores de flujo de trabajo (wfserver) y distribuirlos en dos o más equipos. Si elige este tipo de arquitectura, configure el modo de conexión de los equilibradores de carga según el acceso de Adobe Campaign.

Para obtener acceso desde la Web, seleccione el modo **equilibrador de carga** para limitar los tiempos de conexión.

Si accede a través de la consola de Adobe Campaign, elija el modo **hash** o **ip adhesivo**. Esto le permite mantener la conexión entre el cliente enriquecido y el servidor y evitar que una sesión de usuario se interrumpa durante una operación de importación o exportación, por ejemplo.

Puede elegir forzar la ejecución de un flujo de trabajo o una actividad de flujo de trabajo en un equipo concreto. Para ello, debe definir una o varias afinidades para el flujo de trabajo o la actividad correspondiente.

1. Cree las afinidades del flujo de trabajo o la actividad ingresándolas en el campo **[!UICONTROL Affinity]**.

   Puede elegir libremente los nombres de las afinidades. Sin embargo, asegúrese de que no utiliza espacios ni signos de puntuación. Si utiliza diferentes servidores, especifique nombres diferentes.

   ![](assets/s_ncs_install_server_wf_affinity01.png)

   ![](assets/s_ncs_install_server_wf_affinity02.png)

   La lista desplegable contiene afinidades que antes se usaban. Se completa con el tiempo con los diferentes valores introducidos.

1. Abra el archivo **nl6/conf/config-`<instance>.xml`**.
1. Modifique la línea que coincide con el módulo **[!UICONTROL wfserver]** de la siguiente manera:

   ```
   <wfserver autoStart="true" affinity="XXX,"/>
   ```

   Si define varias afinidades, deben separarse con comas sin espacios:

   ```
   <wfserver autoStart="true" affinity="XXX,YYY,"/>
   ```

   La coma que sigue al nombre de la afinidad es necesaria para la ejecución de flujos de trabajo para los que no se ha definido ninguna afinidad.

   Si desea ejecutar solo flujos de trabajo para los que se ha definido una afinidad, no agregue una coma al final de la lista de sus afinidades. Por ejemplo, modifique la línea de la siguiente manera:

   ```
   <wfserver autoStart="true" affinity="XXX"/>
   ```

## Reinicio automático del proceso {#automatic-process-restart}

De forma predeterminada, los diferentes procesos de Adobe Campaign se reinician automáticamente a las 6 de la mañana (hora del servidor) todos los días.

Sin embargo, puede cambiar esta configuración.

Para ello, vaya al archivo **serverConf.xml**, ubicado en el repositorio **conf** de la instalación. Todos los parámetros disponibles en **serverConf.xml** se enumeran en esta [sección](../../installation/using/the-server-configuration-file.md).

Cada proceso configurado en este archivo tiene un atributo **processRestartTime**. Puede modificar el valor de este atributo para adaptar el tiempo de reinicio de cada proceso según sus necesidades.

>[!IMPORTANT]
>
>No elimine este atributo. Todos los procesos deben reiniciarse todos los días.

## Limitación de archivos cargables {#limiting-uploadable-files}

Un nuevo atributo **uploadWhiteList** permite restringir los tipos de archivo disponibles para la carga en el servidor de Adobe Campaign.

Este atributo está disponible dentro del elemento **dataStore** del archivo **serverConf.xml**. Todos los parámetros disponibles en **serverConf.xml** se enumeran en esta [sección](../../installation/using/the-server-configuration-file.md).

El valor predeterminado de este atributo es **.+** y le permite cargar cualquier tipo de archivo.

Para limitar los posibles formatos, debe reemplazar el valor de atributo por una expresión regular de java válida. Puede introducir varios valores separándolos con una coma.

Por ejemplo: **uploadWhiteList=&quot;.*.png,.*.jpg&quot;** le permitirá cargar formatos PNG y JPG en el servidor. No se aceptarán otros formatos.

>[!IMPORTANT]
>
>En Internet Explorer, la ruta completa del archivo debe ser verificada por la expresión regular.

## Configuración de conexión proxy {#proxy-connection-configuration}

Puede conectar el servidor de Campaña a un sistema externo a través de un proxy, utilizando, por ejemplo, una actividad de flujo de trabajo **File Transfer**. Para lograrlo, debe configurar la sección **proxyConfig** del archivo **serverConf.xml** mediante un comando específico. Todos los parámetros disponibles en **serverConf.xml** se enumeran en esta [sección](../../installation/using/the-server-configuration-file.md).

Las siguientes conexiones proxy son posibles: HTTP, HTTPS, FTP, SFTP. Tenga en cuenta que, a partir de la versión de Campaña 20.2, los parámetros de protocolo HTTP y HTTPS ya no están **disponibles**. Estos parámetros aún se mencionan a continuación, ya que siguen estando disponibles en las compilaciones anteriores, incluido 9032.

>[!CAUTION]
>
>Solo se admite el modo de autenticación básico. No se admite la autenticación NTLM.
>
>No se admiten los proxies SOCKS.


Puede utilizar el siguiente comando:

```
nlserver config -setproxy:[protocol]/[serverIP]:[port]/[login][:‘https’|'http’]
```

los parámetros de protocolo pueden ser ‘http’, ‘https’ o ‘ftp’.

Si está configurando FTP en el mismo puerto que el tráfico HTTP/HTTPS, puede utilizar lo siguiente:

```
nlserver config -setproxy:http/198.51.100.0:8080/user
```

Las opciones ‘http’ y ‘https’ solo se utilizan cuando el parámetro de protocolo es ‘ftp’ e indican si la tunelización en el puerto especificado se realizará a través de HTTPS o HTTP.

Si utiliza diferentes puertos para el tráfico FTP/SFTP y HTTP/HTTPS a través del servidor proxy, debe establecer el parámetro de protocolo ‘ftp’.


Por ejemplo:

```
nlserver config -setproxy:ftp/198.51.100.0:8080/user:’http’
```

A continuación, introduzca la contraseña.

Las conexiones HTTP están definidas en el parámetro proxyHTTP:

```
<proxyConfig enabled=“1” override=“localhost*” useSingleProxy=“0”>
<proxyHTTP address=“198.51.100.0" login=“user” password=“*******” port=“8080”/>
</proxyConfig>
```

Las conexiones HTTPS se definen en el parámetro proxyHTTPS:

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyHTTPS address=“198.51.100.0” login=“user” password=“******” port=“8080"/>
</proxyConfig>
```

Las conexiones FTP/FTPS se definen en el parámetro proxyFTP:

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyFTP address=“198.51.100.0” login=“user” password=“******” port=“5555" https=”true”/>
</proxyConfig>
```

Si utiliza el mismo proxy para varios tipos de conexión, solo el proxyHTTP se definirá con useSingleProxy establecido en &quot;1&quot; o &quot;true&quot;.

Si tiene conexiones internas que deben pasar por el proxy, agréguelas en el parámetro override.

Si desea deshabilitar temporalmente la conexión proxy, establezca el parámetro enabled en &quot;false&quot; o &quot;0&quot;.
