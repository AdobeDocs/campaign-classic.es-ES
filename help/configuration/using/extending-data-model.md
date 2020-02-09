---
title: Uso de la tabla Destinatarios de Adobe Campaign Classic
description: Descubra cómo utilizar la tabla de destinatarios lista para usar en Adobe Campaign Classic al diseñar su modelo de datos.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 65affa58a66090c3bffc837fdbd85aa46338bd3e

---


# Ampliación del modelo de datos{#extending-data-model}

Al empezar con Adobe Campaign, debe evaluar el modelo de datos predeterminado para comprobar qué tabla es la más adecuada para almacenar los datos de marketing.

Si es relevante, puede utilizar la tabla Destinatario predeterminada con los campos predeterminados, como se describe en esta [sección](../../configuration/using/default-recipient-table.md).

Si es necesario, puede ampliarlo con dos mecanismos:

* Extender una tabla existente con campos nuevos. Por ejemplo, puede agregar un nuevo campo &quot;Lealtad&quot; a la tabla Destinatario.
* Cree una nueva tabla, por ejemplo una tabla de &quot;Compra&quot; que enumere todas las compras realizadas por cada perfil de la base de datos y vincúlelo a la tabla Destinatario.

Para obtener más información sobre la configuración de esquemas de extensión para ampliar el modelo de datos conceptuales, consulte [Acerca de la edición](../../configuration/using/about-schema-edition.md)de esquemas.

>[!IMPORTANT]
>
>La ampliación del modelo de datos está reservada para usuarios avanzados.
