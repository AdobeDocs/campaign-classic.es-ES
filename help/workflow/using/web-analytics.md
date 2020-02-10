---
title: Web Analytics
seo-title: Web Analytics
description: Web Analytics
seo-description: null
page-status-flag: never-activated
uuid: 63742453-16d9-48c2-9a3d-d96f5b131fb3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: cc2d4741-2b26-4933-a28d-5dd7b5f436be
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Web Analytics{#web-analytics}

Los flujos de trabajo detallados a continuación se instalan con el módulo **Conectores web de
				Analytics** de forma predeterminada. Para obtener más información sobre este módulo, consulte esta [sección](../../platform/using/adobe-analytics-data-connector.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etiqueta</strong><br /> </td> 
   <td> <strong>Nombre
								 interno</strong><br /> </td> 
   <td> <strong>Descripción</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Envío de indicadores y atributos</span> de campaña <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsSendMetrics</span><br /> </td> 
   <td> Este flujo de trabajo permite enviar indicadores de campaña por correo electrónico desde Adobe Campaign
								a Adobe Experience Cloud Suite a través del conector Adobe® Genesis. The indicators concerned are as follows: <strong>Sent</strong> (iSent), <strong>Total count of opens</strong> (iTotalRecipientOpen), <strong>Total number of recipients who clicked</strong> (iTotalRecipientClick), <strong>Errors</strong> (iError), <strong>Opt-Out</strong> (opt-out) (iOptOut).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Identificación de los contactos</span> convertidos <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span><br /> </td> 
   <td> Este flujo de trabajo lista a los visitantes del sitio que han finalizado su compra después de la campaña de remarketing. The data recovered by this workflow can be accessed in the <span class="uicontrol">Re-marketing efficiency report</span> (Refer to this <a href="../../platform/using/adobe-analytics-data-connector.md#creating-a-re-marketing-campaign"> page</a>). <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Purga</span> de eventos <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsPurgeWebEvents</span><br /> </td> 
   <td> This workflow lets you delete every event from the database field according to the period configured in the <span class="uicontrol">Lifespan</span> field. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Recuperación de eventos</span> Web <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsGetWebEvents</span><br /> </td> 
   <td> Cada hora, este flujo de trabajo descarga segmentos sobre el comportamiento de los usuarios de Internet en un sitio determinado, los integra en la base de datos de Adobe Campaign e inicia el flujo de trabajo de remarketing. <br /> </td> 
  </tr> 
 </tbody> 
</table>

