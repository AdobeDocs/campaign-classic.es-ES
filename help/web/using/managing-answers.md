---
title: Gestión de respuestas
seo-title: Gestión de respuestas
description: Gestión de respuestas
seo-description: null
page-status-flag: never-activated
uuid: 329e2f4a-c5bc-4654-bdef-71a0818fc2b7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: online-surveys
discoiquuid: affecd87-00a3-4d50-92d3-31ac6228948b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Gestión de respuestas{#managing-answers}

## Almacenamiento de respuestas recopiladas {#storing-collected-answers}

Además de los modos de almacenamiento estándar comunes a todos los formularios web en Adobe Campaign (campo de base de datos y variable local), las encuestas permiten la ampliación dinámica del modelo de datos utilizando campos archivados.

>[!CAUTION]
>
>Esta opción está disponible solo para las aplicaciones web de tipo **Encuesta.** No se ofrece para otros tipos de formularios Web.

### Almacenamiento en un campo archivado {#storing-in-an-archived-field}

Es fácil ampliar la plantilla de datos mediante la adición de nuevos espacios de almacenamiento para guardar las respuestas que se proporcionan en las encuestas. To do this, select the **[!UICONTROL Store answers to a question]** option when creating the input field. Click the **[!UICONTROL New field...]** link and give its properties:

![](assets/s_ncs_admin_survey_new_space.png)

Introduzca la etiqueta y el nombre del campo y seleccione el tipo de campo: Texto, Booleano, Número entero o decimal, Fecha, etc.

El tipo de campo seleccionado implica un control de los datos cuando los usuarios introducen respuestas. Para los campos de **texto** , puede agregar una restricción (mayúsculas y minúsculas, formato) o un vínculo a una enumeración existente para forzar la selección.

Para agregar una restricción, selecciónela en la lista desplegable. Hay dos tipos de restricciones:

1. De caracteres

   La información introducida se puede almacenar en el campo en los siguientes formatos: todas mayúsculas, todas minúsculas o todas con inicial mayúscula. Esta restricción no requiere que el usuario introduzca los datos del formato seleccionado, pero el contenido introducido en el campo se convierte después de guardarlo.

1. Formato de datos

If this field is used in a list, the values of the enumeration can be retrieved automatically in the table of values using the **[!UICONTROL Initialize the list of values from the database]** link above the list of values.

Por ejemplo, puede crear una lista desplegable para que el usuario seleccione su lengua materna. El campo archivado correspondiente se puede asociar a la enumeración **idioma** que contiene una lista de idiomas:

![](assets/s_ncs_admin_survey_database_values_2b.png)

The **[!UICONTROL Edit link]** icon located to the right of the field lets you edit the content of this enumeration:

![](assets/s_ncs_admin_survey_database_values_2c.png)

En la **[!UICONTROL General]** ficha del campo, el **[!UICONTROL Initialize the list of values from the database]** vínculo le permite introducir automáticamente la lista de etiquetas ofrecidas.

![](assets/s_ncs_admin_survey_database_values_2.png)

**Ejemplo**: almacene los contratos de un destinatario en un campo

To store different types of contracts in one field, create a **[!UICONTROL Text]** input field and select the **[!UICONTROL Store answers to a question]** option.

Click the **[!UICONTROL New field...]** link and enter the field properties. Select the **[!UICONTROL Multiple values]** option to enable several values to be stored.

![](assets/s_ncs_admin_survey_storage_multi_ex1.png)

Cree campos de entrada para los demás contratos y almacene los datos en el mismo campo archivado.

![](assets/s_ncs_admin_survey_storage_multi_ex2.png)

When users approve the survey, their answers will be stored in the **[!UICONTROL Contracts]** field.

En nuestro ejemplo, para las siguientes respuestas:

![](assets/s_ncs_admin_survey_storage_multi_ex3.png)

El perfil del encuestado contiene los cuatro contratos especificados.

They can be viewed in the **[!UICONTROL Answers]** tab of the survey by displaying the relevant columns.

![](assets/s_ncs_admin_survey_storage_multi_ex4.png)

También puede filtrar los destinatarios en función de las respuestas para mostrar solo los usuarios que le interesen. To do this, create a targeting workflow and use the **[!UICONTROL Survey responses]** box.

![](assets/s_ncs_admin_survey_read_responses_wf.png)

Cree la consulta en función de los perfiles que desee recuperar. En el ejemplo siguiente, la consulta permite seleccionar perfiles con al menos dos contratos, incluido un contrato de tipo A.

![](assets/s_ncs_admin_survey_read_responses_edit.png)

Para cada formulario, las respuestas proporcionadas pueden utilizarse en campos o etiquetas. Utilice la siguiente sintaxis para el contenido almacenado en un campo archivado:

```
<%= ctx.webAppLogRcpData.name of the archived field %
```

>[!NOTE]
>
>Para otros tipos de campos, la sintaxis se detalla en [esta sección](../../platform/using/about-queries-in-campaign.md).

### Ajustes de almacenamiento {#storage-settings}

Es posible archivar las respuestas a las encuestas en formato XML. This lets you save a raw copy of the answers collected, which can be useful in case of excessive standardization of the data in an itemized list (for more on this, refer to [Standardizing data](../../web/using/publish--track-and-use-collected-data.md#standardizing-data)).

>[!CAUTION]
>
>El archivado de las respuestas en sin procesar aumenta considerablemente el espacio de almacenamiento necesario. Utilice esta opción con cuidado.

Para ello:

* Edite las propiedades del estudio a través del **[!UICONTROL Properties]** botón de la **[!UICONTROL Edit]** ficha.
* Haga clic en el **[!UICONTROL Advanced parameters]** vínculo y marque la **[!UICONTROL Save a copy of raw answers]** opción.

![](assets/s_ncs_admin_survey_xml_archive_option.png)

Puede activarlo de manera predeterminada para todas las encuestas (esta opción se aplica cuando se publica la encuesta). To do this, create the **[!UICONTROL NmsWebApp_XmlBackup]** option and assign value **[!UICONTROL 1]** to it, as shown below:

![](assets/s_ncs_admin_survey_xml_global_option.png)

## Gestión de la puntuación {#score-management}

Puede asignar una puntuación a las opciones ofrecidas en las páginas del formulario. Solo pueden vincularse con preguntas cerradas: casilla de verificación, valor de una lista desplegable, suscripción, etc.

>[!CAUTION]
>
>La gestión de puntuación solo está disponible para las **Encuestas**.

![](assets/s_ncs_admin_survey_score_create.png)

The scores are accumulated and saved on the server side when the page is confirmed, i.e. when the user clicks the **[!UICONTROL Next]** or **[!UICONTROL Finish]** button.

>[!NOTE]
>
>Puede utilizar valores positivos o negativos, enteros o no enteros.

Las puntuaciones se pueden utilizar en pruebas o secuencias de comandos.

>[!CAUTION]
>
>Las puntuaciones no se pueden utilizar en las condiciones de visibilidad de los campos que se encuentran en la misma página. Sin embargo, se pueden utilizar en páginas posteriores.

* To use scores in tests, use the **[!UICONTROL Score]** field in the test calculation formula, as shown below:

   ![](assets/s_ncs_admin_survey_score_in_a_test.png)

* Puede utilizar la puntuación en una secuencia de comandos.

**Ejemplo**: calcule una puntuación y utilícela como una condición para la visualización de la página siguiente:

* En una encuesta, la siguiente página permite asignar distintas puntuaciones a los usuarios según el valor seleccionado en la lista desplegable:

   ![](assets/s_ncs_admin_survey_score_exa.png)

* Puede combinar esta puntuación con un segundo valor, en función de la opción seleccionada:

   ![](assets/s_ncs_admin_survey_score_exb.png)

* When the user clicks the **[!UICONTROL Next]** button, the two values are added up.

   ![](assets/s_ncs_admin_survey_score_exe.png)

* Se pueden aplicar condiciones para que la página se muestre según la puntuación. Se configura de la siguiente manera:

   ![](assets/s_ncs_admin_survey_score_exd.png)

   ![](assets/s_ncs_admin_survey_score_exg.png)

