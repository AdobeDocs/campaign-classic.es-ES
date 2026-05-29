---
product: campaign
title: Actualización de la consola
description: Actualización de la consola
feature: Monitoring, Upgrade
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
TQID: https://experienceleague.adobe.com/oNVXa9DaMu-b-GpfxT-Z0jFbWEd-MnsSzu8Jdb0S0Fw
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
feature_v2: []
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 55
ht-degree: 10%

---

# Actualización de la consola{#console-update}



Si seleccionó la opción **[!UICONTROL Do not request console update]** y desea reactivar la solicitud de actualización, aplique el procedimiento siguiente:

1. Abra el editor de la base de datos del Registro con el comando **regedit** del menú Windows **[!UICONTROL Start > Execute]**.

   ![](assets/ncs_console_update_1.png)

1. En el árbol, muestre las opciones del nodo **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]**.
1. Elimine la entrada **[!UICONTROL confAdvisedUpgrade]** y cierre el editor del Registro.

   ![](assets/ncs_console_update_2.png)
