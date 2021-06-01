---
product: campaign
title: Actualización de la consola
description: Actualización de la consola
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 10%

---

# Actualización de la consola{#console-update}

Si ha seleccionado la opción **[!UICONTROL Do not request console update]** y desea reactivar la solicitud de actualización, siga el siguiente procedimiento:

1. Abra el editor de la base de datos del Registro utilizando el comando **regedit** en el menú Windows **[!UICONTROL Start > Execute]**.

   ![](assets/ncs_console_update_1.png)

1. En el árbol, muestre las opciones del nodo **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]**.
1. Elimine la entrada **[!UICONTROL confAdvisedUpgrade]** y cierre el editor del Registro.

   ![](assets/ncs_console_update_2.png)
