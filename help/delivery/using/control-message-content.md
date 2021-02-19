---
solution: Campaign Classic
product: campaign
title: Acerca de la capacidad de envío en Adobe Campaign Classic
description: Obtenga más información sobre la administración de la capacidad de envío en Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 100%

---


# Control del contenido del mensaje{#control-message-content}

Para mejorar la tasa de envío de correos electrónicos y asegurarse de que los mensajes lleguen a los destinatarios, el correo electrónico debe respetar cierto número de normas detalladas a continuación.

## Dirección del remitente {#sender-address}

Algunos ISP verifican la validez de la dirección del remitente (Desde) antes de aceptar mensajes. Una dirección mal formada puede resultar en que el servidor receptor la rechace. Debe asegurarse de proporcionar una dirección correcta en el nivel de instancia (menú **[!UICONTROL Tools > Advanced > Deployment wizard...]**) o en los escenarios más utilizados.

## Formulario y vínculo de exclusión {#opt-out}

De forma predeterminada, cuando se analiza el mensaje, una regla de tipología comprueba si se ha incluido un vínculo de exclusión y genera una advertencia si falta. Puede cambiar esta regla para que se produzca un error en lugar de una simple advertencia y evitar que una entrega salga sin este vínculo.

Debe comprobar que el vínculo de exclusión funciona correctamente antes de cada envío. Por ejemplo, al enviar la prueba, asegúrese de que el vínculo sea válido, de que el formulario esté en línea y de que al validarlo se cambie el valor del campo **[!UICONTROL No longer contact this recipient]** a **[!UICONTROL Yes]**. Debe realizar esta comprobación sistemáticamente porque siempre es posible el error humano al introducir el vínculo o al cambiar el formulario.

Si se detecta un problema relacionado con la baja después de que se inicie la entrega, aún es posible realizar una baja manualmente (mediante la función de actualización masiva, por ejemplo) para los destinatarios que hacen clic en el vínculo de exclusión incluso si no pudieron confirmar su elección.

Como regla general, no intente interferir con los destinatarios que deseen optar por la exclusión obligándolos a rellenar campos como, por ejemplo, su dirección de correo electrónico o su nombre. El formulario solo debe tener un botón de validación y la reconciliación solo debe realizarse en el identificador cifrado. La solicitud de confirmación adicional no es fiable: un usuario puede tener dos direcciones de correo electrónico redirigidas al mismo cuadro (por ejemplo: firstname.lastname@club.com y firstname.lastname@internet-club.com). Si el destinatario solo puede recordar la primera dirección y desea cancelar la suscripción a través de un mensaje enviado a la otra, el formulario lo rechazará porque el identificador cifrado y la dirección de correo electrónico introducidos no coincidirán.

## SpamAssassin {#spamassassin}

Adobe Campaign se puede configurar para que funcione con SpamAssassin. Esto le permite puntuar correos electrónicos para determinar si un mensaje corre el riesgo de que las herramientas de filtrado de correo no deseado utilizadas durante la recepción lo consideren como no deseado.

Antes de iniciar una entrega, la pestaña Preview le permite evaluar los riesgos. Un mensaje de advertencia le muestra el resultado de la prueba.

Obtenga más información en esta [sección](../../delivery/using/spamassassin.md).