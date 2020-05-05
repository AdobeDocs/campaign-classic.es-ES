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
translation-type: ht
source-git-commit: b2222b2997105801164f930428c7b05ae7d11336

---


# Propiedades del informe{#properties-of-the-report}

## Información general {#overview}

Puede personalizar y configurar el informe según sus necesidades. Para ello, edite sus propiedades. Se accede a las propiedades del informe a través del botón Propiedad situado sobre el gráfico de secuencia de actividades.

![](assets/s_ncs_advuser_report_properties_01.png)

## Propiedades generales {#overall-properties}

La pestaña **[!UICONTROL General]** permite ver o modificar la etiqueta y el esquema a los que hace referencia el informe. Estos elementos se introducen durante la creación del informe.

No se recomienda cambiar **[!UICONTROL Internal name]**: este nombre se utiliza en la URL de acceso al informe.

La plantilla de informe se selecciona durante la creación del informe y no se puede modificar más adelante.

Para cambiar la tabla a la que hace referencia el informe, haga clic en el icono **[!UICONTROL Select link]** a la derecha del campo **[!UICONTROL Document type]**. Para ver los campos disponibles en la tabla seleccionada, haga clic en el icono **[!UICONTROL Magnifier]**.

![](assets/s_ncs_advuser_report_properties_02.png)

## Accesibilidad de los informes {#report-accessibility}

Se puede acceder a un informe no solo a través de la consola de Adobe Campaign, sino también, por ejemplo, a través de un explorador web. En este caso, puede ser necesario configurar el control de acceso del informe como se muestra a continuación.

![](assets/s_ncs_advuser_report_properties_02b.png)

El principio general es el siguiente:

* La opción **[!UICONTROL Anonymous access]** habilita el acceso al informe sin restricciones. Sin embargo, no es posible realizar ninguna manipulación.

   Los derechos del operador de informe predeterminado (“webapp”) se utilizan para mostrar los elementos del informe.

* La opción **[!UICONTROL Access control]** permite a los operadores de Adobe Campaign acceder a él una vez que han iniciado sesión.
* La opción **[!UICONTROL Specific account]** permite ejecutar el informe con los derechos del operador seleccionado en el campo **[!UICONTROL Operator]**.

Las propiedades de formulario web se detallan en [esta página](../../web/using/about-web-forms.md).

## Administración de la localización de informes {#managing-report-localization}

Puede configurar los idiomas a los que desea traducir el informe. Para ello, haga clic en la pestaña **[!UICONTROL Localization]**.

![](assets/s_ncs_advuser_report_properties_06.png)

El idioma de edición es el idioma en el que se escribe. Cuando se añade un idioma, la subpestaña aparece en la página de edición del informe.

![](assets/s_ncs_advuser_report_properties_05a.png)

>[!NOTE]
>
>Para obtener más información, consulte la sección correspondiente dentro de [esta sección](../../web/using/translating-a-web-form.md).

## Personalización de la renderización HTML {#personalizing-html-rendering}

En la pestaña **[!UICONTROL Rendering]**, se puede personalizar el modo de visualización de datos de la página. Puede seleccionar:

* Motor de renderización de gráficos: Adobe Campaign ofrece dos modos diferentes para generar la renderización de gráficos. De forma predeterminada, el motor de renderización es HTML 5. Si es necesario, puede seleccionar la renderización Flash.
* El tipo de navegación en el informe es mediante botones o vínculos.
* La posición predeterminada de las etiquetas para los elementos del informe. Esta posición se puede sobrecargar para cada elemento.
* La plantilla o tema utilizado para generar páginas del informe.

Las propiedades de formulario web se detallan en [esta página](../../web/using/about-web-forms.md).

![](assets/s_ncs_advuser_report_properties_08.png)

## Definición de configuración adicional {#defining-additional-settings}

La pestaña **[!UICONTROL Parameters]** permite crear configuraciones adicionales para el informe: esta configuración se pasa a la dirección URL durante la llamada.

Las propiedades de formulario web se detallan en [esta página](../../web/using/about-web-forms.md).

>[!CAUTION]
>
>Por motivos de seguridad, estos parámetros deben utilizarse con mucha precaución

Para crear una nueva configuración:

1. Haga clic en el botón **[!UICONTROL Add]** e introduzca el nombre de la configuración.

   ![](assets/s_ncs_advuser_report_properties_09a.png)

1. Si es necesario, especifique si la configuración es obligatoria o no.
1. Seleccione el tipo de configuración que desea crear: **[!UICONTROL Filter]** o **[!UICONTROL Variable]**.

   La opción **[!UICONTROL Filter entities]** permite utilizar un campo de la base de datos como parámetro.

   ![](assets/s_ncs_advuser_report_properties_09b.png)

   Los datos se recuperan directamente a nivel de entidad: **ctx/recipient/@account**.

   La opción **[!UICONTROL Variable]** permite crear o seleccionar una variable que se transfiere como parámetro de la dirección URL y se puede utilizar en los filtros.

**[!UICONTROL Response HTTP headers]** permite evitar el secuestro de clics al incluir la página del informe en una página HTML mediante iframe. Para evitar el secuestro de clics, puede elegir el comportamiento **[!UICONTROL X-Frame-options header]**:

* **[!UICONTROL None]**: El informe no tiene **[!UICONTROL X-Frame-options header]**.
* **[!UICONTROL Same as origin]**: Se configura de forma predeterminada para los informes nuevos y republicados. El nombre de host es el mismo que la dirección URL del informe.
* **[!UICONTROL Deny]**: El informe no se puede incluir en una página HTML mediante iframe.

![](assets/s_ncs_advuser_report_properties_09c.png)

## Adición de variables {#adding-variables}

La pestaña **[!UICONTROL Variables]** contiene la lista de variables configuradas en el informe. Estas variables se exponen en el contexto del informe y se pueden utilizar en cálculos.

Haga clic en el botón **[!UICONTROL Add]** para crear una variable nueva.

Para ver la definición de una variable, selecciónela y haga clic en el botón **[!UICONTROL Detail...]**.

![](assets/s_ncs_advuser_report_properties_10.png)

## Referencia a secuencias de comandos {#referencing-scripts}

La pestaña **[!UICONTROL Scripts]** permite hacer referencia a los códigos JavaScript que se ejecutan del lado del cliente o del servidor cuando solicita la página del informe.

Para la ejecución normal por parte del cliente, las secuencias de comandos a las que se hace referencia deben escribirse en JavaScript y ser compatibles con la mayoría de los navegadores. Para obtener más información, consulte [esta sección](../../web/using/web-forms-answers.md).

## Personalización de la página de error {#personalizing-the-error-page}

La pestaña **[!UICONTROL Error page]** permite configurar el mensaje que aparece en caso de error en la visualización del informe.

Puede definir textos y vincularlos a identificadores específicos para administrar la localización del informe. Para obtener más información, consulte [Adición de un encabezado y un pie de página](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

![](assets/s_ncs_advuser_report_properties_11.png)

