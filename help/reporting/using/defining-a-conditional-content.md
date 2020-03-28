---
title: Definición de contenido condicional
seo-title: Definición de contenido condicional
description: Definición de contenido condicional
seo-description: null
page-status-flag: never-activated
uuid: 2b49958d-6429-445d-a7dc-caaca072f4e4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 0ca5e0f6-cc81-4da9-aecf-a095cc1a19f9
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Definición de contenido condicional{#defining-a-conditional-content}

Se puede condicionar la visualización de elementos o páginas específicas del informe.

Para que los elementos específicos sean condicionales, adapte su configuración de visibilidad. Para obtener más información, consulte [Condicionamiento de la visualización de elementos](#conditioning-item-display).

Para que la visualización de una o más páginas sea condicional, utilice una actividad de tipo **[!UICONTROL Test]**. Para obtener más información, consulte [Determinación de la visualización de la página](#conditioning-page-display).

## Condicionamiento de la visualización de elementos {#conditioning-item-display}

Para que la visualización de parte de un informe sea condicional, debe definir sus condiciones de visibilidad: si no se cumplen, los elementos no se muestran.

Las condiciones de visibilidad pueden depender del estado del operador o de los elementos seleccionados o introducidos en la página del informe.

En [esta sección](../../web/using/form-rendering.md#defining-fields-conditional-display) se ofrecen ejemplos de visualización condicional de elementos en una página.

En el ejemplo siguiente, la condición de visualización depende del idioma:

![](assets/reporting_display_condition.png)

## Condiciones de visualización de la página {#conditioning-page-display}

En el gráfico de un informe, la actividad **[!UICONTROL Test]** permite cambiar la secuencia de las páginas en función de una o varias condiciones.

Esta actividad se basa en el siguiente principio operativo:

1. Coloque una actividad **[!UICONTROL Test]** en un gráfico y edítela.
1. Haga clic en el botón **[!UICONTROL Add]** para crear los distintos casos posibles.

   ![](assets/reporting_test_sample.png)

   Para cada caso, se añade una transición de salida a la actividad **[!UICONTROL Test]**.

   ![](assets/reporting_test_transitions.png)

1. Seleccione **[!UICONTROL Enable default transition]** para añadir una transición en caso de que no se cumpla una de las condiciones configuradas.

   Para obtener más información, consulte [esta sección](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display).

Se puede colocar una actividad **[!UICONTROL Test]** al principio del gráfico para condicionar la visualización en función del perfil del contexto o del operador, por ejemplo.
