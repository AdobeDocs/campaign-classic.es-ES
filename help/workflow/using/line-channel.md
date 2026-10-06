---
product: campaign
title: Canal LINE
description: Canal LINE
hide: true
feature: Workflows
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 100%
---

# Canal LINE{#line-channel}



Los flujos de trabajo detallados a continuación se instalan con el módulo **canal LINE** de forma predeterminada. Para obtener más información sobre este módulo, consulte esta [sección](../../delivery/using/line-channel.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etiqueta</strong><br /> </td> 
   <td> <strong>Nombre interno</strong><br /> </td> 
   <td> <strong>Descripción</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">LINE V2 access token update</span> <br /> </td> 
   <td> <span class="uicontrol">updateLineV2AccessToken</span> <br /> </td> 
   <td> Este flujo de trabajo actualiza el token de acceso a LINE V2.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Delete blocked LINE users</span> <br /> </td> 
   <td> <span class="uicontrol">deleteBlockedLineUsersV2</span> <br /> </td> 
   <td> Este flujo de trabajo garantiza que los datos de los usuarios de LINE V2 se eliminen después de haber bloqueado la cuenta oficial de LINE durante 180 días.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MID to LineUserID migration</span> <br /> </td> 
   <td> <span class="uicontrol">MIDToUserIDMigration</span> <br /> </td> 
   <td> Este flujo de trabajo genera las ID de los usuarios de LINE V2 para la migración de LINE V1 a LINE V2.<br /> </td> 
  </tr> 
 </tbody> 
</table>

