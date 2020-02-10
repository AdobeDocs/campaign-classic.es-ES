---
title: Prueba A/B
seo-title: Prueba A/B
description: Prueba A/B
seo-description: null
page-status-flag: never-activated
uuid: 8887574e-447b-48a5-afc6-95783ffa7fb3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 4113c3fe-a279-4fe1-be89-ea43c96edc34
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Prueba A/B{#a-b-testing}

Si se tiene varios contenidos para un envío de correo electrónico y se desea conocer qué versión tiene el mayor impacto en la población objetivo, se puede enviar las distintas versiones a algunos de los destinatarios y, a continuación, seleccionar la que tenga la tasa de éxito más alta y enviarla al resto de destinatarios.

En este caso de uso, se desea comparar dos contenidos de envío por correo electrónico a través de un flujo de trabajo de objetivo. El mensaje y el texto son idénticos en ambos envíos: solo cambia el diseño.

La población objetivo se divide en tres: dos grupos de prueba y la población restante. Se envía una versión diferente a cada grupo de prueba. Después de la entrega, se configura un período de espera de 5 días antes de recolectar los resultados de las mejores tasas de apertura. El contenido del envío con la puntuación más alta se recupera mediante una secuencia de comandos y se envía a la población no utilizada como grupo de prueba.

Tenga en cuenta que los criterios que determinan cuál envío es el mejor se pueden alterar para satisfacer las necesidades. Puede ser la tasa de apertura, la tasa de pulsaciones, la tasa de suscripción, la reactividad, etc.

Además, la prueba detallada en este caso de uso implica solo dos entregas, pero se pueden probar tantas versiones como sea necesario. Simplemente, agregue actividades al flujo de trabajo.

Para crear la prueba A/B, siga los siguientes pasos:

* [Paso 1: Creación de un flujo de trabajo de objetivo](#step-1--creating-a-targeting-workflow)
* [Paso 2: Configuración de muestras de población](#step-2--configuring-population-samples)
* [Paso 3: Creación de dos plantillas de entrega](#step-3--creating-two-delivery-templates)
* [Paso 4: Configuración de los envíos en el flujo de trabajo](#step-4--configuring-the-deliveries-in-the-workflow)
* [Paso 5: Creación de la secuencia de comandos](#step-5--creating-the-script)
* [Paso 7: Inicio del flujo de trabajo](#step-7--starting-the-workflow)
* [Paso 8: Analizando el resultado](#step-8--analyzing-the-result).

## Step 1: Creating a targeting workflow {#step-1--creating-a-targeting-workflow}

You need to create your workflow in the **[!UICONTROL Targeting and Workflows]** tab of a campaign. Se compone de una **[!UICONTROL Query]** actividad, una **[!UICONTROL Split]** actividad vinculada a dos **[!UICONTROL Email delivery]** actividades, una **[!UICONTROL Wait]** actividad, una **[!UICONTROL JavaScript code]** actividad y una **[!UICONTROL Delivery]** actividad.

1. Si aún no lo ha hecho, cree una campaña (para obtener más información, consulte esta [sección](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)).

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. Vaya a la **[!UICONTROL Targeting and Workflows]** ficha.

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. Change the label of the existing workflow or click **[!UICONTROL Add]** to create a new one (for more on this, refer to this [section](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population)).

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. Utilice el ratón para arrastrar y soltar actividades en el diagrama de flujo de trabajo, incluyendo una **[!UICONTROL Query]** (**[!UICONTROL Target]** ficha), una **[!UICONTROL Split]** (**[!UICONTROL Target]** ficha), dos **[!UICONTROL Email deliveries]** (**[!UICONTROL Deliveries]** ficha), una **[!UICONTROL Wait]** actividad (**[!UICONTROL Flow Control]** ficha), una **[!UICONTROL JavaScript code]** actividad (actividad) y una **[!UICONTROL Actions]** **[!UICONTROL Delivery]****[!UICONTROL Actions]** ficha de actividad (ficha).

![](assets/use_case_abtesting_targetwkfl_004.png)

## Paso 2: Configuración de muestras de población {#step-2--configuring-population-samples}

### Configuración de la actividad Consulta {#configuring-the-query-activity}

* Haga doble clic en la **[!UICONTROL Query]** actividad.

   ![](assets/use_case_abtesting_createrecipients_001.png)

* Click the **[!UICONTROL Edit query]** link and select the recipients you want to target.

   ![](assets/use_case_abtesting_createrecipients_002.png)

* Vincule la **[!UICONTROL Query]** actividad a la **[!UICONTROL Split]** actividad.

   ![](assets/use_case_abtesting_createrecipients_003.png)

### Configuración de la actividad Split {#configuring-the-split-activity}

Esta actividad permite crear varias poblaciones: la que recibe el envío A, la que recibe el envío B y la población restante. El uso de la selección aleatoria permite seleccionar solo parte de la población de cada envío.

1. Creación de la población A:

   * Haga doble clic en la **[!UICONTROL Split]** actividad.

      ![](assets/use_case_abtesting_createrecipients_004.png)

   * En la pestaña existente, cambie la etiqueta a población A.

      ![](assets/use_case_abtesting_createrecipients_005.png)

   * Seleccione la **[!UICONTROL Limit the selected records]** opción.

      ![](assets/use_case_abtesting_createrecipients_006.png)

   * Haga clic en el **[!UICONTROL Edit]** vínculo, selecciónelo **[!UICONTROL Activate random sampling]** y haga clic en **[!UICONTROL Next]**.

      ![](assets/use_case_abtesting_createrecipients_007.png)

   * Set the threshold to 10%, then click **[!UICONTROL Finish]**.

      ![](assets/use_case_abtesting_createrecipients_008.png)

1. Creación de la población B:

   * Click **[!UICONTROL Add]** to create a new tab for population B.

      ![](assets/use_case_abtesting_createrecipients_009.png)

   * Limite la población al 10% como se mostró anteriormente.

      ![](assets/use_case_abtesting_createrecipients_010.png)

1. Creación de la población restante:

   * Vaya a la **[!UICONTROL General]** ficha.

      ![](assets/use_case_abtesting_createrecipients_011.png)

   * Select **[!UICONTROL Generate complement]**.

      ![](assets/use_case_abtesting_createrecipients_012.png)

   * Change the label to specify that this population includes neither A nor B, and click **[!UICONTROL OK]** to close the activity.

      ![](assets/use_case_abtesting_createrecipients_013.png)

## Step 3: Creating two delivery templates {#step-3--creating-two-delivery-templates}

Ahora, se desea crear dos plantillas de envío. Each template will be referenced in an **[!UICONTROL Email delivery]** activity linked to the **[!UICONTROL Split]** activity. Para obtener más información, consulte [esta sección](../../delivery/using/about-templates.md).

1. Vaya a la **[!UICONTROL Resources > Delivery template]** carpeta.
1. Duplique la plantilla de envío **[!UICONTROL Email]** .

   ![](assets/use_case_abtesting_deliverymodel_001.png)

1. Cree el contenido que desea utilizar para el envío A.

   ![](assets/use_case_abtesting_deliverymodel_002.png)

1. Repita este proceso para crear una plantilla para el envío B.

   ![](assets/use_case_abtesting_deliverymodel_003.png)

## Step 4: Configuring the deliveries in the workflow {#step-4--configuring-the-deliveries-in-the-workflow}

El siguiente paso es configurar los envíos. Están destinados a las tres poblaciones creadas durante la etapa anterior: [Paso 2: Configuración de muestras](#step-2--configuring-population-samples)de población. Los dos primeros envíos permiten enviar contenido distinto a las poblaciones A y B. El tercer envío está destinado a la población que no ha recibido A ni B. Su contenido se calcula mediante una secuencia de comandos y es idéntico a A o B, dependiendo de cuál obtuvo la tasa de apertura más alta. We need to configure a wait period for the third delivery, to find out the outcome of deliveries A and B. This is why the third delivery includes a **[!UICONTROL Wait]** activity.

1. Go to the **[!UICONTROL Split]** activity and link the transition destined for population A to one of the email deliveries already in the workflow.

   ![](assets/use_case_abtesting_createdeliveries_001.png)

1. Haga doble clic en el envío para abrirlo.
1. En la lista desplegable, seleccione la plantilla para el envío A.

   ![](assets/use_case_abtesting_createdeliveries_003.png)

1. Click **[!UICONTROL Continue]** to view the delivery, then save it.

   ![](assets/use_case_abtesting_createdeliveries_002.png)

1. Link the transition of the **[!UICONTROL Split]** activity destined for population B to the second email delivery.

   ![](assets/use_case_abtesting_createdeliveries_004.png)

1. Abra el envío, seleccione la plantilla en el envío B y, a continuación, guarde el envío.

   ![](assets/use_case_abtesting_createdeliveries_005.png)

1. Link the transition destined for the remaining population to the **[!UICONTROL Wait]** activity.

   ![](assets/use_case_abtesting_createdeliveries_006.png)

1. Open the **[!UICONTROL Wait]** activity and configure a 5-day waiting period.

   ![](assets/use_case_abtesting_createdeliveries_007.png)

1. Vincule la **[!UICONTROL Wait]** actividad a la **[!UICONTROL JavaScript code]** actividad.

   ![](assets/use_case_abtesting_createdeliveries_008.png)

## Paso 5: Creación de la secuencia de comandos {#step-5--creating-the-script}

La elección del contenido de envío destinado a la población restante se calcula mediante una secuencia de comandos. Esta secuencia de comandos recupera la información relativa al envío con la mayor tasa de apertura y copia el contenido en el envío final.

### Ejemplo de secuencia de comandos {#example-of-a-script}

La siguiente secuencia de comandos se puede utilizar como se encuentra en el flujo de trabajo de objetivos. For more on this, refer to [Implementation](#implementation).

```
 // query the database to find the winner (best open rate)
   var winner = xtk.queryDef.create(
     <queryDef schema="nms:delivery" operation="get">
       <select>
         <node expr="@id"/>
         <node expr="@label"/>
         <node expr="[@operation-id]"/>
         <node expr="[@workflow-id]"/>
       </select>
       <where>
         <condition expr={"@FCP=0 and [@workflow-id]= " + instance.id}/>
       </where>
       <orderBy>
         <node expr="[indicators/@estimatedRecipientOpenRatio]" sortDesc="true"/>
       </orderBy>
     </queryDef>).ExecuteQuery()
   
   // create a new delivery object and initialize it by doing a copy of
   // the winner delivery
   var delivery = nms.delivery.create()
   delivery.Duplicate("nms:delivery|" + winner.@id)

   // append 'final' to the delivery label
   delivery.label = winner.@label + " final"

   // link the delivery to the operation to make sure it will be displayed in
   // the campaign dashboard. This attribute needs to be set manually here since 
   // the Duplicate() method has reset it to its default value => 0
   delivery.operation_id = winner.@["operation-id"]
   delivery.workflow_id = winner.@["workflow-id"]

   // adjust some delivery parameters to make it compatible with the 
   // "Prepare and start" option selected in the Delivery tab of this activity
   delivery.scheduling.validationMode = "manual"
   delivery.scheduling.delayed = 0
 
   // save the delivery in database
   delivery.save()
 
   // store the new delivery Id in event variables
   vars.deliveryId = delivery.id
```

Para obtener una explicación detallada del script, consulte [Detalles del script](#details-of-the-script).

### Implementación {#implementation}

1. Abra la **[!UICONTROL JavaScript code]** actividad.
1. Copie la secuencia de comandos ofrecida en [Ejemplo de una secuencia de comandos](#example-of-a-script) en la **[!UICONTROL JavaScript code]** ventana.

   ![](assets/use_case_abtesting_configscript_002.png)

1. In the **[!UICONTROL Label]** field, enter the name of the script, i.e.

   ```
   <%= vars.deliveryId %>
   ```

   ![](assets/use_case_abtesting_configscript_003.png)

1. Cierre la **[!UICONTROL JavaScript code]** actividad.
1. Guarde el flujo de trabajo.

### Detalles de la secuencia de comandos {#details-of-the-script}

En esta sección se detallan las distintas partes de la secuencia de comandos y su modo operativo.

* La primera parte de la secuencia de comandos es una consulta. The **queryDef** command lets you recover from the **NmsDelivery** table the deliveries created by executing the targeting workflow and to sort them based on their estimated rate of opens, then the information from the delivery with the highest rate of opens is recovered.

   ```
   // query the database to find the winner (best open rate)
      var winner = xtk.queryDef.create(
        <queryDef schema="nms:delivery" operation="get">
          <select>
            <node expr="@id"/>
            <node expr="@label"/>
            <node expr="[@operation-id]"/>
          </select>
          <where>
            <condition expr={"@FCP=0 and [@workflow-id]= " + instance.id}/>
          </where>
          <orderBy>
            <node expr="[indicators/@estimatedRecipientOpenRatio]" sortDesc="true"/>
          </orderBy>
        </queryDef>).ExecuteQuery()
   ```

* Se duplica el envío con la mayor tasa de apertura.

   ```
    // create a new delivery object and initialize it by doing a copy of
    // the winner delivery
   var delivery = nms.delivery.create()
   delivery.Duplicate("nms:delivery|" + winner.@id)
   ```

* La etiqueta del envío duplicado se modifica y la palabra **final** se añade a ella.

   ```
   // append 'final' to the delivery label
   delivery.label = winner.@label + " final"
   ```

* El envío se copia en el tablero de campañas.

   ```
   // link the delivery to the operation to make sure it will be displayed in
   // the campaign dashboard. This attribute needs to be set manually here since 
   // the Duplicate() method has reset it to its default value => 0
   delivery.operation_id = winner.@["operation-id"]
   delivery.workflow_id = winner.@["workflow-id"]
   ```

   ```
   // adjust some delivery parameters to make it compatible with the 
   // "Prepare and start" option selected in the Delivery tab of this activity
   delivery.scheduling.validationMode = "manual"
   delivery.scheduling.delayed = 0
   ```

* El envío se guarda en la base de datos.

   ```
   // save the delivery in database
   delivery.save()
   ```

* El identificador único del envío duplicado se almacena en la variable del flujo de trabajo.

   ```
   // store the new delivery Id in event variables
   vars.deliveryId = delivery.id
   ```

### Otros criterios de selección {#other-selection-criteria}

El ejemplo de arriba permite seleccionar el contenido de un envío según la tasa de apertura de los correos electrónicos. Se puede adaptar para que poder basarse en otros indicadores específicos de envío:

* Mejor rendimiento de los clics: `[indicators/@recipientClickRatio]`,
* Tasa máxima de reacción (correo electrónico abierto y clics en el mensaje): `[indicators/@reactivity]`,
* Tasa de quejas más baja: `[indicators/@refusedRatio]` (utilice el valor false para el atributo sortDesc),
* Tasa máxima de conversión: `[indicators/@transactionRatio]`,
* Número de páginas visitadas después de la recepción de un mensaje: `[indicators/@totalWebPage]`,
* Tasa mínima de cancelación de suscripciones: `[indicators/@optOutRatio]`,
* Cantidad de transacciones: `[indicators/@amount]`.

## Step 6: Defining the final delivery {#step-6--defining-the-final-delivery}

Una vez que la secuencia de comandos se ha creado para seleccionar el ganador de la prueba A/B, se puede definir los parámetros del envío final.

1. Conecte la **[!UICONTROL JavaScript code]** actividad a la **[!UICONTROL Delivery]** actividad restante.
1. Open the **[!UICONTROL Delivery]** activity.
1. Uncheck the **[!UICONTROL Generate an outbound transition]** option to finish the workflow with this activity.
1. Deje las demás opciones en sus valores predeterminados.

   ![](assets/ab_test_final_delivery.png)

By preparing the delivery specified in the transition (defined via the **[!UICONTROL Javascript Code]** activity), you will be then able to approve it and to start the sending, as described in the next step.

## Paso 7: Inicio del flujo de trabajo {#step-7--starting-the-workflow}

1. Haga clic en **[!UICONTROL Start]** el flujo de trabajo.

   ![](assets/use_case_abtesting_startwkfl_001.png)

1. Apruebe el objetivo y el contenido para los envíos A y B mediante el tablero de campañas.
1. Confirme el envío.
1. Espere hasta que finalice el período de 5 días para saber qué contenido se ha calculado tras los resultados de apertura de envíos.

   ![](assets/use_case_abtesting_startwkfl_002.png)

   En este caso, se eligió la plantilla B.

1. Una vez determinado el contenido del tercer envío, apruebe el objetivo y el contenido.

## Paso 8: Análisis del resultado {#step-8--analyzing-the-result}

Una vez remitidos los envíos de prueba, se puede comprobar los destinatarios a los que se han enviado y si se han abierto o no.

* To find out which recipients have been targeted, open a delivery via the campaign dashboard and click the **[!UICONTROL Delivery]** tab.

   ![](assets/use_case_abtesting_analysis_001.png)

* To find out whether the delivery has been opened, go to the **[!UICONTROL Tracking]** tab.

   ![](assets/use_case_abtesting_analysis_002.png)

* Compare con el otro envío.

   ![](assets/use_case_abtesting_analysis_003.png)

En el ejemplo, el envío B ha obtenido la mayor tasa de apertura. Esto significa que el contenido B se utilizará para el envío final.

![](assets/use_case_abtesting_analysis_004.png)

