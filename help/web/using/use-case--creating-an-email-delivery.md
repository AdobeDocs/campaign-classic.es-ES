---
title: '"Ejemplo de uso: creación de un envío por correo electrónico"'
seo-title: '"Ejemplo de uso: creación de un envío por correo electrónico"'
description: '"Ejemplo de uso: creación de un envío por correo electrónico"'
seo-description: null
page-status-flag: never-activated
uuid: 7cd6329c-63d5-4cf0-9451-f0b4c2eaf0dd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: editing-html-content
discoiquuid: 4ec34980-62a2-47b9-b103-de4290925624
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 36beb1eca48c698634c7548e0f931ab3fe17c021

---


# Ejemplo de uso: creación de un envío por correo electrónico{#use-case-creating-an-email-delivery}

En este caso de uso, aprenderá los pasos para diseñar una entrega por correo electrónico con el Editor de contenido digital (DCE) de Adobe Campaign.

El objetivo final es crear un envío con una plantilla personalizada que contenga:

* Una dirección postal para un destinatario (con nombre completo).
* Dos tipos de enlaces a una dirección URL externa
* Una página espejo
* Un enlace a una aplicación web

>[!NOTE]
>
>Antes de empezar, debe tener al menos una **plantilla HTML** configurada para alojar el contenido de los envíos futuros.
>
>En la entrega **[!UICONTROL Properties]** , asegúrese de que la **[!UICONTROL Content editing mode]** (en la **[!UICONTROL Advanced]** ficha) está configurada en **[!UICONTROL DCE]**. Para garantizar el funcionamiento óptimo del editor, consulte las optimizaciones [de edición de](../../web/using/content-editing-best-practices.md)contenido.

## Paso 1: Creación de un envío {#step-1---creating-a-delivery}

To create a new delivery, place your cursor in the **Campaigns** tab and click **Deliveries**. Después, haga clic en el botón **Crear** situado encima de la lista de envíos existentes. Para obtener más información sobre la creación de envíos, consulte [esta página](../../delivery/using/about-email-channel.md).

![](assets/delivery_step_1.png)

## Paso 2: Selección de una plantilla {#step-2---selecting-a-template}

Seleccione una plantilla de envío y asigne un nombre al envío. Este nombre solo está visible para los usuarios de la consola de Adobe Campaign y no para los destinatarios. Sin embargo, este título se muestra en la lista de envíos. Haga clic **[!UICONTROL Continue]**.

![](assets/dce_delivery_model.png)

## Paso 3: Selección de contenido {#step-3---selecting-a-content}

El editor de contenido incluye varias plantillas predeterminadas con distintas estructuras (columnas, áreas de texto, etc.).

Select the content template that you want to use, then click the **[!UICONTROL Start with the selected content]** button to display the template in the created delivery.

![](assets/dce_select_model.png)

You can also import an HTML content created outside of Adobe Campaign by selecting **[!UICONTROL From a file]**.

![](assets/dce_select_from_file_template.png)

Se puede guardar este contenido como una plantilla para su uso futuro. Una vez creada una plantilla de contenido personalizada, se puede obtener una vista previa de la misma en la lista de plantillas. For more on this, refer to [Template management](../../web/using/template-management.md).

>[!CAUTION]
>
>Si utiliza la **interfaz web de Adobe Campaign**, debe importar un archivo .zip que incluya el contenido HTML y las imágenes relacionadas.

## Paso 4: Diseño del mensaje {#step-4---designing-the-message}

* Mostrar el nombre completo de los destinatarios

   Para insertar el primer y el segundo nombre de los destinatarios en un campo de texto de su envío, haga clic en el campo de texto seleccionado y, a continuación, coloque el cursor donde desee mostrarlos. Click the first icon in the pop-up toolbar, then click **[!UICONTROL Personalization block]**. Seleccione **[!UICONTROL Greetings]** y haga clic en **[!UICONTROL OK]**.

   ![](assets/dce_personalizationblock_greetings.png)

* Inserción de un enlace en una imagen

   To take delivery recipients to an external address via an image, click on the relevant image to display the pop-up toolbar, place the cursor on the first icon then click **[!UICONTROL Link to an external URL]**. For more on this, refer to [Adding a link](../../web/using/editing-content.md#adding-a-link).

   ![](assets/dce_externalpage.png)

   Introduzca la dirección URL del enlace en el campo **URL** con el formato **https://www.myURL.com** y, a continuación, confirme la acción.

   El enlace se puede cambiar en cualquier momento con la sección a la derecha de la ventana.

* Inserción de un enlace en el texto

   Para integrar un enlace externo en el texto del envío, seleccione un texto o un bloque de texto y, a continuación, haga clic en el primer icono de la barra de herramientas emergente. Haga clic en **[!UICONTROL Link to an external URL]**, introduzca la dirección del vínculo en el **[!UICONTROL URL]** campo. For more on this, refer to [Adding a link](../../web/using/editing-content.md#adding-a-link).

   El enlace se puede cambiar en cualquier momento con la sección a la derecha de la ventana.

   >[!CAUTION]
   >
   >The text entered in the **[!UICONTROL Label]** field replaces the original text.

* Adición de una página espejo

   Para permitir a los destinatarios ver el contenido del envío en un navegador web, se puede integrar un enlace a una página espejo en el envío.

   Haga clic en el campo de texto en el que desea ver el enlace publicado. Haga clic en el primer icono de la barra de herramientas emergente, seleccione **[!UICONTROL Personalization block]** y luego **[!UICONTROL Link to Mirror Page (MirrorPage)]**. Click **[!UICONTROL Save]** to confirm.

   ![](assets/dce_mirrorpage.png)

   >[!CAUTION]
   >
   >La etiqueta de bloque de personalización sustituye automáticamente el texto original del envío.

* Integración de un enlace a una aplicación web

   El editor de contenido permite integrar enlaces a aplicaciones web desde la consola de Adobe Campaign, como una página de destino o una página de formulario. Para obtener más información sobre esto, consulte [Vínculo a una aplicación](../../web/using/editing-content.md#link-to-a-web-application)Web.

   Seleccione un campo de texto para enlazar a una aplicación web y, a continuación, haga clic en el primer icono. Choose **[!UICONTROL Link to a Web application]**, then select the desired application by clicking the icon at the end of the **Web Application** field.

   ![](assets/dce_webapp.png)

   Haga clic en **Guardar** para confirmar.

   >[!NOTE]
   >
   >Este paso requiere haber guardado al menos una aplicación web previamente. Se pueden encontrar en la **[!UICONTROL Campaigns > Web applications]** ficha de la consola.

## Paso 5: Guardado de un envío {#step-5---saving-the-delivery}

Una vez que el contenido esté integrado, guarde el envío haciendo clic en **Guardar**. It will now be displayed in your list of deliveries, found in the **[!UICONTROL Campaigns > Deliveries]** tab.
