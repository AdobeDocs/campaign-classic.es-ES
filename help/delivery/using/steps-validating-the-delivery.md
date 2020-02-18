---
title: Validación del envío
seo-title: Validación del envío
description: Validación del envío
seo-description: null
page-status-flag: never-activated
uuid: 8bf70ea4-5f28-4d85-b5ce-0bd3ed3eea55
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: df29492f-ed73-4ab8-b075-e76b3b9ebce3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7bcf222f41c0e40368644b76197b07f2ded699f0

---


# Validación del envío {#validating-the-delivery}

Cuando se ha creado y configurado un envío, se debe validar antes de enviarlo al objetivo principal.

Para ello:

1. **Analizar la entrega**: este paso le permite preparar los mensajes que se van a enviar. Consulte [Análisis del envío](#analyzing-the-delivery).

   Los modos de validación disponibles se detallan en [Cambio del modo](../../delivery/using/steps-validating-the-delivery.md#changing-the-approval-mode)de aprobación.

1. **Enviar pruebas**: este paso le permite aprobar contenido, direcciones URL, campos de personalización, etc. Consulte [Envío de una prueba](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof) y [Definición de un destino](../../delivery/using/steps-defining-the-target-population.md#defining-a-specific-proof-target)de prueba específico.

>[!CAUTION]
>
>Ambos pasos deben llevarse a cabo después de cada modificación en el contenido del mensaje.

## Análisis del envío {#analyzing-the-delivery}

El análisis es la fase durante la cual se calcula la población objetivo y se prepara el contenido de envío. Una vez finalizada, la entrega está lista para ser enviada. Para iniciar el análisis de envío, haga clic en **[!UICONTROL Send]** y seleccione **[!UICONTROL Deliver as soon as possible]**.

![](assets/s_ncs_user_email_del_send.png)

The **[!UICONTROL Analyze]** button lets you launch the analysis manually. La barra de progreso muestra el progreso del análisis. La sección inferior de la ventana muestra el resultado del análisis. Los iconos especiales muestran las advertencias.

![](assets/s_ncs_user_interface_delivery04b.png)

>[!NOTE]
>
>Las reglas de validación se describen en el proceso [de validación con tipologías](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies).

You can stop this job at any time by clicking **[!UICONTROL Stop]**.

![](assets/s_ncs_user_wizard_email01_16.png)

No se envían mensajes durante la fase de análisis. Por lo tanto, puede iniciar o cancelar este trabajo sin riesgos.

>[!CAUTION]
>
>El análisis bloquea el envío (o la prueba) en el momento del análisis. Cualquier modificación al envío (o la prueba) debe ir seguida de otro análisis antes de ser válida.

El último mensaje de “log” muestra los mensajes de error y el número de errores. Un icono especial muestra el tipo de error: el icono amarillo indica un error de procesamiento no crítico, el icono rojo indica un error crítico que impide el inicio del envío.

![](assets/s_ncs_user_email_del_analyze_error.png)

Haga clic en **[!UICONTROL Close]** para corregir los errores. Después de realizar los cambios, se debe reiniciar el análisis.

Check the result of the analysis before clicking **[!UICONTROL Confirm delivery]** to send the message to the specified target. Un mensaje de confirmación permite iniciar el envío.

![](assets/s_ncs_user_email_del_analyze_ok.png)

>[!NOTE]
>
>Click the **[!UICONTROL Change the main delivery target]** link if the number of messages to send does not match your configuration. Esto permite cambiar la definición de la población objetivo y reiniciar el análisis.

The delivery parameters **[!UICONTROL Analysis]** tab lets you define a set of information concerning the preparation of messages during the analysis phase.

![](assets/s_ncs_user_email_del_analyze_adv_param.png)

Esta pestaña proporciona acceso a las siguientes opciones:

* **[!UICONTROL Label and code of the delivery]** :: las opciones relativas a esta sección de la pantalla se utilizan para calcular los valores de estos campos durante la fase de análisis de envío. The **[!UICONTROL Calculate the execution folder during the delivery analysis]** field computes the name of the folder that will contain this delivery action during the analysis phase.
* **[!UICONTROL Approval mode]** :: este campo permite seleccionar el tipo de aprobación de envío. Los modos de aprobación se presentan en el proceso [de validación con tipologías](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies).
* **[!UICONTROL Prepare the personalization data with a workflow]** :: esta opción permite preparar los datos de personalización contenidos en la entrega en un flujo de trabajo automático. Permite mejorar el rendimiento del análisis de envío cuando se procesan muchos datos, especialmente si los datos de personalización proceden de una tabla externa a través de FDA. Consulte la sección [Acceso a una base de datos externa (FDA)](../../platform/using/additional-options.md#optimizing-email-personalization-with-external-data).
* **[!UICONTROL Start job in a detached process]** : Esta opción le permite iniciar el análisis de envío en un proceso independiente. La función de análisis utiliza el proceso del servidor de aplicaciones de Adobe Campaign (web nlserver) de forma predeterminada. Al seleccionar esta opción, se asegura de que el análisis se complete incluso en caso de que falle el servidor de aplicaciones.
* **[!UICONTROL Log SQL queries generated during the analysis in the journal]** :: esta opción agrega los registros de consulta SQL al diario de envío durante la fase de análisis.
* **[!UICONTROL Ignore personalization scripts during sending]** :: esta opción le permite omitir la interpretación de las directivas JavaScript que se encuentran en el contenido HTML. Se visualizan tal y como están en los contenidos enviados. These directives are introduced with the **&lt;%=** tag).

### Configuración de la prioridad de análisis {#analysis-priority-}

When the delivery is part of a campaign, the **[!UICONTROL Advanced]** tab offers an additional option. Esto permite organizar el orden de procesamiento de los envíos en la misma campaña.

Cada envío se analiza antes de realizarlo. La duración del análisis depende del archivo de extracción de envíos. Cuanto más significativo sea el tamaño del archivo, más dura el análisis, lo que hace que los siguientes envíos deban esperar.

The options for the **[!UICONTROL Message preparation by the scheduler]** let you prioritize the delivery analysis in a campaign workflow.

![](assets/delivery_analysis_priority.png)

Si un envío es demasiado grande, es mejor asignarle una prioridad baja para evitar ralentizar el análisis de otros envíos del flujo de trabajo.

>[!NOTE]
>
>To ensure that the larger delivery analyses do not slow down the progress of your workflows, you can schedule their executions by ticking the **[!UICONTROL Schedule execution for a time of low activity]**.

## Envío de una prueba {#sending-a-proof}

Para detectar posibles errores en la configuración del mensaje, Adobe recomienda configurar un ciclo de validación de envío. Asegúrese de que el contenido se aprueba con la frecuencia necesaria al enviar pruebas a los destinatarios de prueba. Se debe enviar una prueba cada vez que se realiza un cambio para aprobar el contenido.

>[!NOTE]
>
>* Los modos de validación disponibles se detallan en [Cambio del modo](../../delivery/using/steps-validating-the-delivery.md#changing-the-approval-mode)de aprobación.
>* La configuración del objetivo de prueba se explica en [Definición de un objetivo](../../delivery/using/steps-defining-the-target-population.md#defining-a-specific-proof-target)de prueba específico.
>



Para enviar una prueba, siga los pasos a continuación:

1. Asegúrese de que el destino de prueba se ha configurado tal como se describe en [Definición de un destino](../../delivery/using/steps-defining-the-target-population.md#defining-a-specific-proof-target)de prueba específico.
1. Click **[!UICONTROL Send a proof]** on the top bar of the delivery wizard.

   ![](assets/s_ncs_user_email_del_send_proof.png)

1. Inicie el análisis del mensaje. Consulte [Análisis del envío](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).
1. Ahora puede enviar la entrega (consulte [Envío de la entrega](../../delivery/using/steps-sending-the-delivery.md)).

   Una vez que se envía la entrega, la prueba aparecerá en la lista de entrega y se creará y numerará automáticamente. Se puede editar si se desea acceder a su contenido y sus propiedades. Para obtener más información, consulte [esta página](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard).

   ![](assets/s_ncs_user_delivery_validation_cycle_03a.png)

   >[!NOTE]
   >
   >Si se han creado varios formatos para el envío (HTML y texto), se puede elegir el formato de los mensajes que se envían a los destinatarios de la prueba en la sección inferior de la ventana.

   ![](assets/s_ncs_user_email_del_send_proof_formats.png)

Quizá desee modificar el contenido del envío como resultado de los comentarios realizados por el grupo de validación que recibe la prueba. Después de realizar los cambios, debe reiniciar el análisis y enviar otra prueba. Cada nueva prueba se numera y registra en el diario de envíos.

Once the delivery has been analyzed, you can view the various proofs sent via the **[!UICONTROL Proofs]** sub-tab of the log (**[!UICONTROL Audit]** tab).

![](assets/s_ncs_user_delivery_validation_cycle_03.png)

Debe enviar tantas pruebas como sean necesarias hasta finalizar el contenido del envío. Después, puede realizar el envío al destino principal y cerrar el ciclo de validación.

The **[!UICONTROL Advanced]** tab of delivery properties lets you define the properties of the proof. Cuando sea necesario, puede anular las reglas de exclusión de destinatarios.

![](assets/s_ncs_user_wizard_email01_145.png)

Estas son las opciones disponibles:

* La primera opción permite mantener las pruebas duplicadas.
* Las dos opciones siguientes le permiten mantener los destinatarios en la lista negra y las direcciones en cuarentena. See the description of these options for the main target in [Customizing exclusion settings](../../delivery/using/steps-defining-the-target-population.md#customizing-exclusion-settings). A diferencia del objetivo de un envío, donde estas direcciones se excluyen de forma predeterminada, se mantienen de forma predeterminada para el objetivo de una prueba.
* The **[!UICONTROL Keep the delivery code for the proof]** option lets you give the proof the same delivery code as the one defined for the delivery to which it relates. Este código se especifica en el primer paso del asistente de envíos.
* De forma predeterminada, el asunto de la prueba incluye el prefijo “Proof #”, donde # es el número de la prueba. You can change this prefix in the **[!UICONTROL Label prefix]** field.

## Proceso de validación con tipologías {#validation-process-with-typologies}

Antes de enviar cualquier mensaje, se debe analizar la campaña para aprobar su contenido y configuración. Las reglas de comprobación aplicadas durante la fase de análisis se definen en una **tipología**. De forma predeterminada, en el caso de los correos electrónicos, el análisis cubre los siguientes puntos:

* Aprobación del objeto
* Aprobación de las URL e imágenes
* Aprobación de las etiquetas de URL
* Aprobación del enlace de baja
* Comprobación del tamaño de las pruebas
* Comprobación del periodo de validez
* Comprobación de la programación de las olas

The typology to be applied for each delivery is selected in the **[!UICONTROL Typologies]** tab in the delivery parameters.

You can view and edit the approval rules, their content, their order of execution, and their full description via the **[!UICONTROL Administration > Campaign execution > Typology management > Typology rules]** node.

Puede crear nuevas reglas y definir nuevas tipologías a partir de este nodo. Sin embargo, estas tareas se reservan para los usuarios expertos que conocen JavaScript.

To edit the current typology, click the **[!UICONTROL Edit link]** icon to the right of the **[!UICONTROL Typology]** field.

![](assets/s_ncs_user_email_del_typo_tab.png)

The **[!UICONTROL Rule]** tab gives a list of the typology rules to apply. Select a rule and click the **[!UICONTROL Detail...]** icon to view its configuration:

![](assets/s_ncs_user_email_del_typo_rules_edit.png)

>[!NOTE]
>
>**[!UICONTROL Arbitration]** las tipologías de tipo se utilizan en el marco de la gestión de la presión de ventas. Para obtener más información, consulte [esta sección](../../campaign/using/about-marketing-resource-management.md).

## Cambio del modo de aprobación {#changing-the-approval-mode}

The **[!UICONTROL Analysis]** tab for delivery properties lets you select the validation mode. Si se generan advertencias durante el análisis (por ejemplo, si se acentúan ciertos caracteres en el asunto del envío, etc.), puede configurar el envío para definir si se debe ejecutar o no. De forma predeterminada, el usuario debe confirmar el envío de los mensajes al final de la fase de análisis: esta es la validación **manual**.

Seleccione otro modo de aprobación en la lista desplegable del campo apropiado.

![](assets/s_ncs_user_email_del_validation_mode.png)

Están disponibles los siguientes modos de aprobación:

* **[!UICONTROL Manual]**: Al final de la fase de análisis, el usuario debe confirmar el envío para iniciarlo. To do this, click the **[!UICONTROL Start]** button to launch the delivery.
* **[!UICONTROL Semi-automatic]**: El envío comienza automáticamente si la fase de análisis no genera mensajes de advertencia.
* **[!UICONTROL Automatic]**: El envío comienza automáticamente al final de la fase de análisis, independientemente de su resultado.
