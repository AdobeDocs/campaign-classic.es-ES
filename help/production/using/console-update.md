---
product: campaign
title: Actualización de la consola
description: Actualización de la consola
feature: Monitoring, Upgrade
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '62'
ht-degree: 20%

---

# Actualización de la consola{#console-update}



Si seleccionó la **[!UICONTROL Do not request console update]** y desea reactivar la solicitud de actualización, siga el siguiente procedimiento:

1. Abra el editor de la base de datos del Registro mediante el **regedit** en el menú Windows **[!UICONTROL Start > Execute]** menú.

   ![](assets/ncs_console_update_1.png)

1. En el árbol, muestre las opciones del **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** nodo.
1. Elimine el **[!UICONTROL confAdvisedUpgrade]** y cierre el Editor del Registro.

   ![](assets/ncs_console_update_2.png)
