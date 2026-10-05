---
product: campaign
title: Message Center (Execution)
description: Message Center (Execution)
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
source-wordcount: '232'
ht-degree: 100%
---

# Message Center (Execution){#message-center-execution}



Los flujos de trabajo detallados a continuación se instalan con el complemento **Message Center - Execution** de forma predeterminada.

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
   <td> <span class="uicontrol">Actualizar estado del evento</span> <br /> </td> 
   <td> <span class="uicontrol">updateEventsStatus</span> <br /> </td> 
   <td> Este flujo de trabajo permite asignar un estado a un evento. Los estados de eventos son los siguientes:<br /> 
    <ul> 
     <li> <p><strong>Pendiente</strong>: el evento está en cola. Aún no se le ha asociado ninguna plantilla de mensaje.</p> </li> 
     <li> <p><strong>Envío pendiente</strong>: el evento está en cola, se le ha asociado una plantilla de mensaje y la entrega se está procesando en ese momento.</p> </li> 
     <li> <p><strong>Enviado</strong>: este estado se copia desde los “logs” de envío. Significa que la entrega se realizó.</p> </li> 
     <li> <p><strong>Envío ignorado</strong>: este estado se copia desde los “logs” de envío. Significa que la entrega se ha ignorado.</p> </li> 
     <li> <p><strong>Error de envío</strong>: este estado se copia desde los “logs” de envío. Significa que la entrega ha fallado.</p> </li> 
     <li> <p><strong>Evento no cubierto</strong>: el evento no se ha podido asociar con una plantilla de mensaje. El evento no se vuelve a procesar.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Procesamiento de eventos por lotes</span> <br /> </td> 
   <td> <span class="uicontrol">batchEventsProcessing</span> <br /> </td> 
   <td> Este flujo de trabajo permite colocar eventos en lote en cola antes de asociarlos con una plantilla de mensaje. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Procesamiento de eventos en tiempo real</span> <br /> </td> 
   <td> <span class="uicontrol">rtEventsProcessing</span> <br /> </td> 
   <td> Este flujo de trabajo permite colocar eventos en tiempo real en cola antes de asociarlos con una plantilla de mensaje. <br /> </td> 
  </tr> 
 </tbody> 
</table>

