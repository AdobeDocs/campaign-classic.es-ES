---
title: Diseño de elementos
seo-title: Diseño de elementos
description: Diseño de elementos
seo-description: null
page-status-flag: never-activated
uuid: 60dc80d9-f81b-48ce-9341-f975daaf5ebc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 8fdda764-3e42-4972-a9c9-63567588931e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Diseño de elementos{#element-layout}

Además de los diversos gráficos detallados aquí: Tipos [de gráficos y variantes](../../reporting/using/creating-a-chart.md#chart-types-and-variants), puede adaptar la visualización y agregar elementos a las páginas de informes.

Puede utilizar contenedores: estos permiten vincular varios elementos de una página y configurar su diseño en columnas o celdas. En [esta sección](../../web/using/defining-web-forms-layout.md#creating-containers) se describe cómo utilizarlos.

Puede configurar el diseño del informe en la raíz del árbol y recargarlo para cada contenedor. Las páginas se ordenan en columnas. Los contenedores también se ordenan en columnas. Solo los elementos estáticos y gráficos se ordenan en celdas.

## Definición de las opciones de cada página {#defining-the-options-for-each-page}

Puede utilizar las opciones en cada página del informe.

The **[!UICONTROL General]** tab lets you change the title of the page, as well as configure legend positions and browsing between the report pages.

![](assets/s_ncs_advuser_report_wizard_022.png)

The **[!UICONTROL Title]** field lets you personalize the label in the header of the report page. The title of the window can be configured via the **[!UICONTROL Properties]** window of the report. Para obtener más información sobre esto, consulte [Adición de un encabezado y un pie de página](#adding-a-header-and-a-footer).

The **[!UICONTROL Display settings]** options enable you to select the position of the control caption within a report page and to define the number of columns on the page. Para obtener más información acerca del diseño de la página, consulte la sección **Diseño de elementos** de [esta sección](../../web/using/defining-web-forms-layout.md#positioning-the-fields-on-the-page).

Select the various options in the **[!UICONTROL Browse]** section to authorize browsing from one report page to another. Si se selecciona la **[!UICONTROL Disable next page]** opción o la **[!UICONTROL Disable previous page]** , los botones **[!UICONTROL Next]** y **[!UICONTROL Previous]** desaparecen de la página del informe.

## Adición de un encabezado y un pie de página {#adding-a-header-and-a-footer}

La ventana de propiedades del informe también permite definir los elementos de diseño, como el título de la ventana o el contenido HTML de los encabezados y pies de página.

To access the properties window, click the **[!UICONTROL Properties]** button of the report.

![](assets/reporting_properties.png)

The **[!UICONTROL Page]** tab enables you to personalize your display.

![](assets/s_ncs_advuser_report_properties_04.png)

El contenido configurado en esta pestaña es visible en todas las páginas del informe.

The **[!UICONTROL Texts]** sub-tab enables you to define variable content: it will be taken into account during the translation cycle if the report is designed for use in several languages.

Esto permite crear una lista de fragmentos de texto y vincularlos a identificadores:

![](assets/s_ncs_advuser_report_properties_04a.png)

A continuación, inserte estos identificadores en el contenido HTML del informe:

![](assets/s_ncs_advuser_report_properties_04b.png)

Se sustituyen automáticamente por el contenido apropiado cuando se muestra el informe.

Al igual que para los textos HTML, este modo operativo permite centralizar los textos utilizados en el informe y administrar su traducción. La herramienta de traducción integrada de Adobe Campaign recopila automáticamente los textos creados en esta pestaña.
