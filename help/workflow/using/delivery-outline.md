---
product: campaign
title: Descripción de la entrega
description: Descubra más información sobre la actividad del flujo de trabajo Descripción de la entrega
feature: Workflows, Targeting Activity
hide: true
exl-id: b4dee085-ccc4-43fd-850d-1501a99272aa
TQID: https://experienceleague.adobe.com/-KNip5bdMEMgGw7dz6Y4SQ4ueu-iPvYDF0D01hvGn94
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
  - id: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 267
ht-degree: 100%

---

# Descripción del envío{#delivery-outline}



La **descripción de la entrega** permite utilizar una descripción en un flujo de trabajo de la campaña. El esquema debe haberse creado con anterioridad en la campaña.

Para obtener más información sobre los esquemas de entrega en Adobe Campaign, consulte esta [sección](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

Para configurar la actividad, simplemente se debe seleccionar el esquema que desee y la fecha de contacto planificada. Se pueden agregar reglas de filtrado añadiendo tipologías o reglas tipológicas.

## Ejemplo: Inserción de una oferta mediante un esquema de entrega {#example--inserting-an-offer-via-a-delivery-outline}

La actividad **Descripción de entrega**, disponible en los flujos de trabajo de la campaña, permite presentar ofertas especificadas en una descripción de entrega de la campaña en curso.

>[!NOTE]
>
>El paquete de **Interaction** debe estar instalado.

1. En un flujo de trabajo, añada una actividad de descripción de la entrega antes de añadir una de entrega.
1. En la actividad del esquema de entrega, especifique el que desee utilizar.

   Para obtener más información sobre esquemas de entrega específicos, consulte esta [sección](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

1. Rellene los campos disponibles en función de la entrega.
1. Hay dos casos posibles:

   * Si desea acceder al motor de oferta, marque la casilla **[!UICONTROL Restrict the number of propositions selected]**. Especifique el espacio de oferta y el número de propuestas que se presentarán en la entrega.

     El motor de oferta tendrá en cuenta las reglas de elegibilidad y las consideraciones de oferta.

   * Si no selecciona la casilla, todas las ofertas del esquema de entrega se presentarán sin recurrir al motor de oferta.

   La vista previa tiene en cuenta el número de ofertas especificadas en la entrega. Cuando se ejecuta un flujo de trabajo, se tiene en cuenta el número especificado en el esquema de entrega.

   ![](assets/int_compo_offre_wf1.png)
