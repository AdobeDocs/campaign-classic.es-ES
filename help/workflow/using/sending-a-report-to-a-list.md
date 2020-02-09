---
title: Envío de informes a una lista
seo-title: Envío de informes a una lista
description: Envío de informes a una lista
seo-description: null
page-status-flag: never-activated
uuid: 29759fd8-47f3-47cc-9f7e-263e305fd6fb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 41b8a8a8-efac-4e8e-8aea-d4fd06c46e74
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Envío de informes a una lista{#sending-a-report-to-a-list}

This use case details how to generate a monthly out-of-the-box **[!UICONTROL Tracking indicators]** report in PDF format and how to send it to a list of recipients.

![](assets/use_case_report_intro.png)

Los pasos de implementación principales para este caso de uso son:

* Creación de una lista de destinatarios que recibirán la entrega (consulte: [Paso 1: Creación de la lista](#step-1--creating-the-recipient-list)de destinatarios).
* Creating a delivery template that will let you generate a new delivery each time the workflow is executed (refer to: [Step 2: Creating the delivery template](#step-2--creating-the-delivery-template)).
* Creating a workflow that will let you generate the report in PDF format and send it to the list of recipients (refer to: [Step 3: Creating the workflow](#step-3--creating-the-workflow)).

## Step 1: Creating the recipient list {#step-1--creating-the-recipient-list}

Vaya al **[!UICONTROL Profiles and targets]** universo, haga clic en el **[!UICONTROL Lists]** vínculo y luego en el **[!UICONTROL Create]** botón. Select **[!UICONTROL New list]** and create a new recipient list for the report to be sent to.

![](assets/use_case_report_1.png)

Para obtener más información sobre la creación de listas, consulte [esta sección](../../platform/using/creating-and-managing-lists.md).

## Step 2: Creating the delivery template {#step-2--creating-the-delivery-template}

1. Vaya al **[!UICONTROL Resources > Templates > Delivery templates]** nodo del explorador de Adobe Campaign y duplique la plantilla **[!UICONTROL Email delivery]** lista para usar.

   ![](assets/use_case_report_2.png)

   Para obtener más información sobre la creación de plantillas de envío, consulte [esta sección](../../delivery/using/about-templates.md).

1. Introduzca los distintos parámetros de plantilla: etiqueta, objetivo (la lista de destinatarios creados anteriormente), asunto y contenido.

   ![](assets/use_case_report_3.png)

1. Cada vez que se ejecuta el flujo de trabajo, se actualiza el **[!UICONTROL Tracking indicators]** informe (consulte el [paso 3: Creación del flujo de trabajo](#step-3--creating-the-workflow)). To include the latest version of the report in the delivery, you need to add a **[!UICONTROL Calculated attachment]**:

   Para obtener más información sobre la creación de archivos adjuntos calculados, consulte [esta sección](../../delivery/using/attaching-files.md#creating-a-calculated-attachment).

   * Haga clic en el **[!UICONTROL Attachments]** vínculo, haga clic en **[!UICONTROL Add]** y, a continuación, seleccione **[!UICONTROL Calculated attachment]**.

      ![](assets/use_case_report_4.png)

   * Go to the **[!UICONTROL Type]** field and select the fourth option: **[!UICONTROL File name is computed during delivery of each message (it may then depend on the recipient profile)]**.

      ![](assets/use_case_report_5.png)

      The value entered in the **[!UICONTROL Label]** field will not appear in the final delivery.

   * Vaya a la zona de edición e introduzca la ruta de acceso y el nombre del archivo.

      ![](assets/use_case_report_6.png)

      >[!CAUTION]
      >
      >El archivo debe estar presente en el servidor. Su ruta y nombre deben ser idénticos a los especificados en la actividad de **[!UICONTROL JavaScript code]** tipo del flujo de trabajo (consulte: [Paso 3: Creación del flujo de trabajo](#step-3--creating-the-workflow)).

   * Seleccione la **[!UICONTROL Advanced]** ficha y marque **[!UICONTROL Script the name of the file name displayed in the mails sent]**. Vaya a la zona de edición e introduzca el nombre que desea asignar al archivo adjunto en el envío final.

      ![](assets/use_case_report_6bis.png)

## Paso 3: Creación del flujo de trabajo {#step-3--creating-the-workflow}

El siguiente flujo de trabajo se creó para este caso de uso. Tiene tres actividades:

* One **[!UICONTROL Scheduler]** type activity that lets you execute the workflow once a month,
* One **[!UICONTROL JavaScript code]** type activity that lets you generate the report in PDF format,
* one **[!UICONTROL Delivery]** type activity that uses the previously created delivery template.

![](assets/use_case_report_8.png)

1. Now go to the **[!UICONTROL Administration > Production > Technical workflows]** node and create a new workflow.

   ![](assets/use_case_report_7.png)

1. Start by adding a **[!UICONTROL Scheduler]** type activity and configure it so that the workflow executes on the first Monday of the month.

   ![](assets/use_case_report_9.png)

   For more on configuring the scheduler, refer to [Scheduler](../../workflow/using/scheduler.md).

1. A continuación, agregue un **[!UICONTROL JavaScript code]** tipo de actividad.

   ![](assets/use_case_report_10.png)

   Introduzca el código siguiente en la zona de edición:

   ```
   var reportName = "deliveryFeedback";
   var path = "/tmp/deliveryFeedback.pdf";
   var exportFormat = "PDF";
   var reportURL = "<PUT THE URL OF THE REPORT HERE>";
   var _ctx = <ctx _context="global" _reportContext="deliveryFeedback" />
   var isAdhoc = 0;
   
   xtk.report.export(reportName, _ctx, exportFormat, path, isAdhoc);
   ```

   Se utilizan las siguientes variables:

   * **var reportName**: introduzca el nombre interno del informe en comillas dobles. En este caso, el nombre interno del informe **Indicador de seguimiento** es “deliveryFeedback”.
   * **var path**: introduzca la ruta donde se guarda el archivo (“tmp/files/”), el nombre que desea dar al archivo (“deliveryFeedback”) y la extensión de archivo (“.pdf”). En este caso, se ha utilizado el nombre interno como nombre de archivo. Los valores deben estar entre comillas dobles y separados por el carácter “+”.

      >[!CAUTION]
      >
      >El archivo debe guardarse en el servidor. You must enter the same path and the same name in the **[!UICONTROL General]** tab of the edit window for the calculated attachment (refer to: [Step 2: Creating the delivery template](#step-2--creating-the-delivery-template)).

   * **var exportFormat**: introduzca el formato de exportación del archivo (“PDF”).
   * **var_ctx** (contexto): en este caso, estamos utilizando el **[!UICONTROL Tracking indicators]** informe en su contexto mundial.

1. Finish by adding a **[!UICONTROL Delivery]** type activity with the following options:

   * **[!UICONTROL Delivery]**:: seleccione **[!UICONTROL New, created from a template]** y seleccione la plantilla de envío creada anteriormente.
   * Para los campos **[!UICONTROL Recipients]** y **[!UICONTROL Content]** , seleccione **[!UICONTROL Specified in the delivery]**.
   * **[!UICONTROL Action to execute]**:: seleccione **[!UICONTROL Prepare and start]**.
   * Desmarcar **[!UICONTROL Generate an outbound transition]** y **[!UICONTROL Process errors]**.
   ![](assets/use_case_report_11.png)

