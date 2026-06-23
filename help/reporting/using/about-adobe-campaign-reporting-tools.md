---
product: campaign
title: Acerca de las herramientas del sistema de informes de Adobe Campaign
description: Analice el éxito de sus campañas en informes integrados o personalizados
feature: Reporting, Monitoring
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
exl-id: 1ef30004-e1b0-4dde-8104-0ee9e8aa9d8b
TQID: https://experienceleague.adobe.com/4D-bCeMQakNjr7OXhiZ1u0Sfp5MZWwzZzHtykBfFzZ8
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: c309ee4e-82e4-4f7e-b608-ef345678c34e
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
subfeature_v2: id: b3a4149f-2b3a-44d1-894e-e3ac4c77fb47id: cfda811a-e413-43a4-adf0-7370888f5cfcid: afe938ea-bc18-44a4-a3fb-03e1031466cb
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 362
ht-degree: 100%

---

# Introducción a la creación de informes {#about-adobe-campaign-reporting-tools}



Además de los [informes integrados](../../reporting/using/about-campaign-built-in-reports.md), Adobe Campaign permite generar informes en distintos contextos y satisfacer diferentes necesidades. En este documento se describen los principios de uso y los modos de implementación.

Adobe Campaign no es una herramienta de sistema de informes especializada: los informes creados en Adobe Campaign principalmente le permiten ver los datos añadidos. Los informes de Adobe Campaign, dedicados a analizar y representar los datos, no están diseñados para exportaciones de bases de datos.

Para exportar datos de la base de datos de Adobe Campaign, debe crear un flujo de trabajo y utilizar una actividad de exportación de datos. Para obtener más información al respecto, consulte la [documentación de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/action-activities.html?lang=es){target="_blank"}.

Adobe Campaign proporciona varias herramientas de sistema de informes:

1. **Informe integrados**: Adobe Campaign ofrece un conjunto de informes sobre envíos, campañas, actividades de la plataforma, funcionalidades opcionales, etc. Estos informes están disponibles a través de las diversas funcionalidades a las que se refieren.Pueden adaptarse a sus necesidades específicas.

   Para obtener más información, consulte [esta sección](../../reporting/using/about-campaign-built-in-reports.md).

1. **Descriptive data analysis**: Adobe Campaign proporciona una herramienta visual para generar estadísticas de los datos de la base de datos. Puede crear informes de análisis descriptivos utilizando el asistente dedicado y adaptar su contenido y diseño según sus necesidades.

   Para obtener más información, consulte [esta sección](../../reporting/using/about-descriptive-analysis.md).

1. **Personalized reports**: Adobe Campaign permite crear informes de los datos de la base de datos. Una vez creados, se puede acceder a ellos en los contextos correspondientes.

   Según la complejidad de las consultas, los cálculos y los volúmenes, los datos analizados en estos informes pueden recopilarse mediante una consulta y preacumularse en una lista (flujo de trabajo de tipo “gestión de datos”) o en un cubo (con Marketing Analytics). Se muestra en forma de tabla dinámica o lista de grupos.

   Para obtener más información, consulte [esta sección](../../reporting/using/about-reports-creation-in-campaign.md).

1. **Analysis reports**: Marketing Analytics permite la exploración intuitiva de datos.

   Para obtener más información, consulte [esta sección](../../reporting/using/ac-cubes.md).

>[!CAUTION]
>
>Para facilitar su visualización y su manipulación, así como su exportación eficaz, los informes no deben contener más de 1000 líneas.
