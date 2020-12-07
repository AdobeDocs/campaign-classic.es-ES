---
solution: Campaign Classic
product: campaign
title: Interacción
description: Interacción
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: ht
source-git-commit: affc541c480ad7e618120fe90270841add06b711
workflow-type: ht
source-wordcount: '153'
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
   <td> Este flujo de trabajo actualiza el acumulado <strong>Completo</strong> del cubo <strong>Centro de mensajes</strong>. Se activa cada día a la 3 de la mañana de forma predeterminada. Este acumulado captura las siguientes dimensiones: canal, fecha, estado y tipo de evento.<br /> Luego se utiliza el cubo <strong>Centro de mensajes</strong> para generar informes basados en eventos. Puede obtener más información sobre los cubos en <a href="../../reporting/using/about-cubes.md">esta sección</a>.<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

