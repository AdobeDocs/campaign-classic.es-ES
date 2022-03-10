---
product: campaign
title: Acerca de las tipologías de campaña
description: Acerca de las tipologías de campaña
feature: Typology Rules
exl-id: 6d5b8584-4aa1-4d9a-89d9-d41da75dd323
source-git-commit: 36e546a34d8c2345fefed5d459095a76c6224a38
workflow-type: ht
source-wordcount: '483'
ht-degree: 100%

---

# Acerca de las tipologías de campaña{#about-campaign-typologies}

![](../../assets/common.svg)

Campaign Optimization (optimización de la campaña) es el módulo de Adobe Campaign que permite controlar, filtrar y monitorizar las entregas. Para evitar conflictos entre campañas, Adobe Campaign puede probar distintas combinaciones mediante la aplicación de reglas de restricción específicas. Esto garantiza que los mensajes enviados respondan de la mejor forma a las necesidades y expectativas de los clientes, de acuerdo con las políticas de comunicación de la compañía.

![](assets/do-not-localize/how-to-video.png) [Descubra esta función en vídeo](#typologies-video)

>[!NOTE]
>
>Según la oferta, Campaign Optimization puede estar incluido o ser un complemento. Compruebe el acuerdo de licencia.

## Reglas de tipología {#typology-rules}

Con Adobe Campaign puede diseñar y aplicar cuatro tipos de reglas de tipología:

* Reglas de **filtrado**, que permiten excluir parte del objetivo según los criterios. Para obtener más información, consulte [Reglas del filtro](filtering-rules.md).
* Reglas de **presión**, que permiten controlar la fatiga de marketing. Para obtener más información, consulte [Reglas de presión](pressure-rules.md).
* Reglas de **capacidad** que permiten limitar las cargas para garantizar condiciones de procesamiento óptimas. Para obtener más información, consulte [Capacidad de control](consistency-rules.md#controlling-capacity).
* Reglas de **control** que permiten comprobar la validez de los mensajes antes de enviarlos. Para obtener más información, consulte [Reglas de control](control-rules.md).

Una vez creadas, las reglas de tipología se agrupan en las tipologías de campaña a las que se hace referencia en las entregas. Consulte [Aplicación de tipologías](#applying-typologies).

## Tipologías {#typologies}

Una tipología de campaña puede contener varias [reglas de tipología](#typology-rules), pero una entrega solo puede hacer referencia a una tipología.

La pestaña **[!UICONTROL Rules]** permite añadir, eliminar o ver las reglas de tipología que se pueden aplicar.

![](assets/campaign_opt_rules_tab.png)

## Aplicación de tipologías {#applying-typologies}

A continuación se enumeran los pasos para crear y aplicar una tipología a las entregas:

1. Creación de reglas de tipología.

   Las reglas de tipología se encuentran en el nodo **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]**.

   Las distintas reglas disponibles en Campaign se describen en las siguientes secciones: reglas [de presión de ](pressure-rules.md)ventas, reglas [de ](consistency-rules.md#controlling-capacity)capacidad, reglas [de](control-rules.md) control y reglas [de ](filtering-rules.md)filtrado.

1. Cree una tipología y haga referencia a las reglas que creó en ella.

   Se puede acceder a las tipologías a través del nodo **[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]**.

1. Configure su envío para utilizar la tipología creada. Para obtener más información, consulte [esta sección](applying-rules.md#applying-a-typology-to-a-delivery).
1. Pruebe y controle el comportamiento a través de simulaciones de campañas. Para obtener más información sobre simulaciones de campaña, consulte [esta sección](campaign-simulations.md).

Durante la preparación de la entrega, los destinatarios se excluyen cuando se cumple el criterio. Puede comprobar los registros para controlar las exclusiones. En [esta página](pressure-rules.md#use-cases-on-pressure-rules) se encuentran disponibles ejemplos de uso de las reglas de tipología de presión.

## Tutoriales en vídeo {#typologies-video}

### Configuración de la administración de la fatiga mediante reglas de tipología

En este vídeo se explica cómo implementar la administración de la fatiga en Adobe Campaign mediante reglas de tipología.

>[!VIDEO](https://video.tv.adobe.com/v/25090?quality=12)

### Configuración de la gestión de la fatiga mediante filtros predefinidos

La gestión de la fatiga controla la frecuencia y la cantidad de mensajes para evitar el exceso de solicitudes de destinatarios. Si no tiene el módulo de optimización de la campaña en la instancia de campaña, puede configurar un filtro predefinido que filtrará la población de destinatarios por el número de mensajes recibidos.
En este vídeo se explica cómo implementar la administración de fatiga en Adobe Campaign Classic mediante filtros.

>[!VIDEO](https://video.tv.adobe.com/v/25091?quality=12)

Puede encontrar disponibles más vídeos de procedimientos para Campaign [aquí](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=es).

**Tema relacionado**

* [Aplicar reglas comerciales automáticas a las entregas en cualquier canal](https://helpx.adobe.com/es/campaign/kb/simplifying-campaign-management-acc.html#Applyautomaticbusinessrulestodeliveriesonanychannel)

* [Introducción a la administración de tipologías y fatiga](pressure-rules.md)

