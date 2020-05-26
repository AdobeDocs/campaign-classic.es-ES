---
title: Objetos de aplicación
seo-title: Objetos de aplicación
description: Objetos de aplicación
seo-description: null
page-status-flag: never-activated
uuid: 84fbad0f-872d-4aca-8ea9-007577be076d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: database-maintenance
discoiquuid: 24d4875b-81fa-4bf3-8cf0-e6998bec4949
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b369a17fabc55607fc6751e7909e1a1cb3cd4201
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 4%

---


# Objetos de aplicación{#application-objects}

Los objetos incorporados deben monitorearse y es importante evitar que crezcan demasiado.

## Secuencia de ID {#sequence-of-ids}

Adobe Campaign utiliza una secuencia de ID que se debe consumir en consecuencia: **xtkNewId**. Si la secuencia se consume muy rápidamente (es decir, desde 100.000 al día), debe verificar que sea coherente con los requisitos comerciales, como enviar millones de correos electrónicos al día. Es posible definir una secuencia dedicada para tablas concretas. Puede configurar un flujo de trabajo para supervisar el uso del ID.

Cuando la secuencia llega a más de 2 mil millones (2,147,483,648 es el número exacto), regresa a cero. Debe evitarse y crear problemas, razón por la cual debe supervisarse esta secuencia.

Para evitar esto con tablas grandes, considere el uso de una secuencia específica. Esto se puede hacer con el **atributo pkSequence** en el esquema.

Los flujos de trabajo de alta frecuencia que crean muchos registros consumirán muchos ID. Por lo tanto, se recomienda evitar demasiados registros y frecuencias altas en flujos de trabajo.

Si la secuencia ya ha pasado a un ciclo, la mejor solución es cambiar a ID negativos, empezando por -2.147.483.648.

## Carpetas {#folders}

Debe haber menos de 1000 carpetas en cualquier instancia. Tener más carpetas que éstas puede provocar problemas de rendimiento con el cliente de Campaña. Puede configurar un trabajo de supervisión para que cuente el número de carpetas, flujos de trabajo, etc., y que informe de forma periódica.

Este método también resalta a los usuarios que crean demasiados objetos.

## Entregas {#deliveries}

Debe haber menos de 1000 envíos en la instancia en cualquier momento. Tener muchos envíos consume espacio en la base de datos y crea problemas. Una instancia que crea más de 10 envíos al día debe comprobarse en función de los requisitos comerciales. Considere utilizar envíos continuos para crear menos envíos. Para obtener más información, consulte [esta sección](../../workflow/using/continuous-delivery.md).

Los Envíos mayores de dos años deben ser purgados de la instancia.

## Archivos {#files}

El número de archivos en el disco del servidor de aplicaciones no debe aumentar indefinidamente.

Los flujos de trabajo de importación crean archivos y, por lo tanto, provocan la expansión del disco. Esto se puede evitar mediante la actividad de [Recolector de ficheros](../../workflow/using/file-collector.md) estándar. El selector de archivos mueve los archivos a una carpeta temporal y los purga automáticamente.

Si un flujo de trabajo importa archivos y no utiliza las funciones estándar, debe purgarse para reducir al mínimo el espacio en disco.

## Registros y datos transaccionales {#transactional-data-and-logs}

Cada [flujo de trabajo](../../workflow/using/data-life-cycle.md#work-table) que importa datos en Adobe Campaign hace que aumente el tamaño de la base de datos.

Compruebe que los flujos de trabajo de limpieza o depuración se están ejecutando y purgando los registros de forma efectiva. Todos los registros y datos transaccionales deben eliminarse. La tarea de limpieza purga únicamente las tablas estándar: seguimiento y registros amplios. Las tablas específicas deben eliminarse con flujos de trabajo específicos. Consulte [esta sección](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs).

Observe los datos transaccionales de antigüedad comprobando la fecha de creación más antigua de los registros.
