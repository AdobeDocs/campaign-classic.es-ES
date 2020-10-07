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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 82%

---


# SMS entrante{#inbound-sms}

La actividad de **Inbound SMS** permite descargar y procesar mensajes de texto desde una cuenta externa.

## Propiedades {#properties}

![](assets/sms_rec_edit.png)

La primera pestaña de la actividad de **Inbound SMS** permite introducir los parámetros de enrutamiento para mensajes SMS e introducir la secuencia de comandos que se ejecutará al recibir cada mensaje. La segunda pestaña le permite asignar una programación a la actividad y la tercera pestaña define las condiciones de caducidad de la actividad.

1. **[!UICONTROL SMS routing]**: Seleccione la cuenta externa que desea utilizar para la recuperación de SMS. External accounts are configured via the **[!UICONTROL Administration > Platform > External accounts]** node of the tree.
1. **[!UICONTROL Script]**
1. **[!UICONTROL Schedule]**

   ![](assets/sms_rec_edit_2.png)

1. **[!UICONTROL Expiration]**

The **[!UICONTROL Script]**, **[!UICONTROL Schedule]** and **[!UICONTROL Expiry]** tabs are detailed in [Inbound Emails](../../workflow/using/inbound-emails.md).
