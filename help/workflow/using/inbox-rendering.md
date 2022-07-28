---
product: campaign
title: Flujo de trabajo técnico de renderización de la bandeja de entrada
description: En esta sección se describe el flujo de trabajo técnico instalado con el paquete de renderización de la bandeja de entrada
feature: Workflows, Inbox Rendering
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: ht
source-wordcount: '75'
ht-degree: 100%

---


# Procesamiento de la bandeja de entrada (IR){#inbox-rendering}

![](../../assets/v7-only.svg)

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

