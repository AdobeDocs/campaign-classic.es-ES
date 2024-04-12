---
product: campaign
title: Configuración de seguridad del servidor
description: Obtenga más información acerca de las prácticas recomendadas de configuración del servidor
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: e1aff73a-54fb-444e-b183-df11c9b3df31
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 11%

---

# Configuración de seguridad del servidor {#server-configuration}

## Protección de carga de archivos

Compruebe con los usuarios operativos qué tipo de archivos cargan en el servidor mediante la consola del cliente de Campaign o la interfaz web. Como recordatorio, las necesidades empresariales pueden ser:

* imágenes (jpg, gif, png, ...)
* contenido (zip, html, css, ...)
* recursos de marketing (doc, xls, pdf, psd, tiff, ...)
* archivo adjunto de correo electrónico (doc, pdf, ...)
* ETL (txt, csv, tab, ...)
* Etc.

Añádalos todos en serverConf/shared/datastore/@uploadAllowlist (expresión regular java válida). Obtenga más información en [esta página](../../installation/using/file-res-management.md).

Adobe Campaign no restringe el tamaño del archivo. Pero puede hacerlo configurando IIS/Apache. Obtenga más información en [esta sección](../../installation/using/web-server-configuration.md).

## Relé

Consulte la [esta página](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays) para obtener más información.

De forma predeterminada, todas las páginas dinámicas se transmiten automáticamente al servidor Tomcat local del equipo cuyo módulo web se haya iniciado. Puede optar por no transmitir algunos de ellos. Si no utiliza algunos módulos de Adobe Campaign (como webapp, interaction, some jsp), puede eliminarlos de las reglas de retransmisión.

De forma predeterminada, hemos forzado la capacidad de mostrar los recursos del usuario final mediante http (httpAllowed=&quot;true&quot;). Como estas páginas pueden mostrar algunas PII (como contenido de correo electrónico, direcciones), canjear vales y ofertas, debe forzar el uso de HTTPS en estas rutas.

Si utiliza nombres de host diferentes (uno público y otro para operadores), también puede evitar la retransmisión de algunos recursos necesarios por los operadores sobre el nombre DNS público.

## Protección de conexión saliente

La lista predeterminada de direcciones URL a las que pueden llamar los códigos JavaScript (flujos de trabajo, etc.) está limitada. Para permitir una nueva URL, el administrador debe hacer referencia a ella en la [archivo serverConf.xml](../../installation/using/the-server-configuration-file.md).

Existen tres modos de protección de conexión:

* **Bloqueo** : todas las direcciones URL que no pertenecen a la lista de permitidos están bloqueadas y muestran un mensaje de error. Es el modo predeterminado después de una posactualización.
* **Permisivo** : se permiten todas las direcciones URL que no pertenecen a la lista de permitidos.
* **Advertencia** : se permiten todas las direcciones URL que no están en la lista de permitidos, pero el intérprete JS emite una advertencia para que el administrador pueda recopilarlas. Este modo agrega mensajes de advertencia JST-310027.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

Los nuevos clientes utilizarán el modo de bloqueo. Si desea permitir una nueva dirección URL, debe ponerse en contacto con el administrador para añadirla a la lista de permitidos.

Los clientes existentes que provengan de una migración pueden utilizar el modo de advertencia durante un tiempo. Mientras tanto, deben analizar el tráfico saliente antes de autorizar las direcciones URL.

## Restricción de comandos (del lado del servidor)

En la lista de bloqueados de la se incluyen varios comandos que no se pueden ejecutar mediante la función execCommand. Un usuario de Unix dedicado proporciona una seguridad adicional para ejecutar comandos externos. Para instalaciones alojadas, esta restricción se aplica automáticamente. Para las instalaciones in situ, puede configurar manualmente esta restricción siguiendo las instrucciones de [esta página](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands). Además, **[!UICONTROL Script]** y **[!UICONTROL External task]** las actividades de flujo de trabajo no están disponibles (instancias recién instaladas).

## Otras configuraciones

Puede agregar encabezados HTTP adicionales para todas las páginas (para obtener más información, consulte [esta página](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands)):

* Puede añadir algunos encabezados adicionales, como HSTS, X-FRAME-OPTIONS, CSP...
* Debe probarlos en un entorno de prueba antes de aplicarlos en producción.

  >[!IMPORTANT]
  >
  >Adobe Campaign se puede romper añadiendo ciertos encabezados.

Adobe Campaign permite establecer una contraseña sin formato en la variable `<dbcnx .../>` Elemento. No utilice esta función.

De forma predeterminada, Adobe Campaign no fija una sesión a una IP específica, pero puede activarla para evitar que se robe la sesión. Para ello, en el [archivo serverConf.xml](../../installation/using/the-server-configuration-file.md), establezca el atributo checkIPConsistent en **true** en el `<authentication>` nodo.

De forma predeterminada, el MTA de Adobe Campaign no utiliza una conexión segura para enviar contenido al servidor SMTP. Debe habilitar esta función (puede reducir la velocidad de envío). Para ello, establezca **enableTLS** hasta **true** en el `<smtp ...>` nodo.

Puede reducir la duración de una sesión en el nodo de autenticación (atributo sessionTimeOutSec).
