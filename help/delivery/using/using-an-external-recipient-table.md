---
product: campaign
title: Uso de una lista de destinatarios externa
description: Uso de una lista de destinatarios externa
badge-v8: label="También se aplica a la versión 8" type="Positive" tooltip="También se aplica a Campaign v8"
feature: Audiences
exl-id: b6aabc68-707d-4c6c-b008-277609166c6c
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 95%

---

# Uso de una lista de destinatarios externa{#using-an-external-recipient-table}



Si la lista de distribución es una tabla externa, debe realizar ajustes adicionales. Se debe ampliar el esquema **[!UICONTROL nms:seedmember]**. Se añade una pestaña a las direcciones sembradas para definir los campos adecuados, como se muestra a continuación:

![](assets/s_ncs_user_seedlist_new_tab.png)

En este caso, para añadir direcciones sembradas al envío, introduzca los campos adecuados directamente en la pestaña correspondiente o importe las plantillas de dirección:

![](assets/s_ncs_user_seedlist_add_new_tab.png)

La extensión del esquema **nms:seedMember** se encuentra en [esta sección](../../configuration/using/seed-addresses.md).
