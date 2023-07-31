---
product: campaign
title: Objetos de aplicación
description: Objetos de aplicación
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Solo se aplica a Campaign Classic v7"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: fb4798d7-0a2c-455b-86b6-3dcb5fd25c82
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 4%

---

# Objetos de aplicación{#application-objects}



Los objetos incorporados deben ser monitoreados y es importante evitar que crezcan demasiado.

## Secuencia de ID {#sequence-of-ids}

Adobe Campaign utiliza una secuencia de ID que debe consumirse en consecuencia: **xtkNewId**. Si la secuencia se consume muy rápidamente (es decir, desde 100 000 al día), debe verificar que sea coherente con los requisitos de su empresa, como enviar millones de correos electrónicos al día. Es posible definir una secuencia dedicada para tablas específicas. Puede configurar un flujo de trabajo para monitorizar el uso de ID.

Cuando la secuencia alcanza más de 2 mil millones (2.147.483.648 es el número exacto), vuelve a cero. Debe evitarse y crea problemas, por lo que esta secuencia debe monitorizarse.

Para evitarlo con tablas grandes, considere la posibilidad de utilizar una secuencia específica. Esto se puede hacer con la variable **pkSequence** en el esquema.

Los flujos de trabajo de alta frecuencia que crean muchos registros consumirán muchos ID. Por lo tanto, es muy recomendable evitar demasiados registros y altas frecuencias en los flujos de trabajo.

Si la secuencia ya ha cambiado, la mejor solución es cambiar a ID negativos, a partir de -2 147 483 648.

## Carpetas {#folders}

Debe haber menos de 1000 carpetas en cualquier instancia. Tener más carpetas que esto puede causar problemas de rendimiento con el cliente de Campaign. Puede configurar un trabajo de monitorización para contar el número de carpetas, flujos de trabajo, etc., e informar de nuevo periódicamente.

Este método también resalta a los usuarios que crean demasiados objetos.

## Envíos {#deliveries}

Debe haber menos de 1000 envíos en la instancia en cualquier momento. Tener muchos envíos consume espacio en la base de datos y crea problemas. Una instancia que crea más de 10 envíos por día debe comprobarse con los requisitos comerciales. Considere utilizar envíos continuos para crear menos envíos. Para obtener más información, consulte [esta sección](../../workflow/using/continuous-delivery.md).

Las entregas de más de dos años deben purgarse de la instancia.

## Archivos {#files}

El número de archivos en el disco del servidor de aplicaciones no debe aumentar indefinidamente.

Los flujos de trabajo de importación crean archivos y, por lo tanto, provocan expansión de disco. Esto se puede evitar utilizando el estándar de [Recopilador de archivos](../../workflow/using/file-collector.md) actividad. El recolector de archivos mueve los archivos a una carpeta temporal y los purga automáticamente.

Si un flujo de trabajo importa archivos y no utiliza las funciones estándar, debe purgarse para mantener el espacio en disco al mínimo.

## Datos transaccionales y registros {#transactional-data-and-logs}

Cada [workflow](../../workflow/using/data-life-cycle.md#work-table) que importa datos en Adobe Campaign hace que el tamaño de la base de datos crezca.

Compruebe que los flujos de trabajo de limpieza o depuración se estén ejecutando y purguen los registros de forma eficaz. Se deben purgar todos los datos transaccionales y los registros. La tarea de limpieza depura solo las tablas estándar: seguimiento y registros generales. Flujos de trabajo específicos deben depurar tablas específicas. Consulte [esta sección](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs).

Compruebe los datos transaccionales de caducidad comprobando la fecha de creación más antigua de los registros.
