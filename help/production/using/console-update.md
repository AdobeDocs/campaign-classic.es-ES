---
title: Actualización de la consola
seo-title: Actualización de la consola
description: Actualización de la consola
seo-description: null
page-status-flag: never-activated
uuid: d2193d4f-b98c-47b1-88f1-7e5ccf4c453c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 9281808b-1c2f-4095-9051-f181f089f205
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '57'
ht-degree: 14%

---


# Actualización de la consola{#console-update}

Si ha seleccionado la **[!UICONTROL Do not request console update]** opción y desea reactivar la solicitud de actualización, siga el procedimiento siguiente:

1. Abra el editor de la base de datos del Registro mediante el comando **regedit** en el **[!UICONTROL Start > Execute]** menú de Windows.

   ![](assets/ncs_console_update_1.png)

1. En el árbol, muestre las opciones del **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** nodo.
1. Elimine la **[!UICONTROL confAdvisedUpgrade]** entrada y cierre el editor del Registro.

   ![](assets/ncs_console_update_2.png)

