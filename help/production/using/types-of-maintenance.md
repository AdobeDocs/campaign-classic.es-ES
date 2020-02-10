---
title: Tipos de mantenimiento
seo-title: Tipos de mantenimiento
description: Tipos de mantenimiento
seo-description: null
page-status-flag: never-activated
uuid: 44faee3d-0549-4f63-8fdc-b24e6de47bc4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: database-maintenance
discoiquuid: 4a436ccf-097c-43e6-9eda-492bada5512a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Tipos de mantenimiento{#types-of-maintenance}

## Mantenimiento de aplicaciones {#application-maintenance}

Adobe Campaign ofrece un flujo de trabajo integrado que le permite programar determinadas tareas de mantenimiento de la base de datos: flujo de trabajo **de limpieza de la base de datos**. Este flujo de trabajo lleva a cabo las siguientes tareas:

* eliminación de registros caducados,
* eliminación de registros huérfanos y reinicialización de estado para objetos caducados,
* actualización de las estadísticas de la base de datos.

>[!CAUTION]
>
>Tenga en cuenta que la tarea de limpieza se ocupa principalmente del mantenimiento del nivel de aplicación, no del mantenimiento del nivel de RDBMS (con excepción de la actualización de estadísticas). Sin embargo, se necesitarán operaciones de mantenimiento en la base de datos. Aunque el flujo de trabajo de limpieza de la base de datos se ejecute correctamente, esto no significa que la base de datos esté optimizada.

## Mantenimiento técnico {#technical-maintenance}

El flujo de trabajo de limpieza de la base de datos no incluye ninguna herramienta de mantenimiento de la base de datos: depende de usted organizar el mantenimiento. Para ello, puede:

* trabaje con el administrador de la base de datos para configurar el mantenimiento de la base de datos con herramientas de terceros,
* utilice el motor de flujo de trabajo de Adobe Campaign para programar y realizar el seguimiento de estas actividades de mantenimiento.

Estos procedimientos de mantenimiento deberán llevarse a cabo de forma periódica e incluir lo siguiente:

* volver a indexar las tablas actualizadas con frecuencia,
* compactar/reconstruir las tablas para evitar la fragmentación.

### Calendario de mantenimiento {#maintenance-schedule}

Debe encontrar las ranuras adecuadas para realizar estas actividades de mantenimiento. Pueden tener un gran impacto en el rendimiento de la base de datos mientras se ejecuta o incluso bloquear la aplicación (debido al bloqueo).

Estas tareas suelen ejecutarse una vez a la semana durante un período de baja actividad que no entra en conflicto con las copias de seguridad, la recarga de datos o el cálculo agregado. Algunos sistemas muy solicitados requieren un mantenimiento más frecuente.

Se puede realizar un mantenimiento más profundo, como las reconstrucciones completas de tablas, una vez al mes, preferiblemente con las aplicaciones totalmente detenidas, ya que el sistema no se puede utilizar de todos modos.

### Reconstrucción de una tabla {#rebuilding-a-table}

Hay varias estrategias disponibles:

<table> 
 <thead> 
  <tr> 
   <th> Operaciones </th> 
   <th> Descripción </th> 
   <th> Beneficios </th> 
   <th> Desventajas </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Desfragmentación en línea<br /> </td> 
   <td> La mayoría de los motores de base de datos proporcionan métodos de desfragmentación.<br /> </td> 
   <td> Utilice simplemente el método de desfragmentación de la base de datos. Estos métodos generalmente se ocupan de los problemas de integridad al bloquear los datos durante la desfragmentación.<br /> </td> 
   <td> Dependiendo de la base de datos, estos métodos de desfragmentación pueden proporcionarse como una opción RDBMS (Oracle) y no siempre son la manera más eficiente de tratar tablas más grandes.<br /> </td> 
  </tr> 
  <tr> 
   <td> Volcar y restaurar<br /> </td> 
   <td> Volcar la tabla a un archivo, eliminar la tabla de la base de datos y restaurar desde el volcado.<br /> </td> 
   <td> Esta es la forma más sencilla de desfragmentar una tabla. También la única solución cuando la base de datos está casi llena.<br /> </td> 
   <td> Dado que la tabla se elimina y se vuelve a crear, la aplicación no se puede dejar en línea, ni siquiera en modo de solo lectura (la tabla no está disponible durante la fase de restauración).<br /> </td> 
  </tr> 
  <tr> 
   <td> Duplicar, cambiar nombre y soltar<br /> </td> 
   <td> De este modo, se crea una copia de una tabla y sus índices y, a continuación, se elimina la existente y se cambia el nombre de la copia para que ocupe su lugar.<br /> </td> 
   <td> Este método es más rápido que el primer método, ya que genera menos E/S (sin copia como archivo y lectura desde este archivo).<br /> </td> 
   <td> Requiere el doble de espacio.<br /> Todos los procesos activos que escriben en la tabla durante el proceso deben detenerse. Sin embargo, los procesos de lectura no se verán afectados, ya que la tabla se intercambiará en el último momento una vez reconstruida. <br /> </td> 
  </tr> 
 </tbody> 
</table>

