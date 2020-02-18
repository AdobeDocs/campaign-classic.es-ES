---
title: Power Booster y Power Cluster
seo-title: Power Booster y Power Cluster
description: Power Booster y Power Cluster
seo-description: null
page-status-flag: never-activated
uuid: 4d23ed42-a368-4bd6-afaf-48452e253d19
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: deployment-types-
discoiquuid: 715d2b69-5b47-4890-8b7d-1dc0a0d4ead8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c25e2a4f2280cdcc61e0522f8235149410b5dacf

---


# Power Booster y Power Cluster{#power-booster-and-power-cluster}

## Información general {#overview}

Adobe Campaign ofrece dos conjuntos de opciones de arquitectura preempaquetadas para dimensionar la implementación:

* **Ampliador de alimentación**

   Esta opción proporciona compatibilidad con una sola instancia de ejecución adicional separada de la instancia de aplicación principal de Adobe Campaign. Las instancias de ejecución dedicadas se pueden alojar de forma remota o por un tercero. Cuando se implementa, la ejecución por correo electrónico, el seguimiento, las páginas espejo y los mensajes de devolución se gestionan de forma independiente de las funciones centrales de la aplicación.

* **Clúster de energía**

   Esta opción proporciona compatibilidad con instancias de ejecución en clúster de 2 a N desacopladas de la instancia de aplicación principal de Adobe Campaign en relación con una aplicación determinada. Los clústeres se pueden alojar de forma remota, en implementaciones distribuidas y por terceros. Además de las ventajas del aislamiento de procesos, la opción Power Cluster de Adobe Campaign permite la redundancia y amplía las estrategias mediante el uso de hardware de productos básicos para una evolución simplificada del SLA o del rendimiento.

![](assets/architectural_options_diagram.png)

## Solicitudes admisibles {#eligible-applications}

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
   <td> Campañas de correo electrónico e interacciones salientes<br /> </td> 
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
   <td> 24 horas al día, 7 días a la semana, excepto las ventanas de mantenimiento y los tiempos de inactividad para la instancia de ejecución<br /> </td> 
   <td> Servicio posible las 24 horas, los 7 días de la semana y los 365 días del año<br /> </td> 
  </tr> 
  <tr> 
   <td> Seguridad<br /> </td> 
   <td> El mercado de datos es potencialmente accesible desde el internet público<br /> </td> 
   <td> El data mart está aislado de componentes frontales orientados a Internet<br /> </td> 
   <td> El data mart está aislado de componentes frontales orientados a Internet<br /> </td> 
  </tr> 
  <tr> 
   <td> Plantilla de implementación<br /> </td> 
   <td> Todo en un sitio (puede estar in situ o en la nube)<br /> </td> 
   <td> Marketing in situ con ejecución en la nube posible<br /> </td> 
   <td> Mercadotecnia in situ con ejecución en la nube; ejecución en diferentes regiones posibles<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Recomendaciones {#recommendations}

* Una instancia de ejecución debe estar dedicada a un servicio. No puede instalar un paquete para un servicio al que no se ha suscrito. Por ejemplo, si se suscribe a la opción **Power Booster** para el servicio **Message Center** **[!UICONTROL Execution of transactional messages]** , sólo podrá instalar el paquete en la instancia de ejecución dedicada. Compruebe el acuerdo de licencia.
* Dado que las instancias dedicadas (o clústeres) son instancias de Adobe Campaign, las recomendaciones son las mismas que para una instancia principal. For more on this, refer to [this document](../../production/using/foreword.md).
* Para configurar correctamente la instancia desde un punto de vista de componentes de hardware o base de datos, póngase en contacto con los servicios profesionales de Adobe Campaign.

