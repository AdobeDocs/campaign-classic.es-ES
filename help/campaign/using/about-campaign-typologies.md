---
title: Acerca de las tipologías de campaña
seo-title: Acerca de las tipologías de campaña
description: Acerca de las tipologías de campaña
seo-description: null
page-status-flag: never-activated
uuid: ec89fb14-7e2f-4e9f-b7ab-3c2caf93a697
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: 72c5151c-ce1e-425a-9aee-beefe9f21a67
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 44d8ba19f2e79d30229239312e6a5148d247fb28

---


# Acerca de las tipologías de campaña{#about-campaign-typologies}

Campaign Optimization (optimización de la campaña) es el módulo de Adobe Campaign que permite controlar, filtrar y monitorizar las entregas. Para evitar conflictos entre campañas, Adobe Campaign puede probar distintas combinaciones mediante la aplicación de reglas de restricción específicas. Esto garantiza que los mensajes enviados respondan de la mejor forma a las necesidades y expectativas de los clientes, de acuerdo con las políticas de comunicación de la compañía.

>[!NOTE]
>
>Según la oferta, Campaign Optimization puede estar incluido o ser un complemento. Compruebe el acuerdo de licencia.

## Reglas de tipología {#typology-rules}

Con Adobe Campaign puede diseñar y aplicar cuatro tipos de reglas de tipología:

1. Reglas de **filtrado**, que permiten excluir parte del objetivo según los criterios. Para obtener más información, consulte [Reglas del filtro](../../campaign/using/filtering-rules.md).
1. Reglas de **presión**, que permiten controlar la fatiga de marketing. Para obtener más información, consulte [Reglas de presión](../../campaign/using/pressure-rules.md).
1. Reglas de **capacidad** que permiten limitar las cargas para garantizar condiciones de procesamiento óptimas. Para obtener más información, consulte [Capacidad de control](../../campaign/using/consistency-rules.md#controlling-capacity).
1. Reglas de **control** que permiten comprobar la validez de los mensajes antes de enviarlos. Para obtener más información, consulte [Reglas de control](../../campaign/using/control-rules.md).

Una vez creadas, las reglas de tipología se agrupan en las tipologías de campaña a las que se hace referencia en las entregas. Consulte [Aplicación de tipologías](#applying-typologies).

## Tipologías {#typologies}

Una tipología de campaña puede contener varias [reglas de tipología](#typology-rules), pero una entrega solo puede hacer referencia a una tipología.

La pestaña **[!UICONTROL Rules]** permite añadir, eliminar o ver las reglas de tipología que se pueden aplicar.

![](assets/campaign_opt_rules_tab.png)

## Aplicación de tipologías {#applying-typologies}

A continuación se enumeran los pasos para crear y aplicar una tipología a las entregas:

1. Creación de reglas de tipología.

   Las reglas de tipología se encuentran en el nodo **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]**.

   Las distintas reglas disponibles en Campaign se describen en las siguientes secciones: reglas [de presión de ](../../campaign/using/pressure-rules.md)ventas, reglas [de ](../../campaign/using/consistency-rules.md#controlling-capacity)capacidad, reglas [de](../../campaign/using/control-rules.md) control y reglas [de ](../../campaign/using/filtering-rules.md)filtrado.

1. Cree una tipología y haga referencia a las reglas que creó en ella.

   Se puede acceder a las tipologías a través del nodo **[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]**.

1. Configure su envío para utilizar la tipología creada. Para obtener más información, consulte [esta sección](../../campaign/using/applying-rules.md#applying-a-typology-to-a-delivery).
1. Pruebe y controle el comportamiento a través de simulaciones de campañas. Para obtener más información sobre simulaciones de campaña, consulte [esta sección](../../campaign/using/campaign-simulations.md).

Durante la preparación de la entrega, los destinatarios se excluyen cuando se cumple el criterio. Puede comprobar los registros para controlar las exclusiones. En [esta página](../../campaign/using/pressure-rules.md#use-cases-on-pressure-rules) se encuentran disponibles ejemplos de uso de las reglas de tipología de presión.

**Temas relacionados**

* [Aplicar reglas comerciales automáticas a las entregas en cualquier canal](https://helpx.adobe.com/es/campaign/kb/simplifying-campaign-management-acc.html#Applyautomaticbusinessrulestodeliveriesonanychannel)