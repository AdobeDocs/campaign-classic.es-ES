---
title: Configuración del acceso al informe
seo-title: Configuración del acceso al informe
description: Configuración del acceso al informe
seo-description: null
page-status-flag: never-activated
uuid: d32d9805-f84f-457f-b37b-a8278642336a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: dd50ca25-8fa2-48fa-84cc-a63e476701a0
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 74%

---


# Configuración del acceso al informe{#configuring-access-to-the-report}

## Contexto de visualización del informe {#report-display-context}

Define the display context of the report in the Adobe Campaign platform using the **[!UICONTROL Display]** tab. El acceso a un informe depende de su tipo de selección, de las condiciones de visualización y de las autorizaciones de acceso.

### Tipo de selección {#selection-type}

El acceso al informe se puede limitar a un contexto específico o a un espacio de oferta, por ejemplo una entrega, un destinatario, una selección de destinatarios, etc. This access is configured in the **[!UICONTROL Selection type]** section of the **[!UICONTROL Display]** tab.

![](assets/s_ncs_advuser_report_visibility_4.png)

* **[!UICONTROL Single selection]** :: el informe solo es accesible cuando se selecciona una entidad específica.
* **[!UICONTROL Multiple selection]** :: se accede al informe cuando se seleccionan varias entidades.
* **[!UICONTROL Global]**: se accede al informe a través de la lista de informes disponibles en el entorno de informes.

### Secuencia de visualización {#display-sequence}

The **[!UICONTROL Sequence]** field lets you enter a numeric value that specifies the display sequence of the report in the list.

De manera predeterminada, los informes se muestran por relevancia: el valor introducido en este campo permite ordenar los informes desde el más relevante (valor más alto) al menos relevante (valor más bajo).

Puede seleccionar la escala que desee utilizar en función de sus necesidades: 1 a 10, 0 a 100, -10 a 10, etc.

### Condiciones de visualización {#display-conditions}

También puede condicionar la visualización del informe mediante una consulta.

![](assets/s_ncs_advuser_report_visibility_5.png)

En el siguiente ejemplo, el informe se muestra si el canal de campaña principal es correo electrónico.

![](assets/s_ncs_advuser_report_visibility_6.png)

Esto significa que si el canal principal de la campaña es correo postal, el informe no aparece disponible en los informes de campaña.

### Autorización de acceso {#access-authorization}

El informe se puede compartir con otros operadores.

Para que el informe sea accesible, seleccione la **[!UICONTROL Report shared with other operators]** opción. Si no se selecciona esta opción, solo el operador que creó el informe puede acceder a él.

El informe también se puede compartir con operadores o grupos de operadores específicos añadidos a través de la ventana de autorizaciones.

![](assets/s_ncs_advuser_report_visibility_8.png)

### Definición de las opciones de filtrado {#defining-the-filtering-options}

The **[!UICONTROL Reports]** universe displays all available reports in the platform and for which the connected operator has an access right.

De forma predeterminada se clasifican por relevancia, pero puede aplicar otros tipos de filtros: alfabético, por edad, etc.

También puede filtrar la visualización en función de la categoría del informe:

![](assets/report_ovv_select_type.png)

To define the category of a report, select it via the **[!UICONTROL Display]** tab, as shown below:

![](assets/report_select_category.png)

Puede introducir una nueva categoría aquí y añadirla a la lista de categorías disponibles. La enumeración correspondiente se actualiza automáticamente.

## Creación de un vínculo a un informe {#creating-a-link-to-a-report-}

Se puede hacer que un informe sea accesible a través de un nodo específico del árbol, como una lista, un destinatario, una entrega, etc. Para hacerlo, simplemente genere un vínculo al informe correspondiente y especifique la entidad donde desea que esté disponible.

Por ejemplo, generemos un vínculo a un informe para que sea accesible a través de una lista de destinatarios.

1. Haga clic **[!UICONTROL New]** y seleccione **[!UICONTROL Create a link to an existing report]** en el asistente para la creación de informes.

   ![](assets/s_ncs_advuser_report_wizard_link_01.png)

1. Seleccione en la lista desplegable el informe al que desee crear un vínculo. En este ejemplo, seleccione el informe **Desglose por país**.

   ![](assets/s_ncs_advuser_report_wizard_link_02.png)

1. Introduzca una etiqueta y seleccione el esquema. En este ejemplo, seleccione la tabla de listas de destinatarios.

   ![](assets/s_ncs_advuser_report_wizard_link_03.png)

   Esto significa que se puede acceder al informe a través de cualquier lista de destinatarios y que las estadísticas hacen referencia a los destinatarios en la lista seleccionada.

1. Guardar y mostrar el informe.
1. Introduzca la clave del vínculo. En este caso, la clave externa del vínculo “Carpetas”.

   ![](assets/s_ncs_advuser_report_wizard_link_04.png)

1. Publique el informe.
1. Go to one of your recipient lists and click the **[!UICONTROL Reports]** link: the report you have just created is accessible.

   ![](assets/s_ncs_advuser_report_wizard_link_05.png)

## Previsualización del informe {#preview-of-the-report}

Before publishing your report, make sure it is displayed correctly in the **[!UICONTROL Preview]** tab.

![](assets/s_ncs_advuser_report_preview_01.png)

To display the preview of the report, select the **[!UICONTROL Global]** or the **[!UICONTROL Selection]** option.

Estas dos opciones se seleccionan según la configuración de visualización del informe. Si la configuración de visualización es **[!UICONTROL Global]**, se debe seleccionar la opción de previsualización **[!UICONTROL Global]**. Si la configuración de visualización es **[!UICONTROL Single selection]** o **[!UICONTROL Multiple selection]**, se debe seleccionar la opción de **[!UICONTROL Selection]** previsualización.

Para más información, consulte [Informe de contexto de visualización](#report-display-context).

La configuración específica permite controlar los errores. El parámetro **_uuid** se encuentra en la dirección URL del informe. Se le puede añadir la configuración **&amp;_preview** o **&amp;_debug**.

Para obtener más información sobre esta configuración, consulte la sección de **definición de propiedades de formulario web** del capítulo de [formularios web](../../web/using/about-web-forms.md).

## Publicación del informe {#publishing-the-report}

La publicación del informe es obligatoria para poder compartirlo con otros operadores y mostrarlo en la lista de informes disponibles (también consulte [Informe de contexto de visualización](#report-display-context)). Esta operación debe llevarse a cabo cada vez que se modifica el informe.

1. Open the publishing wizard by clicking **[!UICONTROL Publish]** in the toolbar.

   ![](assets/s_ncs_advuser_report_publish_01.png)

1. Haga clic en **[!UICONTROL Start]** para publicar.

   ![](assets/s_ncs_advuser_report_publish_02.png)

1. Click the **[!UICONTROL Enlarge]** icon to open the report in a web browser.

