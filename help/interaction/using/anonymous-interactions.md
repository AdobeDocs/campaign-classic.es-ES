---
solution: Campaign Classic
product: campaign
title: Interacciones anónimas
description: Interacciones anónimas
audience: interaction
content-type: reference
topic-tags: unitary-interactions
translation-type: tm+mt
source-git-commit: 20dcdd91d71158bc373db68c3f61f6808b240bd2
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 100%

---


# Interacciones anónimas{#anonymous-interactions}

![](assets/do-not-localize/how-to-video.png) Vea este [vídeo](https://helpx.adobe.com/campaign/classic/how-to/indetified-and-anonymous-interaction-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/digital-marketers/explevel/intermediate/applaunch/get-started/collection.ccx.js&amp;ref=helpx.adobe.com) para obtener información general sobre cómo se entregan las ofertas a objetivos identificados y anónimos.

## Objetivo y almacenamiento de un entorno para interacciones anónimas {#targeting-and-storing-an-environment-for-anonymous-interactions}

De forma predeterminada, la interacción viene con un entorno preconfigurado para dirigirse la tabla de destinatarios (ofertas identificadas). Si desea dirigirse a otra tabla (tabla de visitante para ofertas anónimas o a una tabla de destinatarios específica), debe utilizar el asistente de asignación de destino para crear el entorno. Para obtener más información sobre esto, consulte [Creación de un entorno de ofertas](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

Cuando se crea un entorno anónimo a través del asistente para la creación de asignaciones, la casilla **[!UICONTROL Environment dedicated to incoming anonymous interactions]** se marca automáticamente en la pestaña **[!UICONTROL General]** del entorno.

El **[!UICONTROL Targeting dimension]** se completa automáticamente. De manera predeterminada, se vincula a la tabla del visitante.

Aparece el campo **[!UICONTROL Visitor folder]**. Se completa automáticamente para vincular la carpeta **[!UICONTROL Visitors]**. Este campo permite elegir dónde almacenar los perfiles de visitantes.

![](assets/anonymous_environment_option.png)

>[!NOTE]
>
>Si se desea filtrar varios tipos de visitantes, por ejemplo, en el caso de ofertas anónimas presentadas para una o más marcas, se debe crear un entorno para cada marca y una carpeta de tipo **[!UICONTROL Visitors]** cada entorno.

## Catálogo de ofertas para interacciones anónimas {#offer-catalog-for-anonymous-interactions}

Al igual que las interacciones de salida, las interacciones entrantes se organizan en un catálogo de ofertas que consta de categorías y ofertas.

Para crear categorías y espacios, aplique el mismo proceso que para los visitantes identificados (consulte [Creación de categorías de ofertas](../../interaction/using/creating-offer-categories.md) y [Creación de un entorno de ofertas](../../interaction/using/live-design-environments.md#creating-an-offer-environment)).

## Visitantes anónimos {#anonymous-visitors}

Los visitantes anónimos pueden enviarse a un proceso de identificación de cookie cuando se conectan. Este reconocimiento implícito se basa en el historial del explorador del visitante.

Durante este paso, se realiza una comparación entre los datos que recuperan las cookies y los de la base de datos. En algunos casos, el visitante se reconoce (se identifica de forma implícita); en otros casos, no se reconoce (y, por lo tanto, permanece anónimo).

Para ejecutar este análisis, para el espacio de ofertas, marque la opción **[!UICONTROL Implicitly identify the individual based on their browser history]**.

![](assets/identification_anonymous_visitors.png)

## Procesamiento de visitantes anónimos sin identificar {#processing-unidentified-anonymous-visitors}

Tras el análisis, si un visitante anónimo no se identifica, se puede almacenar sus datos en un espacio determinado. Esto permite sugerir ofertas especialmente destinadas a este tipo de visitante, que coincide con las reglas especificadas de tipología.

Si no hay ningún elemento que permita identificar un contacto o si no se desea sugerir una oferta identificada a un contacto que pueda identificarse implícitamente, se puede optar por realizar una reserva en un entorno anónimo.

Para ello, marque la casilla de verificación **[!UICONTROL Fall back on an anonymous environment if no individuals were identified]** y, a continuación, especifique el entorno dedicado a estos visitantes no identificados en el **[!UICONTROL Linked anonymous space]** al especificar un espacio de ofertas.

![](assets/anonymous_to_anonymous_environment.png)

