---
title: Publicación, seguimiento y utilización de datos recopilados
seo-title: Publicación, seguimiento y utilización de datos recopilados
description: Publicación, seguimiento y utilización de datos recopilados
seo-description: null
page-status-flag: never-activated
uuid: eac16f2c-0423-4727-a2da-3af1d6c616ec
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: online-surveys
discoiquuid: 434a4bda-0907-42a7-8a75-2db658bba046
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Publicación, seguimiento y utilización de datos recopilados{#publish-track-and-use-collected-data}

Una vez creado, configurado y publicado el formulario, puede compartir el vínculo con su audiencia y rastrear las respuestas.

>[!NOTE]
>
>El ciclo de vida de una encuesta en Adobe Campaign, así como sus modos de publicación y envío, son similares a los de los formularios web: estos se detallan en [esta sección](../../web/using/about-web-forms.md).

## Panel de encuesta {#survey-dashboard}

Cada encuesta tiene su propio panel que le permite ver su estado, descripción, dirección URL pública y programación de disponibilidad. También le permite ver los informes disponibles. For more on this, refer to [Reports on surveys](#reports-on-surveys).

La URL pública de la encuesta se muestra en el panel:

![](assets/survey_public_url.png)

## Seguimiento de respuestas {#response-tracking}

Puede realizar un seguimiento de las respuestas a la encuesta en los “logs” e informes.

### “Logs” de encuesta{#survey-logs}

For each survey delivered, you can track the responses in the **[!UICONTROL Logs]** tab. Esta pestaña muestra la lista de usuarios que han completado la encuesta y su origen:

![](assets/s_ncs_admin_survey_logs.png)

Haga doble clic en una línea para mostrar el formulario de la encuesta tal y como lo ha rellenado el encuestado. Puede examinar la encuesta y acceder a las respuestas en su totalidad. Se pueden exportar en un archivo externo. For more on this, refer to [Exporting answers](#exporting-answers).

El origen se indica en la dirección URL de la encuesta añadiendo los caracteres siguientes:

```
?origin=xxx
```

while the survey is being edited, its URL contains the parameter **[!UICONTROL __uuid]**, which indicates that it is in a test phase and not yet online. Al acceder a la encuesta a través de esta dirección URL, los archivos creados no se tienen en cuenta en el seguimiento (informes). The origin is forced to the value **[!UICONTROL Adobe Campaign]**.

Para obtener más información sobre los parámetros URL, consulte [esta página](../../web/using/defining-web-forms-properties.md#form-url-parameters).

### Informes sobre las encuestas {#reports-on-surveys}

La pestaña del panel le permite acceder a los informes sobre las encuestas. Haga clic en el nombre del informe para verlo.

![](assets/s_ncs_admin_survey_report_doc.png)

The structure of the survey is visible in the **[!UICONTROL Documentation]** report.

Two other reports on Web surveys are available in the **[!UICONTROL Reports]** tab of the surveys: **[!UICONTROL General]** and **[!UICONTROL Breakdown of responses]**.

* General

   Este informe contiene información general sobre la encuesta: cómo cambia el número de respuestas con el tiempo y la distribución por origen e idioma.

   Ejemplo de informe general:

   ![](assets/s_ncs_admin_survey_report_0.png)

* Desglose de respuestas

   Este informe muestra el desglose de las respuestas por cada pregunta. This breakdown is only available for answers given to fields stored in **[!UICONTROL Question]** type containers. Solo es válido para controles de selección (sin desglose en campos de texto, por ejemplo).

   ![](assets/s_ncs_admin_survey_report_2.png)

## Exportación de respuestas {#exporting-answers}

Las respuestas a una encuesta se pueden exportar a un archivo externo para su procesado posterior. Hay dos formas de hacerlo:

1. Exportación de datos del informe

   To export report data, click the **[!UICONTROL Export]** button and choose the export format.

   Para obtener más información sobre la exportación de los datos de un informe, consulte [esta sección](../../reporting/using/about-reports-creation-in-campaign.md).

1. Exportación de respuestas

   To export answers, click the **[!UICONTROL Responses]** tab of the survey and right-click. Select **[!UICONTROL Export...]**.

   ![](assets/s_ncs_admin_survey_logs_export_menu.png)

   A continuación, introduzca la información que desea exportar y el archivo de almacenamiento.

   Puede configurar el contenido y el formato del archivo de salida en el asistente de exportación.

   Esto le permite:

   * añadir columnas al archivo de salida y recuperar la información sobre el destinatario (que se almacena en la base de datos).
   * formatear los datos exportados,
   * seleccionar el formato de codificación para la información del archivo.
   If the survey you want to export contains several **[!UICONTROL Multi-line text]** or **[!UICONTROL HTML text]** fields, it has to be exported in **[!UICONTROL XML]** format. To do this, select this format in the drop-down list of the **[!UICONTROL Output format]** field, as shown below:

   ![](assets/s_ncs_admin_survey_logs_export_xml.png)

   Haga clic en **[!UICONTROL Start]** para ejecutar la exportación.

   >[!NOTE]
   >
   >En [esta sección](../../platform/using/generic-imports-and-exports.md) se describen las exportaciones de datos y las fases de su configuración.

## Uso de los datos recopilados {#using-the-collected-data}

La información recopilada mediante encuestas en línea se puede recuperar dentro del marco de un flujo de trabajo de objetivos. Para ello, utilice el **[!UICONTROL Survey responses]** cuadro.

En el siguiente ejemplo, queremos crear una oferta web especialmente para los cinco destinatarios con al menos dos hijos y con las puntuaciones más altas en la encuesta en línea. Las respuestas a esta encuesta son:

![](assets/s_ncs_admin_survey_responses_wf_box_4.png)

In the targeting workflow, the **[!UICONTROL Survey responses]** will be configured as follows:

![](assets/s_ncs_admin_survey_responses_wf_box_1.png)

Comience por seleccionar la encuesta que le interese y los datos que desea extraer en la sección central de la ventana. En este caso necesitamos extraer al menos la columna puntuación, ya que pretendemos usarla en el cuadro de división para recuperar las cinco puntuaciones más altas.

Indicate the filtering conditions for answers by clicking the **[!UICONTROL Edit query...]** link.

![](assets/s_ncs_admin_survey_responses_wf_box_2.png)

Inicio de un flujo de trabajo de objetivos La consulta recupera 8 destinatarios.

![](assets/s_ncs_admin_survey_responses_wf_box_5.png)

Haga clic con el botón derecho en la transición de salida del cuadro de recopilación para verlas.

![](assets/s_ncs_admin_survey_responses_wf_box_6.png)

A continuación, coloque un cuadro de divisón en el flujo de trabajo para recuperar los 5 destinatarios con la máxima puntuación.

Edite el cuadro de división para configurarlo:

* Start by selecting the adequate schema in the **[!UICONTROL General]** tab, then configure the sub-set:

   ![](assets/s_ncs_admin_survey_responses_wf_box_6b.png)

* Vaya a la **[!UICONTROL Sub-sets]** ficha, seleccione la **[!UICONTROL Limit the selected records]** opción y haga clic en el **[!UICONTROL Edit...]** vínculo.

   ![](assets/s_ncs_admin_survey_responses_wf_box_7.png)

* Seleccione la **[!UICONTROL Keep only the first records after sorting]** opción y seleccione la columna de ordenación. Marque la **[!UICONTROL Descending sort]** opción.

   ![](assets/s_ncs_admin_survey_responses_wf_box_8.png)

* Click the **[!UICONTROL Next]** button and limit the number of records to 5.

   ![](assets/s_ncs_admin_survey_responses_wf_box_9.png)

* Click **[!UICONTROL Finish]** then restart the workflow to approve targeting.

## Estandarización de datos {#standardizing-data}

Se pueden configurar procesos de estandarización en Adobe Campaign para los datos recopilados mediante alias. Esto permite estandarizar los datos almacenados en la base de datos: para ello, defina alias en la lista desglosada que contengan la información relevante.

Para obtener más información, consulte [esta página](../../platform/using/managing-enumerations.md#about-enumerations).
