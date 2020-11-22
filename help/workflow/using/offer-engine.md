---
solution: Campaign Classic
product: campaign
title: Motor de oferta
description: Motor de oferta
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 100%

---


# Motor de oferta{#offer-engine}

La actividad **[!UICONTROL Offer engine]** permite definir una llamada al motor de oferta antes de una entrega.

Esta actividad funciona con el mismo principio que la actividad de enriquecimiento con acceso al motor, enriquece los datos de población entrantes con una oferta calculada por el motor antes de una entrega.

![](assets/int_offerengine_activity2.png)

Después de configurar la consulta (consulte esta [sección](../../workflow/using/query.md)):

1. Añada y abra una actividad **[!UICONTROL Offer engine]**.
1. Complete los diferentes campos disponibles para especificar el uso de los parámetros del motor de oferta (ofrecer espacio, categoría o tema, fecha de contacto, número de ofertas que desea mantener). Según estos parámetros, el motor calculará automáticamente las ofertas a agregar.

   >[!CAUTION]
   >
   >Si utiliza esta actividad, solo se almacenará la oferta que se haya utilizado en la entrega.

   ![](assets/int_offerengine_activity1.png)

1. A continuación, configure una actividad de entrega que corresponda al canal elegido. Consulte [Envíos multicanal](../../workflow/using/cross-channel-deliveries.md).

