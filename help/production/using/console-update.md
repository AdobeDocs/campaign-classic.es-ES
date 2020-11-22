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

Si ha seleccionado la **[!UICONTROL Do not request console update]** opción y desea reactivar la solicitud de actualización, siga el procedimiento siguiente:

1. Abra el editor de la base de datos del Registro mediante el comando **regedit** en el **[!UICONTROL Start > Execute]** menú de Windows.

   ![](assets/ncs_console_update_1.png)

1. En el árbol, muestre las opciones del **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** nodo.
1. Elimine la **[!UICONTROL confAdvisedUpgrade]** entrada y cierre el editor del Registro.

   ![](assets/ncs_console_update_2.png)

