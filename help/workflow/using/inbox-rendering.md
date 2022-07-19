---
product: campaign
title: Flujo de trabajo técnico de renderización de la bandeja de entrada
description: En esta sección se describe el flujo de trabajo técnico instalado con el paquete de renderización de la bandeja de entrada
feature: Workflows, Inbox Rendering
source-git-commit: 378788764e244dcad12018d6d703048707d4c3e6
workflow-type: tm+mt
source-wordcount: '75'
ht-degree: 70%

---


# Procesamiento de la bandeja de entrada (IR){#inbox-rendering}

![](../../assets/common.svg)

El flujo de trabajo detallado a continuación se instala con el módulo **Renderización de la bandeja de entrada (IR)** de forma predeterminada. Para obtener más información sobre Renderización de la bandeja de entrada, consulte esta [sección](../../delivery/using/inbox-rendering.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etiqueta</strong><br /> </td> 
   <td> <strong>Nombre interno</strong><br /> </td> 
   <td> <strong>Descripción</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Actualizar la red semilla para la renderización de la bandeja de entrada</strong><br /> </td> 
   <td> <span class="uicontrol">updateRenderingSeeds</span><br /> </td> 
   <td> Este flujo de trabajo actualiza las direcciones de correo electrónico utilizadas para la renderización de la bandeja de entrada y solo funciona si el puerto HTTPS está abierto para <strong>https://deliverability-app.neolane.net/deliverability</strong>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

