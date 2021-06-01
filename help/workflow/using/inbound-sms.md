---
product: campaign
title: SMS entrante
description: Descubra más información sobre la actividad del flujo de trabajo SMS entrante
audience: workflow
content-type: reference
topic-tags: event-activities
exl-id: 94a9d50b-4ead-4815-8d12-942fa78b4e8a
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 100%

---

# SMS entrante{#inbound-sms}

La actividad de **Inbound SMS** permite descargar y procesar mensajes de texto desde una cuenta externa.

## Propiedades {#properties}

![](assets/sms_rec_edit.png)

La primera pestaña de la actividad de **Inbound SMS** permite introducir los parámetros de enrutamiento para mensajes SMS e introducir la secuencia de comandos que se ejecutará al recibir cada mensaje. La segunda pestaña le permite asignar una programación a la actividad y la tercera pestaña define las condiciones de caducidad de la actividad.

1. **[!UICONTROL SMS routing]**: Seleccione la cuenta externa que desea utilizar para la recuperación de SMS. Las cuentas externas se configuran en el nodo **[!UICONTROL Administration > Platform > External accounts]** del árbol.
1. **[!UICONTROL Script]**
1. **[!UICONTROL Schedule]**

   ![](assets/sms_rec_edit_2.png)

1. **[!UICONTROL Expiration]**

Las pestañas **[!UICONTROL Script]**, **[!UICONTROL Schedule]** y **[!UICONTROL Expiry]** se detallan en [Correos electrónicos entrantes](../../workflow/using/inbound-emails.md).
