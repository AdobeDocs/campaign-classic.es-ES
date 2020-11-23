---
solution: Campaign Classic
product: campaign
title: Ejecución de entrega
description: Ejecución de entrega
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '130'
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