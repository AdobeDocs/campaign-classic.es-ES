---
product: campaign
title: Prácticas recomendadas para la creación de informes
description: Prácticas recomendadas para la creación de informes de Campaign
audience: reporting
content-type: reference
topic-tags: reporting-in-adobe-campaign
exl-id: 0c7f00f3-b16d-41c5-a7b1-f5a59201bf8c
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '839'
ht-degree: 100%

---

# Prácticas recomendadas para la creación de informes{#best-practices-reporting}

## Análisis de las necesidades{#analyzing-needs}

La utilización de una herramienta de sistema de informes depende del volumen de datos a manipular, de su complejidad y del tipo de sistema de informes que se deben configurar.

Para optimizar la creación, el uso y la duración de un informe, debe revisar las necesidades que desee satisfacer. Este primer análisis le permite identificar el tipo de informe que va crear y la mejor forma de crearlo. Para crear el informe, siga estos pasos:

1. Identificación de la necesidad

   El primer paso es identificar claramente la necesidad: lo que desea mostrar en el informe y cuál es su cometido (monitorización, análisis, exportación de datos, etc.).

   Adobe Campaign ofrece una amplia gama de capacidades de elaboración de informes. Es importante analizar su necesidad para identificar la funcionalidad más adecuada.

   Por ejemplo, puede:

   * Explore los datos de la base de datos y defina las medidas. Obtenga más información [en esta sección](../../reporting/using/about-cubes.md)
   * Añada indicadores a un informe existente. Obtenga más información [en esta sección](../../reporting/using/about-reports-creation-in-campaign.md)
   * Vista de los datos en la base de datos. Obtenga más información [en esta sección](../../reporting/using/about-descriptive-analysis.md)
   * Creación de un nuevo informe de envío. Obtenga más información [en esta sección](../../reporting/using/about-reports-creation-in-campaign.md)),
   * Exportar datos de la base de datos de Adobe Campaign (a través de un flujo de trabajo, consulte [esta sección](../../workflow/using/about-workflows.md)).
   * Cree una tabla dinámica. Obtenga más información [en esta sección](../../reporting/using/creating-a-table.md#creating-a-breakdown-or-pivot-table)
   * Explorar datos agregados. Obtenga más información [en esta sección](../../reporting/using/about-cubes.md)
   * Utilice un asistente para analizar los datos. Obtenga más información [en esta sección](../../reporting/using/about-descriptive-analysis.md)
   * Analice grandes volúmenes de datos. Obtenga más información [en esta sección](../../reporting/using/about-reports-creation-in-campaign.md)

1. Identificación de la población objetivo

   Después, necesita saber a quién se dirige el informe que desea crear, saber el tipo de público que desea que lo vea y el modo de visualización del informe (en un navegador, en Adobe Campaign, para un objeto específico, para la plataforma completa, etc.).

   También puede crear informes para:

   * Todos los operadores de Adobe Campaign.
   * Operadores con derechos de acceso a una única campaña de marketing.
   * Un operador individual para uso temporal.
   * Todos los operadores con acceso web, etc.

   Estas consideraciones también deben tener en cuenta los problemas relacionados con los derechos de acceso y de seguridad.

1. Definición del contenido

   Luego necesita saber qué tipo de datos desea mostrar: indicadores de envío, informes sobre los perfiles de base de datos, etc.

   También es necesario conocer la naturaleza de estos datos (simples, resultantes de un cálculo, importantes, etc.), su ubicación (en Adobe Campaign, en un sistema de terceros), la frecuencia de actualización para definir la periodicidad del cálculo (diariamente, semanalmente, sobre la marcha), así como su volumen.

   Los problemas relacionados con los volúmenes de datos y las actualizaciones se deben observar cuidadosamente para evitar problemas en la visualización de informes, especialmente en términos de tiempo. Por lo tanto, se recomienda crear acumulados para precalcular algunos datos fuera del informe. Las tablas que contienen los “logs” de envío y seguimiento pueden incluir millones de registros: esto significa que es necesario acumular los datos a través de un flujo de trabajo para utilizarlo en un informe.

## Optimización de la creación de informes{#optimizing-report-creation}

### Volumen de datos {#data-volume}

Para garantizar un rendimiento óptimo, el volumen de datos manipulados no debe ser demasiado grande.

Es decir:

* El tiempo de cálculo de un informe nunca debe exceder los 5 minutos.

   Del mismo modo, durante la fase de diseño, si el cálculo del informe supera los 60 segundos con un volumen pequeño de datos, se deben modificar los métodos de cálculo.

* Al utilizar el módulo Marketing Analytics, los datos del sistema de informes no deben superar los 10 millones de líneas.

También se recomienda calcular los acumulados por la noche y utilizar estos datos acumulados directamente en los informes. Estos acumulados deben crearse mediante flujos de trabajo de gestión de datos específicos (consultas SQL).

También puede calcular los informes durante la noche y crear automáticamente un historial que se pueda ver en cualquier momento sin sobrecargar la base de datos.

### Consultas {#queries}

Se recomienda utilizar consultas SQL siempre que sea posible y evitar el posprocesamiento por JavaScript. Si es necesario, utilice una actividad de secuencia de comandos en un flujo de trabajo y elimine los datos utilizados para el cálculo. También puede utilizar datos archivados para acelerar el tiempo de procesamiento.

En este caso, se debe utilizar la siguiente sintaxis:

```
if(string(ctx@_historyId)!==""))
```

Las consultas que permiten recopilar los datos mostrados en los informes no deben ser demasiado complejas, especialmente si se aplican a todos los datos de la base de datos. Para mejorar el rendimiento, puede resultar útil filtrar los datos antes de ejecutar estas consultas: esto significa que el cálculo solo incluye parte de los datos.

### Rendimientos {#performances}

Las recomendaciones anteriores permiten optimizar el cálculo del informe.

Además, Adobe Campaign recomienda las siguientes mejoras:

* Trabaje en el modelo de datos: los campos indexados se deben utilizar principalmente para mejorar las fórmulas de cálculo.

   Para buscar un campo indexado rápidamente, observe el nombre de la columna en la interfaz de Adobe Campaign: la flecha de clasificación aparece subrayada en rojo si el campo está indexado.

   Para obtener más información sobre índices, consulte [esta sección](../../configuration/using/data-model-best-practices.md#indexes).

* Asegúrese de que el informe sea escalable: el volumen de datos puede aumentar significativamente con el tiempo.

   Del mismo modo, el volumen de datos manipulado durante las fases de prueba puede diferir del volumen de datos real de la producción. Por este motivo las fases de prueba son importantes.

   Por último, es necesario conocer y adaptar la depuración de los datos cuando sea necesario para una manipulación de datos más sencilla.

   Para obtener más información sobre limpieza y retención de datos, consulte [esta sección](../../configuration/using/data-model-best-practices.md#data-retention).

### Exportación de informes {#exporting-reports}

En [esta sección](../../reporting/using/actions-on-reports.md#exporting-a-report) se describen las recomendaciones específicas para exportar informes.
