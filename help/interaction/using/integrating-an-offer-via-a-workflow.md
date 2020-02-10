---
title: Integración de una oferta mediante un flujo de trabajo
seo-title: Integración de una oferta mediante un flujo de trabajo
description: Integración de una oferta mediante un flujo de trabajo
seo-description: null
page-status-flag: never-activated
uuid: 57c4d4e0-6594-46f0-b9ce-2c689fb2eaa2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: delivering-an-offer
discoiquuid: 6e27caea-1f1a-457d-bdec-1f93a12b01cf
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 67dce820b7a90163032ee72263a9dd23b521ea69

---


# Integración de una oferta mediante un flujo de trabajo{#integrating-an-offer-via-a-workflow}

Fuera de la actividad del envío, varias actividades de flujo de trabajo permiten definir la forma en que se presentan las ofertas:

* Descripción del envío
* Enriquecimiento
* Motor de oferta
* Ofertas por celda

## Descripción del envío {#delivery-outline}

La actividad de descripción de envío, disponible en los flujos de trabajo de la campaña, permite presentar ofertas especificadas en una descripción de envío de la campaña en curso.

1. En un flujo de trabajo, añada una actividad de descripción del envío antes de añadir una de envío.
1. En la actividad del esquema de entrega, especifique el que desee utilizar.

   Para obtener más información sobre la descripción de envíos específicos, consulte la guía [Campaign - MRM](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

1. Rellene los campos disponibles en función del envío.
1. Hay dos casos posibles:

   * If you would like to call the offer engine, check the **[!UICONTROL Restrict the number of propositions selected]** box. Especifique el espacio de oferta y el número de propuestas que se presentarán en la entrega.

      El motor de oferta tendrá en cuenta las normas de idoneidad y las consideraciones de oferta.

   * Si no selecciona la casilla, todas las ofertas del esquema de entrega se presentarán sin recurrir al motor de oferta.
   >[!NOTE]
   >
   >La vista previa tiene en cuenta el número de ofertas especificadas en la entrega. Cuando se ejecuta un flujo de trabajo, se tiene en cuenta el número especificado en el esquema de entrega.

   ![](assets/int_compo_offre_wf1.png)

## Enriquecimiento {#enrichment}

La actividad de enriquecimiento permite añadir ofertas o enlaces a ofertas para los destinatarios del envío.

>[!NOTE]
>
>Para obtener más información sobre la actividad de enriquecimiento, consulte la documentación correspondiente en la [guía sobre flujos de trabajo](../../workflow/using/enrichment.md).

Por ejemplo, puede ampliar los datos de una consulta al destinatario antes de un envío.

![](assets/int_enrichment_offer1.png)

Existen dos métodos para especificar propuestas de oferta.

* Especificación de una oferta o acceso al motor de oferta.
* Referencia al enlace de una oferta.

### Especificación de una oferta o acceso al motor de ofertas {#specifying-an-offer-or-a-call-to-the-offer-engine}

Después de configurar la consulta (consulte la [guía sobre flujos de trabajo](../../workflow/using/query.md)).

1. Añada y abra una actividad de enriquecimiento.
1. En la **[!UICONTROL Enrichment]** ficha, seleccione **[!UICONTROL Add data]**.
1. Select **[!UICONTROL An offer proposition]** in the types of data to add.

   ![](assets/int_enrichment_offer2.png)

1. Especifique un identificador y una etiqueta para la propuesta a añadir.
1. Especifique la selección de la oferta. Hay dos formas de hacerlo:

   * **[!UICONTROL Search for the best offer in a category]** :: marque esta opción y especifique los parámetros de llamada del motor de oferta (espacio de oferta, categoría o tema(s), fecha de contacto, número de ofertas que desea mantener). Según estos parámetros, el motor calculará automáticamente las ofertas a agregar. We recommend completing either the **[!UICONTROL Category]** or the **[!UICONTROL Theme]** field, rather than both at the same time.

      ![](assets/int_enrichment_offer3.png)

   * **[!UICONTROL A predefined offer]** : marque esta opción y especifique un espacio de oferta, una oferta específica y una fecha de contacto para configurar directamente la oferta que desee añadir, sin recurrir al motor de oferta.

      ![](assets/int_enrichment_offer4.png)

1. A continuación, configure una actividad de envío que corresponda al canal elegido. Para obtener más información sobre esto, consulte la sección [Inserción de una propuesta de oferta en una sección de envío](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery) .

   >[!NOTE]
   >
   >El número de propuestas disponibles para la vista previa depende de la configuración realizada en la actividad de enriquecimiento y no de cualquier configuración realizada directamente en el envío.

### Referencia al enlace de una oferta {#referencing-a-link-to-an-offer}

También puede hacer referencia a un enlace de oferta en una actividad de ampliación.

Para ello, utilice el proceso siguiente:

1. Seleccione **[!UICONTROL Add data]** en la **[!UICONTROL Enrichment]** ficha de la actividad.
1. In the window where you choose the type of data to add, select **[!UICONTROL A link]**.
1. Seleccione el tipo de enlace que desea establecer y su destino. En este caso, el destino es el esquema de oferta.

   ![](assets/int_enrichment_link1.png)

1. Especifique el vínculo entre los datos de la lista entrante en la actividad de ampliación (lista de destinatarios) y la lista de oferta. Por ejemplo, se puede vincular un código de oferta a un destinatario.

   ![](assets/int_enrichment_link2.png)

1. A continuación, configure una actividad de envío que corresponda al canal elegido. Para obtener más información sobre esto, consulte la sección [Inserción de una propuesta de oferta en una sección de envío](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery) .

   >[!NOTE]
   >
   >El número de propuestas disponibles para la vista previa depende de la configuración realizada en el envío.

### Almacenamiento de calificaciones y consideraciones de oferta {#storing-offer-rankings-and-weights}

De forma predeterminada, cuando se utiliza una actividad **enrichment** para entregar ofertas, sus calificaciones y sus consideraciones no se almacenan en la lista de propuestas.

>[!NOTE]
>
>Recuerde: La **[!UICONTROL Offer engine]** actividad almacena esta información de forma predeterminada.

Sin embargo, se puede almacenar esta información de la siguiente manera:

1. Cree un recurso al motor de oferta en una actividad ampliada colocada después de una consulta y antes de una actividad de entrega. Consulte la sección [Especificación de una oferta o una llamada al motor](../../interaction/using/integrating-an-offer-via-a-workflow.md#specifying-an-offer-or-a-call-to-the-offer-engine) de ofertas.
1. En la ventana principal de la actividad, seleccione **[!UICONTROL Edit additional data...]**.

   ![](assets/ita_enrichment_rankweight_1.png)

1. Add the **[!UICONTROL @rank]** columns for the ranking and **[!UICONTROL @weight]** for the offer weight.

   ![](assets/ita_enrichment_rankweight_2.png)

1. Confirme su adición y guarde el flujo de trabajo.

La entrega almacena automáticamente la clasificación y las consideraciones de las ofertas. This information is visible in the delivery&#39;s **[!UICONTROL Offers]** tab.

## Motor de oferta {#offer-engine}

The **[!UICONTROL Offer engine]** activity also lets you specify a call to the offer engine prior to the delivery.

Esta actividad funciona con el mismo principio que la actividad de enriquecimiento con acceso al motor, enriquece los datos de población entrantes con una oferta calculada por el motor antes de un envío.

![](assets/int_offerengine_activity2.png)

Después de configurar la consulta (consulte la [guía sobre flujos de trabajo](../../workflow/using/query.md)).

1. Add and open an **[!UICONTROL Offer engine]** activity.
1. Complete los diferentes campos disponibles para especificar el uso de los parámetros del motor de oferta (ofrecer espacio, categoría o tema, fecha de contacto, número de ofertas que desea mantener). Según estos parámetros, el motor calculará automáticamente las ofertas a agregar.

   >[!NOTE]
   >
   >Si utiliza esta actividad, solo se almacenará la oferta que se haya utilizado en el envío.

   ![](assets/int_offerengine_activity1.png)

1. A continuación, configure una actividad de envío que corresponda al canal elegido. Para obtener más información sobre esto, consulte la sección [Inserción de una propuesta de oferta en una sección de envío](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery) .

## Ofertas por celda {#offers-by-cell}

The **[!UICONTROL Offers by cell]** activity lets you distribute the inbound population (from a query for example) into several segments and to specify an offer to present for each of these segments.

Para ello, utilice el proceso siguiente:

1. Add the **[!UICONTROL Offers by cell]** activity once you have specified the target population, then open it.
1. In the **[!UICONTROL General]** tab, select the offer space on which you want to present the offers.
1. En la **[!UICONTROL Cells]** ficha, especifique los distintos subconjuntos utilizando el **[!UICONTROL Add]** botón:

   * Especifique la población del subconjunto utilizando las reglas de filtrado y limitación disponibles.
   * A continuación, seleccione la oferta que desea presentar al subconjunto. Las ofertas disponibles son las admitidas en el entorno de oferta seleccionado en el paso anterior.

      ![](assets/int_offer_per_cell1.png)

1. A continuación, configure una actividad de envío que corresponda al canal elegido. Para obtener más información sobre esto, consulte la sección [Inserción de una propuesta de oferta en una sección de envío](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery) .

