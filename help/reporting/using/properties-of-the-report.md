---
title: Propiedades del informe
seo-title: Propiedades del informe
description: Propiedades del informe
seo-description: null
page-status-flag: never-activated
uuid: 56163f53-d115-45b8-94a5-c173ac4c6533
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 5ec88743-be51-438c-9064-dd0196fdd7d3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: af768da6ee8cc0ca2ea1f24f297239b974c113a5

---


# Propiedades del informe{#properties-of-the-report}

## Información general {#overview}

Puede personalizar y configurar el informe según sus necesidades. Para ello, edite sus propiedades. Se accede a las propiedades del informe a través del botón Propiedad situado sobre el gráfico de secuencia de actividades.

![](assets/s_ncs_advuser_report_properties_01.png)

## Propiedades generales {#overall-properties}

The **[!UICONTROL General]** tab lets you view or alter the label and the schema which the report concerns. Estos elementos se introducen durante la creación del informe.

We do not recommend changing the **[!UICONTROL Internal name]** : this is used in the report access URL.

La plantilla de informe se selecciona durante la creación del informe y no se puede modificar más adelante.

To change the table which the report concerns, click the **[!UICONTROL Select link]** icon to the right of the **[!UICONTROL Document type]** field. To view the available fields in the selected table, click the **[!UICONTROL Magnifier]** icon.

![](assets/s_ncs_advuser_report_properties_02.png)

## Accesibilidad de los informes {#report-accessibility}

Se puede acceder a un informe no solo a través de la consola de Adobe Campaign, sino también, por ejemplo, a través de un explorador web. En este caso, puede ser necesario configurar el control de acceso del informe como se muestra a continuación.

![](assets/s_ncs_advuser_report_properties_02b.png)

El principio general es el siguiente:

* The **[!UICONTROL Anonymous access]** option enables unrestricted access to the report. Sin embargo, no es posible realizar ninguna manipulación.

   Los derechos del operador de informe predeterminado (“webapp”) se utilizan para mostrar los elementos del informe.

* The **[!UICONTROL Access control]** option enables Adobe Campaign operators to access it once they are logged on.
* The **[!UICONTROL Specific account]** option lets you execute the report with the rights of the operator selected in the **[!UICONTROL Operator]** field.

Las propiedades de formulario web se detallan en [esta página](../../web/using/about-web-forms.md).

## Administración de la localización de informes {#managing-report-localization}

Puede configurar los idiomas a los que desea traducir el informe. To do this, click the **[!UICONTROL Localization]** tab.

![](assets/s_ncs_advuser_report_properties_06.png)

El idioma de edición es el idioma en el que se escribe. Cuando se añade un idioma, la subpestaña aparece en la página de edición del informe.

![](assets/s_ncs_advuser_report_properties_05a.png)

>[!NOTE]
>
>Para obtener más información, consulte la sección correspondiente dentro de [esta sección](../../web/using/translating-a-web-form.md).

## Personalización de la renderización HTML {#personalizing-html-rendering}

In the **[!UICONTROL Rendering]** tab, you can personalize the data display mode for the page. Puede seleccionar:

* Motor de procesamiento de gráficos: Adobe Campaign ofrece dos modos diferentes para generar el procesamiento de gráficos. De forma predeterminada, el motor de renderización es HTML 5. Si es necesario, puede seleccionar la renderización Flash.
* El tipo de navegación en el informe es mediante botones o vínculos.
* La posición predeterminada de las etiquetas para los elementos del informe. Esta posición se puede sobrecargar para cada elemento.
* La plantilla o tema utilizado para generar páginas del informe.

Las propiedades de formulario web se detallan en [esta página](../../web/using/about-web-forms.md).

![](assets/s_ncs_advuser_report_properties_08.png)

## Definición de configuración adicional {#defining-additional-settings}

The **[!UICONTROL Settings]** tab lets you create additional settings for the report: these settings will be passed into the URL during the call up.

Las propiedades de formulario web se detallan en [esta página](../../web/using/about-web-forms.md).

>[!CAUTION]
>
>Por motivos de seguridad, estos parámetros deben utilizarse con mucha precaución

Para crear una nueva configuración:

1. Click the **[!UICONTROL Add]** button and enter the name of the setting.

   ![](assets/s_ncs_advuser_report_properties_09a.png)

1. Si es necesario, especifique si la configuración es obligatoria o no.
1. Select the type of setting you want to create: **[!UICONTROL Filter]** or **[!UICONTROL Variable]**.

   The **[!UICONTROL Filter entities]** option lets you use a field of the database as a parameter.

   ![](assets/s_ncs_advuser_report_properties_09b.png)

   Los datos se recuperan directamente a nivel de entidad: **ctx/Recipiente/@account**.

   The **[!UICONTROL Variable]** option lets you create or select a variable which will be passed as a parameter of the URL and can be used in the filters.

## Adición de variables {#adding-variables}

The **[!UICONTROL Variables]** tab contains the list of variables configured in the report. Estas variables se exponen en el contexto del informe y se pueden utilizar en cálculos.

Click the **[!UICONTROL Add]** button to create a new variable.

To view the definition of a variable, select it and click the **[!UICONTROL Detail...]** button.

![](assets/s_ncs_advuser_report_properties_10.png)

## Referencia a secuencias de comandos {#referencing-scripts}

The **[!UICONTROL Scripts]** tab lets you reference JavaScript codes that will be executed on the client and/or server side when the report page is called up.

Para la ejecución normal por parte del cliente, las secuencias de comandos a las que se hace referencia deben escribirse en JavaScript y ser compatibles con la mayoría de los navegadores. Para obtener más información, consulte [esta sección](../../web/using/web-forms-answers.md).

## Personalización de la página de error {#personalizing-the-error-page}

The **[!UICONTROL Error page]** tab lets you configure the message that will come up in case of an error in the report display.

Puede definir textos y vincularlos a identificadores específicos para administrar la localización del informe. Para obtener más información sobre esto, consulte [Adición de un encabezado y un pie de página](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

![](assets/s_ncs_advuser_report_properties_11.png)

