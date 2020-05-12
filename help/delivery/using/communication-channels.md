---
title: Canales de comunicación
seo-title: Canales de comunicación
description: Canales de comunicación
seo-description: null
page-status-flag: never-activated
uuid: 42975431-64c9-4ecb-98ed-b1f9b13c157e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: 2e2d1134-9b83-4ada-b74f-c3842a0cf044
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 15581517df8d2f397285bbadebd83b7f4539dfd7
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 99%

---


# Canales de comunicación{#communication-channels}

Con Adobe Campaign, puede enviar campañas en canales múltiples incluidos correos electrónicos, SMS, mensajes LINE, notificaciones push y correo postal y medir su eficacia mediante varios [informes](../../reporting/using/delivery-reports.md) dedicados. Estos mensajes están diseñados y enviados por medio de envíos y pueden personalizarse para cada destinatario.

Las funciones principales incluyen establecimiento de objetivos, definición y personalización de mensajes, ejecución de comunicaciones y los informes operativos asociados. El punto de acceso funcional principal es el asistente de envío. Este punto de acceso lleva a varias funciones incluidas en Adobe Campaign.

>[!NOTE]
>
>Adobe Campaign ofrece un conjunto de herramientas para supervisar su capacidad de envío y optimizar la entrega por correo electrónico. Para obtener más información, consulte [Introducción a las entregas](https://docs.adobe.com/content/help/es-ES/campaign-classic/using/sending-messages/deliverability-management/about-deliverability.html) y [Gestión de envíos](../../delivery/using/about-deliverability.md).

El envío puede automatizarse al preparar una entrega o al enviarlo en el proceso de un flujo de trabajo. Para obtener más información sobre las actividades de tipo envío en los flujos de trabajo, consulte [esta sección](../../workflow/using/about-action-activities.md).

Adobe Campaign ofrece los siguientes canales de envío:

1. **Canal de correo electrónico**: las entregas de correo electrónico le permiten enviar correos electrónicos personalizados a la población objetivo. Consulte [Acerca del canal de correo electrónico](../../delivery/using/about-email-channel.md).
1. **Canal de correo postal**: las entregas de correo postal permiten generar un archivo de extracción que contenga datos sobre la población objetivo. [Acerca del canal de correo postal](../../delivery/using/about-direct-mail-channel.md).
1. **Canal móvil**: las entregas en canales móviles permiten enviar mensajes SMS o de LINE personalizados a la población objetivo. Consulte [el canal de SMS](../../delivery/using/sms-channel.md).
1. **Canal de aplicación móvil**: los envíos de aplicaciones móviles permiten enviar notificaciones a sistemas iOS y Android. Consulte el capítulo [canal de aplicaciones móviles](../../delivery/using/about-mobile-app-channel.md).

   Other channels are described on [this page](../../delivery/using/other-channels.md).

   >[!NOTE]
   >
   >El uso de varios canales depende del paquete. Compruebe el acuerdo de licencia.

Los envíos se pueden realizar **en línea** (por correo electrónico, uno de los canales móviles y por notificaciones push) y **sin conexión** (por el canal de correo postal).

Dependiendo del canal, los modos de envío pueden ser:

* Envío directo mediante Adobe Campaign (modo predeterminado del canal por correo electrónico).
* Envío externo a través de un operador especializado que recibe el archivo de salida generado por el asistente de envío (modo predeterminado del canal por correo postal).

Las cuentas externas se configuran mediante el nodo **[!UICONTROL Administration > Platform > External accounts]**. Esta configuración solo deben realizarla usuarios expertos.

## Envíos por correo electrónico {#email-deliveries}

El [canal de correo electrónico](../../delivery/using/about-email-channel.md) es uno de los canales principales de Adobe Campaign, el cual permite programar y enviar correos electrónicos personalizados a objetivos específicos.

Se pueden enviar diferentes tipos de correos electrónicos:

* Correos electrónicos de envío único: correos electrónicos que se pueden enviar una vez a un destino definido. Suelen utilizarse para promocionar un contenido específico que se prepara y se envía una sola vez (boletín informativo, correo electrónico promocional, etc.).
* Correos electrónicos recurrentes: en una campaña, envíe el mismo correo electrónico regularmente y añada cada envío y sus informes periódicamente. Se envía el mismo correo electrónico, pero normalmente a un destino diferente, en función del destino apto para el día de la entrega. Un ejemplo común es un correo electrónico de cumpleaños. Para obtener más información, consulte [envíos recurrentes](../../workflow/using/recurring-delivery.md).
* Correos electrónicos de transacción: correos electrónicos individuales que se activan según el comportamiento de los clientes. Consulte [mensajería transaccional](../../message-center/using/about-transactional-messaging.md).

Para obtener más información sobre uso de las entregas y recomendaciones, consulte [Prácticas recomendadas de envío](https://helpx.adobe.com/es/campaign/kb/delivery-best-practices.html) de Campaign.

Para obtener más información sobre los distintos tipos de envíos, consulte [esta sección](../../delivery/using/types-of-deliveries.md).

## Envíos a móviles {#mobile-deliveries}

Adobe Campaign le permite enviar mensajes [SMS](../../delivery/using/sms-channel.md) y de [LINE](../../delivery/using/line-channel.md) a móviles.

En los mensajes SMS, puede crear, modificar y personalizar mensajes solo de formato de texto. También puede obtener una previsualización de los mensajes SMS antes de enviarlos.

Para los mensajes de LINE, puede enviar texto o imágenes y vínculos.

Para enviar mensajes SMS o de LINE a un teléfono móvil se necesita:

* Una cuenta externa configurada en el canal **[!UICONTROL Mobile (SMS)]** o en el canal **[!UICONTROL LINE]**.
* Una plantilla de envío de SMS o LINE vinculada correctamente a esta cuenta externa.

## Notificaciones push {#push-notifications}

Adobe Campaign permite enviar [notificaciones push](../../delivery/using/about-mobile-app-channel.md) personalizadas y segmentadas a dispositivos móviles iOS y Android mediante aplicaciones especializadas. Una vez realizados los pasos de configuración e integración, se pueden crear y realizar las entregas de iOS y Android. También se pueden diseñar notificaciones rich con imágenes o vídeos.

## Correo postal {#direct-mail}

El [correo postal](../../delivery/using/about-direct-mail-channel.md) es un canal sin conexión que le permite personalizar y generar el archivo requerido por los proveedores de correo postal. Esto le ofrece la posibilidad de mezclar canales en línea y sin conexión para los viajes de los clientes.

Los canales en línea permiten crear los mensajes (correo electrónico, SMS, envío por aplicaciones móviles, etc.) y enviarlos a su público directamente desde Adobe Campaign. Con los canales sin conexión esto es diferente. Al preparar una entrega de correo postal, Adobe Campaign genera un archivo con todos los perfiles de destino y la información de contacto elegida (por ejemplo, una dirección postal). Después, puede enviar este archivo al proveedor de correo postal que se encarga de la entrega real.
