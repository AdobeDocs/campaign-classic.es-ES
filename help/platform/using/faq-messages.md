---
product: campaign
title: Preguntas más frecuentes sobre Test and Send
description: Preguntas frecuentes sobre Campaign Classic
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 7fc24ef2-b021-440b-b1f2-8c77e2425328
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 100%

---

# Validación, envío y seguimiento de mensajes {#validate-send-track}

## Pruebas y validación {#test-and-validate-before-sending}

Aprenda a realizar pasos de prueba y validación antes de enviar mensajes en Adobe Campaign.

### ¿Qué es el análisis de entrega? {#what-is-the-delivery-analysis-}

El análisis de envíos es la fase durante la cual se calcula la población objetivo y se prepara el contenido de entrega. Una vez finalizada, la entrega está listo para realizarse. Consulte los registros para asegurarse de que todo es correcto.

[Haga clic aquí para obtener más información](../../delivery/using/steps-validating-the-delivery.md).

### ¿Por qué debería generar pruebas? {#why-should-i-create-proofs-}

Adobe recomienda encarecidamente crear mensajes de prueba para probar la entrega en un grupo de aprobación antes de enviarlo al objetivo principal. A continuación, puede validar los parámetros de contenido, personalización y envío de mensajes.

[Haga clic aquí para obtener más información](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### ¿Cómo se utilizan las direcciones semilla en Adobe Campaign? {#how-to-use-seed-addresses-in-adobe-campaign-}

Las direcciones semilla se utilizan para dirigirse a los destinatarios que no coinciden con los criterios de destino definidos. Estos destinatarios se añaden al objetivo: pueden importarse o crearse directamente en la entrega o la campaña. Para las entregas de correo postal, se añaden durante la extracción y la mezcla en el documento de salida.

Estas son sus ventajas:

* Sustitución aleatoria de campos con datos de perfiles de destinatario. Esto permite introducir solo la dirección de correo electrónico, por ejemplo, en la sección de dirección semilla.
* Al utilizar un flujo de trabajo con funcionalidades de gestión de datos, los datos adicionales procesados en las entregas se pueden introducir en el nivel de dirección semilla para forzar los valores: esto evita la sustitución aleatoria de valores.

[Haga clic aquí para obtener más información sobre las direcciones semilla](../../delivery/using/about-seed-addresses.md).

### ¿Cómo puedo configurar un proceso de aprobación antes de enviar mensajes? {#how-can-i-set-up-an-approval-process-before-sending-messages-}

Para detectar posibles errores en la configuración del mensaje, Adobe recomienda configurar un ciclo de validación de entrega. Asegúrese de que el contenido se aprueba con la frecuencia necesaria al enviar pruebas a los destinatarios de prueba. Se debe enviar una prueba cada vez que se realiza un cambio para aprobar el contenido.

[Haga clic aquí para obtener más información](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### ¿Qué es una regla de tipología? {#what-is-a-typology-rule-}

Para evitar conflictos entre campañas, Adobe Campaign puede probar distintas combinaciones mediante la aplicación de reglas de restricción específicas. Esto garantiza que los mensajes enviados respondan de la mejor forma a las necesidades y expectativas de los clientes, de acuerdo con las políticas de comunicación de la compañía.

[Haga clic aquí para obtener más información](../../campaign/using/about-campaign-typologies.md).

## Enviar mensajes {#send-your-messages}

Aprenda a enviar mensajes en varios canales con Adobe Campaign.

### ¿Cómo puedo enviar correos electrónicos en cadena? {#how-can-i-send-emails-in-waves-}

Antes de enviar un contenido a una población grande, puede [configurar una cadena](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves) para dividir mensajes en varios lotes y equilibrar la carga.

### ¿Cuáles son los pasos clave para crear un correo electrónico en Campaign? {#which-are-the-key-steps-to-create-an-email-in-campaign-}

Una vez que la entrega de correo electrónico se haya creado y validado, puede enviarlo. Puede decidir enviar el correo electrónico al objetivo principal inmediatamente o programar una entrega para una fecha posterior. Si es necesario, antes de que esto suceda, también puede estimar la población objetivo.

[Haga clic aquí para obtener más información](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### ¿Cómo se puede programar una entrega? {#how-to-schedule-a-delivery-}

Puede retrasar la entrega de mensajes para programar su fecha o manejar la presión de ventas y evitar solicitar en exceso a una población.

[Haga clic aquí para obtener más información](../../delivery/using/steps-sending-the-delivery.md#scheduling-the-delivery-sending).

### ¿Se puede añadir un adjunto a los correos electrónicos? {#can-i-add-an-attachment-to-emails-}

Con Campaign Classic, puede añadir archivos adjuntos personalizados a sus correos electrónicos.

[Haga clic aquí para obtener más información sobre los archivos adjuntos en correos electrónicos](../../delivery/using/attaching-files.md).

## Realizar un seguimiento de mensajes y medir su impacto {#track-your-messages-and-measure-their-impact}

Una vez enviados los mensajes, aprenda a hacer un seguimiento y medir su impacto con Adobe Campaign.

### ¿Cómo puedo configurar los vínculos rastreados en una entrega de correo electrónico? {#how-can-i-configure-tracked-links-in-an-email-delivery-}

Para cada entrega, puede hacer un seguimiento de la recepción de mensajes y la activación de los vínculos insertados en el contenido del mensaje. Esto permite hacer un seguimiento del comportamiento de los destinatarios haciendo un seguimiento de las acciones de entrega para las que se segmentaron.

Para cada URL del mensaje, puede elegir si desea activar o no el seguimiento, cambiar la etiqueta del vínculo o agrupar vínculos por categorías con el propósito de generar informes, por ejemplo.

[Haga clic aquí para obtener más información](../../delivery/using/about-message-tracking.md) sobre cómo realizar un seguimiento de los mensajes en Campaign Classic.

### ¿Dónde puedo acceder a los &quot;logs&quot; de envío y seguimiento? {#where-can-i-access-delivery-and-tracking-logs-}

Aprenda a realizar un seguimiento de las entregas y comprender el comportamiento de los destinatarios [desde esta página](../../delivery/using/delivery-dashboard.md).

### ¿Dónde puedo obtener los informes de envío? {#where-can-i-get-delivery-reports-}

Adobe Campaign incluye un conjunto de informes para supervisar las entregas y realizar un seguimiento de los mensajes.

[Haga clic aquí para obtener más información sobre los informes integrados](../../reporting/using/delivery-reports.md).

### ¿Cómo califica y gestiona las direcciones en cuarentena Adobe Campaign? {#how-does-adobe-campaign-qualify-and-manage-quarantine-addresses-}

Adobe Campaign administra una lista de direcciones en cuarentena. Los destinatarios cuya dirección se haya puesto en cuarentena se excluyen de forma predeterminada durante el análisis de la entrega y no se tendrán en cuenta para la segmentación. Una dirección de correo electrónico se puede poner en cuarentena, por ejemplo, cuando el buzón está lleno o si la dirección no existe.

[Haga clic aquí para obtener más información sobre la gestión de cuarentena](../../delivery/using/understanding-quarantine-management.md).
