---
product: campaign
title: Adición de direcciones semilla
description: Adición de direcciones semilla
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
feature: Seed Address
role: User
exl-id: ae6eb4b0-b419-4661-9d63-e758f0242a0f
TQID: https://experienceleague.adobe.com/pVYaTG48-HiK0RwJXgBbIMWa-o-R7jlEpauXNXvGi5E
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
feature_v2: id: b631758a-142d-425f-b9aa-f756d85cb979id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2: id: e95a583b-fcfa-4524-8666-46a29c828119id: c8da4fdd-eb94-4751-a43c-f82733fb2d6eid: d5bbe3da-ba85-4242-817e-54f7c4b943e0id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 336
ht-degree: 91%

---

# Adición de direcciones semilla{#adding-seed-addresses}

## Direcciones semilla en una entrega {#seed-addresses-in-a-delivery}

Para añadir direcciones semilla específicas a una entrega, haga clic en el vínculo **[!UICONTROL To]** y después seleccione la pestaña **[!UICONTROL Seed addresses]**.

![](assets/s_ncs_user_edit_del_addresses_tab.png)

Hay tres modos de inserción posibles:

1. Introducción de direcciones semilla individuales.

   Para ello, haga clic en el botón **[!UICONTROL Add]** y defina el contenido de los campos de dirección. Repita este proceso con cada dirección.

1. Importación de plantillas de direcciones y adaptación a sus necesidades.

   Para ello, haga clic en el enlace **[!UICONTROL Import seed templates...]** y seleccione la carpeta que contiene las plantillas de dirección. Para obtener más información, consulte [esta sección](creating-seed-addresses.md#creating-seed-address-templates).

   Si es necesario, una vez añadidas, se puede hacer doble clic en ellas o hacer clic en el botón **[!UICONTROL Detail...]** para adaptar el contenido de cada dirección.

1. Creación de una condición para seleccionar de forma dinámica los directorios de control que desea insertar.

   Para ello, haga clic en el enlace **[!UICONTROL Edit the dynamic condition...]** e introduzca los parámetros de selección de las direcciones semilla. Por ejemplo, puede incluir todas las direcciones semilla que contenga una carpeta específica o las pertenecientes a un departamento específico de su organización.

   En esta sección se presenta un ejemplo de esto: [Caso de uso: selección de direcciones semilla en los criterios](use-case-selecting-seed-addresses-on-criteria.md).

>[!NOTE]
>
>Esta opción se usa cuando la tabla de destinatarios utilizada no es la tabla predeterminada **nms:recipient** y está usando la funcionalidad de procesamiento de la bandeja de entrada proporcionada con el módulo **[!UICONTROL Deliverability]** de Adobe Campaign.
>
>Para obtener más información, consulte [Uso de una tabla de destinatarios externa](using-an-external-recipient-table.md) y la documentación sobre la [Renderización de la bandeja de entrada](inbox-rendering.md).

Para las entregas, también se puede personalizar la forma en que se insertan las direcciones en los archivos de extracción. De forma predeterminada, se insertan en el orden de clasificación del archivo de salida, pero se puede elegir insertarlos al final o al principio del archivo o aleatoriamente entre los receptores del destino principal.

![](assets/s_ncs_user_edit_del_addresses_sort.png)

## Direcciones semilla en una campaña {#seed-addresses-in-a-campaign}

Para añadir direcciones semilla a un destinatario para una campaña, seleccione la operación y haga clic en la pestaña **[!UICONTROL Edit]**.

Haga clic en el enlace **[!UICONTROL Advanced campaign settings...]** y luego en la pestaña **[!UICONTROL Seed addresses]**, como se muestra a continuación:

![](assets/s_ncs_user_edit_op_addresses_tab.png)

Las direcciones semilla insertadas desde la campaña se añaden al objetivo de cada envío de la campaña.
