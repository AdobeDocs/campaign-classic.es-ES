---
title: Acerca de las herramientas del sistema de informes de Adobe Campaign
seo-title: Acerca de las herramientas del sistema de informes de Adobe Campaign
description: Acerca de las herramientas del sistema de informes de Adobe Campaign
seo-description: null
page-status-flag: never-activated
uuid: a8122c9e-60ba-4ef7-bc63-05d6cf16fad0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: reporting-in-adobe-campaign
discoiquuid: c5dad561-0708-4b7a-84a0-eb00beff58c6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1719d6ac9643f0b3e9339037cf4d0f209d16340e

---


# Introducción a los informes {#about-adobe-campaign-reporting-tools}

Además de los [informes integrados](../../reporting/using/about-campaign-built-in-reports.md), Adobe Campaign permite generar informes en varios contextos y satisfacer diferentes necesidades. En este documento se describen los principios de uso y los modos de implementación.

Adobe Campaign no es una herramienta de sistema de informes especializada: los informes creados en Adobe Campaign principalmente le permiten ver los datos añadidos. Los informes de Adobe Campaign, dedicados a analizar y representar los datos, no están diseñados para exportaciones de bases de datos.

Para exportar datos de la base de datos de Adobe Campaign, debe crear un flujo de trabajo y utilizar una actividad de exportación de datos. Para obtener más información, consulte [esta sección](../../workflow/using/about-action-activities.md).

Adobe Campaign proporciona varias herramientas de sistema de informes:

1. **Informes** integrados: Adobe Campaign ofrece un conjunto de informes sobre entregas, campañas, actividades de plataforma, funcionalidades opcionales, etc. Estos informes están disponibles a través de las diversas funciones a las que se refieren. Pueden adaptarse a sus necesidades específicas.

   Para obtener más información, consulte [esta sección](../../reporting/using/about-campaign-built-in-reports.md).

1. **Análisis** de datos descriptivos: Adobe Campaign proporciona una herramienta visual para generar estadísticas sobre los datos de la base de datos. Puede crear informes de análisis descriptivos utilizando el asistente dedicado y adaptar su contenido y diseño según sus necesidades.

   Para obtener más información, consulte [esta sección](../../reporting/using/about-descriptive-analysis.md).

1. **Informes** personalizados: Adobe Campaign permite crear informes sobre los datos de la base de datos. Una vez creados, se puede acceder a ellos en los contextos correspondientes.

   Según la complejidad de las consultas, los cálculos y los volúmenes, los datos analizados en estos informes pueden recopilarse mediante una consulta y preacumularse en una lista (flujo de trabajo de tipo “gestión de datos”) o en un cubo (con Marketing Analytics). Se muestra en forma de tabla dinámica o lista de grupos.

   Para obtener más información, consulte [esta sección](../../reporting/using/about-reports-creation-in-campaign.md).

1. **Informes** de análisis: Marketing Analytics permite la exploración intuitiva de datos.

   Para obtener más información, consulte [esta sección](../../reporting/using/about-cubes.md).

>[!CAUTION]
>
>Para facilitar su visualización y su manipulación, así como su exportación eficaz, los informes no deben contener más de 1000 líneas.