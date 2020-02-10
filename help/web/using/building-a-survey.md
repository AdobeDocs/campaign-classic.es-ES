---
title: Generación de una encuesta
seo-title: Generación de una encuesta
description: Generación de una encuesta
seo-description: null
page-status-flag: never-activated
uuid: 50d501b9-2b4f-48d1-b394-f7f71c413990
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: online-surveys
discoiquuid: 6850851d-1dbe-44f0-bbff-18dbac2cad9a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Generación de una encuesta{#building-a-survey}

## Creación de una nueva encuesta {#creating-a-new-survey}

Este capítulo detalla el diseño de un formulario de tipo **Encuesta** utilizando Adobe Campaign, así como las opciones y configuraciones disponibles. Adobe Campaign le permite poner esta encuesta a disposición de los usuarios y recopilar y archivar respuestas en la base de datos.

Web forms are accessed via the **[!UICONTROL Resources > Online > Web applications]** node of the tree. To create a survey, click the **[!UICONTROL New]** button above the list of applications, or right-click the list and choose **[!UICONTROL New]**.

Select the survey template (**[!UICONTROL newSurvey]** by default).

![](assets/s_ncs_admin_survey_select_template.png)

Las páginas del formulario se crean utilizando un editor especial que permite definir y configurar campos de entrada (texto), campos de selección (listas, casillas de verificación, etc.) y elementos estáticos (imágenes, contenido HTML, etc.). They can be collected in &quot;containers&quot; and laid out according to requirements (see [Adding questions](#adding-questions)).

>[!NOTE]
>
>Para obtener más información sobre cómo definir contenido y crear diseños de pantalla para un formulario web, consulte [esta sección](../../web/using/about-web-forms.md).

## Adición de campos {#adding-fields}

Los campos de un formulario permiten a los usuarios introducir información y seleccionar opciones. For each page in the form, they are created via the first button in the toolbar using the **[!UICONTROL Add using the wizard]** menu.

![](assets/s_ncs_admin_survey_add_field_menu.png)

>[!NOTE]
>
>También puede hacer clic con el botón derecho e insertar una zona de entrada. De forma predeterminada, la zona se inserta al final del directorio seleccionado. Utilice las flechas de la barra de herramientas para moverla.

### Tipos de campos {#types-of-fields}

Cuando añada un campo a una encuesta, debe seleccionar su tipo. Estas son las opciones disponibles:

1. **[!UICONTROL Answer a question]**:: esta opción permite declarar un nuevo campo (conocido como &quot;campo archivado&quot;) para almacenar respuestas. En este caso, se guardan todos los valores recopilados, incluso cuando un participante rellene el formulario más de una vez. Este modo de almacenamiento solo está disponible en **Encuestas**. Consulte [Almacenamiento de las respuestas](../../web/using/managing-answers.md#storing-collected-answers)recopiladas.
1. **[!UICONTROL Edit a recipient]**:: esta opción permite seleccionar un campo en la base de datos. En este caso, las respuestas del usuario se almacenan en este campo. Para cada usuario, se conserva únicamente el último valor guardado y se añade a los datos del perfil.
1. **[!UICONTROL Add a variable]**:: esta opción le permite crear una configuración para que la información no se almacene en la base de datos. Las variables locales se pueden declarar en sentido ascendente. También se puede añadirlos directamente al crear el campo.
1. **[!UICONTROL Import an existing question]**:: esta opción le permite importar preguntas existentes creadas en otros estudios.

   >[!NOTE]
   >
   >Los modos de almacenamiento y las importaciones de campo se detallan en [Almacenamiento de las respuestas](../../web/using/managing-answers.md#storing-collected-answers)recopiladas.

La naturaleza del campo que desea añadir (lista desplegable, campo de texto, casillas de verificación, etc.) se adapta al modo de almacenamiento seleccionado. You can change it using the **[!UICONTROL Type]** field of the **[!UICONTROL General]** tab, but make sure to remain consistent with the data type.

![](assets/s_ncs_admin_survey_change_type.png)

En [esta sección](../../web/using/about-web-forms.md) se describen los distintos tipos de campos disponibles.

## Elementos específicos de las encuestas {#survey-specific-elements}

Las encuestas en línea utilizan funcionalidades de las aplicaciones web. A continuación, se describen funciones específicas vinculadas a los campos de encuesta.

### Opción múltiple {#multiple-choice}

For **[!UICONTROL Multiple choice]** type controls, you can define a minimum and maximum number of selections. Por ejemplo, esta opción le permite forzar la selección de al menos **2** valores y como máximo **4** valores de las opciones disponibles:

![](assets/s_ncs_admin_survey_multichoice_ex1.png)

Si el número de selecciones es demasiado grande o demasiado pequeño, se muestra el mensaje correspondiente.

![](assets/s_ncs_admin_survey_multichoice_ex2.png)

>[!NOTE]
>
>En este caso, las opciones se seleccionan mediante las casillas de verificación. Cuando solo se puede seleccionar una opción, se utilizan botones de radio.

La configuración correspondiente es la siguiente:

![](assets/s_ncs_admin_survey_multichoice_ex3.png)

In addition, the storage location for this input field must be a **[!UICONTROL Multiple values]** type **archived field**:

![](assets/s_ncs_admin_survey_multiple_values_field.png)

>[!CAUTION]
>
>* Esta funcionalidad solo está disponible para los formularios de tipo **Encuesta** .
>* Esta opción no es compatible con la visualización de preguntas aleatorias. For more on this, refer to [Adding questions](#adding-questions).


### Adición de preguntas {#adding-questions}

Existen dos tipos de contenedores: estándar y de pregunta. Los contenedores estándar se utilizan para configurar el diseño de página y la visualización condicional en una página. Se detallan en [esta sección](../../web/using/about-web-forms.md).

Utilice un contenedor de **Pregunta** para añadir una pregunta a la página y para insertar las posibles respuestas por debajo en la jerarquía. Las respuestas del usuario a preguntas colocadas en este tipo de contenedor se pueden analizar en los informes.

>[!CAUTION]
>
>Nunca inserte un contenedor **Pregunta** debajo de otro contenedor **Pregunta** en la jerarquía.

![](assets/s_ncs_admin_question_label.png)

La etiqueta de la pregunta se introduce en el campo de etiqueta. En este caso, se aplica el estilo de la hoja de estilo del formulario. Seleccione la **[!UICONTROL Enter the title in HTML format]** opción para personalizarla. Esto le proporciona acceso al editor HTML.

>[!NOTE]
>
>Consulte [esta sección](../../web/using/about-web-forms.md) para obtener más información sobre el uso del editor de HTML.

Por ejemplo:

![](assets/s_ncs_admin_survey_containers_qu_arbo.png)

En el ejemplo anterior, el procesamiento es el siguiente:

![](assets/s_ncs_admin_survey_containers_qu_ex.png)

>[!NOTE]
>
>Cada pregunta tiene un contenedor de tipo de **Pregunta**.

Adobe Campaign permite habilitar el planteamiento de preguntas de forma aleatoria. A continuación, es posible especificar la cantidad de preguntas que desea mostrar en la página, en el campo situado en la parte inferior de la ventana de configuración.

![](assets/s_ncs_admin_survey_containers_qu_display.png)

La renderización debería tener este aspecto:

![](assets/s_ncs_admin_survey_containers_qu_display_rendering.png)

Cuando se actualiza la página, las preguntas mostradas no son las mismas.

>[!CAUTION]
>
>When you display a question randomly (**[!UICONTROL Display randomly]** option checked on the page), be careful not to use multiple choice questions for which one or more selections are mandatory.

