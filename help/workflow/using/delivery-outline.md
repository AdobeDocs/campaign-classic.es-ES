---
solution: Campaign Classic
product: campaign
title: Descripción de la entrega
description: Descubra más información sobre la actividad del flujo de trabajo Descripción de la entrega
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: b4dee085-ccc4-43fd-850d-1501a99272aa
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '267'
ht-degree: 100%

---

# Descripción de la entrega{#delivery-outline}

La **descripción de la entrega** permite utilizar una descripción en un flujo de trabajo de la campaña. El esquema debe haberse creado con anterioridad en la campaña.

Para obtener más información sobre los esquemas de entrega en Adobe Campaign, consulte esta [sección](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

Para configurar la actividad, simplemente se debe seleccionar el esquema que desee y la fecha de contacto planificada. Se pueden agregar reglas de filtrado añadiendo tipologías o reglas tipológicas.

## Inserción de una oferta mediante un esquema de entrega {#example--inserting-an-offer-via-a-delivery-outline}

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

      El motor de oferta tendrá en cuenta las normas de idoneidad y las consideraciones de oferta.

   * Si no selecciona la casilla, todas las ofertas del esquema de entrega se presentarán sin recurrir al motor de oferta.

   La vista previa tiene en cuenta el número de ofertas especificadas en la entrega. Cuando se ejecuta un flujo de trabajo, se tiene en cuenta el número especificado en el esquema de entrega.

   ![](assets/int_compo_offre_wf1.png)
