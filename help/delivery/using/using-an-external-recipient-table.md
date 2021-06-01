---
product: campaign
title: Uso de una lista de distribución externa
description: Uso de una lista de distribución externa
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
exl-id: b6aabc68-707d-4c6c-b008-277609166c6c
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 100%

---

# Uso de una lista de distribución externa{#using-an-external-recipient-table}

Si la lista de distribución es una tabla externa, debe realizar ajustes adicionales. Se debe ampliar el esquema **[!UICONTROL nms:seedmember]**. Se añade una pestaña a las direcciones sembradas para definir los campos adecuados, como se muestra a continuación:

![](assets/s_ncs_user_seedlist_new_tab.png)

En este caso, para añadir direcciones sembradas al envío, introduzca los campos adecuados directamente en la pestaña correspondiente o importe las plantillas de dirección:

![](assets/s_ncs_user_seedlist_add_new_tab.png)

La extensión del esquema **nms:seedMember** se encuentra en [esta sección](../../configuration/using/seed-addresses.md).
