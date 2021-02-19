---
solution: Campaign Classic
product: campaign
title: Diseño de elementos
description: Diseño de elementos
audience: reporting
content-type: reference
topic-tags: creating-new-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 100%

---


# Diseño de elementos{#element-layout}

Además de los diversos gráficos detallados aquí: [Tipos de gráficos y variantes](../../reporting/using/creating-a-chart.md#chart-types-and-variants), puede adaptar la visualización y agregar elementos a las páginas de informes.

Puede utilizar contenedores: estos permiten vincular varios elementos de una página y configurar su diseño en columnas o celdas. En [esta sección](../../web/using/defining-web-forms-layout.md#creating-containers) se describe cómo utilizarlos.

Puede configurar el diseño del informe en la raíz del árbol y recargarlo para cada contenedor. Las páginas se ordenan en columnas. Los contenedores también se ordenan en columnas. Solo los elementos estáticos y gráficos se ordenan en celdas.

## Definición de las opciones de cada página {#defining-the-options-for-each-page}

Puede utilizar las opciones en cada página del informe.

La pestaña **[!UICONTROL General]** permite cambiar el título de la página, además de configurar las posiciones de los pies de ilustración y navegar entre las páginas del informe.

![](assets/s_ncs_advuser_report_wizard_022.png)

El campo **[!UICONTROL Title]** permite personalizar la etiqueta en el encabezado de la página del informe. El título de la ventana se puede configurar mediante la ventana **[!UICONTROL Properties]** del informe. Para obtener más información, consulte [Adición de un encabezado y un pie de página](#adding-a-header-and-a-footer).

Las opciones de **[!UICONTROL Display settings]** permiten seleccionar la posición del pie de ilustración del control dentro de una página del informe y definir el número de columnas de la página. Para obtener más información acerca del diseño de la página, consulte la sección **Diseño de elementos** de [esta sección](../../web/using/defining-web-forms-layout.md#positioning-the-fields-on-the-page).

Seleccione las distintas opciones de la sección **[!UICONTROL Browse]** para autorizar la navegación desde una página de informes a otra. Si la opción **[!UICONTROL Disable next page]** o **[!UICONTROL Disable previous page]** está seleccionada, los botones **[!UICONTROL Next]** y **[!UICONTROL Previous]** desaparecen de la página del informe.

## Adición de un encabezado y un pie de página {#adding-a-header-and-a-footer}

La ventana de propiedades del informe también permite definir los elementos de diseño, como el título de la ventana o el contenido HTML de los encabezados y pies de página.

Para acceder a la ventana de propiedades, haga clic en el botón **[!UICONTROL Properties]** del informe.

![](assets/reporting_properties.png)

La pestaña **[!UICONTROL Page]** permite personalizar la visualización.

![](assets/s_ncs_advuser_report_properties_04.png)

El contenido configurado en esta pestaña es visible en todas las páginas del informe.

La subpestaña **[!UICONTROL Texts]** permite definir el contenido variable: se tiene en cuenta durante el ciclo de traducción si el informe está diseñado para utilizarse en varios idiomas.

Esto permite crear una lista de fragmentos de texto y vincularlos a identificadores:

![](assets/s_ncs_advuser_report_properties_04a.png)

A continuación, inserte estos identificadores en el contenido HTML del informe:

![](assets/s_ncs_advuser_report_properties_04b.png)

Se sustituyen automáticamente por el contenido apropiado cuando se muestra el informe.

Al igual que para los textos HTML, este modo operativo permite centralizar los textos utilizados en el informe y administrar su traducción. La herramienta de traducción integrada de Adobe Campaign recopila automáticamente los textos creados en esta pestaña.
