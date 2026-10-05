---
product: campaign
title: Análisis web
description: Descubra más información sobre el paquete Web Analytics
hide: true
feature: Workflows, Analytics Integration
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
    internal-label: Integrations
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
    internal-label: Analytics integration
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 100%
---

# Análisis web{#web-analytics}



Los flujos de trabajo detallados a continuación se instalan con el módulo **Conectores web de Analytics** de forma predeterminada. Para obtener más información sobre este módulo, consulte esta [sección](../../integrations/using/gs-aa.md).

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
   <td> Este flujo de trabajo permite enviar indicadores de campaña de correo electrónico desde Adobe Campaign a Adobe Experience Cloud Suite a través del conector de Adobe® Analytics. Los indicadores correspondientes son los siguientes: <strong>Sent</strong> (iSent), <strong>Total count of opens</strong> (iTotalRecipientOpen), <strong>Total number of recipients who clicked</strong> (iTotalRecipientClick), <strong>Errors</strong> (iError), <strong>Opt-Out</strong> (opt-out) (iOptOut).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Identification of converted contacts</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span><br /> </td> 
   <td> Este flujo de trabajo lista a los visitantes del sitio que han finalizado su compra después de la campaña de remarketing. Los datos recopilados por este flujo de trabajo se pueden consultar en el <span class="uicontrol">Informe de eficiencia de remarketing</span>. <br /> </td> 
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

