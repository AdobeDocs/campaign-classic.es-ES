---
product: campaign
title: Power Booster y Power Cluster
description: Power Booster y Power Cluster
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 59364cfc-9917-4057-ad5f-fbca7e261b07
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 6%

---

# Power Booster y Power Cluster{#power-booster-and-power-cluster}

## Información general {#overview}

Adobe Campaign le ofrece dos conjuntos de opciones de arquitectura preempaquetadas para dimensionar su implementación:

* **Power Booster**

   Esta opción proporciona compatibilidad con una sola instancia de ejecución adicional disociada de la instancia principal de la aplicación Adobe Campaign. Las instancias de ejecución dedicadas se pueden alojar de forma remota o por terceros. Cuando se implementa, la ejecución por correo electrónico, el seguimiento, las páginas espejo y los mensajes de rechazo se gestionan de forma independiente de las funciones de la aplicación central.

* **Power Cluster**

   Esta opción proporciona compatibilidad con instancias de ejecución en clúster de 2 a N disociadas de la instancia principal de la aplicación Adobe Campaign en relación con una aplicación determinada. Los clústeres se pueden alojar de forma remota, en implementaciones distribuidas y por terceros. Además de los beneficios del aislamiento de procesos, la opción Adobe Campaign Power Cluster permite la redundancia y la ampliación de estrategias utilizando hardware de productos básicos para una evolución simplificada del SLA o el performance.

![](assets/architectural_options_diagram.png)

## Aplicaciones aptas {#eligible-applications}

Las opciones Power Booster y Power Cluster pueden ser utilizadas por las siguientes aplicaciones:

* Campaña
* Entrega
* Centro de mensajes

## Matriz de recomendaciones arquitectónicas {#matrix-of-architectural-recommendations}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Arquitectura estándar</strong><br /> </td> 
   <td> <strong>Power Booster</strong><br /> </td> 
   <td> <strong>Power Cluster</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Campañas de correo electrónico e interacciones salientes<br /> </td> 
   <td> Hasta aproximadamente 30 millones de correos electrónicos al mes<br /> </td> 
   <td> De 30 a 100 millones de correos electrónicos al mes<br /> </td> 
   <td> Más de 100 millones de correos electrónicos al mes<br /> </td> 
  </tr> 
  <tr> 
   <td> Mensajes transaccionales<br /> </td> 
   <td> 50 000 por hora por servidor de ejecución<br /> </td> 
   <td> 50 000 por hora por servidor de ejecución<br /> </td> 
   <td> 50 000 por hora por servidor de ejecución<br /> </td> 
  </tr> 
  <tr> 
   <td> Disponibilidad<br /> </td> 
   <td> El de la base de datos principal<br /> </td> 
   <td> 24/7 excepto las ventanas de mantenimiento y los tiempos de inactividad para la instancia de ejecución<br /> </td> 
   <td> 24/7/365 servicio posible<br /> </td> 
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
   <td> Marketing local con ejecución en la nube posible<br /> </td> 
   <td> Marketing local con ejecución en la nube; ejecución en diferentes geos posible<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Recomendaciones {#recommendations}

* Una instancia de ejecución debe estar dedicada a un servicio. No puede instalar un paquete para un servicio al que no se ha suscrito. Por ejemplo, si se suscribe a la opción **Power Booster** para el servicio **Message Center**, solo puede instalar el paquete **[!UICONTROL Execution of transactional messages]** en la instancia de ejecución dedicada. Compruebe el acuerdo de licencia.
* Dado que las instancias (o clústeres) dedicadas son instancias de Adobe Campaign, las recomendaciones son las mismas que para una instancia principal. Para obtener más información, consulte [este documento](../../production/using/foreword.md).
* Para configurar correctamente la instancia desde el punto de vista de los componentes de hardware/base de datos, póngase en contacto con Adobe Campaign Professional Services.
