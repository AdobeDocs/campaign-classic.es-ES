---
title: Message Center (Execution)
seo-title: Message Center (Execution)
description: Message Center (Execution)
seo-description: null
page-status-flag: never-activated
uuid: 8dfb09d1-da00-43fb-9df4-243bb915cbde
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: dc3d8998-9493-4d71-b3e2-6f9531cb9bac
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Message Center (Execution){#message-center-execution}

Los flujos de trabajo detallados a continuación se instalan con el módulo **Message
				Center - Execution** de forma predeterminada. Para obtener más información sobre este módulo, consulte esta [sección](../../message-center/using/about-transactional-messaging.md).

Para obtener más información sobre cómo configurar los flujos de trabajo técnicos relacionados con el módulo Message Center, consulte [esta página](../../message-center/using/technical-workflows.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etiqueta</strong><br /> </td> 
   <td> <strong>Nombre
								 interno</strong><br /> </td> 
   <td> <strong>Descripción</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Actualizar estado</span> del evento <br /> </td> 
   <td> <span class="uicontrol">updateEventsStatus</span><br /> </td> 
   <td> Este flujo de trabajo permite asignar un estado a un evento. Los estados de eventos son los siguientes:<br /> 
    <ul> 
     <li> <p><strong>Pendiente</strong>: el evento está en cola. Aún no se le ha asociado ninguna plantilla de mensaje.</p> </li> 
     <li> <p><strong>Envío pendiente</strong>: el evento está en cola, se le ha asociado una plantilla de mensaje y el envío se está procesando en ese momento.</p> </li> 
     <li> <p><strong>Enviado</strong>: este estado se copia desde los “logs” de envío. Significa que el envío se realizó.</p> </li> 
     <li> <p><strong>Envío ignorado</strong>: este estado se copia desde los “logs” de envío. Significa que el envío se ha ignorado.</p> </li> 
     <li> <p><strong>Error de envío</strong>: este estado se copia desde los “logs” de envío. Significa que el envío ha fallado.</p> </li> 
     <li> <p><strong>Evento no cubierto</strong>: el evento no se ha podido asociar con una plantilla de mensaje. El evento no se vuelve a procesar.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Procesamiento de eventos</span> por lotes <br /> </td> 
   <td> <span class="uicontrol">batchEventsProcessing</span><br /> </td> 
   <td> Este flujo de trabajo permite colocar eventos en lote en cola antes de asociarlos con una plantilla de mensaje. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Procesamiento de eventos</span> en tiempo real <br /> </td> 
   <td> <span class="uicontrol">rtEventsProcessing</span><br /> </td> 
   <td> Este flujo de trabajo permite colocar eventos en tiempo real en cola antes de asociarlos con una plantilla de mensaje. <br /> </td> 
  </tr> 
 </tbody> 
</table>

