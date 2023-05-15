---
product: campaign
title: Tipos de mantenimiento
description: Tipos de mantenimiento
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: 08e179aa-fd83-4c0a-879e-ab7aec168d92
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 2%

---

# Tipos de mantenimiento{#types-of-maintenance}



## Mantenimiento de aplicaciones {#application-maintenance}

Adobe Campaign proporciona un flujo de trabajo integrado que le permite programar determinadas tareas de mantenimiento de la base de datos: el **flujo de trabajo de limpieza de la base de datos**. Este flujo de trabajo lleva a cabo las siguientes tareas:

* eliminación de registros caducados,
* eliminación de registros huérfanos y reinicio del estado de los objetos caducados,
* actualizar las estadísticas de la base de datos.

>[!IMPORTANT]
>
>Tenga en cuenta que la tarea de limpieza se ocupa principalmente del mantenimiento a nivel de aplicación, no del mantenimiento a nivel de RDBMS (con excepción de la actualización de estadísticas). Sin embargo, se requerirán operaciones de mantenimiento en la base de datos. Aunque el flujo de trabajo de limpieza de la base de datos se ejecute correctamente, esto no significa que la base de datos esté optimizada.

## Mantenimiento técnico {#technical-maintenance}

El flujo de trabajo de limpieza de la base de datos no incluye ninguna herramienta de mantenimiento de la base de datos: es responsabilidad suya organizar el mantenimiento. Para ello, puede:

* trabaje con el administrador de bases de datos para configurar el mantenimiento de bases de datos con herramientas de terceros,
* utilice el motor de flujo de trabajo de Adobe Campaign para programar y realizar un seguimiento de estas actividades de mantenimiento.

Estos procedimientos de mantenimiento deben llevarse a cabo de forma periódica y deben incluir lo siguiente:

* volver a indexar tablas actualizadas con frecuencia,
* compacte/reconstruya las tablas para evitar la fragmentación.

### Calendario de mantenimiento {#maintenance-schedule}

Debe encontrar las ranuras adecuadas para realizar estas actividades de mantenimiento. Pueden afectar en gran medida al rendimiento de la base de datos mientras se ejecuta o incluso bloquea la aplicación (debido al bloqueo).

Estas tareas suelen ejecutarse una vez a la semana durante un periodo de actividad baja que no entra en conflicto con las copias de seguridad, la recarga de datos o el cálculo agregado. Algunos sistemas muy solicitados requieren un mantenimiento más frecuente.

Se puede realizar un mantenimiento más profundo, como recompilaciones de tablas completas, una vez al mes, preferiblemente con aplicaciones totalmente detenidas, ya que el sistema no se puede utilizar de todos modos.

### Reconstrucción de una tabla {#rebuilding-a-table}

Hay varias estrategias disponibles:

<table> 
 <thead> 
  <tr> 
   <th> Operaciones </th> 
   <th> Descripción </th> 
   <th> Ventajas </th> 
   <th> Inconvenientes </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Desfragmentación en línea<br /> </td> 
   <td> La mayoría de los motores de base de datos proporcionan métodos de desfragmentación.<br /> </td> 
   <td> Utilice simplemente el método de desfragmentación de la base de datos. Estos métodos generalmente se ocupan de los problemas de integridad bloqueando los datos durante la desfragmentación.<br /> </td> 
   <td> Dependiendo de la base de datos, estos métodos de desfragmentación pueden proporcionarse como una opción de RDBMS (Oracle) y no siempre son la forma más eficiente de lidiar con tablas más grandes.<br /> </td> 
  </tr> 
  <tr> 
   <td> Volcar y restaurar<br /> </td> 
   <td> Volque la tabla a un archivo, elimine la tabla de la base de datos y restaure el volcado.<br /> </td> 
   <td> Esta es la forma más sencilla de desfragmentar una tabla. También es la única solución cuando la base de datos está casi llena.<br /> </td> 
   <td> Como la tabla se elimina y se vuelve a crear, la aplicación no se puede dejar en línea, ni siquiera en modo de solo lectura (la tabla no está disponible durante la fase de restauración).<br /> </td> 
  </tr> 
  <tr> 
   <td> Duplicar, cambiar nombre y soltar<br /> </td> 
   <td> Esto crea una copia de una tabla y sus índices, luego reemplaza la existente y cambia el nombre de la copia para que ocupe su lugar.<br /> </td> 
   <td> Este método es más rápido que el primer método, ya que genera menos IO (sin copia como archivo y lectura desde este archivo).<br /> </td> 
   <td> Requiere el doble de espacio.<br /> Se deben detener todos los procesos activos que escriben en la tabla durante el proceso. Sin embargo, los procesos de lectura no se verán afectados, ya que la tabla se intercambiará en el último momento una vez que se vuelva a crear. <br /> </td> 
  </tr> 
 </tbody> 
</table>
