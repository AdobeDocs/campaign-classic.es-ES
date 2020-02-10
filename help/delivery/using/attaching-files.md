---
title: Archivos adjuntos
seo-title: Archivos adjuntos
description: Archivos adjuntos
seo-description: null
page-status-flag: never-activated
uuid: a4dc1908-a6ef-4bc8-a310-605fc80c34ca
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-emails
discoiquuid: f3666c12-5e6f-452e-b1d6-b69a7e9f6f6e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 06f2106c7c37fd5f115d15f3530997571f1f8e70

---


# Archivos adjuntos{#attaching-files}

## Acerca de los archivos adjuntos por correo electrónico {#about-email-attachments}

Puede adjuntar uno o varios archivos a un envío de correo electrónico. Hay dos casos posibles:

* Seleccione un archivo y adjúntelo al envío tal cual.
* Personalice el contenido del archivo adjunto para cada destinatario. In this case, you need to create a **calculated attachment**: the name of the attachment is computed at the time of delivery for each message depending on the recipient. El contenido también se puede personalizar y convertir en formato PDF en el momento del envío si tiene la opción **Impresión digital de variable**.

>[!NOTE]
>
>Este tipo de configuración se suele aplicar a las plantillas de envío. For more on this, refer to [About templates](../../delivery/using/about-templates.md).

## Adjuntar un archivo local {#attaching-a-local-file}

Para adjuntar un archivo local a una entrega, siga los pasos a continuación.

>[!NOTE]
>
>Puede adjuntar varios archivos a una entrega. Los archivos adjuntos pueden tener cualquier formato, incluido el formato compactado.

1. Haga clic en el **[!UICONTROL Attachments]** vínculo.
1. Haga clic en el **[!UICONTROL Add]** botón y, a continuación, haga clic **[!UICONTROL File...]** para seleccionar el archivo que se adjuntará al envío.

![](assets/s_ncs_user_wizard_email_attachement.png)

También puede arrastrar y soltar directamente el archivo en el campo de envío **[!UICONTROL Attachments]** , o bien utilizar el icono **[!UICONTROL Attach]** de la barra de herramientas del asistente de envío,

![](assets/s_ncs_user_wizard_add_file_ico.png)

1. Una vez seleccionado el archivo, se carga inmediatamente en el servidor para que esté disponible en el momento de la entrega. Se muestra en el **[!UICONTROL Attachments]** campo.

![](assets/s_ncs_user_wizard_email_attachement_e.png)

## Creación de archivos adjuntos calculados {#creating-a-calculated-attachment}

Al crear un archivo adjunto calculado, el nombre del archivo adjunto se puede calcular durante el análisis o el envío de cada mensaje y puede depender del destinatario. También se puede personalizar y convertir a PDF.

![](assets/s_ncs_user_wizard_attachment.png)

Para crear un archivo adjunto personalizado, siga estos pasos:

1. Haga clic en el **[!UICONTROL Attachments]** vínculo.
1. Haga clic en el **[!UICONTROL Add]** botón y seleccione **[!UICONTROL Calculated attachment]**.
1. Select the type of calculation from the **[!UICONTROL Type]** drop-down list:

![](assets/s_ncs_user_wizard_email01_136.png)

Estas son las opciones disponibles:

* **El nombre del archivo se especifica al crear la plantilla de envío.**
* **El contenido del archivo se personaliza y se convierte a PDF durante el envío de cada mensaje.**
* **El nombre del archivo se calcula durante el análisis del envío (no puede depender del perfil del destinatario).**
* **El nombre del archivo se calcula en el momento del envío para cada destinatario (puede depender del destinatario).**

### Adjuntar un archivo local {#attach-a-local-file}

If the attachment is a local file, select the option: **[!UICONTROL File name is specified when creating the delivery template]**. El archivo se selecciona localmente y se carga en el servidor. Siga estos pasos:

1. Select the file to upload in the **[!UICONTROL Local file]** field.
1. Especifique la etiqueta si es necesario. La etiqueta sustituye al nombre de archivo cuando se visualiza en los sistemas de mensajería. Si no se especifica nada, se utiliza el nombre de archivo de forma predeterminada.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_02.png)

1. Si es necesario, seleccione **[!UICONTROL Upload file on the server]** y haga clic en **[!UICONTROL Update on server]** para iniciar la transferencia.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_01.png)

   A continuación, el archivo está disponible en el servidor para asociarlo a los diferentes envíos creados a partir de esta plantilla.

### Adjuntar un mensaje personalizado {#attach-a-personalized-message}

The option **[!UICONTROL The file content is personalized and converted into PDF format at the time of delivery for each message]** lets you select a fine with personalization fields, such as the last name and first name of the intended recipient.

![](assets/s_ncs_user_wizard_email_calc_attachement_06.png)

Para este tipo de archivos adjuntos, aplique los siguientes pasos de configuración:

1. Seleccione el archivo que desea subir.

   >[!NOTE]
   >
   >El archivo de origen debe crearse en LibreOffice. La instancia debe configurarse en consonancia con los requisitos previos detallados en [esta sección](../../installation/using/before-starting.md).

1. Especifique la etiqueta si es necesario.
1. Seleccione **[!UICONTROL Upload file on the server]** y, a continuación, haga clic **[!UICONTROL Update on server]** para iniciar la transferencia.
1. Puede mostrar una previsualización. Para ello, seleccione un destinatario.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_07.png)

1. Analice su envío y, a continuación, inícielo.

   Cada destinatario recibe un PDF personalizado adjunto al envío.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_08.png)

### Adjuntar un archivo calculado {#attach-a-calculated-file}

Puede calcular el nombre del archivo adjunto durante la preparación del envío. Para ello, seleccione la opción **[!UICONTROL The file name is calculated during delivery analysis (it cannot depend on the recipient)]**.

>[!NOTE]
>
>Esta opción solo se utiliza cuando el envío se realiza mediante un proceso externo o un flujo de trabajo.

1. Especifique la etiqueta que desea aplicar al archivo adjunto.
1. Especifique la ruta de acceso del archivo y su nombre exacto en la ventana de definición.

   >[!CAUTION]
   >
   >El archivo debe estar presente en el servidor.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_04.png)

1. Analice y, a continuación, inicie su envío.

   El nombre de archivo se puede ver en el “log” de análisis.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_05.png)

### Adjuntar un archivo personalizado {#attach-a-personalized-file}

Al seleccionar los datos adjuntos, puede elegir la opción **[!UICONTROL The file name is calculated during delivery for each recipient (it can depend on the recipient)]**. A continuación, puede asignar los datos de personalización del destinatario con el nombre del archivo que se va a enviar.

>[!NOTE]
>
>Esta opción solo se utiliza cuando el envío se realiza mediante un proceso externo o un flujo de trabajo.

1. Especifique la etiqueta que desea aplicar al archivo adjunto.
1. Especifique la ruta de acceso del archivo y su nombre exacto en la ventana de definición. Si el nombre de archivo es personalizado, puede utilizar los campos personalizados para los valores relevantes.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_010.png)

   >[!CAUTION]
   >
   >El archivo debe estar presente en el servidor.

1. Analice y, a continuación, inicie su envío.

   En el ejemplo que se muestra a continuación, el archivo adjunto se eligió en función del nombre definido con los campos de combinación.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_011.png)

### Configuración de archivos adjuntos {#attachment-settings}

For the first two options, you can choose **[!UICONTROL Upload file on the server]** by selecting the appropriate option. El **[!UICONTROL Update the file on the server]** vínculo le permite empezar a cargar.

![](assets/s_ncs_user_wizard_email01_137.png)

Un mensaje le informa de que el archivo se ha cargado en el servidor:

![](assets/s_ncs_user_wizard_email01_1371.png)

Al tratar de cambiar el archivo, aparece un mensaje de advertencia:

![](assets/s_ncs_user_wizard_email01_1372.png)

The **[!UICONTROL Advanced]** tab lets you define advanced options on attached files:

* Puede definir opciones de filtro para evitar enviar el archivo adjunto a todos los destinatarios. The option **[!UICONTROL Enable filtering of recipients who will receive the attachment]** activates an input field used to define a recipient selection script, which must be entered in JavaScript.
* Puede crear una secuencia de comandos del nombre del archivo para personalizarlo.

   Introduzca el texto en la ventana y utilice los campos personalizados disponibles en la lista desplegable. En el ejemplo siguiente, el nombre de archivo está personalizado para contener la fecha del día y el nombre del destinatario.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_09.png)
