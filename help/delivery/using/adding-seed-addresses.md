---
title: Adición de direcciones sembradas
seo-title: Adición de direcciones sembradas
description: Adición de direcciones sembradas
seo-description: null
page-status-flag: never-activated
uuid: e94ddd46-bed6-4505-91b7-7e17abb0e9c8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: 0b9b53bf-4dd2-416c-894e-393aded489f8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# Adición de direcciones sembradas{#adding-seed-addresses}

## Direcciones sembradas en un envío {#seed-addresses-in-a-delivery}

To add specific seed addresses for a delivery, click the **[!UICONTROL To]** link, then select the **[!UICONTROL Seed addresses]** tab.

![](assets/s_ncs_user_edit_del_addresses_tab.png)

Hay tres modos de inserción posibles:

1. Introducción de direcciones sembradas individuales.

   To do this, click the **[!UICONTROL Add]** button and define the content of the address fields. Repita este proceso para cada dirección. Para obtener más información, consulte [esta sección](../../message-center/using/managing-seed-addresses-in-transactional-messages.md#creating-a-seed-address).

1. Importación de plantillas de direcciones y adaptación a sus necesidades.

   To do this, click the **[!UICONTROL Import seed templates...]** link and select the folder which contains the address templates. Para obtener más información sobre este tema, consulte [Creación de plantillas](../../delivery/using/creating-seed-addresses.md#creating-seed-address-templates)de direcciones de raíz.

   If necessary, once they are added, you can doucle-click them or click the **[!UICONTROL Detail...]** button to adapt the content of each address.

1. Creación de una condición para seleccionar de forma dinámica los directorios de control que desea insertar.

   To do this, click the **[!UICONTROL Edit the dynamic condition...]** link, then enter the seed address selection parameters. Por ejemplo, puede incluir todas las direcciones sembradas que contenga una carpeta específica o las pertenecientes a un departamento específico de su organización.

   En esta sección se presenta un ejemplo de esto: Caso [de uso: seleccionar direcciones de raíz en los criterios](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md).

>[!NOTE]
>
>This option is used when the recipient table used is not the default **nms:recipient** table and you are using the Inbox Rendering functionality provided with Adobe Campaign&#39;s **[!UICONTROL Deliverability]** module.
>
>Para obtener más información sobre esto, consulte [Uso de una tabla](../../delivery/using/using-an-external-recipient-table.md) de destinatarios externa y la documentación sobre el procesamiento [de la](../../delivery/using/inbox-rendering.md)Bandeja de entrada.

Para los envíos, también se puede personalizar la forma en que se insertan las direcciones en los archivos de extracción. De forma predeterminada, se insertan en el orden de clasificación del archivo de salida, pero se puede elegir insertarlos al final o al principio del archivo o aleatoriamente entre los receptores del destino principal.

![](assets/s_ncs_user_edit_del_addresses_sort.png)

## Direcciones sembradas en una campaña {#seed-addresses-in-a-campaign}

To add seed addresses to a target for a campaign, select the operation and click the **[!UICONTROL Edit]** tab.

Haga clic en el **[!UICONTROL Advanced campaign settings...]** vínculo y, a continuación, en la **[!UICONTROL Seed addresses]** ficha, como se muestra a continuación:

![](assets/s_ncs_user_edit_op_addresses_tab.png)

Las direcciones sembradas insertadas desde la campaña se añaden al objetivo de cada envío de la campaña.
