---
product: campaign
title: Tipos de mantenimiento
description: Tipos de mantenimiento
feature: Monitoring
badge-v7-prem: label="On-Premise e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: 08e179aa-fd83-4c0a-879e-ab7aec168d92
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 4%

---

# Tipos de mantenimiento{#types-of-maintenance}



## Mantenimiento de aplicaciones {#application-maintenance}

Adobe Campaign proporciona un flujo de trabajo integrado que le permite programar determinadas tareas de mantenimiento de la base de datos: **flujo de trabajo limpieza base datos**. Este flujo de trabajo realiza las siguientes tareas:

* eliminación de registros caducados,
* eliminación de registros huérfanos y reinicio de estados para objetos caducados,
* actualizar las estadísticas de la base de datos.

>[!IMPORTANT]
>
>Tenga en cuenta que la tarea de limpieza trata principalmente del mantenimiento a nivel de aplicación, no del mantenimiento a nivel de RDBMS (con la excepción de la actualización de estadísticas). Sin embargo, se requerirán operaciones de mantenimiento en la base de datos. Incluso si el flujo de trabajo de limpieza de la base de datos se ejecuta correctamente, esto no significa que la base de datos esté optimizada.

## Mantenimiento técnico {#technical-maintenance}

El flujo de trabajo de limpieza de la base de datos no incluye ninguna herramienta de mantenimiento de la base de datos: depende de usted organizar el mantenimiento. Para ello, puede hacer lo siguiente:

* trabaje con el administrador de la base de datos para configurar el mantenimiento de la base de datos con herramientas de terceros,
* utilice el motor de flujos de trabajo de Adobe Campaign para programar y realizar un seguimiento de estas actividades de mantenimiento.

Estos procedimientos de mantenimiento deben llevarse a cabo de forma regular e incluir lo siguiente:

* reindexe las tablas actualizadas con frecuencia,
* compacte o reconstruya las tablas para evitar la fragmentación.

### Programa de mantenimiento {#maintenance-schedule}

Debe encontrar las ranuras adecuadas para realizar estas actividades de mantenimiento. Pueden afectar gravemente al rendimiento de la base de datos mientras se ejecuta o incluso bloquear la aplicación (debido al bloqueo).

Estas tareas se ejecutan normalmente una vez a la semana durante un período de baja actividad que no entra en conflicto con las copias de seguridad, la recarga de datos o el cálculo agregado. Algunos sistemas altamente solicitados requieren un mantenimiento más frecuente.

Una vez al mes se puede realizar un mantenimiento más detallado, como reconstrucciones de tabla completas, preferiblemente con aplicaciones totalmente detenidas, ya que el sistema no se puede utilizar de todos modos.

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
   <td> Simplemente utilice el método de desfragmentación de la base de datos. Estos métodos suelen encargarse de los problemas de integridad bloqueando los datos durante la desfragmentación.<br /> </td> 
   <td> Según la base de datos, estos métodos de desfragmentación se pueden proporcionar como una opción RDBMS (Oracle) y no siempre son la forma más eficaz de tratar con tablas más grandes.<br /> </td> 
  </tr> 
  <tr> 
   <td> Volcar y restaurar<br /> </td> 
   <td> Volcar la tabla en un archivo, eliminar la tabla de la base de datos y restaurar desde el volcado.<br /> </td> 
   <td> Esta es la forma más sencilla de desfragmentar una tabla. También es la única solución cuando la base de datos está casi llena.<br /> </td> 
   <td> Dado que la tabla se elimina y se vuelve a crear, la aplicación no se puede dejar en línea, ni siquiera en modo de solo lectura (la tabla no está disponible durante la fase de restauración).<br /> </td> 
  </tr> 
  <tr> 
   <td> Duplicar, cambiar nombre y soltar<br /> </td> 
   <td> Esto crea una copia de una tabla y sus índices, luego suelta el existente y cambia el nombre de la copia para que ocupe su lugar.<br /> </td> 
   <td> Este método es más rápido que el primer enfoque, ya que genera menos E/S (sin copia como archivo y leer de este archivo).<br /> </td> 
   <td> Requiere el doble de espacio.<br /> Se deben detener todos los procesos activos que escriben en la tabla durante el proceso. Sin embargo, los procesos de lectura no se verán afectados, ya que la tabla se intercambia en el último momento una vez reconstruida. <br /> </td> 
  </tr> 
 </tbody> 
</table>
