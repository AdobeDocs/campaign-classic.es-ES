---
title: Definición de la secuenciación de la página de formularios web
seo-title: Definición de la secuenciación de la página de formularios web
description: Definición de la secuenciación de la página de formularios web
seo-description: null
page-status-flag: never-activated
uuid: 297fad62-d806-4bd8-9b8c-313c20344ab0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: 85bf3244-6896-43e7-96b8-84c45c282fec
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# Definición de la secuenciación de la página de formularios web{#defining-web-forms-page-sequencing}

El formulario puede contener una o más páginas. Se crea mediante un diagrama que permite secuenciar las páginas y las pruebas, la ejecución de secuencias de comandos y las fases de registro de saltos de página. El modo de creación del diagrama es el mismo que para un flujo de trabajo.

## Sobre la página anterior y la página siguiente {#about-previous-page-and-next-page}

Para cada página, puede eliminar los botones **[!UICONTROL Next]** o **[!UICONTROL Previous]** . Para ello, seleccione la página correspondiente y seleccione la opción **[!UICONTROL Disable next page]** o **[!UICONTROL Disallow returning to the previous page]** .

![](assets/s_ncs_admin_survey_no_next_page.png)

Puede reemplazar estos botones con enlaces. Consulte [Inserción de contenido](../../web/using/static-elements-in-a-web-form.md#inserting-html-content)HTML.

## Inserción de un salto {#inserting-a-jump}

The **[!UICONTROL Jump]** object gives access to another page or another form when the user clicks **[!UICONTROL Next]**.

El destino puede ser:

* otra página del formulario. To do this, select **[!UICONTROL Internal activity]** and then specify the desired page, as below:

   ![](assets/s_ncs_admin_jump_param1.png)

* otro formulario. To do this, select the **[!UICONTROL Explicit]** option and specify the destination form.

   ![](assets/s_ncs_admin_jump_param2.png)

* El destino se puede almacenar en una variable. En este caso, selecciónelo en la lista desplegable, como se muestra a continuación:

   ![](assets/s_ncs_admin_jump_param3.png)

* The **[!UICONTROL Comment]** tab lets you enter information that will be visible by the operator when they click the object in the diagram.

   ![](assets/s_ncs_admin_survey_jump_comment.png)

## Example: accessing another form according to a parameter of the URL {#example--accessing-another-form-according-to-a-parameter-of-the-url}

En el ejemplo siguiente, se desea configurar un formulario web que, cuando está aprobado, muestra otro formulario designado por un parámetro de la dirección URL. Para ello, siga los siguientes pasos:

1. Insert a jump at the end of a form: this replaces the **[!UICONTROL End]** box.

   ![](assets/s_ncs_admin_survey_jump_sample1.png)

1. En las propiedades del formulario, añada un parámetro (**siguiente**) almacenado en una variable local (**siguiente**). Las variables locales se detallan en [Almacenamiento de datos en una variable](../../web/using/web-forms-answers.md#storing-data-in-a-local-variable)local.

   ![](assets/s_ncs_admin_survey_jump_sample2.png)

1. Edit the **[!UICONTROL Jump]** object, select the **[!UICONTROL Stored in a variable]** option and select the **next** variable from the drop-down box.

   ![](assets/s_ncs_admin_survey_jump_sample3.png)

1. La dirección URL de envío debe incluir el nombre interno del formulario de destino, por ejemplo:

   ```
   https://[myserver]/webForm/APP62?&next=APP22
   ```

   When the user clicks the **[!UICONTROL Approve]** button, form **APP22** is displayed.

## Inserción de un enlace a otra página del formulario {#inserting-a-link-to-another-page-of-the-form}

Puede insertar enlaces a otras páginas del formulario. To do this, add a **[!UICONTROL Link]** type static element to the page. For more on this, refer to [Inserting a link](../../web/using/static-elements-in-a-web-form.md#inserting-a-link).

## Visualización condicional de la página {#conditional-page-display}

### Mostrar según las respuestas {#display-based-on-responses}

The **[!UICONTROL Test]** box lets you condition the sequencing of pages in a form. Permite definir varias líneas de ramificación según los resultados de la prueba. Esto permite mostrar diferentes páginas según las respuestas de los usuarios.

Por ejemplo, se puede mostrar una página diferente para los clientes que ya hayan realizado un pedido en línea y otra para aquellos que hayan realizado más de diez pedidos. To do this, in the first page of the form, insert a **[!UICONTROL Number]** type input field for the user to state how many orders they have placed.

![](assets/s_ncs_admin_survey_test_ex0.png)

Se puede almacenar esta información en un campo de la base de datos o utilizar una variable local.

>[!NOTE]
>
>Los modos de almacenamiento se detallan en los campos [de almacenamiento de](../../web/using/web-forms-answers.md#response-storage-fields)respuesta.

En este ejemplo, se desea utilizar una variable:

![](assets/s_ncs_admin_survey_test_ex1.png)

En el diagrama del formulario, inserte un cuadro de prueba para definir las condiciones. Para cada condición, se añade una nueva rama en la salida del cuadro de prueba.

![](assets/s_ncs_admin_survey_test_ex2.png)

Select the **[!UICONTROL Activate the default branching]** option to add a transition for cases where none of the conditions is true. Esta opción no es necesaria si las condiciones abarcan cada caso posible.

A continuación, defina la secuenciación de la página cuando una o varias de las condiciones sean verdaderas, por ejemplo:

![](assets/s_ncs_admin_survey_test_ex3.png)

### Mostrar según los parámetros {#display-based-on-parameters}

Asimismo, se puede personalizar la secuenciación de la página según los parámetros de inicialización del formulario web o según los valores almacenados en la base de datos. Consulte Parámetros [de URL del formulario](../../web/using/defining-web-forms-properties.md#form-url-parameters).

## Adición de secuencias de comandos {#adding-scripts}

The **[!UICONTROL Script]** object lets you enter a JavaScript script directly, for example to modify the value of a field, retrieve data from the database, or call an Adobe Campaign API.

## Personalización de la página final {#personalizing-the-end-page}

Se debe colocar una página final al final del diagrama. The end page is displayed when the user clicks the **[!UICONTROL Approve]** button in the Web form.

To personalize this page, double-click **[!UICONTROL End]** and enter the content of the page in the central editor.

![](assets/s_ncs_admin_survey_end_page_edit.png)

* Puede copiar y pegar contenido HTML existente. To do this, click **[!UICONTROL Display source code]** and insert the HTML code.
* Se puede utilizar una URL externa. Para ello, seleccione la opción correspondiente e introduzca la dirección URL de la página que desea mostrar.

