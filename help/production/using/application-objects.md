---
product: campaign
title: Objetos de aplicación
description: Objetos de aplicación
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: fb4798d7-0a2c-455b-86b6-3dcb5fd25c82
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 4%

---

# Objetos de aplicación{#application-objects}

Los objetos integrados deben vigilarse y es importante evitar que crezcan demasiado.

## Secuencia de ID {#sequence-of-ids}

Adobe Campaign utiliza una secuencia de ID que debe consumirse de forma correspondiente: **xtkNewId**. Si la secuencia se consume muy rápidamente (es decir, de 100 000 al día), debe verificar que sea coherente con los requisitos de su empresa, como el envío de millones de correos electrónicos al día. Es posible definir una secuencia dedicada para tablas específicas. Puede configurar un flujo de trabajo para controlar el uso del ID.

Cuando la secuencia llega a más de 2 mil millones (2,147,483,648 es el número exacto), vuelve a cero. Debe evitarse y crea problemas, razón por la cual esta secuencia debe monitorizarse.

Para evitar esto con tablas grandes, considere la posibilidad de utilizar una secuencia específica. Esto se puede hacer con el atributo **pkSequence** en el esquema.

Los flujos de trabajo de alta frecuencia que crean muchos registros consumirán muchos ID. Por lo tanto, se recomienda evitar demasiados registros y frecuencias altas en los flujos de trabajo.

Si la secuencia ya ha pasado de ciclo, la mejor solución es cambiar a ID negativos, empezando por -2.147.483.648.

## Carpetas {#folders}

Debe haber menos de 1000 carpetas en cualquier instancia. Tener más carpetas que esto puede causar problemas de rendimiento con el cliente de Campaign. Puede configurar un trabajo de monitorización para contar el número de carpetas, flujos de trabajo, etc., y volver a informar de forma periódica.

Este método también resalta a los usuarios que crean demasiados objetos.

## Entregas {#deliveries}

Debe haber menos de 1000 envíos en la instancia en cualquier momento. Tener muchos envíos consume espacio en la base de datos y crea problemas. Se debe comprobar una instancia que crea más de 10 envíos por día según los requisitos comerciales. Considere la posibilidad de utilizar envíos continuos para crear menos envíos. Para obtener más información, consulte [esta sección](../../workflow/using/continuous-delivery.md).

Los envíos mayores de dos años se deben eliminar de la instancia.

## Archivos {#files}

El número de archivos en el disco del servidor de aplicaciones no debe aumentar indefinidamente.

Los flujos de trabajo de importación crean archivos y, por lo tanto, provocan la expansión del disco. Esto se puede evitar utilizando la actividad estándar [File collector](../../workflow/using/file-collector.md). El recolector de archivos mueve los archivos a una carpeta temporal y los purga automáticamente.

Si un flujo de trabajo importa archivos y no utiliza las funciones estándar, debe purgarse para reducir al mínimo el espacio en disco.

## Registros y datos transaccionales {#transactional-data-and-logs}

Cada [flujo de trabajo](../../workflow/using/data-life-cycle.md#work-table) que importa datos en Adobe Campaign hace que aumente el tamaño de la base de datos.

Compruebe que los flujos de trabajo de limpieza o depuración se estén ejecutando y depuren registros de forma eficaz. Todos los datos y registros transaccionales deben depurarse. La tarea de limpieza purga solo las tablas estándar: seguimiento y registros amplios. Las tablas específicas deben purgarse mediante flujos de trabajo específicos. Consulte [esta sección](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs).

Observe los datos transaccionales de antigüedad comprobando la fecha de creación más antigua de los registros.
