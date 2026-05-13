---
product: campaign
title: Power Booster y Power Cluster
description: Power Booster y Power Cluster
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 59364cfc-9917-4057-ad5f-fbca7e261b07
TQID: https://experienceleague.adobe.com/lcr5Xfipd9cDuglWBqBsiVXJUUZqQxLEmzzZPrAEhHU
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: a7760dfc-5c44-4d77-bb68-c50b1e265c93
subfeature_v2: id: ac9c0a9c-8a76-4419-bd64-9c34c5782666id: fb2a841f-c522-491f-9901-a1b939d252df
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080bid: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 412
ht-degree: 6%

---

# Power Booster y Power Cluster{#power-booster-and-power-cluster}



## Información general {#overview}

Adobe Campaign proporciona dos conjuntos de opciones de arquitectura empaquetadas previamente para dimensionar la implementación:

* **Power Booster**

  Esta opción proporciona compatibilidad con una única instancia de ejecución adicional disociada de la instancia de aplicación principal de Adobe Campaign. Las instancias de ejecución dedicadas se pueden alojar de forma remota o por un tercero. Cuando se implementa, la ejecución por correo electrónico, el seguimiento, las páginas espejo y los mensajes de devolución se gestionan de forma independiente de las funciones de la aplicación central.

* **Clúster de energía**

  Esta opción es compatible con instancias de ejecución en clúster de 2 a N disociadas de la instancia de aplicación de Adobe Campaign principal en relación con una aplicación determinada. Los clústeres se pueden alojar de forma remota, en implementaciones distribuidas y por terceros. Además de las ventajas del aislamiento de procesos, la opción Adobe Campaign Power Cluster permite la redundancia y las estrategias de ampliación mediante el uso de hardware básico para simplificar la evolución de SLA o el rendimiento.

![](assets/architectural_options_diagram.png)

## Solicitudes elegibles {#eligible-applications}

Las opciones Power Booster y Power Cluster se pueden utilizar en las siguientes aplicaciones:

* Campaña
* Envío
* Centro de mensajes

## Matriz de recomendaciones arquitectónicas {#matrix-of-architectural-recommendations}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Arquitectura estándar</strong><br /> </td> 
   <td> <strong>Power Booster</strong><br /> </td> 
   <td> <strong>Clúster de energía</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Campañas de correo electrónico e interacciones salientes<br /> </td> 
   <td> Hasta aproximadamente 30 millones de correos electrónicos al mes<br /> </td> 
   <td> De 30 a 100 millones de correos electrónicos al mes<br /> </td> 
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
   <td> La de la base de datos principal <br /> </td> 
   <td> 24/7 excepto ventanas de mantenimiento y tiempos de inactividad para la instancia de ejecución <br /> </td> 
   <td> Servicio posible el 24/7/365<br /> </td> 
  </tr> 
  <tr> 
   <td> Seguridad<br /> </td> 
   <td> Se puede acceder potencialmente a Data Mart desde el Internet público<br /> </td> 
   <td> Data Mart está aislado de los componentes frontales orientados a Internet <br /> </td> 
   <td> Data Mart está aislado de los componentes frontales orientados a Internet <br /> </td> 
  </tr> 
  <tr> 
   <td> Plantilla de implementación <br /> </td> 
   <td> Todo en un sitio (puede ser local o en la nube)<br /> </td> 
   <td> Marketing local con ejecución posible en la nube<br /> </td> 
   <td> Marketing local con ejecución en la nube; ejecución en diferentes geos posible<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Recomendaciones {#recommendations}

* Una instancia de ejecución debe estar dedicada a un servicio. No puede instalar un paquete para un servicio al que no se ha suscrito. Por ejemplo, si se suscribe a la opción **Power Booster** para el servicio **Message Center**, solo puede instalar el paquete **[!UICONTROL Execution of transactional messages]** en la instancia de ejecución dedicada. Compruebe el acuerdo de licencia.
* Dado que las instancias dedicadas (o clústeres) son instancias de Adobe Campaign, las recomendaciones son las mismas que para una instancia principal. Para obtener más información, consulte [este documento](../../production/using/foreword.md).
* Para configurar correctamente la instancia desde el punto de vista de los componentes de base de datos/hardware, póngase en contacto con Adobe Campaign Professional Services.
