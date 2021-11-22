---
product: campaign
title: Actualización de la consola
description: Actualización de la consola
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 10%

---

# Actualización de la consola{#console-update}

![](../../assets/v7-only.svg)

Si seleccionó la variable **[!UICONTROL Do not request console update]** y desea reactivar la solicitud de actualización, aplique el siguiente procedimiento:

1. Abra el editor de la base de datos del Registro utilizando la **regedit** en Windows **[!UICONTROL Start > Execute]** para abrir el Navegador.

   ![](assets/ncs_console_update_1.png)

1. En el árbol, muestre las opciones de **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** nodo .
1. Elimine el **[!UICONTROL confAdvisedUpgrade]** y cierre el editor del Registro.

   ![](assets/ncs_console_update_2.png)
