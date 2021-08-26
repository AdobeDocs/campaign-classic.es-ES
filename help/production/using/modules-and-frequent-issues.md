---
product: campaign
title: Módulos y problemas frecuentes
description: Módulos y problemas frecuentes
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: dbd50178-0a16-46ed-bfad-47beb3c2a420
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 5%

---

# Módulos y problemas frecuentes{#modules-and-frequent-issues}

![](../../assets/v7-only.svg)

Esta es una lista de módulos afectados por problemas frecuentes:

<table> 
 <thead> 
  <tr> 
   <th> Módulo </th> 
   <th> Ámbito de ejecución </th> 
   <th> Solución de problemas </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> exportar </td> 
   <td> Ejecución de un proceso de exportación<br /> </td> 
   <td> El operador que programó esta exportación debe volver a iniciarla. delta o reinicio completo.<br /> </td> 
  </tr> 
  <tr> 
   <td> importar </td> 
   <td> Ejecución de un proceso de importación<br /> </td> 
   <td> El operador que programó esta exportación debe volver a iniciarla. Compruebe si hay duplicados en la base de datos.<br /> </td> 
  </tr> 
  <tr> 
   <td> inMail </td> 
   <td> Lectura del cuadro de correo rechazado<br /> </td> 
   <td> Compruebe este módulo si los correos rechazados ya no se reenvían.<br /> </td> 
  </tr> 
  <tr> 
   <td> mta </td> 
   <td> Entrega correos electrónicos<br /> </td> 
   <td> Compruebe este módulo si ya no se están enviando correos.<br /> </td> 
  </tr> 
  <tr> 
   <td> stat </td> 
   <td> Mantiene las estadísticas de conexión MTA<br /> </td> 
   <td> Compruebe este módulo si ya no se están enviando correos.<br /> </td> 
  </tr> 
  <tr> 
   <td> syslogd </td> 
   <td> Escritura de registro<br /> </td> 
   <td> Si faltan algunos registros en los archivos de registro, compruebe que el módulo esté utilizando el puerto 6666. Consulte <a href="../../production/using/general-architecture.md#list-of-open-ports" target="_blank">Lista de puertos abiertos</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> seguimiento </td> 
   <td> Consolidación y recuperación de registros de seguimiento<br /> </td> 
   <td> Compruebe este módulo si los registros de seguimiento ya no se reenvían.<br /> </td> 
  </tr> 
  <tr> 
   <td> trackinglogd </td> 
   <td> Seguimiento de la escritura de registros y del servidor de depuración<br /> </td> 
   <td> Compruebe este módulo si los registros de seguimiento ya no se reenvían y no hay rastros de registros en los archivos del servidor. Consulte <a href="../../production/using/tracking-logs-issues.md" target="_blank">Problemas de registros de seguimiento</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> watchdog </td> 
   <td> Instancia de inicio y monitorización<br /> </td> 
   <td> Compruebe este módulo si no se inician procesos.<br /> </td> 
  </tr> 
  <tr> 
   <td> web </td> 
   <td> Servidor de aplicaciones (HTTP y SOAP)<br /> </td> 
   <td> Compruebe este módulo si la consola y las conexiones web no funcionan y cree un déclencheur de error de tipo <strong>xtk:session</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> wfserver </td> 
   <td> Controla la ejecución de la instancia de flujo de trabajo.<br /> </td> 
   <td> Si encuentra algún problema, reinicie este módulo. Si es necesario, aplique el procedimiento para aumentar la precisión de los registros detallados en la sección <a href="../../production/using/log-precision.md" target="_blank">Log accuracy</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>
