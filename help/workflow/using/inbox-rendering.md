---
title: Bandeja de entrada que procesa el flujo de trabajo técnico en Adobe Campaign Classic.
description: En esta sección se describe el flujo de trabajo técnico instalado con el paquete de procesamiento Bandeja de entrada en Adobe Campaign Classic.
page-status-flag: never-activated
uuid: f60a09f0-47a0-4fc0-b0ac-47178af6ad55
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: da0779dc-b734-483b-81e9-ff4706a2b6de
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '81'
ht-degree: 100%

---


# Renderización de la bandeja de entrada (IR){#inbox-rendering}

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
   <td> Este flujo de trabajo actualiza las direcciones de correo electrónico utilizadas para la renderización de la bandeja de entrada y solo funciona si el puerto HTTPS está abierto para <strong>deliverability.neolane.net</strong>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

