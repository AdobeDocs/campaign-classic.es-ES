---
solution: Campaign Classic
product: campaign
title: Diseño de una encuesta
description: Diseño de una encuesta
audience: web
content-type: reference
topic-tags: online-surveys
translation-type: tm+mt
source-git-commit: e76eb171aac1f7088ff8647f99c928ec349b24fc
workflow-type: tm+mt
source-wordcount: '796'
ht-degree: 100%

---


# Diseño de una encuesta{#building-a-survey}

## Creación de una nueva encuesta {#creating-a-new-survey}

Este capítulo detalla el diseño de un formulario de tipo **Encuesta** utilizando Adobe Campaign, así como las opciones y configuraciones disponibles. Adobe Campaign le permite poner esta encuesta a disposición de los usuarios y recopilar y archivar respuestas en la base de datos.

Se accede a los formularios web a través del nodo de árbol **[!UICONTROL Resources > Online > Web applications]**. Para crear una encuesta, haga clic en el botón **[!UICONTROL New]** situado encima de la lista de aplicaciones o haga clic con el botón derecho en la lista y seleccione **[!UICONTROL New]**.

Seleccione la plantilla de encuesta (**[!UICONTROL newSurvey]** de forma predeterminada).

![](assets/s_ncs_admin_survey_select_template.png)

Las páginas del formulario se crean utilizando un editor especial que permite definir y configurar campos de entrada (texto), campos de selección (listas, casillas de verificación, etc.) y elementos estáticos (imágenes, contenido HTML, etc.). Se pueden recopilar en “contenedores” y mostrar según los requisitos (consulte [Añadir preguntas](#adding-questions)).

>[!NOTE]
>
>Para obtener más información sobre cómo definir contenido y crear diseños de pantalla para un formulario web, consulte [esta sección](../../web/using/about-web-forms.md).

## Adición de campos {#adding-fields}

Los campos de un formulario permiten a los usuarios introducir información y seleccionar opciones. Se crean mediante el primer botón de la barra de herramientas de cada página del formulario, con el menú **[!UICONTROL Add using the wizard]**.

![](assets/s_ncs_admin_survey_add_field_menu.png)

>[!NOTE]
>
>También puede hacer clic con el botón derecho e insertar una zona de entrada. De forma predeterminada, la zona se inserta al final del directorio seleccionado. Utilice las flechas de la barra de herramientas para moverla.

### Tipos de campos {#types-of-fields}

Cuando añada un campo a una encuesta, debe seleccionar su tipo. Estas son las opciones disponibles:

1. **[!UICONTROL Answer a question]**: esta opción le permite declarar un nuevo campo (denominado “campo archivado”) para almacenar respuestas. En este caso, se guardan todos los valores recopilados, incluso cuando un participante rellene el formulario más de una vez. Este modo de almacenamiento solo está disponible en **Encuestas**. Consulte [Almacenamiento de las respuestas recopiladas](../../web/using/managing-answers.md#storing-collected-answers).
1. **[!UICONTROL Edit a recipient]**: esta opción permite seleccionar un campo en la base de datos. En este caso, las respuestas del usuario se almacenan en este campo. Para cada usuario, se conserva únicamente el último valor guardado y se añade a los datos del perfil.
1. **[!UICONTROL Add a variable]**: esta opción permite crear una configuración para que la información no se almacene en la base de datos. Las variables locales se pueden declarar en sentido ascendente. También se puede añadirlos directamente al crear el campo.
1. **[!UICONTROL Import an existing question]**: esta opción permite importar los campos existentes creados en otras encuestas.

   >[!NOTE]
   >
   >Los modos de almacenamiento y las importaciones de campo se detallan en [Almacenamiento de las respuestas recopiladas](../../web/using/managing-answers.md#storing-collected-answers).

La naturaleza del campo que desea añadir (lista desplegable, campo de texto, casillas de verificación, etc.) se adapta al modo de almacenamiento seleccionado. Se puede cambiar con el campo **[!UICONTROL Type]** de la pestaña **[!UICONTROL General]**, pero asegúrese de mantener la coherencia con el tipo de datos.

![](assets/s_ncs_admin_survey_change_type.png)

En [esta sección](../../web/using/about-web-forms.md) se describen los distintos tipos de campos disponibles.

## Elementos específicos de las encuestas {#survey-specific-elements}

Las encuestas en línea utilizan funcionalidades de las aplicaciones web. A continuación, se describen funciones específicas vinculadas a los campos de encuesta.

### Opción múltiple {#multiple-choice}

Para los controles de tipo **[!UICONTROL Multiple choice]**, puede definir una cantidad mínima y máxima de selecciones. Por ejemplo, esta opción le permite forzar la selección de al menos **2** valores y como máximo **4** valores de las opciones disponibles:

![](assets/s_ncs_admin_survey_multichoice_ex1.png)

Si el número de selecciones es demasiado grande o demasiado pequeño, se muestra el mensaje correspondiente.

![](assets/s_ncs_admin_survey_multichoice_ex2.png)

>[!NOTE]
>
>En este caso, las opciones se seleccionan mediante las casillas de verificación. Cuando solo se puede seleccionar una opción, se utilizan botones de radio.

La configuración correspondiente es la siguiente:

![](assets/s_ncs_admin_survey_multichoice_ex3.png)

Además, la ubicación de almacenamiento para este campo de entrada debe ser un **campo archivado** de tipo **[!UICONTROL Multiple values]**:

![](assets/s_ncs_admin_survey_multiple_values_field.png)

>[!CAUTION]
>
>* Esta funcionalidad solo está disponible para los formularios de tipo **Encuesta**.
>* Esta opción no es compatible con la visualización de preguntas aleatorias. Para obtener más información, consulte [Añadir preguntas](#adding-questions).


### Adición de preguntas {#adding-questions}

Existen dos tipos de contenedores: estándar y de pregunta. Los contenedores estándar se utilizan para configurar el diseño de página y la visualización condicional en una página. Se detallan en [esta sección](../../web/using/about-web-forms.md).

Utilice un contenedor de **Pregunta** para añadir una pregunta a la página y para insertar las posibles respuestas por debajo en la jerarquía. Las respuestas del usuario a preguntas colocadas en este tipo de contenedor se pueden analizar en los informes.

>[!CAUTION]
>
>Nunca inserte un contenedor **Pregunta** debajo de otro contenedor **Pregunta** en la jerarquía.

![](assets/s_ncs_admin_question_label.png)

La etiqueta de la pregunta se introduce en el campo de etiqueta. En este caso, se aplica el estilo de la hoja de estilo del formulario. Seleccione la opción **[!UICONTROL Enter the title in HTML format]** para personalizarla. Esto le proporciona acceso al editor HTML.

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
>Cuando visualice una pregunta de forma aleatoria (opción **[!UICONTROL Display randomly]** activada en la página), asegúrese de no utilizar preguntas de opción múltiple para las que una o más selecciones sean obligatorias.

