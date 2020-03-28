---
title: SMS entrante
seo-title: SMS entrante
description: SMS entrante
seo-description: null
page-status-flag: never-activated
uuid: 895e54df-e795-48ac-ac94-96dab454c550
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: event-activities
discoiquuid: fa9ae600-91fc-4aea-ae02-8ab9064947ac
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# SMS entrante{#inbound-sms}

La actividad de **Inbound SMS** permite descargar y procesar mensajes de texto desde una cuenta externa.

## Propiedades {#properties}

![](assets/sms_rec_edit.png)

La primera pestaña de la actividad de **Inbound SMS** permite introducir los parámetros de enrutamiento para mensajes SMS e introducir la secuencia de comandos que se ejecutará al recibir cada mensaje. La segunda pestaña le permite asignar una programación a la actividad y la tercera pestaña define las condiciones de caducidad de la actividad.

1. **[!UICONTROL SMS routing]**: Seleccione la cuenta externa que desea utilizar para la recuperación de SMS. Las cuentas externas se configuran en el nodo **[!UICONTROL Administration > Platform > External accounts]** del árbol.
1. **[!UICONTROL Secuencia de comandos]**
1. **[!UICONTROL Programación]**

   ![](assets/sms_rec_edit_2.png)

1. **[!UICONTROL Caducidad]**

Las pestañas **[!UICONTROL Script]**, **[!UICONTROL Schedule]** y **[!UICONTROL Expiry]** se detallas en [Correos electrónicos entrantes](../../workflow/using/inbound-emails.md).
