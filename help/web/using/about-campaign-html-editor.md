---
solution: Campaign Classic
product: campaign
title: Acerca del editor HTML de Campaign
description: Acerca del editor HTML de Campaign
audience: web
content-type: reference
topic-tags: editing-html-content
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 100%

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

En esta sección se presentan los pasos principales para editar y cargar contenido editado con el DCE dentro del marco de una aplicación web y en el contexto de una entrega.

La operación general funciona de la siguiente manera:

![](assets/dce_schema.png)

Para crear una aplicación Web, los pasos son los siguientes:

* Cree una aplicación Web, para obtener más información sobre esto, consulte [Creación de una página de destino](../../web/using/creating-a-landing-page.md),
* Selección de contenido existente o creación de contenido desde una plantilla estándar; para obtener más información, consulte [Administración de plantillas](../../web/using/template-management.md),
* Edite y configure contenido. Para obtener más información sobre esto, consulte [Edición de contenido](../../web/using/editing-content.md),
* Publicación de la aplicación Web; para obtener más información, consulte [Publicación de contenidos](../../web/using/creating-a-landing-page.md#step-3---publishing-content) y [esta página](../../web/using/publishing-a-web-form.md#managing-web-forms-delivery-and-tracking).

>[!NOTE]
>
>Para ver un ejemplo completo que detalle la implementación del DCE dentro del marco de una aplicación Web, consulte [Creación de una página de destino](../../web/using/creating-a-landing-page.md).

Para crear una entrega por correo electrónico, los pasos son los siguientes:

* Cree una entrega a partir de una plantilla de tipo correo electrónico en la que el DCE esté activo,
* Seleccione contenido existente o cree contenido desde una plantilla estándar,
* Editar y configurar contenido en línea,
* Realice una entrega; para obtener más información, consulte [esta sección](../../delivery/using/steps-about-delivery-creation-steps.md).

>[!NOTE]
>
>Para ver un ejemplo completo que detalle la implementación del DCE dentro del marco de una entrega por correo electrónico, consulte [este caso de uso](../../web/using/use-case--creating-an-email-delivery.md).

