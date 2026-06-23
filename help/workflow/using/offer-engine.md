---
product: campaign
title: Motor de oferta
description: Motor de oferta
feature: Workflows, Interaction
hide: true
exl-id: 8db4b04f-7754-4a49-ab72-afc916888ebb
TQID: https://experienceleague.adobe.com/oAzSAhtWhfJTWcWowjaewtlVucahY839933SaCQZO10
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
  - id: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 137
ht-degree: 100%

---

# Motor de oferta{#offer-engine}



La actividad **[!UICONTROL Offer engine]** permite definir una llamada al motor de oferta antes de una entrega.

Esta actividad funciona con el mismo principio que la actividad de enriquecimiento con acceso al motor, enriquece los datos de población entrantes con una oferta calculada por el motor antes de una entrega.

![](assets/int_offerengine_activity2.png)

Después de configurar la consulta (consulte esta [sección](query.md)):

1. Añada y abra una actividad **[!UICONTROL Offer engine]**.
1. Complete los diferentes campos disponibles para especificar el uso de los parámetros del motor de oferta (ofrecer espacio, categoría o tema, fecha de contacto, número de ofertas que desea mantener). Según estos parámetros, el motor calculará automáticamente las ofertas a agregar.

   >[!CAUTION]
   >
   >Si utiliza esta actividad, solo se almacenará la oferta que se haya utilizado en la entrega.

   ![](assets/int_offerengine_activity1.png)

1. A continuación, configure una actividad de entrega que corresponda al canal elegido. Consulte [Envíos multicanal](cross-channel-deliveries.md).
