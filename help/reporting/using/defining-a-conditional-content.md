---
solution: Campaign Classic
product: campaign
title: Definición de contenido condicional
description: Definición de contenido condicional
audience: reporting
content-type: reference
topic-tags: creating-new-reports
exl-id: efee50f7-d917-4c71-add2-116c4b8f7013
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '245'
ht-degree: 100%

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
