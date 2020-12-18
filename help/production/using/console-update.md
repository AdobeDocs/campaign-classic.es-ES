---
solution: Campaign Classic
product: campaign
title: Actualización de la consola
description: Actualización de la consola
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 10%

---


# Actualización de la consola{#console-update}

Si seleccionó la opción **[!UICONTROL Do not request console update]** y desea reactivar la solicitud de actualización, aplique el procedimiento siguiente:

1. Abra el editor de la base de datos del Registro mediante el comando **regedit** del menú de Windows **[!UICONTROL Start > Execute]**.

   ![](assets/ncs_console_update_1.png)

1. En el árbol, muestre las opciones del nodo **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]**.
1. Elimine la entrada **[!UICONTROL confAdvisedUpgrade]** y cierre el editor del Registro.

   ![](assets/ncs_console_update_2.png)

