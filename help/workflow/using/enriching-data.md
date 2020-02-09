---
title: Enriquecimiento de datos
seo-title: Enriquecimiento de datos
description: Enriquecimiento de datos
seo-description: null
page-status-flag: never-activated
uuid: 3f65a8a2-b3e1-4c4c-9653-b8a7c4d7557a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: f87da08f-68b9-4e2b-821f-b3ff20e390f1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Enriquecimiento de datos{#enriching-data}

## Acerca del enriquecimiento de datos {#about-enriching-data}

This use case details possible uses of the **[!UICONTROL Enrichment]** activity in a targeting workflow. Para obtener más información sobre el uso de la **[!UICONTROL Enrichment]** actividad, consulte: [Enriquecimiento](../../workflow/using/enrichment.md).

Se envía una invitación a los contactos de la base de datos de marketing para que participen en una competición a través de una aplicación web. The results of the competition are recovered in the **[!UICONTROL Competition results]** table. This table is linked to the contact table (**[!UICONTROL Recipients]**). La **[!UICONTROL Competition results]** tabla contiene los campos siguientes:

* Nombre de la competición (@game)
* Número de prueba (@trial)
* Puntuación (@score)

![](assets/uc1_enrich_1.png)

A contact found in the **[!UICONTROL Recipients]** table can be linked to several lines in the **[!UICONTROL Competition results]** table. La relación entre estas dos tablas es de tipo 1-n. A continuación, se muestra un ejemplo de los registros de resultados de un destinatario:

![](assets/uc1_enrich_2.png)

El objetivo de este caso de uso es realizar envíos personalizados a las personas que forman parte de la competición más reciente según sus puntuaciones más altas. El destinatario con la máxima puntuación obtiene el primer premio, el destinatario con la segunda puntuación más alta obtiene un premio de consolación y todos los demás obtienen un mensaje que les desea mejor suerte para la próxima.

Para configurar este caso de uso, se ha creado el siguiente flujo de trabajo de objetivo:

![](assets/uc1_enrich_3.png)

Para crear el flujo de trabajo, siga los siguientes pasos:

1. Two **[!UICONTROL Query]** activities and one **[!UICONTROL Intersection]** activity are added to target new subscribers who entered last the competition.
1. La **[!UICONTROL Enrichment]** actividad nos permite agregar datos almacenados en la **[!UICONTROL Competition results]** tabla. The **[!UICONTROL Score]** field which our delivery personalization will take place on is added to the work table of the workflow.
1. The **[!UICONTROL Split]** type activity enables us to create recipient subsets based on scores.
1. For each subset, a **[!UICONTROL Delivery]** type activity is added.

## Paso 1: Objetivo {#step-1--targeting}

La primera consulta permite dirigirse a los destinatarios que se agregaron a la base de datos en los últimos seis meses.

![](assets/uc1_enrich_4.png)

La segunda consulta permite dirigirse a los destinatarios que participaron en la última competición.

![](assets/uc1_enrich_5.png)

An **[!UICONTROL Intersection]** type activity is then added to target the recipients added to the database within the last six months and who entered the last competition.

## Paso 2: Enriquecimiento {#step-2--enrichment}

In this example, we want to personalize deliveries according to the **[!UICONTROL Score]** field stored in the **[!UICONTROL Competition results]** table. Esta tabla tiene una relación de tipo 1-n con la tabla de destinatarios. The **[!UICONTROL Enrichment]** activity enables us to add data from a table linked to the filtering dimension to the work table of the workflow.

1. En la pantalla de edición de la actividad de enriquecimiento, seleccione **[!UICONTROL Add data]**, luego **[!UICONTROL Data linked to the filtering dimension]** y haga clic en **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_6.png)

1. A continuación, seleccione la **[!UICONTROL Data linked to the filtering dimension]** opción, seleccione la **[!UICONTROL Competition results]** tabla y haga clic en **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_7.png)

1. Introduzca un ID y una etiqueta y seleccione la **[!UICONTROL Limit the line count]** opción en el **[!UICONTROL Data collected]** campo. In the **[!UICONTROL Lines to retrieve]** field, select &#39;1&#39; as a value. For each recipient, the enrichment activity will add a single line from the **[!UICONTROL Competition results]** table to the work table of the workflow. Haga clic **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_8.png)

1. En este ejemplo, se desea recuperar la puntuación más alta del destinatario, pero solo para la última competición. To do this, add a filter to the **[!UICONTROL Competition name]** field to exclude all lines related to previous competitions. Haga clic **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_9.png)

1. Go to the **[!UICONTROL Sort]** screen and click the **[!UICONTROL Add]** button, select the **[!UICONTROL Score]** field and check the box in the **[!UICONTROL descending]** column to sort items of the **[!UICONTROL Score]** fields in descending order. Para cada destinatario, la actividad de enriquecimiento agrega una línea que coincide con la puntuación más alta para el último juego. Haga clic **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_10.png)

1. En la **[!UICONTROL Data to add]** ventana, haga doble clic en el **[!UICONTROL Score]** campo. For each recipient, the enrichment activity will add only the **[!UICONTROL Score]** field. Haga clic **[!UICONTROL Finish]**.

   ![](assets/uc1_enrich_11.png)

Right-click the inbound transition of the enrichment activity and select **[!UICONTROL Display the target]**. La tabla de trabajo contiene los siguientes datos:

![](assets/uc1_enrich_13.png)

El esquema vinculado es:

![](assets/uc1_enrich_15.png)

Realice nuevamente esta operación en la transición saliente de la actividad de enriquecimiento. Se puede ver que se han agregado los datos vinculados a las puntuaciones del destinatario. Se ha recuperado la mayor puntuación de cada destinatario.

![](assets/uc1_enrich_12.png)

El esquema coincidente también se ha enriquecido.

![](assets/uc1_enrich_14.png)

## Paso 3: División y envío {#step-3--split-and-delivery}

To sort the recipients based on their scores, a **[!UICONTROL Split]** activity is added after the enrichment.

![](assets/uc1_enrich_18.png)

1. Se ha definido un primer subconjunto (**Winner**) para incluir el destinatario con la máxima puntuación. Para ello, defina una limitación del número de registros, aplique una ordenación descendente a la puntuación y limite el número de registros a 1.

   ![](assets/uc1_enrich_16.png)

1. El segundo subconjunto (**Second place**) incluye el destinatario con la segunda puntuación más alta. La configuración es la misma que para el primer subconjunto.

   ![](assets/uc1_enrich_17.png)

1. El tercer subconjunto (**losers**) contiene todos los demás destinatarios. Go to the **[!UICONTROL General]** tab and check the **[!UICONTROL Generate complement]** box to target all recipients who did not achieve the two highest scores.

   ![](assets/uc1_enrich_19.png)

1. Add a **[!UICONTROL Delivery]** type activity for each subset, using a different delivery template for each.

   ![](assets/uc1_enrich_20.png)

