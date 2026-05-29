---
product: campaign
title: Selección de una asignación de destino
description: Obtenga información sobre cómo asignar destinos
feature: Delivery Templates
hide: true
role: User
exl-id: b5514fa3-1e65-45dc-8e40-d1ba3b673e7a
TQID: https://experienceleague.adobe.com/VpmfQdFoJ2Lfzetqx-s5MAdFdTTEsHxz2ISL15wNXIo
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 177
ht-degree: 100%

---

# Selección de una asignación de destino{#selecting-a-target-mapping}

De forma predeterminada, las plantillas de envío tienen como destino **[!UICONTROL Recipients]**. Por consiguiente, la asignación de destinatario utiliza los campos de la tabla **nms:recipient**. Adobe Campaign ofrece otros destinos de mapeo para las entregas, que puede usar según sus necesidades.

![](assets/delivery_select_mapping.png)

Estos mapeos son los siguientes:

| Name | Uso | Esquema estándar |
|---|---|---|
| Recipients | Envío a destinatarios de la base de datos de Adobe Campaign | nms:recipient |
| Visitantes | Envío a los visitantes cuyos perfiles se hayan recopilado mediante recomendación (marketing viral) o a través de redes sociales como por ejemplo Facebook o X (anteriormente conocido como Twitter). | mns:visitor |
| Suscripciones | Envío a destinatarios suscritos a un servicio de información como un boletín informativo | nms:subscription |
| Suscripciones de visitantes | Envío a los visitantes que están suscritos a un servicio de información | nms:visitorSub |
| Servicio | Publicación en una cuenta de X o en una página de Facebook | nms:service |
| Operadores | Envío a los operadores de Adobe Campaign | nms:operator |
| Archivo externo | Envío a través de un archivo que contiene toda la información necesaria para la entrega | No hay ningún esquema vinculado, no se ha introducido ningún destino |

>[!NOTE]
>
>También puede crear nuevos destinos de mapeo. Esta operación está reservada para usuarios expertos. Para obtener más información, consulte [esta sección](../../configuration/using/target-mapping.md).
