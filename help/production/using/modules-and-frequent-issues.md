---
title: Módulos y problemas frecuentes
seo-title: Módulos y problemas frecuentes
description: Módulos y problemas frecuentes
seo-description: null
page-status-flag: never-activated
uuid: d53324ce-b6e2-40d7-932d-36ce4a6f5cf8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: a44f5e71-3f9b-4d02-8b7a-a9782bb6bdd8
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 6%

---


# Módulos y problemas frecuentes{#modules-and-frequent-issues}

Esta es una lista de los módulos afectados por problemas frecuentes:

<table> 
 <thead> 
  <tr> 
   <th> Módulo </th> 
   <th> Ámbito de ejecución </th> 
   <th> Resolución de problemas </th> 
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
   <td> El operador que programó esta exportación debe volver a iniciarla. Compruebe la existencia de duplicados en la base de datos.<br /> </td> 
  </tr> 
  <tr> 
   <td> inMail </td> 
   <td> Lectura del cuadro de correo de devolución<br /> </td> 
   <td> Compruebe este módulo si ya no se reenvían los mensajes de devolución.<br /> </td> 
  </tr> 
  <tr> 
   <td> mta </td> 
   <td> Entrega correos electrónicos<br /> </td> 
   <td> Compruebe este módulo si ya no se envían mensajes de correo electrónico.<br /> </td> 
  </tr> 
  <tr> 
   <td> stat </td> 
   <td> Mantiene las estadísticas de conexión MTA<br /> </td> 
   <td> Compruebe este módulo si ya no se envían mensajes de correo electrónico.<br /> </td> 
  </tr> 
  <tr> 
   <td> syslogd </td> 
   <td> Escritura de registros<br /> </td> 
   <td> Si faltan algunos registros en los archivos de registro, asegúrese de que el módulo esté utilizando el puerto 6666. Consulte <a href="../../production/using/general-architecture.md#list-of-open-ports" target="_blank">Lista de puertos</a>abiertos.<br /> </td> 
  </tr> 
  <tr> 
   <td> seguimiento </td> 
   <td> Consolidación y recuperación de registros de seguimiento<br /> </td> 
   <td> Compruebe este módulo si ya no se reenvían registros de seguimiento.<br /> </td> 
  </tr> 
  <tr> 
   <td> trackinglogd </td> 
   <td> Seguimiento de la escritura y depuración del registro en el servidor<br /> </td> 
   <td> Compruebe este módulo si los registros de seguimiento ya no se reenvían y no hay rastros de registros en los archivos del servidor. Consulte los problemas <a href="../../production/using/tracking-logs-issues.md" target="_blank">de</a>Registros de seguimiento.<br /> </td> 
  </tr> 
  <tr> 
   <td> watchdog </td> 
   <td> Instancia de inicio y supervisión<br /> </td> 
   <td> Compruebe este módulo si no se procesa el inicio.<br /> </td> 
  </tr> 
  <tr> 
   <td> web </td> 
   <td> Servidor de aplicaciones (HTTP y SOAP)<br /> </td> 
   <td> Compruebe este módulo si la consola y las conexiones web no funcionan y active un error de tipo <strong>xtk:session</strong> .<br /> </td> 
  </tr> 
  <tr> 
   <td> wfserver </td> 
   <td> Controla la ejecución de instancias de flujo de trabajo.<br /> </td> 
   <td> Si tiene algún problema, reinicie este módulo. Si es necesario, aplique el procedimiento para aumentar la precisión de los registros detallados en la sección Precisión <a href="../../production/using/log-precision.md" target="_blank">del</a> registro.<br /> </td> 
  </tr> 
 </tbody> 
</table>

