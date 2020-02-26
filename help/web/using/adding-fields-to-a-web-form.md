---
title: Adición de campos a un formulario web
seo-title: Adición de campos a un formulario web
description: Adición de campos a un formulario web
seo-description: null
page-status-flag: never-activated
uuid: 33c6ab85-b021-422a-a224-c9eff27e6fc0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: d63892b3-260d-45e8-b99a-1e7c78353395
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 963aaa81971a8883b944bfcf4d1a00d729627916

---


# Adición de campos a un formulario web{#adding-fields-to-a-web-form}

En un formulario web, los campos permiten a los usuarios introducir información y seleccionar opciones. Los formularios web pueden ofrecer campos de entrada, campos de selección, contenido estático y avanzado (captchas, suscripciones, etc.).

Cuando utiliza el asistente para añadir campos, el tipo de campo se detecta automáticamente en función del campo o de la variable de almacenamiento seleccionados. You can edit it using the **[!UICONTROL Type]** drop-down box in the **[!UICONTROL General]** tab.

![](assets/s_ncs_admin_webform_change_type.png)

Al utilizar los botones de la barra de herramientas, seleccione el tipo de campo que desea añadir.

Están disponibles los siguientes tipos de campo:

* Entrada de texto/número. Consulte [Adición de campos](#adding-input-fields)de entrada.
* Selección de lista desplegable. Consulte [Adición de listas](#adding-drop-down-lists)desplegables.
* Opción múltiple mediante casillas de verificación. Consulte [Adición de casillas](#adding-checkboxes)de verificación.
* Selección exclusiva mediante botones de opción. Consulte [Adición de botones](#adding-radio-buttons)de radio.
* Voto en una cuadrícula de opciones. Consulte [Adición de cuadrículas](#adding-grids).
* Números y fechas. See [Adding dates and numbers](#adding-dates-and-numbers).
* Suscripción/cancelación de suscripciones a un servicio de información. Consulte Casillas [de verificación](#subscription-checkboxes)de suscripción.
* Validación de captcha. Consulte [Inserción de un captcha](#inserting-a-captcha).
* Botón Descargar. [Carga de un archivo](#uploading-a-file).
* Constante oculta. Consulte [Inserción de una constante](#inserting-a-hidden-constant)oculta.

Especifique el modo de almacenamiento de respuesta: actualice un campo de la base de datos (solo almacena el último valor guardado) o almacene en una variable (la respuesta no se almacena). Para obtener más información sobre esto, consulte Campos [de almacenamiento de](../../web/using/web-forms-answers.md#response-storage-fields)respuesta.

>[!NOTE]
>
>De forma predeterminada, el campo se inserta en la parte inferior del directorio actual. Utilice las flechas de la barra de herramientas para moverla hacia arriba o hacia abajo.

## Asistente de creación de campos {#field-creation-wizard}

Para cada página del formulario, puede añadir un campo mediante el primer botón de la barra de herramientas. To do this, go to the **[!UICONTROL Add using the wizard]** menu.

![](assets/s_ncs_admin_survey_add_field_menu.png)

Seleccione el tipo de campo que desea crear: puede elegir añadir un campo en la base de datos, añadir una variable o importar un grupo de campos creados en otro formulario y recopilados en un contenedor.

Click **[!UICONTROL Next]** and select the storage field or variable, or the container you want to import.

![](assets/s_ncs_admin_webform_wz_confirm_db.png)

Click **[!UICONTROL Finish]** to insert the selected field into the page.

![](assets/s_ncs_admin_webform_wz_insert_field.png)

## Adición de campos de entrada {#adding-input-fields}

To add an input field, click the **[!UICONTROL Input control]** button and choose the type of field you want to add.

![](assets/s_ncs_admin_webform_select_field.png)

### Tipos de campos de entrada {#types-of-input-fields}

Se pueden insertar cinco tipos diferentes de campos de texto en una página de formulario:

* **Texto**: permite al usuario introducir un texto en una línea.

   ![](assets/s_ncs_admin_survey_txt_ex.png)

* **Número**: permite al usuario introducir un número en una línea. for more on this, refer to [Adding numbers](#adding-numbers).

   Cuando se aprueba la página, se comprueba el contenido del campo para asegurarse de que el valor introducido sea compatible con el campo. Para obtener más información sobre esto, consulte [Definición de la configuración](../../web/using/form-rendering.md#defining-control-settings)de control.

* **Contraseña**: permite al usuario introducir texto en una sola línea. Durante la entrada de texto, los caracteres se sustituyen por puntos:

   ![](assets/s_ncs_admin_survey_passwd_ex.png)

   >[!CAUTION]
   >
   >Las contraseñas se almacenan sin encriptar en la base de datos.

* **Texto multilínea**: permite al usuario introducir texto en varias líneas.

   ![](assets/s_ncs_admin_survey_txtmulti_ex.png)

   >[!CAUTION]
   >
   >Los campos de texto multilínea son campos específicos que pueden contener retornos de carro. Su espacio de almacenamiento debe estar asociado a un campo asignado a un elemento XML, no a un atributo XML. Para obtener más información sobre los tipos de datos en los esquemas, consulte el capítulo “Referencia de esquema” en [esta sección](../../configuration/using/about-schema-reference.md).
   >   
   >Si utiliza el módulo **Encuesta**, puede almacenar este tipo de campo en un campo archivado que se adapta automáticamente al formato. Para obtener más información, consulte [esta sección](../../web/using/about-surveys.md).

* **Texto enriquecido multilínea**: permite al usuario introducir texto con un diseño que se almacena en formato HTML.

   ![](assets/s_ncs_admin_survey_txthtmli_ex.png)

   Se puede seleccionar el tipo de editor ofrecido a los usuarios. To do this, use the drop-down box of the **[!UICONTROL HTML editor]** field in the **[!UICONTROL Advanced]** tab.

   ![](assets/webapp_enrich_text_type.png)

   El número de iconos mostrados varía en función del tipo de editor. For an **[!UICONTROL Advanced]** editor, the rendering will be as follows:

   ![](assets/webapp_enrich_text_max.png)

### Configuración de campos de entrada {#configure-input-fields}

Todos los campos de entrada se configuran en función del mismo modo, con las siguientes opciones:

![](assets/s_ncs_admin_survey_txt_param.png)

The **[!UICONTROL General]** tab lets you enter the name of the field and attribute a default value to it if necessary.

The answer storage mode can be altered via the **[!UICONTROL Edit storage...]** link. Los valores se pueden almacenar en un campo existente de la base de datos; o bien puede optar por no guardar información en la base de datos (utilice una variable local).

>[!NOTE]
>
>Los modos de almacenamiento se detallan en los campos de almacenamiento de [respuesta](../../web/using/web-forms-answers.md#response-storage-fields)

The **[!UICONTROL Advanced]** tab lets you define display parameters for the field (position of labels, alignment, etc.). See [Defining web forms layout](../../web/using/defining-web-forms-layout.md).

## Adición de listas desplegables {#adding-drop-down-lists}

Puede insertar una lista desplegable en una página de encuesta. Esto permite al usuario seleccionar un valor de los que se ofrecen en un menú desplegable.

![](assets/s_ncs_admin_survey_dropdown_sample.png)

To add a drop-down box to a form page, click the **[!UICONTROL Selection controls > Drop-down list]** button in the toolbar of the page editor.

![](assets/s_ncs_admin_survey_create_dropdown.png)

Seleccione el modo de almacenamiento de respuestas y confirme su selección.

Define the labels and values of the list in the lower section of the **[!UICONTROL General]** tab. If the information is stored in an existing field of the database and it is an enumeration field, you can fill in the values automatically by clicking **[!UICONTROL Initialize the list of values from the database]** , as shown below:

![](assets/s_ncs_admin_survey_database_values.png)

>[!NOTE]
>
>Utilice las flechas a la derecha de la lista de valores para cambiar su secuencia.

Si los datos se almacenan en una tabla vinculada, puede seleccionar el campo en el que se guardan los valores sugeridos en la lista. For example, if you select the table of countries, click **[!UICONTROL Initialize the list of values from the database...]** and select the desired field.

![](assets/s_ncs_admin_survey_preload_values.png)

Next, click the **[!UICONTROL Load]** link to retrieve the values:

![](assets/s_ncs_admin_survey_load_button.png)

>[!CAUTION]
>
>Repita esta operación siempre que la lista se actualice para actualizar los valores ofrecidos.

## Adición de casillas de verificación {#adding-checkboxes}

Para que el usuario seleccione una opción, debe utilizar una casilla de verificación.

![](assets/s_ncs_admin_survey_check_box.png)

To add a checkbox to a form, click the **[!UICONTROL Selection controls > Checkbox...]** icon in the toolbar of the page editor.

Seleccione el modo de almacenamiento de respuestas y confirme su selección.

Enter the label of the box in the **[!UICONTROL Label]** field of the **[!UICONTROL General]** tab.

![](assets/s_ncs_admin_survey_check_box_edit.png)

Una casilla de verificación permite asignar un valor al campo (o valor) de almacenamiento en función de si se ha marcado o no la casilla. The **[!UICONTROL Values]** section lets you enter the value to assign if the box is checked (in the **[!UICONTROL Value]** field), and the value to assign if it is not checked (in the **[!UICONTROL Empty value]** field). Estos valores dependen del formato de almacenamiento de datos.

Si el campo de almacenamiento (o variable) es booleano, el valor que se asigna si la casilla no está marcada se deduce automáticamente. In this case, only the **[!UICONTROL Value if checked]** field is offered, as shown below:

![](assets/s_ncs_admin_survey_check_box_enum.png)

## Example: Assign a value to a field if a box is checked {#example--assign-a-value-to-a-field-if-a-box-is-checked}

Se busca insertar una casilla en un formulario para enviar una solicitud de mantenimiento, como se muestra a continuación:

![](assets/s_ncs_admin_survey_check_box_ex.png)

The information will be uploaded to the database and into an existing field (in this case, the **[!UICONTROL Comment]** field):

![](assets/s_ncs_admin_survey_check_box_ex_list.png)

If the &quot;Maintenance required&quot; box is checked, the **[!UICONTROL Comment]** column will contain &quot;Maintenance required&quot;. Si la casilla no está marcada, la columna contiene “Mantenimiento no requerido”. Para obtener este resultado, aplique la configuración siguiente a la casilla de verificación de la página del formulario:

![](assets/s_ncs_admin_survey_check_box_ex_edit.png)

## Adición de botones de opción {#adding-radio-buttons}

Los botones de opción le permiten ofrecer al usuario varias opciones exclusivas entre las que elegir. Estas opciones son valores diferentes para un mismo campo.

![](assets/s_ncs_admin_survey_radio_button.png)

Puede crear botones de opción por separado (botones de unidad) o a través de una lista de selección múltiple, pero ya que el objetivo de los botones de opción es seleccionar una opción u otra, siempre creamos al menos un par de botones de opción en vez de uno solo.

>[!CAUTION]
>
>Para hacer la selección obligatoria, debe crear una lista de selección múltiple.

### Agregar botones únicos {#add-single-buttons}

To add a radio button to a form page, go to the **[!UICONTROL Selection controls > Radio button]** menu in the toolbar of the page editor and choose a storage mode.

![](assets/s_ncs_admin_survey_radio_button_sample.png)

Radio buttons are configured in a similar way to checkboxes (see [Adding checkboxes](#adding-checkboxes)). Sin embargo, no se asigna ningún valor si no se selecciona la opción. Para que varios botones puedan ser interdependientes, es decir, que se deseleccione uno automáticamente si se selecciona el otro, se deben almacenar en el mismo campo. Si no se almacenan en la base de datos, se debe utilizar la misma variable local para el almacenamiento temporal. Consulte Campos [de almacenamiento de respuesta](../../web/using/web-forms-answers.md#response-storage-fields).

### Add a list of buttons {#add-a-list-of-buttons}

To add radio buttons via a list, go to the **[!UICONTROL Selection controls>Multiple choice]** menu in the toolbar of the page editor.

![](assets/s_ncs_admin_survey_radio_button_sample2.png)

Añada tantos botones de opción como etiquetas. La ventaja de esta función es que puede importar valores de un campo existente (en el caso de un campo desglosado) y hacer que el usuario seleccione una opción. Sin embargo, el diseño de los botones es menos flexible.

>[!NOTE]
>
>Los formularios web no permiten la selección de varios valores. La selección múltiple solo se puede activar para los formularios de tipo **Encuesta.** Para obtener más información, consulte [esta sección](../../web/using/about-surveys.md).\
>It is possible, however, to insert a **[!UICONTROL Multiple choice]** type field into a Web application; but without authorizing the selection of several values: the options offered can be selected using radio buttons.

## Adición de cuadrículas {#adding-grids}

Las cuadrículas se utilizan para diseñar páginas de votación en aplicaciones web. Esto permite ofrecer listas de botones de opción para responder a los formularios web de tipo encuesta o evaluación, como se muestra a continuación:

![](assets/s_ncs_admin_survey_vote_param.png)

Para utilizar este tipo de elemento en un formulario, cree una cuadrícula sencilla y añada una línea para cada elemento que desea evaluar.

![](assets/s_ncs_admin_survey_vote_sample.png)

El número de botones de opción de cada línea de la cuadrícula coincide con el número de valores definidos en la cuadrícula simple.

![](assets/s_ncs_admin_survey_vote_ex.png)

Solo se puede seleccionar una opción por cada línea de cuadrícula.

>[!NOTE]
>
>En este ejemplo, la etiqueta de la cuadrícula está oculta. Para ello, vaya a la **[!UICONTROL Advanced]** ficha , la **[!UICONTROL Label position]** pantalla se define como **[!UICONTROL Hidden]** . See [Defining the position of labels](../../web/using/defining-web-forms-layout.md#defining-the-position-of-labels).

## Adición de fechas y números {#adding-dates-and-numbers}

Se puede dar formato al contenido de los campos del formulario para que coincida con los datos almacenados en la base de datos o para satisfacer un requisito en particular. Puede crear campos adecuados para la introducción de números y fechas.

### Adición de fechas {#adding-dates}

![](assets/s_ncs_admin_survey_date_calendar.png)

To allow the user to enter a date in a form page, select **[!UICONTROL Add input field > Date...]** in the toolbar or page editor.

Introduzca una etiqueta para el campo y configure el modo de almacenamiento de datos.

![](assets/s_ncs_admin_survey_date_edit.png)

La sección inferior de la ventana permite seleccionar los formatos de fecha y hora para los valores almacenados en este campo.

![](assets/s_ncs_admin_survey_date_edit_values.png)

También puede optar por no mostrar la fecha (o la hora).

Las fechas se pueden seleccionar mediante un calendario o casillas desplegables. También puede introducirlos directamente en el campo, pero tienen que coincidir con el formato especificado en la pantalla anterior.

>[!NOTE]
>
>De forma predeterminada, las fechas utilizadas en los formularios se introducen mediante un calendario. Para los formularios multilingües, compruebe que los calendarios están disponibles en todos los idiomas utilizados. See [Translating a web form](../../web/using/translating-a-web-form.md).

Sin embargo, en algunos casos (para introducir fechas de nacimiento, por ejemplo), puede ser más fácil utilizar las listas desplegables.

![](assets/s_ncs_admin_survey_date_list_select.png)

To do this, click the **[!UICONTROL Advanced]** tab and choose the input mode using **[!UICONTROL Drop-down lists]**.

![](assets/s_ncs_admin_survey_date_selection.png)

A continuación, puede establecer límites de los valores ofrecidos en la lista.

![](assets/s_ncs_admin_survey_date_first_last_y.png)

### Adición de números {#adding-numbers}

Puede crear campos adecuados para introducir números.

![](assets/s_ncs_admin_survey_number.png)

En un campo numérico, el usuario solo puede introducir números. El control de introducción se aplica automáticamente cuando se aprueba la página.

Según el campo en el que se almacenen los datos en la base de datos, puede aplicar formatos especiales o determinadas restricciones. Asimismo, puede especificar valores máximos y mínimos. Este tipo de campo se configura de la siguiente manera:

![](assets/s_ncs_admin_survey_number_edit.png)

El valor predeterminado es el valor mostrado en el campo cuando se publica el formulario. El usuario puede corregirlo.

You can add a prefix and/or suffix to the numeric field via the **[!UICONTROL Advanced]** tab, as shown below:

![](assets/s_ncs_admin_survey_number_ex_conf.png)

En el formulario, la renderización es la siguiente:

![](assets/s_ncs_admin_survey_number_ex.png)

## Casillas de verificación de suscripción {#subscription-checkboxes}

Puede añadir controles para permitir a los usuarios suscribirse o dar de baja la suscripción de uno o más servicios de información (boletines informativos, avisos, notificaciones en tiempo real, etc.). Para suscribirse, el usuario comprueba el servicio correspondiente.

Para crear una casilla de verificación de suscripción, haga clic en **[!UICONTROL Advanced controls>Subscription]**.

![](assets/s_ncs_admin_survey_subscription_edit.png)

Indicate the label for the checkbox and select the information service concerned using the **[!UICONTROL Service]** drop-down box.

>[!NOTE]
>
>Los servicios de información se describen en [esta página](../../delivery/using/managing-subscriptions.md).

El usuario se suscribe al servicio seleccionando la opción correspondiente.

![](assets/s_ncs_admin_survey_subscribe.png)

>[!CAUTION]
>
>Si el usuario ya está suscrito a un servicio de información y la casilla vinculada a este servicio no está marcada al aprobar el formulario, se da de baja su suscripción.

En [esta sección](../../web/using/about-surveys.md) se encuentran disponibles ejemplos de suscripciones y reenvíos.

## Inserción de un captcha {#inserting-a-captcha}

El propósito de las pruebas de **captcha** es evitar el uso fraudulento de los formularios web.

>[!CAUTION]
>
>Si el formulario contiene varias páginas, el captcha siempre debe colocarse en la última página, justo antes del cuadro de almacenamiento para evitar la elusión de las medidas de seguridad.

To insert a Captcha into a form, click the first button on the toolbar and Select **[!UICONTROL Advanced controls>Captcha]**.

![](assets/s_ncs_admin_survey_add_captcha.png)

Introduzca la etiqueta del campo. Esta etiqueta se muestra delante del área de visualización del captcha. You can change the position of this label in the **[!UICONTROL Advanced]** tab.

![](assets/s_ncs_admin_survey_captcha_adv.png)

>[!NOTE]
>
>For **[!UICONTROL captcha]** type controls, there is no need to indicate a storage field or variable.

El componente captcha se inserta en la página con un campo de entrada situado bajo la ilustración. Estos dos elementos son inseparables y se consideran un solo elemento de cara al diseño de la página (ocupan una sola celda).

![](assets/s_ncs_admin_survey_captcha_sample.png)

Cuando se confirma la página, el campo de entrada aparece en rojo si el contenido del captcha no se ha introducido correctamente.

![](assets/s_ncs_admin_survey_captcha_error.png)

Puede crear el mensaje de error que desea mostrar. Para ello, utilice el **[!UICONTROL Personalize the message]** vínculo de la **[!UICONTROL General]** ficha.

![](assets/s_ncs_admin_survey_captcha_error_msg.png)

>[!NOTE]
>
>Los captchas siempre tienen 8 caracteres de longitud. No puede modificar este valor.

## Carga de un archivo {#uploading-a-file}

Puede añadir un campo de carga a una página. Esta funcionalidad puede ser útil para compartir archivos de la intranet, por ejemplo.

![](assets/s_ncs_admin_survey_download_file.png)

To insert an upload field to a form page, select the **[!UICONTROL Advanced controls > File...]** menu in the toolbar of the page editor.

By default, the uploaded files are stored in resource files accessible via the **[!UICONTROL Resources > Online > Public resources]** menu. Se puede utilizar una secuencia de comandos para cambiar este comportamiento. Esta secuencia de comandos puede utilizar las funciones definidas en [Campaign JSAPI documentation](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html), incluidas las que afectan a la manipulación de archivos.

Se puede almacenar el enlace a estos archivos en una variable local o en un campo de base de datos. Por ejemplo, se puede ampliar el esquema del destinatario para añadir un enlace a recursos basados en archivos.

>[!CAUTION]
>
>* Este tipo de archivo debe reservarse para formularios con acceso seguro (con credenciales).
>* Adobe Campaign no controla el tamaño ni el tipo de recurso cargado: por lo tanto, se recomienda encarecidamente utilizar campos de carga únicamente para sitios de intranet de tipo seguro.
>* Si varios servidores están vinculados a la instancia (arquitectura de equilibrio de carga), debe asegurarse de que las llamadas al formulario Web llegan al mismo servidor.
>* Estas implementaciones requieren la asistencia del equipo de consultoría de Adobe Campaign.
>



## Inserción de una constante oculta {#inserting-a-hidden-constant}

Se puede resaltar un campo cuando el usuario pase una de las páginas del formulario. Para ello, coloque una constante en la página y especifique el valor y la ubicación de almacenamiento.

Este campo no es visible para el usuario, pero puede utilizarse para enriquecer los datos en el perfil de usuario.

En el ejemplo siguiente, el archivo de **origen** del perfil de destinatario se rellena automáticamente cada vez que un usuario aprueba esta página. La constante no se muestra en la página.

![](assets/s_ncs_admin_survey_constante.png)

