---
product: campaign
title: Configuración de zonas de seguridad
description: Obtenga información sobre cómo configurar zonas de seguridad
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
badge-v7-prem: label="on-premise e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 67dda58f-97d1-4df5-9648-5f8a1453b814
source-git-commit: a94c361c5bdd9d61ae9232224af910a78245a889
workflow-type: tm+mt
source-wordcount: '1475'
ht-degree: 3%

---

# Definición de zonas de seguridad (locales){#defining-security-zones}



Cada operador debe estar vinculado a una zona para iniciar sesión en una instancia y la IP del operador debe incluirse en las direcciones o conjuntos de direcciones definidos en la zona de seguridad. La configuración de la zona de seguridad se realiza en el archivo de configuración del servidor de Adobe Campaign.

Los operadores están vinculados a una zona de seguridad desde su perfil en la consola, a la que se puede acceder desde el **[!UICONTROL Administration > Access management > Operators]** nodo. [Más información](#linking-a-security-zone-to-an-operator).

>[!NOTE]
>
>Este procedimiento está restringido a **on-premise** implementaciones.
>
>As a **alojado** cliente, si puede acceder a [Panel de control de Campaign de campaña](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=es), puede utilizar la interfaz de autoservicio Zona de seguridad. [Más información](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html?lang=es)
>
>Otros **híbrido/alojado** Los clientes de deberán ponerse en contacto con el equipo de asistencia del Adobe de para añadir la IP a la lista de permitidos.
>

## Creación de zonas de seguridad {#creating-security-zones}

Una zona está definida por:

* uno o más rangos de direcciones IP (IPv4 e IPv6)
* un nombre técnico asociado a cada rango de direcciones IP

Las zonas de seguridad están interbloqueadas, lo que significa que la definición de una nueva zona dentro de otra zona reduce el número de operadores que pueden iniciar sesión en ella al tiempo que aumenta los derechos asignados a cada operador.

Las zonas deben definirse durante la configuración del servidor, en el **serverConf.xml** archivo. Todos los parámetros disponibles en **serverConf.xml** se enumeran en [esta sección](../../installation/using/the-server-configuration-file.md).

Cada zona define derechos como, por ejemplo:

* Conexión HTTP en lugar de HTTPS
* Visualización de errores (errores de Java, JavaScript, C++, etc.)
* Previsualización de informes y aplicaciones web
* Autenticación mediante inicio de sesión/contraseña
* Modo de conexión no seguro

>[!NOTE]
>
>**Cada operador debe estar vinculado a una zona**. Si la dirección IP del operador pertenece al rango definido por la zona, el operador puede iniciar sesión en la instancia.\
>La dirección IP del operador puede definirse en varias zonas. En este caso, el operador recibe la variable **set** de derechos disponibles para cada zona.

El producto listo para usar **serverConf.xml** el archivo incluye tres zonas: **pública, VPN y LAN**.

>[!NOTE]
>
>**La configuración predeterminada es segura.**. Sin embargo, antes de migrar desde una versión anterior de Adobe Campaign, puede ser necesario reducir temporalmente la seguridad para migrar y aprobar las nuevas reglas.

Ejemplo de cómo definir una zona en **serverConf.xml** archivo:

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

* **allowDebug**: permite ejecutar una aplicación web en modo de &quot;depuración&quot;
* **allowEmptyPassword**: autoriza una conexión a una instancia sin contraseña
* **allowHTTP**: se puede crear una sesión sin utilizar el protocolo HTTPS
* **allowUserPassword**: el token de sesión puede tener el siguiente formulario &quot;`<login>/<password>`&quot;
* **sessionTokenOnly**: el token de seguridad no es necesario en la dirección URL de conexión
* **showErrors**: los errores del lado del servidor se reenvían y muestran

>[!IMPORTANT]
>
>En una definición de zona, cada atributo con la variable **true** reduce la seguridad.

Al utilizar el Centro de mensajes, si hay varias instancias de ejecución, debe crear una zona de seguridad adicional con el **sessionTokenOnly** atributo definido como **true**, donde solo se deben añadir las direcciones IP necesarias. Para obtener más información sobre la configuración de instancias, consulte [este documento](../../message-center/using/configuring-instances.md).

## Prácticas recomendadas para zonas de seguridad {#best-practices-for-security-zones}

En la definición de **lan** zona de seguridad, es posible añadir una máscara de dirección IP que defina el acceso técnico. Esta adición habilita el acceso a todas las instancias alojadas en el servidor.

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

Se recomienda definir intervalos de direcciones IP directamente en el archivo de configuración dedicado a la instancia para los operadores que solo acceden a una instancia específica.

En el **`config-<instance>.xml`** archivo:

```
  <securityZone name="public">
   ...
    <securityZone name="vpn">
      <subNetwork id="cus1" mask="a.b.c.d/xx"/>
```

## Redes secundarias y proxies en una zona de seguridad {#sub-networks-and-proxies-in-a-security-zone}

El **proxy** El parámetro se puede utilizar en un **subNetwork** para especificar el uso del proxy en una zona de seguridad.

Cuando se hace referencia a un proxy y entra una conexión a través de este proxy (visible a través del encabezado HTTP X-Forwarded-For), la zona verificada es la de los clientes del proxy y no la del proxy.

>[!IMPORTANT]
>
>Si se configura un proxy y es posible anularlo (o hacerlo si no existe), la dirección IP que se probará podrá falsificarse.
>
>Además, los relés ahora se generan como proxies. Por lo tanto, puede agregar la dirección IP 127.0.0.1 a la lista de servidores proxy de la configuración de zona de seguridad.
>
>Por ejemplo: &quot; `<subnetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" proxy="127.0.0.1,10.100.2.135" />`&quot;.

Pueden producirse varios casos:

* Se hace referencia directamente a una subred en la zona de seguridad y no se configura ningún proxy: los usuarios de la subred pueden conectarse directamente al servidor de Adobe Campaign.

  ![](assets/8101_proxy1.png)

* Se especifica un proxy para una subred en la zona de seguridad: los usuarios de esta subred pueden acceder al servidor de Adobe Campaign a través de este proxy.

  ![](assets/8101_proxy2.png)

* Un proxy se incluye en una subred de zonas de seguridad: los usuarios que tienen acceso a través de este proxy, independientemente de su origen, pueden acceder al servidor de Adobe Campaign.

  ![](assets/8101_proxy3.png)

Las direcciones IP de los proxies que tienen probabilidades de acceder al servidor de Adobe Campaign deben introducirse en **`<subnetwork>`** y la subred de primer nivel **`<subnetwork name="all"/>`**. Por ejemplo, aquí para un proxy cuya dirección IP es 10.131.146.102:

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

## Vinculación de una zona de seguridad a un operador {#linking-a-security-zone-to-an-operator}

Una vez definidas las zonas, cada operador debe vincularse a una de ellas para poder iniciar sesión en una instancia y la dirección IP del operador debe incluirse en las direcciones o rango de direcciones a las que se hace referencia en la zona.

La configuración técnica de las zonas se realiza en el archivo de configuración del servidor de Campaign: **serverConf.xml**.

Antes de esto, debe empezar configurando la de forma predeterminada **[!UICONTROL Security zone]** enumeración para vincular una etiqueta al nombre interno de la zona definida en la variable **serverConf.xml** archivo.

Esta configuración se realiza en el explorador de Campaign:

1. Haga clic en el nodo **[!UICONTROL Administration > Platform > Enumerations]**.
1. Seleccione el **[!UICONTROL Security zone (securityZone)]** enumeración del sistema.

   ![](assets/enum_securityzone.png)

1. Para cada zona de seguridad definida en el archivo de configuración del servidor, haga clic en **[!UICONTROL Add]** botón.
1. En el **[!UICONTROL Internal name]** , introduzca el nombre de la zona definida en el campo **serverConf.xml** archivo. Corresponde a la variable **@name** atributo del `<securityzone>`  Elemento. Introduzca la etiqueta vinculada al nombre interno en la variable  **Etiqueta** field.

   ![](assets/enum_addsecurityvalue.png)

1. Haga clic en Aceptar y guarde las modificaciones.

Una vez definidas las zonas y la variable **[!UICONTROL Security zone]** Cuando se haya configurado la enumeración, es necesario vincular cada operador a una zona de seguridad:

1. Haga clic en el nodo **[!UICONTROL Administration > Access management > Operators]**.
1. Seleccione el operador al que desea vincular una zona de seguridad y haga clic en el botón **[!UICONTROL Edit]** pestaña.
1. Vaya a la pestaña **[!UICONTROL Access rights]** y haga clic en el vínculo **[!UICONTROL Edit access parameters...]**.

   ![](assets/zone_operator.png)

1. Seleccione una zona de la lista **[!UICONTROL Authorized connection zone]** lista desplegable

   ![](assets/zone_operator_selection.png)

1. Clic **[!UICONTROL OK]** y guarde las modificaciones para aplicar estos cambios.



## Recomendaciones

* Asegúrese de que el proxy inverso no esté permitido en subNetwork. Si es el caso, **todo** se detectará tráfico proveniente de esta IP local, por lo que se confiará en él.

* Minimice el uso de sessionTokenOnly=&quot;true&quot;:

   * Advertencia: Si este atributo se establece en &quot;true&quot;, el operador puede exponerse a un **Ataque de CRSF**.
   * Además, la cookie sessionToken no se establece con un indicador httpOnly, por lo que algunos códigos JavaScript del lado del cliente pueden leerla.
   * Sin embargo, el Centro de mensajes de varias celdas de ejecución necesita sessionTokenOnly: cree una nueva zona de seguridad con sessionTokenOnly establecida en &quot;true&quot; y agregue **solo las IP necesarias** en esta zona.

* Cuando sea posible, establezca todos allowHTTP, showErrors como false (no para localhost) y compruébelos.

   * allowHTTP = &quot;false&quot;: obliga a los operadores a utilizar HTTPS
   * showErrors = &quot;false&quot;: oculta los errores técnicos (incluidos los SQL). Evita mostrar demasiada información, pero reduce la capacidad del experto en marketing para resolver errores (sin solicitar más información a un administrador)

* Establezca allowDebug en true solo en las direcciones IP que usan los usuarios/administradores de marketing que necesitan crear (de hecho, previsualizar) encuestas, aplicaciones web e informes. Este indicador permite que estas direcciones IP obtengan reglas de retransmisión y las depuren.

   * Cuando allowDebug se establece en false, el resultado es:

     ```
     <redir status='OK' date='...' sourceIP='...'/>
     ```

   * Cuando allowDebug se establece en true, el resultado es:

     ```
     <redir status='OK' date='...' build='...' OR version='...' sha1='...' instance='...' sourceIP='...' host='...' localHost='...'/>
     ```

* Nunca establezca allowEmptyPassword, allowUserPassword, allowSQLInjection en true.

   * **allowEmptyPassword** permite que los operadores tengan una contraseña vacía. Si este es el caso, notifique a todos los operadores para pedirles que establezcan una contraseña con una fecha límite. Una vez transcurrido este plazo, cambie este atributo a false.

   * **allowUserPassword** permite a los operadores enviar sus credenciales como parámetros (para que las registre apache/IIS/proxy). Esta función se utilizaba anteriormente para simplificar el uso de la API. Puede comprobar en el libro de cocina (o en la especificación) si algunas aplicaciones de terceros lo utilizan. Si es así, debe notificarles que cambien la forma en que usan nuestra API y que eliminen esta función lo antes posible.

   * **allowSQLInjection** permite al usuario realizar inyecciones SQL utilizando una sintaxis antigua. Este atributo debe establecerse en false. Puede utilizar /nl/jsp/ping.jsp?zones=true para comprobar la configuración de la zona de seguridad. Esta página muestra el estado activo de las medidas de seguridad (calculadas con estos indicadores de seguridad) para la IP actual.

* Cookie HttpOnly/useSecurityToken: consulte **sessionTokenOnly** Indicador.

* Minimizar las direcciones IP agregadas a la lista de permitidos: en las zonas de seguridad, hemos agregado los 3 rangos para redes privadas. Es poco probable que vaya a utilizar todas estas direcciones IP. Así que conserve sólo los que necesite.

* Actualice el operador webApp/internal para que solo sea accesible en localhost.
