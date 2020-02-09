---
title: Descripción del envío
seo-title: Descripción del envío
description: Descripción del envío
seo-description: null
page-status-flag: never-activated
uuid: 2b924cc6-6b71-481e-acab-2d035bbc2852
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: a2a65f97-425b-44b2-8cf4-beea850423bc
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 67dce820b7a90163032ee72263a9dd23b521ea69

---


# Descripción del envío{#delivery-outline}

La descripción del envío permite utilizar una descripción en un flujo de trabajo de Campaign. El esquema debe haberse creado con anterioridad en la campaña.

Para obtener más información sobre los esquemas de entrega en Adobe Campaign, consulte esta [sección](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

Para configurar la actividad, simplemente se debe seleccionar el esquema que desee y la fecha de contacto planificada. Se pueden agregar reglas de filtrado añadiendo tipologías o reglas tipológicas.

## Example: Inserting an offer via a delivery outline {#example--inserting-an-offer-via-a-delivery-outline}

La actividad de descripción de envío, disponible en los flujos de trabajo de la campaña, permite presentar ofertas especificadas en una descripción de envío de la campaña en curso.

>[!NOTE]
>
>El paquete de **Interaction** debe estar instalado.

1. En un flujo de trabajo, añada una actividad de descripción del envío antes de añadir una de envío.
1. En la actividad del esquema de entrega, especifique el que desee utilizar.

   Para obtener más información sobre esquemas de entrega específicos, consulte esta [sección](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

1. Rellene los campos disponibles en función del envío.
1. Hay dos casos posibles:

   * If you would like to call the offer engine, check the **[!UICONTROL Restrict the number of propositions selected]** box. Especifique el espacio de oferta y el número de propuestas que se presentarán en la entrega.

      El motor de oferta tendrá en cuenta las normas de idoneidad y las consideraciones de oferta.

   * Si no selecciona la casilla, todas las ofertas del esquema de entrega se presentarán sin recurrir al motor de oferta.
   La vista previa tiene en cuenta el número de ofertas especificadas en la entrega. Cuando se ejecuta un flujo de trabajo, se tiene en cuenta el número especificado en el esquema de entrega.

   ![](assets/int_compo_offre_wf1.png)

