---
title: Ejecución de envío
seo-title: Ejecución de envío
description: Ejecución de envío
seo-description: null
page-status-flag: never-activated
uuid: d4f4cea7-783b-45d3-b004-297104f0a906
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: afb375de-2de3-47ad-8b37-664cc04864e8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 211556bbf023731ffeab2e90692410a852ab3555

---


# Ejecución de envío{#delivery-execution}

>[!NOTE]
>
>El MTA prioriza el procesamiento de los mensajes transaccionales sobre cualquier otro envío.

En la instancia de ejecución, una vez que se hayan completado las etapas de enriquecimiento y se haya vinculado una plantilla de envío al evento, se realiza el envío. Todas las entregas se agrupan en la **[!UICONTROL Administration > Production > Message Center > Default > Deliveries]** carpeta.

![](assets/messagecenter_deliveries_execinstances_001.png)

De forma predeterminada, se clasifican en subcarpetas por mes de envío.

Esta ordenación se puede cambiar en las propiedades de la plantilla de mensaje como se muestra a continuación.

![](assets/messagecenter_deliveries_properties_001.png)

>[!NOTE]
>
>En el caso de instalaciones alojadas o híbridas, si se ha actualizado a la MTA mejorada, todos los mensajes transaccionales también se pueden enviar con la MTA mejorada de Adobe Campaign para mejorar la entrega, el rendimiento y la gestión de devoluciones. Todos los impactos son los mismos que para los mensajes de marketing estándar y se detallan en el documento MTA [mejorado de](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html) Adobe Campaign.