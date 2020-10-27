---
title: Datos de personalización
seo-title: Datos de personalización
description: Datos de personalización
seo-description: null
page-status-flag: never-activated
uuid: d3d66216-502a-410b-b062-fb413eb9363f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 2cd8a320-37e8-410a-b71b-0c13c8e15482
translation-type: tm+mt
source-git-commit: 95dff2f3704e316e9ec9e454a8f3fb9835508ccd
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 100%

---


# Datos de personalización{#personalization-data}

Es posible utilizar los datos en la plantilla de mensaje para probar la personalización del mensaje transaccional. Esta funcionalidad se utiliza para generar una vista previa o enviar una prueba. Si instala el módulo **Envío**, estos datos le permiten mostrar un procesamiento de los mensajes para varios proveedores de acceso a Internet (**Procesamiento de la bandeja de entrada**: para obtener más información, consulte [esta sección](../../delivery/using/inbox-rendering.md)).

La finalidad de estos datos es probar los mensajes antes de la entrega final. Estos mensajes no coinciden con los datos reales que procesa el Centro de mensajería. Sin embargo, la estructura XML debe ser idéntica a la del evento almacenado en la instancia de ejecución, como se muestra a continuación.

![](assets/messagecenter_create_custo_006.png)

Esta información le permite personalizar el contenido del mensaje mediante etiquetas de personalización (para obtener más información, consulte [Creación del contenido de un mensaje.](../../message-center/using/creating-message-content.md)).

1. En la plantilla del mensaje, haga clic en la pestaña **[!UICONTROL Seed addresses]**.
1. En el contenido del evento, introduzca la información de prueba en formato XML.

   ![](assets/messagecenter_create_custo_001.png)
