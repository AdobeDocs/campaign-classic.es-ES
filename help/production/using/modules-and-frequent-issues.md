---
product: campaign
title: Módulos y problemas frecuentes
description: Módulos y problemas frecuentes
feature: Monitoring, Troubleshooting
badge-v7-prem: label="On-premise/híbrido solo" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: dbd50178-0a16-46ed-bfad-47beb3c2a420
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 10%

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
   <td> Ejecución de un proceso de exportación <br /> </td> 
   <td> El operador que programó esta exportación debe volver a iniciarla. Lanzamiento delta o completo.<br /> </td> 
  </tr> 
  <tr> 
   <td> importar </td> 
   <td> Ejecución de un proceso de importación<br /> </td> 
   <td> El operador que programó esta exportación debe volver a iniciarla. Buscar duplicados en la base de datos.<br /> </td> 
  </tr> 
  <tr> 
   <td> inMail </td> 
   <td> Leyendo el cuadro de correo rechazado<br /> </td> 
   <td> Compruebe este módulo si los mensajes devueltos ya no se reenvían.<br /> </td> 
  </tr> 
  <tr> 
   <td> mta. </td> 
   <td> Envía correos electrónicos<br /> </td> 
   <td> Compruebe este módulo si ya no se envían los mensajes.<br /> </td> 
  </tr> 
  <tr> 
   <td> estadísticas </td> 
   <td> Mantiene estadísticas de conexión de MTA<br /> </td> 
   <td> Compruebe este módulo si ya no se envían los mensajes.<br /> </td> 
  </tr> 
  <tr> 
   <td> syslogd </td> 
   <td> Registro de escritura<br /> </td> 
   <td> Si faltan algunos registros en los archivos de registro, asegúrese de que el módulo esté utilizando el puerto 6666. Consulte <a href="../../production/using/general-architecture.md#list-of-open-ports" target="_blank">Lista de puertos abiertos</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> seguimiento </td> 
   <td> Consolidando y recuperando registros de seguimiento<br /> </td> 
   <td> Compruebe este módulo si los registros de seguimiento ya no se reenvían.<br /> </td> 
  </tr> 
  <tr> 
   <td> trackinglogd </td> 
   <td> Seguimiento de la escritura y purga del registro del servidor <br /> </td> 
   <td> Compruebe este módulo si los registros de seguimiento ya no se reenvían y no hay seguimientos de registros en los archivos del servidor. Consulte <a href="../../production/using/tracking-logs-issues.md" target="_blank">Problemas en los registros de seguimiento</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> perro guardián </td> 
   <td> Instancia de inicio y supervisión <br /> </td> 
   <td> Compruebe este módulo si no se inician procesos.<br /> </td> 
  </tr> 
  <tr> 
   <td> web </td> 
   <td> SOAP Servidor de aplicaciones (HTTP y)<br /> </td> 
   <td> Compruebe este módulo si la consola y las conexiones web no funcionan y almacene en déclencheur un <strong>error de tipo xtk:session</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> wfserver </td> 
   <td> Controla la ejecución de la instancia de flujo de trabajo.<br /> </td> 
   <td> Si tiene algún problema, reinicie este módulo. Si es necesario, aplique el procedimiento para aumentar la precisión de los registros detallados en la sección <a href="../../production/using/log-precision.md" target="_blank">Precisión del registro</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>
