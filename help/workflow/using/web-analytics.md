---
solution: Campaign Classic
product: campaign
title: Web Analytics
description: Descubra más información sobre el paquete Web Analytics
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 100%

---


# Web Analytics{#web-analytics}

Los flujos de trabajo detallados a continuación se instalan con el módulo **Conectores web de Analytics** de forma predeterminada. Para obtener más información sobre este módulo, consulte esta [sección](../../platform/using/adobe-analytics-data-connector.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etiqueta</strong><br /> </td> 
   <td> <strong>Nombre interno</strong><br /> </td> 
   <td> <strong>Descripción</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Sending of indicators and campaign attributes</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsSendMetrics</span><br /> </td> 
   <td> Este flujo de trabajo permite enviar indicadores de campaña por correo electrónico desde Adobe Campaign a Adobe Experience Cloud Suite a través del conector Adobe® Genesis. Los indicadores correspondientes son los siguientes: <strong>Sent</strong> (iSent), <strong>Total count of opens</strong> (iTotalRecipientOpen), <strong>Total number of recipients who clicked</strong> (iTotalRecipientClick), <strong>Errors</strong> (iError), <strong>Opt-Out</strong> (opt-out) (iOptOut).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Identification of converted contacts</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span><br /> </td> 
   <td> Este flujo de trabajo lista a los visitantes del sitio que han finalizado su compra después de la campaña de remarketing. Los datos recopilados por este flujo de trabajo se pueden consultar en <span class="uicontrol">Re-marketing efficiency report</span> (consulte esta <a href="../../platform/using/adobe-analytics-data-connector.md#creating-a-re-marketing-campaign">página</a>). <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Event purge</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsPurgeWebEvents</span><br /> </td> 
   <td> Este flujo de trabajo permite eliminar todos los eventos del campo de base de datos según el periodo configurado en el campo <span class="uicontrol">Lifespan</span>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Recovery of web events</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsGetWebEvents</span><br /> </td> 
   <td> Cada hora, este flujo de trabajo descarga segmentos sobre el comportamiento de los usuarios de Internet en un sitio determinado, los integra en la base de datos de Adobe Campaign e inicia el flujo de trabajo de remarketing. <br /> </td> 
  </tr> 
 </tbody> 
</table>

