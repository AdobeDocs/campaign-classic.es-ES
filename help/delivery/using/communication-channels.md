---
solution: Campaign Classic
product: campaign
title: Canales de comunicación
description: Cree envíos para enviar mensajes personalizados en diferentes canales.
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
translation-type: tm+mt
source-git-commit: 8bf1b5b1a6763cf933d86f2af61b2bb68e870222
workflow-type: tm+mt
source-wordcount: '1204'
ht-degree: 100%

---


# Canales de comunicación{#communication-channels}

Con Adobe Campaign, puede enviar campañas en canales múltiples incluidos correos electrónicos, SMS, mensajes LINE, notificaciones push y correo postal y medir su eficacia mediante varios [informes](../../reporting/using/delivery-reports.md) dedicados. Estos mensajes están diseñados y enviados por medio de envíos y pueden personalizarse para cada destinatario.

Las funciones principales incluyen establecimiento de objetivos, definición y personalización de mensajes, ejecución de comunicaciones y los informes operativos asociados. El punto de acceso funcional principal es el asistente de envío. Este punto de acceso lleva a varias funciones incluidas en Adobe Campaign.

>[!NOTE]
>
>Adobe Campaign ofrece un conjunto de herramientas para supervisar su capacidad de envío y optimizar la entrega por correo electrónico. Obtenga más información en [esta sección](../../delivery/using/about-deliverability.md).

El envío puede automatizarse al preparar una entrega o al enviarlo en el proceso de un flujo de trabajo. Para obtener más información sobre las actividades de tipo envío en los flujos de trabajo, consulte [esta sección](../../workflow/using/about-action-activities.md).

Adobe Campaign ofrece los siguientes canales de envío:

1. **Canal de correo electrónico**: las entregas de correo electrónico le permiten enviar correos electrónicos personalizados a la población objetivo. Consulte [Acerca del canal de correo electrónico](../../delivery/using/about-email-channel.md).
1. **Canal de correo postal**: las entregas de correo postal permiten generar un archivo de extracción que contenga datos sobre la población objetivo. [Acerca del canal de correo postal](../../delivery/using/about-direct-mail-channel.md).
1. **Canal móvil**: las entregas en canales móviles permiten enviar mensajes SMS o de LINE personalizados a la población objetivo. Consulte [el canal de SMS](../../delivery/using/sms-channel.md).
1. **Canal de aplicación móvil**: los envíos de aplicaciones móviles permiten enviar notificaciones a sistemas iOS y Android. Consulte el capítulo [canal de aplicaciones móviles](../../delivery/using/about-mobile-app-channel.md).

   En [esta página](../../delivery/using/steps-about-delivery-creation-steps.md#other-channels) se describen otros canales.

   >[!NOTE]
   >
   >El número de canales disponibles depende del contrato. Compruebe el acuerdo de licencia.

Los envíos se pueden realizar **en línea** (por correo electrónico, uno de los canales móviles y por notificaciones push) y **sin conexión** (por el canal de correo postal).

Dependiendo del canal, los modos de envío pueden ser:

* Envío directo mediante Adobe Campaign (modo predeterminado del canal por correo electrónico).
* Envío externo a través de un operador especializado que recibe el archivo de salida generado por el asistente de envío (modo predeterminado del canal por correo postal).

Las cuentas externas se configuran mediante el nodo **[!UICONTROL Administration > Platform > External accounts]**. Esta configuración solo deben realizarla usuarios expertos.

## Envíos por correo electrónico {#email-deliveries}

El [canal de correo electrónico](../../delivery/using/about-email-channel.md) es uno de los canales principales de Adobe Campaign, el cual permite programar y enviar correos electrónicos personalizados a objetivos específicos.

Se pueden enviar diferentes tipos de correos electrónicos:

* Correos electrónicos de envío único: correos electrónicos que se pueden enviar una vez a un destino definido. Suelen utilizarse para promocionar un contenido específico que se prepara y se envía una sola vez (newsletter, correo electrónico promocional, etc.).
* Correos electrónicos recurrentes: en una campaña, envíe el mismo correo electrónico regularmente y añada cada envío y sus informes periódicamente. Se envía el mismo correo electrónico, pero normalmente a un destino diferente, en función del destino apto para el día de la entrega. Un ejemplo común es un correo electrónico de cumpleaños. Para obtener más información, consulte [envíos recurrentes](../../workflow/using/recurring-delivery.md).
* Correos electrónicos de transacción: correos electrónicos individuales que se activan según el comportamiento de los clientes. Consulte [mensajería transaccional](../../message-center/using/about-transactional-messaging.md).

Para obtener más información sobre uso de las entregas y recomendaciones, consulte [Prácticas recomendadas de envío](../../delivery/using/delivery-best-practices.md) de Campaign.

Para obtener más información sobre los distintos tipos de envíos, consulte [esta sección](#types-of-deliveries).

## Envíos a móviles {#mobile-deliveries}

Adobe Campaign le permite enviar mensajes [SMS](../../delivery/using/sms-channel.md) y de [LINE](../../delivery/using/line-channel.md) a móviles.

En los mensajes SMS, puede crear, modificar y personalizar mensajes solo de formato de texto. También puede obtener una previsualización de los mensajes SMS antes de enviarlos.

Para los mensajes de LINE, puede enviar texto o imágenes y vínculos.

Para enviar mensajes SMS o de LINE a un teléfono móvil se necesita:

* Una cuenta externa configurada en el canal **[!UICONTROL Mobile (SMS)]** o en el canal **[!UICONTROL LINE]**.
* Una plantilla de envíos de SMS o LINE vinculada correctamente a esta cuenta externa.

## Notificaciones push {#push-notifications}

Adobe Campaign permite enviar [notificaciones push](../../delivery/using/about-mobile-app-channel.md) personalizadas y segmentadas a dispositivos móviles iOS y Android mediante aplicaciones especializadas. Una vez realizados los pasos de configuración e integración, se pueden crear y realizar las entregas de iOS y Android. También se pueden diseñar notificaciones rich con imágenes o vídeos.

## Correo postal {#direct-mail}

El [correo postal](../../delivery/using/about-direct-mail-channel.md) es un canal sin conexión que le permite personalizar y generar el archivo requerido por los proveedores de correo postal. Esto le ofrece la posibilidad de mezclar canales en línea y sin conexión para los recorridos de los clientes.

Los canales en línea permiten crear los mensajes (correo electrónico, SMS, envío por aplicaciones móviles, etc.) y enviarlos a su público directamente desde Adobe Campaign. Con los canales sin conexión esto es diferente. Al preparar una entrega de correo postal, Adobe Campaign genera un archivo con todos los perfiles de destino y la información de contacto elegida (por ejemplo, una dirección postal). Después, puede enviar este archivo al proveedor de correo postal que se encarga de la entrega real.

## Otros canales {#other-channels}

Plantilla de envíos telefónicos de ofertas de Adobe Campaign, que se utiliza para crear envíos externos. El uso de este canal implica la configuración de metodologías dedicadas para procesar archivos de salida. Los pasos de configuración son los mismos que para el [canal de correo directo](../../delivery/using/about-direct-mail-channel.md).

>[!NOTE]
>
>El canal telefónico no está disponible de forma predeterminada. Su implementación requiere la participación de un asesor o un socio de Adobe. Para obtener más información, póngase en contacto con su representante de Adobe.

Además, las entregas de tipo “Otros” utilizan una plantilla técnica específica que no ejecuta un proceso: esto les permite administrar las acciones de marketing ejecutadas fuera de la plataforma de Adobe Campaign.

Este canal no tiene un mecanismo específico. Es un canal genérico con su propia opción de enrutamiento de cuenta externa, tipo de plantilla de envíos y actividad de flujo de trabajo de campaña, igual que cualquier otro canal de comunicación disponible en Adobe Campaign.

Este canal se ha diseñado únicamente para fines descriptivos, por ejemplo para definir envíos para los que se desea mantener un seguimiento del destinatario de una campaña realizada en una herramienta que no sea Adobe Campaign.

## Tipos de entregas{#types-of-deliveries}

Existen tres tipos de objetos de envío en Campaign:

### Entrega única {#single-delivery}

Una **entrega** es un objeto de envío independiente que se ejecuta una vez. Puede duplicarse y prepararse de nuevo; sin embargo, cuando esté en su estado final (cancelado, detenido, finalizado), no se puede volver a utilizar.

Las entregas se pueden crear desde la lista de entregas o dentro de un flujo de trabajo mediante una actividad de [entrega](../../workflow/using/delivery.md).

Los flujos de trabajo también proporcionan actividades de entrega específicas según el tipo de canal que desee utilizar. Para obtener más información sobre estas actividades, consulte [esta sección](../../workflow/using/cross-channel-deliveries.md).

### Entrega recurrente {#recurring-delivery}

Una **entrega recurrente** le permite crear un nuevo envío cada vez que se ejecute la actividad. Esto evita tener que crear una nueva entrega para las tareas recurrentes.

Por ejemplo, si ejecuta este tipo de actividad una vez al mes, tras un año acaba teniendo 12 envíos.

Las entregas recurrentes se crean en los flujos de trabajo a través de la actividad de [entrega recurrente](../../workflow/using/recurring-delivery.md). En esta sección se muestra un ejemplo de esta actividad: [Creación de una entrega recurrente en un flujo de trabajo de objetivos](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

### Entrega continua {#continuous-delivery}

Una **entrega continua** le permite añadir nuevos destinatarios a una entrega existente, lo que evita tener que crear una nueva entrega cada vez que se ejecuta.

Si cambia la información de la entrega (contenido, nombre, etc.), se crea un nuevo objeto de envío en la ejecución de la entrega. Si no se ha cambiado ninguna información, se vuelve a utilizar el mismo objeto de envío y los “logs” de entrega y seguimiento se añaden en el mismo objeto.

Por ejemplo, si ejecuta este tipo de actividad una vez al mes, acaba teniendo un solo envío después de un año (siempre y cuando no haya realizado ningún cambio en la entrega).

Las entregas continuas se crean dentro de flujos de trabajo a través de la [Actividad de entrega continua](../../workflow/using/continuous-delivery.md).
