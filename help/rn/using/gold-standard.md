---
solution: Campaign Classic
product: campaign
title: '[!DNL Gold Standard] notas de la versión'
description: Notas de la versión para el Campaign Classic [!DNL Gold Standard]
feature: Información general
role: Profesional empresarial
level: Principiante
translation-type: tm+mt
source-git-commit: b77a56a97e499f60c092fae45c7809f7bfd9f2ea
workflow-type: tm+mt
source-wordcount: '1026'
ht-degree: 83%

---


# [!DNL Gold Standard] notas de la versión{#gold-standard}

Esta página enumera las [!DNL Gold Standard] versiones. Obtenga más información sobre Campaign [!DNL Gold Standard] [en esta página](gs-overview.md).

## ![](assets/do-not-localize/green_2.png) [!DNL Gold Standard] Versión 11{#gs-11}

_2 de marzo de 2021_

La versión 9032@10c2709 incluye la siguiente corrección:

* Se ha corregido una regresión que impedía el uso de algunos componentes de la consola, como el selector de fechas y la administración de imágenes en los envíos. (NEO-31453, NEO-31454)

**Solo es obligatorio actualizar la consola. No se requiere ninguna actualización del servidor.**

>[!NOTE]
>
> Conéctese a [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/es/campaign.html) para descargar la nueva versión. Aprenda a proponer la actualización de la consola a todos los usuarios finales [en esta página](../../installation/using/client-console-availability-for-windows.md).


_22 de diciembre de 2020_

>[!CAUTION]
>
> * Esta versión incorpora un nuevo protocolo de conexión: si se conecta a Campaign a través del servicio de identidad de Adobe (IMS), la actualización es obligatoria para que el servidor de Campaign y la consola del cliente puedan conectarse a Campaign después del **30 de junio de 2021**.
> * Esta versión incluye una [corrección de seguridad](https://helpx.adobe.com/security/products/campaign/apsb21-04.html): la actualización es obligatoria para reforzar la seguridad de su entorno.
> * Si está utilizando la integración de Déclencheur de Experience Cloud mediante autenticación oAuth, debe pasar a Adobe I/O como se describe [en esta página](../../integrations/using/configuring-adobe-io.md). El modo de autenticación oAuth heredado con Campaign se eliminará el **30 de noviembre de 2021**.

>
>
Obtenga más información en las [[!DNL Gold Standard] 11 preguntas frecuentes sobre la actualización](https://helpx.adobe.com/es/campaign/kb/sms-connector-protocol-and-settings.html).

La versión 9032@d3b452f incluye las siguientes mejoras y correcciones:

* El protocolo de conexión se ha actualizado para seguir el nuevo mecanismo de autenticación IMS.

* Activa la autenticación de integración, basada originalmente en la configuración de autenticación oAUTH, para acceder al canal que ahora se ha cambiado y se ha movido a Adobe I/O. [Más información](../../integrations/using/configuring-adobe-io.md)

* Después de finalizar [la compatibilidad con el protocolo binario heredado de APN de iOS](https://developer.apple.com/news/?id=c88acm2b), todas las instancias que utilizan este protocolo se actualizan al protocolo HTTP/2 durante la postactualización.

* Se ha corregido un problema de seguridad para reforzar la protección contra los problemas de falsificación de solicitudes del lado del servidor (SSRF). (NEO-27777)




* Se ha corregido un problema que podía provocar errores en los flujos de trabajo al ejecutar una actividad de **Enriquecimiento**. (NEO-17338)

## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] Versión 10{#gs-10}

_7 de julio de 2020_

La versión 9032@efd8a94 incluye la siguiente corrección:

Se ha corregido un problema que impedía que el seguimiento funcionara cuando la función de firma estaba deshabilitada. (NEO-26411)

>[!CAUTION]
>
>Le recomendamos que actualice la consola de cliente con la que está disponible en esta versión. Consulte [esta página](../../installation/using/installing-the-client-console.md)

## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] versión 9{#gs-9}

_22 de junio de 2020_

La versión 9032@800be2e incluye las siguientes correcciones:

* Se ha mejorado el conector HTTP2 de iOS (actualizaciones de terceros y administración de errores). (NEO-25904, NEO-25903, NEO-25799)

Las siguientes correcciones están relacionadas con el mecanismo de seguridad del vínculo de seguimiento (consulte la [lista de comprobación Seguridad y privacidad](https://helpx.adobe.com/es/campaign/kb/acc-security.html#signature-mechanism)):

* Se ha corregido un problema que impedía el funcionamiento del seguimiento de &quot;clics de notificación&quot; (notificaciones push de iOS y Android). (NEO-25965)
* Se ha corregido un problema que podía impedir que se abrieran las direcciones URL de seguimiento al usar ciertas versiones heredadas de Outlook o se hiciera clic en ellas.  (NEO-25688)
* Se ha corregido un problema que impedía que el funcionamiento del seguimiento de direcciones URL mediante fragmentos en parámetros de personalización (etiquetas de anclaje con signo de almohadilla). (NEO-25774)
* Se ha corregido un problema con el servicio de antiphishing. (NEO-25283)
* Se ha corregido un problema de seguimiento al usar fórmulas de seguimiento personalizadas específicas. (NEO-25277)





## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] versión 8{#gs-8}

_29 de abril de 2020_

La versión 9032@3a9dc9c incluye las siguientes correcciones:

* Se ha mejorado la seguridad en el seguimiento de enlaces en el correo electrónico. Esta opción está habilitada de forma predeterminada para todos los clientes. Hay disponible una función de seguridad adicional y mejorada que se puede habilitar si se pone en contacto con el Servicio de atención al cliente. Encuentre más detalles sobre la función y los pasos para que los clientes que no están alojados puedan habilitarla en la [Lista de comprobación de seguridad y privacidad](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism).

>[!CAUTION]
>
>Si tiene problemas con las notificaciones push mediante vínculos de seguimiento o con envíos que utilizan etiquetas de anclaje, le recomendamos que desactive el nuevo mecanismo de firma para el seguimiento de vínculos. El procedimiento se detalla [en esta página](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism).

* Se ha corregido un problema que podía impedir que las imágenes se mostraran en envíos de línea. (NEO-23207)
* Se ha corregido un problema con la actividad **File Transfer** que impedía que la autenticación basada en claves SFTP funcionara en Debian 9. (NEO-23183)
* Se ha corregido un problema que podía afectar a la notificación push cuando se enviaba con una frecuencia alta. (NEO-20516)
* Se ha corregido un problema en la administración de respuestas de oferta que podía provocar bloqueos en el servidor web. (NEO-19482)
* Se ha corregido un error en la administración de LibreOffice que impedía exportar informes. (NEO-20982)
* Se ha corregido un problema que provocaba un error al actualizar numerosos flujos de trabajo mediante una actividad de encuesta.
* Se mejoró la administración de LibreOffice para evitar fallos en la previsualización de correos electrónicos con archivos .odt.
* Se ha mejorado la administración de la conexión de Apache para evitar la latencia en el servicio web.
* Se ha mejorado la visualización de la etiqueta de versión (7 dígitos) en el menú **Acerca de**.
* Se ha corregido una regresión en la administración de listas que impedía que se publicaran ofertas.
* Se ha corregido una regresión que ocasionaba que el flujo de trabajo de limpieza se bloqueara.
* Se ha corregido una regresión menor en los registros del flujo de trabajo de limpieza.

## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] versión 6{#gs-6}

_viernes, 9 de marzo de 2020_

La versión 9032@19f73c5 incluye la siguiente corrección:

* Se ha corregido un problema con cuentas externas que usaban FTP sobre SSL. (NEO-20498)

## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] versión 5{#gs-5}

_17 de diciembre de 2019_

La versión 9032@d6b8062 incluye la siguiente corrección:

* Se ha corregido un problema de seguimiento en los siguientes canales de comunicación: móvil (SMS, MMS), push (iOS, Android) y redes sociales (Facebook, Twitter). (NEO-19595)

## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] versión 4{#gs-4}

_11 de diciembre de 2019_

La versión 9032@bc4a935 incluye la siguiente corrección:

* Se ha corregido un problema de rendimiento al enviar mensajes con una base de datos MSSQL. (NEO-17558)

## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] versión 3{#gs-3}

_20 de noviembre de 2019_

La versión 9032@3468c7b incluye las siguientes correcciones:

* Se ha corregido un problema de inicio de sesión mediante la autenticación IMS. (NEO-17312)
* Se ha corregido un problema al mostrar informes acumulativos en varias entregas. (NEO-18165)
* Se ha corregido un problema que podía bloquear o colapsar el servidor web.

## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] versión 2{#gs-2}

_19 de septiembre de 2019_

La versión 9032@cee805c incluye las siguientes correcciones:

* Se ha corregido un problema al usar el conector CRM para Salesforce. (NEO-17712)
* Se ha corregido un problema de índice que podía provocar problemas de rendimiento al enviar mensajes transaccionales.

## ![](assets/do-not-localize/red_2.png) Versión 19.1.4: compilación 9032{#release-19-1-4-build-9032}

_13 de agosto de 2019_

La versión inicial 19.1.4 incluye las siguientes correcciones:

* Se ha corregido un problema con la actividad del programador que generaba mensajes de error no deseados durante la configuración del asistente. Revertir la actualización desde NEO-11662. (NEO-17097)
* Se ha corregido una regresión causada por el NEO-12727 que hacía que los flujos de trabajo se detuvieran cuando se realizaba una actividad de prueba dos veces. (NEO-16835)
* Se ha corregido un problema que provocaba la devolución de un código HTTP erróneo (HTTP 200 OK en lugar de HTTP 403 Prohibido) cuando se utilizaba un token de sesión no válido o caducado en las llamadas a la API. (NEO-16826)
* Se ha solucionado un problema con la clave DKIM que ya no se incrustaba en los mensajes de correo electrónico, lo que provocaba problemas a la hora de realizar entregas. (NEO-16804)
* Se han corregido varios problemas con la programación de los flujos de trabajo. Los flujos de trabajo se programaban para ejecutarse una vez al día sin tener en cuenta la configuración del programador. (NEO-16619, NEO-16426)
