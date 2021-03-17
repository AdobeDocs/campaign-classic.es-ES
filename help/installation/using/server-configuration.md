---
solution: Campaign Classic
product: campaign
title: Configuración del servidor
description: Obtenga más información sobre las prácticas recomendadas de configuración del servidor.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: d88815e36f7be1b010dcaeee51013a5da769b4a8
workflow-type: tm+mt
source-wordcount: '1156'
ht-degree: 14%

---


# Configuración del servidor {#server-configuration}

## Configuración de zonas de seguridad

>[!IMPORTANT]
>
>A partir de la versión 8977, la interfaz de usuario de autoservicio de zonas de seguridad ya no está disponible.
>
>* Si está alojado en AWS, la adición de IP a la lista de permitidos debe realizarse en Panel de control de Campaign. Para obtener más información, consulte la [documentación especializada](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html).
>* Si no está alojado en AWS, póngase en contacto con el equipo de asistencia de Adobe para añadir la IP a la lista de permitidos.

>
>
Para comprobar si la instancia está alojada en AWS, siga los pasos detallados en [esta sección](https://experienceleague.adobe.com/docs/control-panel/using/faq.html).

* Asegúrese de que el proxy inverso no esté permitido en subNetwork. Si es así, se detectará **todo** tráfico procedente de esta IP local, por lo que se confiará en él.

* Minimice el uso de sessionTokenOnly=&quot;true&quot;:

   * Advertencia: Si este atributo se establece en true, el operador se puede exponer a un **ataque CRSF**.
   * Además, la cookie sessionToken no está configurada con un indicador httpOnly, por lo que parte del código javascript del lado del cliente puede leerla.
   * Sin embargo, el Centro de mensajes en varias celdas de ejecución necesita sessionTokenOnly: cree una nueva zona de seguridad con sessionTokenOnly configurada como &quot;true&quot; y añada **solo las IP necesarias** en esta zona.

* Cuando sea posible, establezca todos allowHTTP, showErrors como falsos (no para localhost) y compruébelos.

   * allowHTTP = &quot;false&quot;: fuerza a los operadores a utilizar HTTPS
   * showErrors = &quot;false&quot;: oculta errores técnicos (incluidos los SQL). Evita mostrar demasiada información, pero reduce la capacidad del experto en marketing para resolver errores (sin solicitar más información a un administrador)

* Establezca allowDebug en true solo en las IP utilizadas por los usuarios/administradores de marketing que necesiten crear estudios, webApps e informes (de hecho, previsualizarlos). Este indicador permite que estas IP obtengan reglas de transmisión mostradas y las depuren.

* Nunca establezca allowEmptyPassword, allowUserPassword, allowSQLInjection como verdadero. Estos atributos solo están aquí para permitir una migración sin problemas desde las versiones 5 y 6.0:

   * **Los operadores** allowEmptyPasswordlets tienen una contraseña vacía. Si este es el caso, notifique a todos los operadores para que les pidan que establezcan una contraseña con una fecha límite. Una vez que haya pasado esta fecha límite, cambie este atributo a false.

   * **** Los operadores allowUserPasswordlets envían sus credenciales como parámetros (por lo que se registrarán mediante apache/IIS/proxy). Esta función se utilizaba en el pasado para simplificar el uso de la API. Puede consultar la guía (o la especificación) si algunas aplicaciones de terceros utilizan esto. Si es así, debe notificarles que deben cambiar la forma en que utilizan nuestra API y, lo antes posible, eliminar esta función.

   * **** allowSQLInjectionpermite al usuario realizar inyecciones SQL utilizando una sintaxis antigua. Lo antes posible, realice las correcciones descritas en [esta página](../../migration/using/general-configurations.md) para poder establecer este atributo en false. Puede utilizar /nl/jsp/ping.jsp?zones=true para comprobar la configuración de su zona de seguridad. Esta página muestra el estado activo de las medidas de seguridad (calculadas con estos indicadores de seguridad) para la IP actual.

* HttpOnly cookie/useSecurityToken: consulte el indicador **sessionTokenOnly** .

* Minimizar las direcciones IP agregadas a la lista de permitidos: en las zonas de seguridad, hemos agregado los 3 rangos para redes privadas. Es poco probable que utilice todas estas direcciones IP. Por lo tanto, mantenga solamente los que necesite.

* Actualice el operador webApp/internal para que solo sea accesible en localhost.

## Protección de carga de archivos

Compruebe con los usuarios operativos qué tipo de archivos se cargan en el servidor mediante la interfaz nlclient/web. Como recordatorio, las necesidades comerciales pueden ser:

* imágenes (jpg, gif, png...)
* contenido (zip, html, css, ...)
* recursos de marketing (doc, xls, pdf, psd, tiff, ...)
* datos adjuntos de correo electrónico (doc, pdf, ...)
* ETL (txt, csv, tab, ...)
* Etc.

Añádalos todos en serverConf/shared/datastore/@uploadAllowlist (expresión regular java válida). Obtenga más información en [esta página](../../installation/using/configuring-campaign-server.md#limiting-uploadable-files).

Adobe Campaign no restringe el tamaño del archivo. Pero puede hacerlo configurando IIS/Apache. Obtenga más información en [esta sección](../../installation/using/web-server-configuration.md).

## Transmisión

Consulte [esta página](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays) para obtener más información.

De forma predeterminada, todas las páginas dinámicas se retransmiten automáticamente al servidor Tomcat local del equipo cuyo módulo web se inicia. Puede optar por no retransmitir algunas de ellas. Si no utiliza algunos módulos de Adobe Campaign (como webapp, interacción, algunos jsp), puede eliminarlos de las reglas de transmisión.

De forma predeterminada, hemos forzado la capacidad de mostrar los recursos del usuario final mediante http (httpAllowed=&quot;true&quot;). Como estas páginas pueden mostrar algunas PII (como contenido de correo electrónico, direcciones), canjear vales y ofertas, debe forzar el uso de HTTPS en estas rutas.

Si utiliza nombres de host diferentes (uno público y otro para operadores), también puede evitar que los operadores reenvíen algunos recursos necesarios sobre el nombre DNS público.

## Protección de conexión saliente

La lista predeterminada de direcciones URL a las que pueden llamar los códigos JavaScript (flujos de trabajo, etc.) es limitada. Para permitir una nueva dirección URL, el administrador debe hacer referencia a ella en el archivo [serverConf.xml](../../installation/using/the-server-configuration-file.md).

Existen tres modos de protección de conexión:

* **Bloqueo** : todas las direcciones URL que no pertenecen a la lista de permitidos están bloqueadas, con un mensaje de error. Es el modo predeterminado después de una posactualización.
* **Permisivo** : se permiten todas las direcciones URL que no pertenecen a la lista de permitidos.
* **Advertencia** : se permiten todas las direcciones URL que no están en la lista de permitidos, pero el intérprete JS emite una advertencia para que el administrador pueda recopilarlas. Este modo añade mensajes de advertencia JST-310027.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

Los nuevos clientes utilizarán el modo de bloqueo. Si desea permitir una nueva dirección URL, debe ponerse en contacto con el administrador para añadirla a la lista de permitidos.

Los clientes existentes procedentes de una migración pueden utilizar el modo de advertencia durante un tiempo. Mientras tanto, deben analizar el tráfico saliente antes de autorizar las direcciones URL.

## Restricción de comandos (lado del servidor)

Varios comandos se incluyen en la lista negra y no se pueden ejecutar mediante la función execCommand. Un usuario de Unix dedicado proporciona una seguridad adicional para ejecutar comandos externos. En el caso de instalaciones alojadas, esta restricción se aplica automáticamente. Para las instalaciones locales, puede configurar manualmente esta restricción siguiendo las instrucciones de [esta página](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands). Además, las actividades de flujo de trabajo **[!UICONTROL Script]** y **[!UICONTROL External task]** no están disponibles (instancias recién instaladas).

## Otras configuraciones

Puede agregar encabezados HTTP adicionales para todas las páginas (para obtener más información, consulte [esta página](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands)):

* Puede añadir algunos encabezados adicionales, como HSTS, OPTIONS X-FRAME, CSP...
* Debe probarlos en un entorno de prueba antes de aplicarlos en producción.

   >[!IMPORTANT]
   >
   >Adobe Campaign se puede desglosar añadiendo ciertos encabezados.

Adobe Campaign permite establecer una contraseña sin formato en el elemento `<dbcnx .../>` . No utilice esta función.

De forma predeterminada, Adobe Campaign no vincula una sesión a una IP específica, pero puede activarla para evitar que se robe la sesión. Para ello, en el archivo [serverConf.xml](../../installation/using/the-server-configuration-file.md), establezca el atributo checkIPConsistent en **true** en el nodo `<authentication>`.

De forma predeterminada, el MTA de Adobe Campaign no utiliza una conexión segura para enviar contenido al servidor SMTP. Debe activar esta función (puede reducir la velocidad de envío). Para ello, establezca **enableTLS** en **true** en el nodo `<smtp ...>`.

Puede reducir la duración de una sesión en el nodo de autenticación (atributo sessionTimeOutSec).
