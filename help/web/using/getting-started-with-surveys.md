---
title: Introducción a las encuestas
seo-title: Introducción a las encuestas
description: Introducción a las encuestas
seo-description: null
page-status-flag: never-activated
uuid: 62ca684c-94a7-465a-9536-75e8a96b1c0e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: online-surveys
discoiquuid: 2df82006-dcc3-4b07-bc36-b646b1c27aaa
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Introducción a las encuestas{#getting-started-with-surveys}

A continuación se muestra una breve descripción general de los pasos principales para crear una encuesta sencilla mediante la siguiente plantilla:

![](assets/s_ncs_admin_survey_result.png)

Estos pasos son:

1. [Paso 1: Creación de una encuesta](#step-1---creating-a-survey),
1. [Paso 2: Selección de la plantilla](#step-2---selecting-the-template),
1. [Paso 3: Generación de una encuesta](#step-3---building-the-survey),
1. [Paso 4: Creación de una página de contenido](#step-4---creating-the-page-content),
1. [Paso 5: Almacenamiento de los datos de la encuesta](#step-5---storing-the-survey-data-),
1. [Paso 6: Publicación de las páginas](#step-6---publishing-the-pages),
1. [Paso 7: Compartir la encuesta en línea](#step-7---sharing-your-online-survey).

## Paso 1: Creación de una encuesta {#step-1---creating-a-survey}

Para crear una nueva encuesta, vaya al entorno **[!UICONTROL Campañas]** o **[!UICONTROL Perfiles y objetivos]** y haga clic en el menú **[!UICONTROL Aplicaciones web]**. Haga clic en el botón **[!UICONTROL Crear]** situado encima de la lista de formularios.

![](assets/s_ncs_admin_survey_create.png)

## Paso 2: Selección de la plantilla {#step-2---selecting-the-template}

Seleccione una plantilla de encuesta y después asígnele un nombre. Los usuarios finales no ven este nombre, pero permite identificar la encuesta dentro de Adobe Campaign. Haga clic en **[!UICONTROL Guardar]** y añada la encuesta a la lista de aplicaciones web.

![](assets/s_ncs_admin_survey_wz_00.png)

## Paso 3: Generación de una encuesta {#step-3---building-the-survey}

Las encuestas se generan en un diagrama en el que se colocan los siguientes elementos: las páginas en las que se crea el contenido, los datos de precarga y los pasos para guardar, y las fases de prueba. También se pueden insertar secuencias de comandos y consultas.

Para crear el gráfico, haga clic en el formulario **[!UICONTROL Editar]** de la encuesta.

Una encuesta debe contener **al menos** los tres componentes siguientes: una página, un cuadro de almacenamiento y una página final.

* Para crear una página, seleccione el objeto **[!UICONTROL Página]** en la sección izquierda del editor y suéltelo en la sección central, como se muestra a continuación:

   ![](assets/s_ncs_admin_survey_new_page.png)

* A continuación, seleccione el objeto **[!UICONTROL Almacenamiento]** y colóquelo en la transición de salida de la página.
* Finalmente, seleccione el objeto **[!UICONTROL Fin]** y colóquelo al final de la transición de salida del cuadro de almacenamiento para obtener el siguiente diagrama:

   ![](assets/s_ncs_admin_survey_end.png)

## Paso 4: Creación de una página de contenido {#step-4---creating-the-page-content}

En el siguiente ejemplo se utiliza una página de tipo **[!UICONTROL Página (v5 compatibility)]**. Se accede a este tipo de página a través del menú avanzado de la pestaña **[!UICONTROL Editar]**.

![](assets/s_ncs_admin_survey_pagev5.png)

* Adición de campos de entrada

   Para crear el contenido de la página, debe editarlo: para hacerlo, haga doble clic en el objeto **[!UICONTROL Página]**. Haga clic en el primer icono de la barra de herramientas para abrir el asistente de creación de campos. Para crear un campo de entrada para almacenar el nombre de usuario en el campo correspondiente del perfil del destinatario, seleccione **[!UICONTROL Editar un destinatario]**.

   ![](assets/s_ncs_admin_survey_add_field_menu.png)

   Haga clic en el botón **[!UICONTROL Siguiente]** para seleccionar el campo dedicado al almacenamiento de datos en la base de datos. En este caso, el campo es “Apellidos”.

   ![](assets/s_ncs_admin_survey_choose_field.png)

   Haga clic en **[!UICONTROL Finalizar]** para confirmar la creación del campo.

   De forma predeterminada, cuando la información se almacena en un campo que ya existe en la base de datos, el campo adopta el nombre del campo seleccionado, es decir, “Apellidos” en este caso. Puede modificar esta etiqueta como se muestra a continuación:

   ![](assets/s_ncs_admin_survey_change_label.png)

   Ahora cree un campo de entrada para el número de cuenta de usuario. Repita la operación y seleccione el campo “n.º de cuenta”.

   Aplique el mismo procedimiento para añadir un campo para que el usuario introduzca una dirección de correo electrónico.

* Para crear una pregunta, haga clic con el botón derecho en el último elemento del directorio y seleccione **[!UICONTROL Contenedores > Pregunta]** o haga clic en el icono **[!UICONTROL Contenedores]** y seleccione **[!UICONTROL Pregunta]**.

   ![](assets/s_ncs_admin_survey_add_qu.png)

   Introduzca la etiqueta de la pregunta e inserte los campos de respuesta como una subcategoría de la pregunta. Para ello, se debe seleccionar el nodo vinculado a la pregunta al crear el campo de respuesta. Añadir una **[!UICONTROL lista desplegable]** mediante el icono **[!UICONTROL Controles de selección]** o haga clic con el botón derecho, como se muestra a continuación:

   ![](assets/s_ncs_admin_survey_add_list.png)

   Seleccione un espacio de almacenamiento: seleccione un campo de enumeración para recuperar los valores automáticamente (en este caso, el formato de correo electrónico).

   ![](assets/s_ncs_admin_survey_add_itz_list.png)

   En la pestaña **[!UICONTROL General]**, haga clic en el vínculo **[!UICONTROL Iniciar la lista de valores de la base de datos]**: la tabla de valores se introduce automáticamente.

   ![](assets/s_ncs_admin_survey_add_value.png)

   Haga clic en **[!UICONTROL OK]** para cerrar el editor y en **[!UICONTROL Guardar]** para guardar los cambios.

   >[!NOTE]
   >
   >Para cada campo o pregunta, puede adaptar el diseño de página según sus necesidades, gracias a las opciones de la pestaña **[!UICONTROL Avanzado]**. El diseño de las pantallas de encuestas se explica en [esta sección](../../web/using/about-web-forms.md).

   En la pantalla de detalles, haga clic en la pestaña **[!UICONTROL Vista previa]** para ver la renderización de la encuesta que acaba de crear.

   ![](assets/s_ncs_admin_survey_preview.png)

## Paso 5: Almacenamiento de los datos de la encuesta {#step-5---storing-the-survey-data-}

El cuadro de almacenamiento le permite guardar las respuestas del usuario en la base de datos. Debe seleccionar una clave de reconciliación para identificar los perfiles que ya se encuentran en la base de datos.

Para ello, edite el cuadro y seleccione el campo que desea utilizar como clave de reconciliación cuando se almacenen los datos.

En el ejemplo que se muestra a continuación, cuando se guarda (confirmación), si un perfil se guarda en la base de datos con el mismo número de cuenta que la entrada del formulario, el perfil se actualiza. Si el perfil no existe, se crea.

![](assets/s_ncs_admin_survey_save_edit.png)

Haga clic en **[!UICONTROL OK]** para confirmar y luego haga clic en **[!UICONTROL Guardar]** para guardar la encuesta

## Paso 6: Publicación de las páginas {#step-6---publishing-the-pages}

Para que los usuarios puedan acceder a las páginas HTML, la aplicación debe estar disponible. No debe estar en fase de edición, sino de producción. Para que una encuesta pase a producción, debe publicarla. Para ello:

* Haga clic en el botón **[!UICONTROL Publicar]** situado encima del panel de encuesta.
* Haga clic en **[!UICONTROL Comenzar]** para iniciar la publicación y cerrar el asistente.

   ![](assets/s_ncs_admin_survey_start_publ.png)

   El estado de la encuesta cambia a **En linea**.

   ![](assets/survey_published.png)

## Paso 7: uso compartido de la encuesta en línea {#step-7---sharing-your-online-survey}

Cuando esté en producción, se puede acceder a la encuesta en el servidor y se puede enviar. La dirección URL para acceder a la encuesta se muestra en el panel.

![](assets/survey_url_from_dashboard.png)

Para enviar la encuesta, puede enviar un mensaje a la población objetivo que contenga un vínculo de acceso o colocar la URL de acceso a la encuesta en una página web, por ejemplo.

Puede monitorizar las respuestas del usuario a través de informes y “logs”. Consulte [Seguimiento de respuestas](../../web/using/publish--track-and-use-collected-data.md#response-tracking).

>[!CAUTION]
>
>La dirección URL pública incluye el nombre interno de la encuesta. Cuando se modifica el nombre interno, la dirección URL se actualiza automáticamente: todos los vínculos a la encuesta deben actualizarse.
>
>Si las entregas que contenían el vínculo al formulario ya se han enviado, este vínculo deja de funcionar.

