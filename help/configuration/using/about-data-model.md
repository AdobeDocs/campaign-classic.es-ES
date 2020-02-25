---
title: Acerca del modelo de datos de Adobe Campaign Classic
description: Este documento describe los conceptos básicos del modelo de datos de Adobe Campaign Classic.
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
source-git-commit: b7fa53a0463c5752a5fe4d11262dbf7b8ad77144

---


# Acerca del modelo de datos de Campaign Classic{#about-data-model}

En esta sección se describen los conceptos básicos del modelo de datos de Adobe Campaign Classic para comprender mejor las tablas integradas de Campaign y su interacción.

El modelo de datos conceptuales de la base de datos de Adobe Campaign consta de un conjunto de tablas integradas y su interacción.

Para acceder a la descripción de cada tabla, vaya a **[!UICONTROL Admin > Configuration > Data schemas]**, seleccione un recurso de la lista y haga clic en la **[!UICONTROL Documentation]** ficha.

![](assets/data-model_documentation-tab.png)

Para obtener más información sobre la descripción predeterminada del modelo de datos de Campaign Classic, consulte este [documento](https://final-docs.campaign.adobe.com/doc/AC/en/technicalResources/_Datamodel_Description_of_the_main_tables.html).

La estructura física y lógica de los datos que se llevan en la aplicación se describe en XML. Obedece a una gramática específica de Adobe Campaign, denominada esquema. Para obtener más información sobre los esquemas de Adobe Campaign, lea esta [sección](../../configuration/using/about-schema-reference.md).

## Información general {#data-model-overview}

Adobe Campaign se basa en una base de datos relacional que contiene tablas vinculadas entre sí.

La estructura básica del modelo de datos de Adobe Campaign se puede describir de la siguiente manera.

## Tabla de destinatarios {#recipient-table}

El modelo de datos se basa en una tabla principal que, de forma predeterminada, es la tabla Destinatario (**NmsRecipient**). Esta tabla permite almacenar todos los perfiles de marketing.

Para obtener más información sobre la tabla Destinatario, consulte esta [sección](../../configuration/using/default-recipient-table.md).

## Tabla de envío {#delivery-table}

El modelo de datos también incluye una parte dedicada a almacenar todas las actividades de marketing. Normalmente es la tabla Entrega (**NmsDelivery**). Cada registro de esta tabla representa una acción de entrega o una plantilla de entrega. Contiene todos los parámetros necesarios para realizar envíos como target, content, etc.

## Registra tablas {#log-tables}

Otra parte del modelo de datos permite almacenar temporalmente todos los registros asociados con la ejecución de las campañas.

Los registros de entrega son todos mensajes enviados a destinatarios o dispositivos en todos los canales. La tabla principal de registros de entrega (**NmsBroadLog**) contiene los registros de entrega de todos los destinatarios.
La tabla de registros de seguimiento principal (**NmsTrackingLog**) almacena los registros de seguimiento de todos los destinatarios. Los registros de seguimiento hacen referencia a reacciones de los destinatarios, como aperturas de correo electrónico y clics. Cada reacción corresponde a un registro de seguimiento.
Los registros de envío y de seguimiento se eliminan después de un período determinado, que se especifica en Adobe Campaign y se puede modificar. Por lo tanto, se recomienda encarecidamente exportar los registros periódicamente.

## Tablas técnicas {#technical-tables}

Finalmente, parte del modelo de datos consiste en datos técnicos utilizados para el proceso aplicativo, incluidos operadores y derechos de usuario (**NmsGroup**), carpetas (**XtkFolder**).