---
title: Plantillas de Hipótesis
seo-title: Plantillas de Hipótesis
description: Plantillas de Hipótesis
seo-description: null
page-status-flag: never-activated
uuid: 080417c2-1c45-4404-961e-2e660d8f0436
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: response-manager
discoiquuid: addfc395-7a85-4be1-a757-a719ed34bb33
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---


# Plantillas de Hipótesis{#hypothesis-templates}

## Creación de un modelo de hipótesis {#creating-a-hypothesis-model}

La configuración de la plantilla de hipótesis permite definir el contexto para medir las reacciones, ya sea para un envío o para una oferta. Aquí es donde se hace referencia a las distintas tablas de medición, incluidas las usadas para definir relaciones entre individuos, hipótesis y la tabla de transacciones.

Para crear una plantilla de hipótesis, aplique los siguientes pasos:

1. In the Adobe Campaign explorer, click **[!UICONTROL Resources>Templates>Hypothesis templates]**.

   ![](assets/response_hypothesis_model_creation_001.png)

1. Click **[!UICONTROL New]** or right-click in the list of templates and choose **[!UICONTROL New]** in the drop-down list.
1. Introduzca la etiqueta de hipótesis.
1. Specify whether the template is destined for hypotheses on offers or deliveries via the **[!UICONTROL Hypothesis type]**.
1. For **[!UICONTROL Delivery]** type templates, specify whether measurements should be carried out with or without a control group (for more on this, refer to [Properties of a hypothesis template](#properties-of-a-hypothesis-template)).
1. For **[!UICONTROL Delivery]** type templates, you can choose a specific channel or decide to apply the template to all available channels in Adobe Campaign using the **[!UICONTROL Channel]** drop-down list (for more on this, refer to [Properties of a hypothesis template](#properties-of-a-hypothesis-template)).
1. Select the **[!UICONTROL Execution folder]** in which you wish to create and automatically execute the hypotheses that will be created from this template.
1. Elija la configuración de ejecución (para obtener más información sobre esto, consulte Configuración [de ejecución de plantilla de](#hypothesis-template-execution-settings)hipótesis).
1. Especifique el período de cálculo de hipótesis (para obtener más información sobre esto, consulte la configuración [de ejecución de la plantilla](#hypothesis-template-execution-settings)Hipótesis).

   >[!CAUTION]
   >
   >Este periodo se determina a partir de la fecha de contacto.

1. In the **[!UICONTROL Transactions]** tab, specify the tables and fields required for the hypothesis calculation (for more on this, refer to [Transactions](#transactions)).
1. If your template is configured for **[!UICONTROL Offer]** type hypotheses, you can enable the **[!UICONTROL Update offer proposition status]** option: in this case, select the status of the offer proposition you want to change.
1. Specify the scope of the hypothesis application (for more on this, refer to [Hypothesis perimeter](#hypothesis-perimeter)).
1. If necessary, use a script to complete filtering (for more on this, refer to [Hypothesis perimeter](#hypothesis-perimeter)).

### Propiedades de una plantilla de hipótesis {#properties-of-a-hypothesis-template}

The template&#39;s **[!UICONTROL General]** tab lets you specify the general template options. Los campos disponibles son:

* **[!UICONTROL Hypothesis type]**:: permite determinar si la plantilla debe estar destinada a hipótesis sobre entregas u ofertas.

   También puede optar por crear una hipótesis que se aplicará a los envíos y a las ofertas.

   >[!NOTE]
   >
   >Si la plantilla se aplica a las ofertas, la **[!UICONTROL Update offer proposition status]** opción está disponible en la **[!UICONTROL Transactions]** ficha.

* **[!UICONTROL Measurement with control group]**:: permite indicar si se ha definido un grupo de control para la entrega o la campaña e incluirlo en los indicadores de medición. El grupo de control, que no recibe envíos, le permite medir el impacto de la campaña después del envío, comparándolo con la población objetivo que recibió el envío.

   >[!NOTE]
   >
   >Si la plantilla está configurada para tener un grupo de control en cuenta pero no se define ningún grupo en el envío, los resultados se basarán únicamente en los destinatarios seleccionados.

   Para obtener más información sobre la definición y configuración de un grupo de control, consulte [Definición de un grupo](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)de control.

* **[!UICONTROL Channel]**:: puede elegir un canal específico o hacer que la plantilla de hipótesis esté disponible para todos los canales de la consola de Adobe Campaign seleccionando **[!UICONTROL All channels]** en la lista desplegable. If you configure the template for a specific channel, this lets you automatically filter deliveries per channel when creating the hypothesis (refer to [Creating hypotheses](../../campaign/using/creating-hypotheses.md)).

   ![](assets/response_properties_001.png)

* **[!UICONTROL Execution folder]**:: permite especificar la carpeta de ejecución para la hipótesis.
* **[!UICONTROL Taken into account in campaign ROI calculation]**:: tiene en cuenta el resultado de la hipótesis en el cálculo del ROI para la campaña relacionada.

### Configuración de ejecución de plantillas de hipótesis {#hypothesis-template-execution-settings}

The template&#39;s **[!UICONTROL General]** tab also lets you specify the hypothesis execution parameters. Las opciones disponibles son las siguientes:

* **[!UICONTROL Schedule execution for a time of low activity]**:: le permite programar el lanzamiento de la hipótesis para optimizar el rendimiento de Adobe Campaign. Cuando se activa esta opción, el flujo de trabajo de procesamiento de las campañas ejecuta el cálculo de hipótesis durante el tiempo de espera.

   ![](assets/response_exec_settings_002.png)

* **[!UICONTROL Priority]**:: nivel aplicado a la hipótesis para limitar las órdenes de cálculo de hipótesis si hay ejecuciones simultáneas.

   ![](assets/response_exec_settings_003.png)

* **[!UICONTROL Automatic execution]**:: si es necesario, le permite programar el nuevo cálculo de hipótesis (por ejemplo, si desea actualizar los indicadores de forma regular hasta el final del envío).

   ![](assets/response_exec_settings_001.png)

   Para especificar una programación, aplique el siguiente proceso:

   1. Haga clic en el **[!UICONTROL Frequency of execution...]** vínculo y luego en el **[!UICONTROL Change...]** botón.

      ![](assets/response_frequency_execution_001.png)

   1. Configure la frecuencia, los eventos relacionados y el periodo de validez.

      ![](assets/response_frequency_execution_002.png)

   1. Haga clic en **[!UICONTROL Finish]** para guardar la programación.

      ![](assets/response_frequency_execution_003.png)

* **[!UICONTROL Log SQL queries in journal]**:: esta función está reservada para usuarios expertos. Le permite añadir una pestaña a la auditoría de hipótesis de medición para mostrar consultas SQL. Esto permite detectar posibles errores que se pueden dar en una simulación.
* **[!UICONTROL Keep execution workflow]**:: le permite mantener el flujo de trabajo que se generó automáticamente al principio del cálculo de hipótesis. En las hipótesis creadas a partir de una plantilla que tiene esta opción activada, el flujo de trabajo generado permite hacer un seguimiento del proceso.

   >[!CAUTION]
   >
   >Esta opción debe activarse solo para fines de depuración, en caso de error al ejecutar la hipótesis.\
   >Además, los flujos de trabajo generados automáticamente no se deben modificar. No se tendrá en cuenta ninguna modificación para realizar cálculos más adelante.\
   >Si ha comprobado esta opción, elimine el flujo de trabajo una vez que se haya ejecutado.

### Transacciones {#transactions}

Esta pestaña contiene los distintos campos y tablas que permiten guardar el historial de reacciones del destinatario en términos de transacciones. Consulte la guía de [configuración](../../configuration/using/about-schema-reference.md) para obtener más información sobre las tablas dedicadas a la gestión de respuestas.

* **[!UICONTROL Schema (reaction log storage)]**:: seleccione la tabla de reacción del destinatario. La tabla predeterminada de Adobe Campaign es **NmsRemaMatchRcp**.
* **[!UICONTROL Transaction schema]**:: elija la tabla con la que se relacionarán las hipótesis, es decir, la transacción o la tabla de compra.
* **[!UICONTROL Querying schema]**:: elija los criterios para filtrar la hipótesis.
* **[!UICONTROL Link to individuals]**:: elija el vínculo entre las personas y la tabla utilizada como esquema de transacción.
* **[!UICONTROL Link to the household]**:: seleccione el enlace al hogar en el esquema de transacciones si desea incluir a todos los miembros de un hogar en una hipótesis. Este campo es opcional.
* **[!UICONTROL Transaction date]**:: este campo es opcional, pero se recomienda, ya que permite definir un ámbito para el cálculo de hipótesis.
* **[!UICONTROL Measurement period]**:: permite configurar las fechas de inicio y finalización durante las cuales se ejecutan las hipótesis y se recuperan las líneas de compra.

   Cuando la hipótesis está vinculada a un envío, la medición se activa automáticamente unos días después de la fecha de contacto para los envíos de correo directo, o después de la fecha de entrega para envíos de correo electrónico o SMS.

   ![](assets/response_measurement_001.png)

   Si la hipótesis se inicia sobre la marcha, se puede forzar si quisiera activarla inmediatamente. De lo contrario, se activa automáticamente en función de la fecha de finalización del cálculo configurada, que se basa en la fecha de creación de la hipótesis (consulte [Creación de una hipótesis sobre la marcha en una entrega](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)).

* **[!UICONTROL Transaction/Margin amount]**:: estos campos son opcionales y permiten calcular automáticamente los indicadores de volumen de negocios (consulte [Indicadores](../../campaign/using/hypothesis-tracking.md#indicators)).
* **[!UICONTROL Unit amount]**:: permite establecer una cantidad para calcular los ingresos (consulte [Indicadores](../../campaign/using/hypothesis-tracking.md#indicators)).

   ![](assets/response_transactions_001.png)

* **[!UICONTROL Additional measures and data]**:: permite especificar medidas o ejes de informes adicionales desde los campos de las distintas tablas.
* **[!UICONTROL Update offer proposition status]**:: permite cambiar el estado de la propuesta de oferta si un destinatario de oferta se identifica mediante la hipótesis.

   ![](assets/response_offer_status_001.png)

### Perímetro de hipótesis {#hypothesis-perimeter}

Una vez que haya definido la tabla de transacciones y los campos a los que se referirá la hipótesis, puede refinar el alcance de sus hipótesis especificando las transacciones y envíos específicos utilizando filtros. También puede utilizar una secuencia de comandos de JavaScript para indicar explícitamente el producto al que se hace referencia en la tabla de transacciones.

* **Filtrado de transacciones**: en la **[!UICONTROL Scope]** ficha, puede configurar un filtro en la hipótesis. Para ello:

   1. Haga clic en el **[!UICONTROL Edit query]** vínculo.

      ![](assets/response_scope_filtering_001.png)

   1. Especifique las condiciones del filtro.

      ![](assets/response_scope_filtering_002.png)

   1. Seleccione la transacción a la que quiere vincular la hipótesis.

      ![](assets/response_scope_filtering_003.png)

* **Filtrar por destinatarios**: en la **[!UICONTROL Scope]** ficha, puede limitar su hipótesis a cualquier información vinculada a un mensaje (entrega, destinatario, dirección de correo electrónico, servicio, etc.):

   1. Haga clic en el **[!UICONTROL Add a filter]** vínculo y luego **[!UICONTROL Edit query]**.

      ![](assets/response_scope_filtering_004.png)

   1. Especifique las condiciones del filtro.

      ![](assets/response_scope_filtering_005.png)

   1. Haga clic **[!UICONTROL Finish]** para guardar la consulta.

      ![](assets/response_scope_filtering_006.png)

* **Script**: puede utilizar una secuencia de comandos de JavaScript para sobrecargar dinámicamente la configuración de hipótesis durante su ejecución.

   To do this, click the **[!UICONTROL Advanced settings]** link then enter the desired script.

   >[!NOTE]
   >
   >Esta opción es para usuarios expertos.

   ![](assets/response_hypothesis_model_creation_011.png)

## Ejemplo: Creación de una plantilla de hipótesis para un envío {#example--creating-a-hypothesis-template-on-a-delivery}

En este ejemplo, vamos a crear una plantilla de hipótesis para un envío de correo postal. La tabla de transacciones (**Purchases** en nuestro ejemplo) en la que se basarán las hipótesis contiene líneas de compra vinculadas a artículos o productos. Queremos configurar nuestro modelo para crear hipótesis sobre artículos o productos en la tabla de compras.

1. In the Adobe Campaign explorer, go to the **[!UICONTROL Resources > Templates > Hypothesis templates]** node.
1. Haga clic en **[!UICONTROL New]** para crear una plantilla.

   ![](assets/response_hypothesis_model_example_001.png)

1. Cambie la etiqueta de la plantilla.

   ![](assets/response_hypothesis_model_example_002.png)

1. Seleccione **[!UICONTROL Deliveries]** como tipo de hipótesis.
1. Especifique que el envío puede contener un grupo de control comprobando el cuadro correspondiente.
1. Elija el **[!UICONTROL Direct mail]** canal.

   >[!NOTE]
   >
   >Debido a que la plantilla es específica para los envíos de correo directo, las hipótesis creadas utilizando este modelo pueden no estar vinculadas a ningún otro tipo de envío.

1. In the **[!UICONTROL Transactions]** tab, select the recipient reactions table.

   ![](assets/response_hypothesis_model_example_006.png)

1. In the **[!UICONTROL Transactions schema]** field, choose your purchase table.

   ![](assets/response_hypothesis_model_example_007.png)

1. Seleccione líneas de compra en el **[!UICONTROL Querying schema]** campo.

   ![](assets/response_hypothesis_model_example_008.png)

1. Seleccione los destinatarios vinculados a la tabla de compra.

   ![](assets/response_hypothesis_model_example_009.png)

1. Seleccione el campo vinculado a la fecha de compra.

   Esto permite definir un intervalo de tiempo para hipótesis. Este paso no es obligatorio; sin embargo, es recomendable.

   ![](assets/response_hypothesis_model_example_010.png)

1. Configure el periodo de cálculo de 5 a 25 días.

   ![](assets/response_hypothesis_model_example_005.png)

1. En la **[!UICONTROL Scope]** ficha, haga clic en **[!UICONTROL Edit query]** para crear un filtro de hipótesis.

   ![](assets/response_hypothesis_model_example_011.png)

   La plantilla creada le permite ejecutar hipótesis sobre los productos o artículos de la tabla de compra.

1. Haga clic en **[!UICONTROL Save]** para registrar la plantilla.

