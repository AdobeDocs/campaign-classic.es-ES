---
title: Interacciones anónimas
seo-title: Interacciones anónimas
description: Interacciones anónimas
seo-description: null
page-status-flag: never-activated
uuid: 6e28e8a4-8d2f-4747-8dd0-680fbf02b25d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: unitary-interactions
discoiquuid: 3fd7a1ef-b0e2-4a7e-9e36-044d997db785
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 75%

---


# Interacciones anónimas{#anonymous-interactions}

Vea este [vídeo](https://helpx.adobe.com/campaign/classic/how-to/indetified-and-anonymous-interaction-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/digital-marketers/explevel/intermediate/applaunch/get-started/collection.ccx.js&amp;ref=helpx.adobe.com) para obtener información general sobre cómo se entregan las ofertas a objetivos identificados y anónimos.

## Objetivo y almacenamiento de un entorno para interacciones anónimas {#targeting-and-storing-an-environment-for-anonymous-interactions}

De forma predeterminada, la interacción viene con un entorno preconfigurado para dirigirse la tabla de destinatarios (ofertas identificadas). Si desea dirigirse a otra tabla (tabla de visitante para ofertas anónimas o a una tabla de destinatarios específica), debe utilizar el asistente de asignación de destino para crear el entorno. Para obtener más información sobre esto, consulte [Creación de un entorno de ofertas](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

When you create an anonymous environment via the mapping creation wizard, the **[!UICONTROL Environment dedicated to incoming anonymous interactions]** box is automatically checked in the environment&#39;s **[!UICONTROL General]** tab.

El **[!UICONTROL Targeting dimension]** se completa automáticamente. De manera predeterminada, se vincula a la tabla del visitante.

Aparece el **[!UICONTROL Visitor folder]** campo. It is automatically completed to link to the **[!UICONTROL Visitors]** folder. Este campo permite elegir dónde almacenar los perfiles de visitantes.

![](assets/anonymous_environment_option.png)

>[!NOTE]
>
>If you want to filter several types of visitors, for instance in the case of anonymous offers presented for one or more brands, you need to create an environment for each brand, and a **[!UICONTROL Visitors]** type folder for each environment.

## Catálogo de ofertas para interacciones anónimas {#offer-catalog-for-anonymous-interactions}

Al igual que las interacciones de salida, las interacciones entrantes se organizan en un catálogo de ofertas que consta de categorías y ofertas.

Para crear categorías y espacios, aplique el mismo proceso que para los visitantes identificados (consulte [Creación de categorías de ofertas](../../interaction/using/creating-offer-categories.md) y [Creación de un entorno de ofertas](../../interaction/using/live-design-environments.md#creating-an-offer-environment)).

## Visitantes anónimos {#anonymous-visitors}

Los visitantes anónimos pueden enviarse a un proceso de identificación de cookie cuando se conectan. Este reconocimiento implícito se basa en el historial del explorador del visitante.

Durante este paso, se realiza una comparación entre los datos que recuperan las cookies y los de la base de datos. En algunos casos, el visitante se reconoce (se identifica de forma implícita); en otros casos, no se reconoce (y, por lo tanto, permanece anónimo).

Para ejecutar esta análisis, para el espacio de ofertas, marque la **[!UICONTROL Implicitly identify the individual based on their browser history]** opción.

![](assets/identification_anonymous_visitors.png)

## Procesamiento de visitantes anónimos sin identificar {#processing-unidentified-anonymous-visitors}

Tras el análisis, si un visitante anónimo no se identifica, se puede almacenar sus datos en un espacio determinado. Esto permite sugerir ofertas especialmente destinadas a este tipo de visitante, que coincide con las reglas especificadas de tipología.

Si no hay ningún elemento que permita identificar un contacto o si no se desea sugerir una oferta identificada a un contacto que pueda identificarse implícitamente, se puede optar por realizar una reserva en un entorno anónimo.

Para ello, marque la casilla de verificación **[!UICONTROL Fall back on an anonymous environment if no individuals were identified]** y, a continuación, especifique el entorno dedicado a estos visitantes no identificados en el **[!UICONTROL Linked anonymous space]** al especificar un espacio de ofertas.

![](assets/anonymous_to_anonymous_environment.png)

