---
title: Acerca del editor HTML de Campaign
seo-title: Acerca del editor HTML de Campaign
description: Acerca del editor HTML de Campaign
seo-description: null
page-status-flag: never-activated
uuid: 1b1d392d-4f19-4092-b57d-02051a242675
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: editing-html-content
discoiquuid: 1ffe9f58-7258-4794-a314-524065f8a33b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# Acerca del editor HTML de Campaign{#about-campaign-html-editor}

El **editor de contenido (DCE)** es un editor de contenido HTML que permite crear o modificar fácilmente plantillas o contenido en formato HTML dentro de Adobe Campaign.

El editor de contenido permite insertar y dar formato a elementos de página y asociar campos de base de datos con elementos de una página HTML. Se ofrece de forma predeterminada al crear una página para una aplicación web o al crear envíos basados en una plantilla en la que esté activo.

>[!NOTE]
>
>El DCE solo permite realizar las operaciones detalladas en esta sección.
>
>Si desea añadir un código JavaScript del lado del servidor, es mejor hacerlo en bloques personalizados. Para obtener más información sobre la creación y modificación de bloques personalizados, consulte [esta página](../../delivery/using/personalization-blocks.md).

>[!CAUTION]
>
>Por razones de privacidad, recomendamos utilizar HTTPS para todos los recursos externos.

## Operación general del editor de contenido {#content-editor-general-operation}

En esta sección se presentan los pasos principales para editar y cargar contenido editado con el DCE dentro del marco de una aplicación web y en el contexto de un envío.

La operación general funciona de la siguiente manera:

![](assets/dce_schema.png)

Para crear una aplicación Web sencilla, siga estos pasos:

* Cree una aplicación Web, para obtener más información sobre esto, consulte [Creación de una página](../../web/using/creating-a-landing-page.md)de aterrizaje,
* Select existing content or creating content from a standard template, for more on this, refer to [Template management](../../web/using/template-management.md),
* Edite y configure contenido. Para obtener más información sobre esto, consulte [Edición de contenido](../../web/using/editing-content.md),
* Publish the Web application, for more on this, refer to [Publishing content](../../web/using/creating-a-landing-page.md#step-3---publishing-content) and [this page](../../web/using/publishing-a-web-form.md#managing-web-forms-delivery-and-tracking).

>[!NOTE]
>
>For a complete example detailing the implementation of the DCE within the framework of a Web application, refer to [Creating a landing page](../../web/using/creating-a-landing-page.md).

Para crear un envío por correo electrónico, los pasos son los siguientes:

* Cree una entrega a partir de una plantilla de tipo de correo electrónico en la que el DCE esté activo.
* Seleccione el contenido existente o cree contenido a partir de una plantilla estándar,
* Editar y configurar contenido en línea,
* Send the delivery, for more on this refer to [this section](../../delivery/using/communication-channels.md).

>[!NOTE]
>
>For a complete example detailing the implementation of the DCE within the framework of an email delivery, refer to [this use case](../../web/using/use-case--creating-an-email-delivery.md).

