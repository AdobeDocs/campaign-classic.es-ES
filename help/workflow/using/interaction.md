---
title: Interacción
seo-title: Interacción
description: Interacción
seo-description: null
page-status-flag: never-activated
uuid: 5c8e2353-bb76-4e8d-95d7-61b6c111b6b3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: 1683477a-9233-4a25-b0d0-0c81051eb440
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: b1a961822224ab0a9551f51942a5f94cf201c8ee
workflow-type: ht
source-wordcount: '100'
ht-degree: 100%

---


# Interacción{#interaction}

El flujo de trabajo detallado a continuación se instala con el módulo **Offer engine (Interaction)** de forma predeterminada. Para obtener más información sobre este módulo, consulte esta [sección](../../interaction/using/interaction-and-offer-management.md).

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
   <td> Este flujo de trabajo actualiza el acumulado <strong>Completo</strong> del cubo <strong>Propuesta de oferta. </strong> Se activa todos los días a las 6 a. m. de manera predeterminada. Este acumulado captura las siguientes dimensiones: Canal, Entrega, Oferta de mercadotecnia y Fecha.<br /> Luego se utiliza el cubo <strong>Propuesta de oferta</strong> para generar informes basados en ofertas. Puede obtener más información sobre los cubos en <a href="../../reporting/using/about-cubes.md">esta sección</a>.<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">MessageCenter full aggregate calculation</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

