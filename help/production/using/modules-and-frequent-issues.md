---
product: campaign
title: Módulos y problemas frecuentes
description: Módulos y problemas frecuentes
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: dbd50178-0a16-46ed-bfad-47beb3c2a420
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 6%

---

# Módulos y problemas frecuentes{#modules-and-frequent-issues}



Esta es una lista de módulos afectados por problemas frecuentes:

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
   <td> El operador que programó esta exportación debe volver a iniciarla. delta o relanzamiento completo.<br /> </td> 
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
   <td> mta. </td> 
   <td> Entrega correos electrónicos<br /> </td> 
   <td> Compruebe este módulo si ya no se están enviando correos electrónicos.<br /> </td> 
  </tr> 
  <tr> 
   <td> stat </td> 
   <td> Mantiene las estadísticas de conexión de MTA<br /> </td> 
   <td> Compruebe este módulo si ya no se están enviando correos electrónicos.<br /> </td> 
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
   <td> Seguimiento de la escritura y depuración de registros en el servidor<br /> </td> 
   <td> Compruebe este módulo si los registros de seguimiento ya no se reenvían y no hay rastros de registros en los archivos del servidor. Consulte <a href="../../production/using/tracking-logs-issues.md" target="_blank">Problemas de registro de seguimiento</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> watchdog </td> 
   <td> Instancia de inicio y monitorización<br /> </td> 
   <td> Compruebe este módulo si no se inician procesos.<br /> </td> 
  </tr> 
  <tr> 
   <td> web </td> 
   <td> Servidor de aplicaciones (HTTP y SOAP)<br /> </td> 
   <td> Compruebe este módulo si la consola y las conexiones web no funcionan y déclencheur un <strong>xtk:session</strong> error de tipo<br /> </td> 
  </tr> 
  <tr> 
   <td> wfserver </td> 
   <td> Controla la ejecución de instancias de flujo de trabajo.<br /> </td> 
   <td> Si encuentra algún problema, reinicie este módulo. Si es necesario, aplique el procedimiento para aumentar la precisión de los registros detallados en la <a href="../../production/using/log-precision.md" target="_blank">Precisión de registro</a> para obtener más información.<br /> </td> 
  </tr> 
 </tbody> 
</table>
