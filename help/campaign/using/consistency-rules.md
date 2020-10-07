---
title: Reglas de coherencia
seo-title: Reglas de coherencia
description: Reglas de coherencia
seo-description: null
page-status-flag: never-activated
uuid: 9b497460-ba42-4bc7-98e0-55c1b4be5e44
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: 9bcb5dc1-8cb4-4781-a8cd-8d072ff28b1a
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '761'
ht-degree: 89%

---


# Reglas de coherencia{#consistency-rules}

## Acerca de las reglas de coherencia {#about-consistency-rules}

Adobe Campaign garantiza comunicaciones coherentes gracias a un conjunto de reglas contenidas en tipologías de campaña. Su objetivo es controlar las entregas que se realizan a los destinatarios como, por ejemplo, volumen, tipo, relevancia, etc.

Las reglas de **capacidad**, por ejemplo, pueden evitar la sobrecarga en la plataforma correspondiente de envío de mensajes. Por ejemplo, las ofertas especiales que contienen un vínculo de descarga no se deben enviar a demasiadas personas a la vez para evitar la saturación del servidor; las campañas telefónicas no deben superar la capacidad de procesamiento de los centros de llamadas, etc. Para obtener más información, consulte [Capacidad de control](#controlling-capacity).

## Control de la capacidad {#controlling-capacity}

Antes de enviar mensajes, debe asegurarse de que su organización tiene la capacidad de procesar la entrega (infraestructura física), las respuestas que puede generar la entrega (mensajes entrantes) y el número de llamadas que se realizan para ponerse en contacto con los suscriptores (capacidad de procesamiento del centro de llamadas), por ejemplo.

Para ello, debe crear reglas de tipología de **[!UICONTROL Capacity]**.

En el siguiente ejemplo, creamos una regla de tipología para una campaña de fidelización telefónica. Restringimos el número de mensajes a 20 por día, es decir, la capacidad de procesamiento diaria de un centro de llamadas. Una vez aplicada la regla a dos envíos, podemos monitorizar el consumo mediante registros.

Para diseñar una regla de capacidad nueva, siga los pasos a continuación:

1. Bajo el **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** nodo, haga clic en **[!UICONTROL New]**.
1. Select a **[!UICONTROL Capacity]** rule type.

   ![](assets/campaign_opt_create_capacity_01.png)

1. En la pestaña **[!UICONTROL Capacity]**, cree las líneas de disponibilidad: en este ejemplo, son periodos durante los cuales se pueden realizar llamadas. Seleccione un periodo de 24 horas e introduzca 150 en la cantidad inicial, lo que significa que el centro de llamadas puede gestionar 150 llamadas al día.

   ![](assets/campaign_opt_create_capacity_02.png)

   >[!NOTE]
   >
   >Las líneas de disponibilidad solo tienen fines informativos. Si necesita excluir mensajes cuando se alcance el límite de capacidad, consulte [esta sección](#exclude-messages-when-capacity-limit-reached).

1. Asocie esta regla a una tipología y luego haga referencia a la misma en su envío para aplicar esta regla de capacidad. Para obtener más información, consulte [esta sección](../../campaign/using/applying-rules.md#applying-a-typology-to-a-delivery).
1. You can monitor consumption from the rule **[!UICONTROL Consumptions]** and **[!UICONTROL Capacity]** tabs.

   Cuando se utiliza una regla en una entrega, las columnas **[!UICONTROL Consumed]** y **[!UICONTROL Remaining]** facilitan información sobre la carga, como se muestra a continuación:

   ![](assets/campaign_opt_create_capacity_03.png)

   Para obtener más información, consulte [esta sección](#monitoring-consumption).

## Definición de la carga máxima {#defining-the-maximum-load}

Para definir la carga máxima, debe definir las líneas de disponibilidad. Para ello, hay dos opciones disponibles: puede crear manualmente una o más líneas de disponibilidad (consulte [Adición de líneas de disponibilidad o una por una](#adding-availability-lines-one-by-one)) o crear intervalos de disponibilidad. La frecuencia de estos periodos se puede automatizar (consulte [Adición de un conjunto de líneas de disponibilidad](#add-a-set-of-availability-lines)).

### Adición de líneas de disponibilidad una por una {#adding-availability-lines-one-by-one}

To create an availability line, click the **[!UICONTROL Add]** button and select **[!UICONTROL Add an availability line]**. Introduzca el periodo de disponibilidad y la carga disponible.

![](assets/campaign_opt_create_capacity_02.png)

Añada tantas líneas como requiera su capacidad de procesamiento.

### Adición de un conjunto de líneas de disponibilidad {#add-a-set-of-availability-lines}

To define availability periods for a given time, click the **[!UICONTROL Add]** button and select the **[!UICONTROL Add a set of availability lines]** option. Indique una duración para cada periodo y el número de periodos que desea crear.

Para automatizar la frecuencia de creación de páginas, haga clic en el botón **[!UICONTROL Change]** y defina la programación del periodo.

![](assets/campaign_opt_create_capacity_07.png)

Por ejemplo, defina una programación para crear periodos de disponibilidad para todos los días laborables a una velocidad de 10 llamadas por hora entre 9 a. m. y 5 p. m. Para ello, siga los siguientes pasos:

1. Seleccione el tipo de periodicidad y los días y horas de validez:

   ![](assets/campaign_opt_create_capacity_08.png)

1. Indique las fechas de validez:

   ![](assets/campaign_opt_create_capacity_09.png)

1. Compruebe la programación antes de aprobarla:

   ![](assets/campaign_opt_create_capacity_10.png)

El flujo de trabajo de **[!UICONTROL Forecasting]** crea automáticamente todas las líneas coincidentes.

![](assets/campaign_opt_create_capacity_12.png)

>[!NOTE]
>
>Recomendamos la creación de líneas de disponibilidad a través de las importaciones de archivos. Esta pestaña le permite consultar y comprobar las líneas de consumo.

## Exclusión de mensajes al alcanzar el límite de capacidad {#exclude-messages-when-capacity-limit-reached}

Las líneas de disponibilidad solo tienen fines informativos. Para excluir mensajes excesivos, marque la **[!UICONTROL Exclude from the target messages in excess of capacity]** opción. Esto evita que se supere la capacidad. Para la misma población que en el ejemplo anterior, es posible que el consumo y la capacidad restante no superen la cantidad inicial:

![](assets/campaign_opt_create_capacity_04.png)

El número de mensajes que se va a procesar se reparte de forma equitativa durante el intervalo de disponibilidad definido. Esto es especialmente relevante para los centros de llamadas, ya que el número máximo de llamadas al día es limitado. In the case of email deliveries, the **[!UICONTROL Do not limit instantaneous delivery capacity]** option lets you ignore this availability range and send your emails at the same time.

![](assets/campaign_opt_create_capacity_05.png)

>[!NOTE]
>
>En caso de sobrecarga, los mensajes guardados se seleccionan según la fórmula definida en las propiedades de entrega.

![](assets/campaign_opt_create_capacity_06.png)

## Monitorización del consumo {#monitoring-consumption}

De forma predeterminada, las reglas de capacidad solo tienen fines ilustrativos. Select the **[!UICONTROL Exclude messages in excess of capacity from the target]** option to prevent the defined load from being exceeded. En este caso, los mensajes sobrantes se excluyen automáticamente de las entregas utilizando esta regla de tipología.

Para monitorizar los consumos, consulte los valores mostrados en la columna **[!UICONTROL Consumed]** de la pestaña **[!UICONTROL Capacity]** en la regla de tipología.

![](assets/campaign_opt_create_capacity_04.png)

Para consultar las líneas de consumo, haga clic en la pestaña **[!UICONTROL Consumptions]** de la regla.
