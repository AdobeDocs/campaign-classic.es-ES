---
product: campaign
title: Interacción
description: Interacción
hide: true
feature: Workflows, Interaction, Offers
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 65702805-0026-5ca1-843a-144fa79f0883
    internal-label: Interaction
  - id: ea08db70-4682-59a2-9408-9aedd9548e07
    internal-label: Offers
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 100%
---

# Interacción{#interaction}



Los flujos de trabajo detallados a continuación se instalan con el complemento **Motor de ofertas (Interacción)** de forma predeterminada.

Para obtener más información, consulte estas secciones en función de la versión de Campaign:

![](assets/do-not-localize/v7.jpeg)[Documentación de Campaign v7](../../interaction/using/interaction-and-offer-management.md)

![](assets/do-not-localize/v8.png)[Documentación de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/interaction/interaction.html?lang=es)


<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etiqueta</strong><br /> </td> 
   <td> <strong>Nombre interno</strong><br /> </td> 
   <td> <strong>Descripción</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Full aggregate calculation (propositionrcp cube)</span> <br /> </td> 
   <td> <span class="uicontrol">agg_nmspropositionrcp_full</span><br /> </td> 
   <td> Este flujo de trabajo actualiza el acumulado <strong>Completo</strong> del cubo <strong>Propuesta de oferta. </strong> Se activa todos los días a las 6 a. m. de manera predeterminada. Este agregado captura las siguientes dimensiones: canal, envío, oferta de marketing y fecha.<br /> A continuación, el cubo <strong>proposición de oferta</strong> se utiliza para generar informes basados en ofertas. Puede obtener más información sobre los cubos en <a href="../../reporting/using/ac-cubes.md">esta sección</a>.<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">MessageCenter full aggregate calculation</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> Este flujo de trabajo actualiza el acumulado <strong>Completo</strong> del cubo <strong>Centro de mensajes</strong>. Se activa cada día a las 3 de la mañana de forma predeterminada. Este agregado captura las siguientes dimensiones: canal, fecha, estado y tipo de evento.<br /> A continuación, el <strong>Centro de mensajes</strong> se utiliza para generar informes basados en eventos. Puede obtener más información sobre los cubos en <a href="../../reporting/using/ac-cubes.md">esta sección</a>.<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

