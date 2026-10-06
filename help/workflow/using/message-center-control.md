---
product: campaign
title: Centro de mensajes (Control)
description: Centro de mensajes (Control)
hide: true
feature: Workflows
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 100%
---

# Centro de mensajes (Control){#message-center-control}



El flujo de trabajo detallado a continuación está programado para ejecutarse cada hora. Se instala con el módulo **Centro de mensajes (Control)** de forma predeterminada.


Para obtener más información, consulte estas secciones en función de la versión de Campaign:

![](assets/do-not-localize/v7.jpeg)[Documentación de Campaign v7](../../message-center/using/about-transactional-messaging.md)

![](assets/do-not-localize/v8.png)[Documentación de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/transactional.html?lang=es)


<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etiqueta</strong><br /> </td> 
   <td> <strong>Nombre interno</strong><br /> </td> 
   <td> <strong>Descripción</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Centro de mensajes &lt;external_account_name&gt;<br /> </td> 
   <td> mcSynch_&lt;external_account_name&gt;<br /> </td> 
   <td> Este flujo de trabajo:<br /> 
    <ul> 
     <li> <p>recupera la lista de eventos procesados por las operaciones.</p> </li> 
     <li> <p>se sincroniza con la tabla NmsBroadLogMsg para poder recuperar las calificaciones del mensaje de la entrega.</p> </li> 
     <li> <p>recupera los registros de envío de eventos en cuanto se completa la sincronización con la tabla NmsBroadLogMsg.</p> </li> 
     <li> <p>se sincroniza con la tabla NmsTrackingUrl para recuperar el seguimiento de las URL de la entrega.</p> </li> 
     <li> <p>recupera las URL de seguimiento de eventos en cuanto se completa la sincronización con la tabla NmsTrackingUrl.</p> </li> 
     <li> <p>permite recuperar todas las direcciones de correo electrónico puestas en cuarentena cada tres horas después de realizar una entrega.</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

