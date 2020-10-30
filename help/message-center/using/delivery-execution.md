---
title: Ejecución de entrega
seo-title: Ejecución de entrega
description: Ejecución de entrega
seo-description: null
page-status-flag: never-activated
uuid: d4f4cea7-783b-45d3-b004-297104f0a906
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: afb375de-2de3-47ad-8b37-664cc04864e8
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '132'
ht-degree: 100%

---


# Ejecución de entrega{#delivery-execution}

>[!NOTE]
>
>El MTA prioriza el procesamiento de los mensajes transaccionales sobre cualquier otro envío.

En la instancia de ejecución, una vez que se haya completado la etapa de enriquecimiento y se haya vinculado una plantilla de envío al evento, se realiza el envío. Todos las entregas se agrupan en la carpeta **[!UICONTROL Administration > Production > Message Center > Default > Deliveries]**.

![](assets/messagecenter_deliveries_execinstances_001.png)

De forma predeterminada, se clasifican en subcarpetas por mes de envío.

Esta ordenación se puede cambiar en las propiedades de la plantilla de mensaje como se muestra a continuación.

![](assets/messagecenter_deliveries_properties_001.png)

>[!NOTE]
>
>En el caso de instalaciones alojadas o híbridas, si se ha actualizado a la MTA mejorada, todos los mensajes transaccionales también se pueden enviar con la MTA mejorada de Adobe Campaign para mejorar la capacidad de envío, el rendimiento y la gestión de rechazos. Todos los impactos son los mismos que para los mensajes de marketing estándar y se detallan en el documento [MTA mejorado de Adobe Campaign](https://helpx.adobe.com/es/campaign/kb/acc-campaign-enhanced-mta.html).