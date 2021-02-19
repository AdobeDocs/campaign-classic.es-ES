---
solution: Campaign Classic
product: campaign
title: Power Booster y Power Cluster
description: Power Booster y Power Cluster
audience: installation
content-type: reference
topic-tags: deployment-types-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 6%

---


# Power Booster y Power Cluster{#power-booster-and-power-cluster}

## Información general {#overview}

Adobe Campaign le ofrece dos conjuntos de opciones de arquitectura preempaquetadas para dimensionar su implementación:

* **Ampliador de alimentación**

   Esta opción proporciona compatibilidad con una sola instancia de ejecución adicional disociada de la instancia de la aplicación Adobe Campaign principal. Las instancias de ejecución dedicadas se pueden alojar de forma remota o por terceros. Cuando se implementa, la ejecución por correo electrónico, el seguimiento, las páginas espejo y los mensajes de devolución se gestionan independientemente de las funciones centrales de la aplicación.

* **Clúster de energía**

   Esta opción proporciona compatibilidad con instancias de ejecución en clúster de 2 a N desacopladas de la instancia de la aplicación Adobe Campaign principal en relación con una aplicación determinada. Los clústeres se pueden alojar de forma remota, en implementaciones distribuidas y por terceros. Además de los beneficios del aislamiento de procesos, la opción Adobe Campaign Power Cluster permite la redundancia y amplía las estrategias utilizando hardware de productos básicos para una evolución simplificada del SLA o el performance.

![](assets/architectural_options_diagram.png)

## Aplicaciones aptas {#eligible-applications}

Las siguientes aplicaciones pueden utilizar las opciones Power Booster y Power Cluster:

* Campaña
* Envío
* Centro de mensajes

## Matriz de recomendaciones arquitectónicas {#matrix-of-architectural-recommendations}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Arquitectura estándar</strong><br /> </td> 
   <td> <strong>Ampliador de alimentación</strong><br /> </td> 
   <td> <strong>Clúster de energía</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Campañas por correo electrónico e interacciones de salida<br /> </td> 
   <td> Hasta aproximadamente 30 millones de correos electrónicos al mes<br /> </td> 
   <td> 30 a 100 millones de correos electrónicos al mes<br /> </td> 
   <td> Más de 100 millones de correos electrónicos al mes<br /> </td> 
  </tr> 
  <tr> 
   <td> Mensajes transaccionales<br /> </td> 
   <td> 50.000 por hora por servidor de ejecución<br /> </td> 
   <td> 50.000 por hora por servidor de ejecución<br /> </td> 
   <td> 50.000 por hora por servidor de ejecución<br /> </td> 
  </tr> 
  <tr> 
   <td> Disponibilidad<br /> </td> 
   <td> El de la base de datos principal<br /> </td> 
   <td> 24 horas al día, 7 días a la semana, excepto las ventanas de mantenimiento y los tiempos de inactividad de la instancia de ejecución<br /> </td> 
   <td> Servicio posible las 24 horas, los 7 días de la semana y los 365<br /> </td> 
  </tr> 
  <tr> 
   <td> Seguridad<br /> </td> 
   <td> El data mart es potencialmente accesible desde el internet público<br /> </td> 
   <td> El data mart está aislado de componentes frontales orientados a Internet<br /> </td> 
   <td> El data mart está aislado de componentes frontales orientados a Internet<br /> </td> 
  </tr> 
  <tr> 
   <td> Plantilla de implementación<br /> </td> 
   <td> Todo en un sitio (puede estar in situ o en la nube)<br /> </td> 
   <td> Comercialización in situ con ejecución en la nube posible<br /> </td> 
   <td> Mercadotecnia in situ con ejecución en la nube; ejecución en diferentes regiones posibles<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Recomendaciones {#recommendations}

* Una instancia de ejecución debe estar dedicada a un servicio. No puede instalar un paquete para un servicio al que no se ha suscrito. Por ejemplo: si se suscribe a la opción **Power Booster** para el servicio **Message Center**, sólo podrá instalar el paquete **[!UICONTROL Execution of transactional messages]** en la instancia de ejecución dedicada. Compruebe el acuerdo de licencia.
* Dado que las instancias dedicadas (o clústeres) son instancias de Adobe Campaign, las recomendaciones son las mismas que para una instancia principal. Para obtener más información sobre esto, consulte [este documento](../../production/using/foreword.md).
* Para configurar correctamente la instancia desde un punto de vista de componentes de base de datos/hardware, póngase en contacto con Adobe Campaign Professional Services.

