---
product: campaign
title: Transfer to Mid-sourcing
description: Descubra más información sobre los flujos de trabajo Transfer to Mid-sourcing
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
source-wordcount: '115'
ht-degree: 100%
---

# Transferir a intermediario{#transfer-to-mid-sourcing}



Los flujos de trabajo detallados a continuación se instalan con el módulo **Transferir a intermediario** de forma predeterminada. Para obtener más información sobre este módulo, consulte la [Guía de instalación de Campaign Classic v7](../../installation/using/mid-sourcing-deployment.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etiqueta</strong><br /> </td> 
   <td> <strong>Nombre interno</strong><br /> </td> 
   <td> <strong>Descripción</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Mid-sourcing (delivery counters)</span> <br /> </td> 
   <td> <span class="uicontrol">defaultMidSourcingDlv</span> <br /> </td> 
   <td> <p>Este flujo de trabajo recopila información de recuento para las entregas en el servidor de mid-sourcing. La información de recuento incluye indicadores de entrega generales como el número de envíos realizados, etc.</p> <p>No se incluye la información de seguimiento como las aperturas.</p> <p>De forma predeterminada, se activa cada diez minutos.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Mid-sourcing (delivery logs)</span> <br /> </td> 
   <td> <span class="uicontrol">defaultMidSourcingLog</span> <br /> </td> 
   <td> Este flujo de trabajo recopila los registros de envío en el servidor intermediario. Se activa cada hora de forma predeterminada.<br /> </td> 
  </tr> 
 </tbody> 
</table>

