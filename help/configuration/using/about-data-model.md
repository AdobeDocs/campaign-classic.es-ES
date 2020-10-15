---
title: Acerca del modelo de datos de Adobe Campaign Classic
description: Obtenga información sobre cómo ampliar el modelo de datos de Campaign, editar esquemas, utilizar API y mucho más.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 8%

---


# About the Campaign data model{#about-data-model}

En esta sección se describen los conceptos básicos del modelo de datos de Adobe Campaign Classic para comprender mejor las tablas integradas de Campaña y su interacción.

El modelo de datos conceptuales de la base de datos de Adobe Campaign consta de un conjunto de tablas integradas y su interacción.

Para acceder a la descripción de cada tabla, vaya a **[!UICONTROL Admin > Configuration > Data schemas]**, seleccione un recurso en la lista y haga clic en la **[!UICONTROL Documentation]** ficha.

![](assets/data-model_documentation-tab.png)

Para obtener más información sobre la descripción del modelo de datos Campaign Classic predeterminado, consulte [esta sección](../../configuration/using/data-model-description.md).

La estructura física y lógica de los datos que se llevan en la aplicación se describe en XML. Obedece a una gramática específica de Adobe Campaign, denominada esquema. For more on Adobe Campaign schemas, read out [this section](../../configuration/using/about-schema-reference.md).

## Información general {#data-model-overview}

Adobe Campaign se basa en una base de datos relacional que contiene tablas vinculadas entre sí. La estructura básica del modelo de datos de Adobe Campaign se puede describir de la siguiente manera.

>[!NOTE]
>
>Para obtener más información sobre la arquitectura del modelo de datos de Campaña y las optimizaciones relacionadas, consulte [esta sección](../../configuration/using/data-model-best-practices.md#data-model-architecture).

### Tabla de destinatarios {#recipient-table}

El modelo de datos se basa en una tabla principal que, de forma predeterminada, es la tabla de Destinatario (**NmsRecipient**). Esta tabla permite almacenar todos los perfiles de mercadotecnia.

Para obtener más información sobre la tabla de Destinatarios, consulte [esta sección](#default-recipient-table).

### Tabla de envíos {#delivery-table}

El modelo de datos también incluye una parte dedicada a almacenar todas las actividades de mercadotecnia. Normalmente es la tabla de Envío (**NmsDelivery**). Cada registro de esta tabla representa una acción de envío o una Plantilla de envíos. Contiene todos los parámetros necesarios para realizar envíos como destinatario, contenido, etc.

### Registra tablas {#log-tables}

Otra parte del modelo de datos permite almacenar temporalmente todos los registros asociados con la ejecución de las campañas.

Registros de envío son todos mensajes enviados a destinatarios o dispositivos en todos los canales. La tabla de Registros de envío principal (**NmsBroadLog**) contiene los registros de envío de todos los destinatarios.
La tabla de Registros de seguimiento principal (**NmsTrackingLog**) almacena los registros de seguimiento de todos los destinatarios. Los registros de seguimiento se refieren a las reacciones de destinatarios, como aperturas de correo electrónico y clics. Cada reacción corresponde a un registro de seguimiento.
Los registros de envío y registros de seguimiento se eliminan después de un período determinado, que se especifica en Adobe Campaign y se puede modificar. Por lo tanto, se recomienda encarecidamente exportar los registros periódicamente.

### Tablas técnicas {#technical-tables}

Finalmente, parte del modelo de datos consiste en datos técnicos utilizados para el proceso aplicativo, incluidos operadores y derechos de usuario (**NmsGroup**), carpetas (**XtkFolder**).

## Uso de la tabla de destinatarios predeterminada {#default-recipient-table}

La tabla de Destinatarios lista para usar en Adobe Campaign proporciona un buen punto de partida para crear el modelo de datos. Tiene una serie de campos predefinidos y vínculos de tabla que se pueden ampliar fácilmente. Esto resulta especialmente útil cuando se dirige principalmente a destinatarios, ya que se ajusta a un modelo de datos sencillo centrado en el destinatario.

Las ventajas de utilizar la tabla de Destinatarios estándar son las siguientes:

* Trabajar de inmediato con funcionalidades como suscripciones, listas de semillas, encuestas, sociales, etc.
* Proporcionar una base de datos de marketing con un modelo de datos centrado en el destinatario.
* Implementación más rápida.
* Fácil mantenimiento por parte del apoyo y los socios.

Sin embargo, es posible ampliar la tabla de Destinatarios, pero no reducir el número de campos o vínculos de la tabla.

>[!IMPORTANT]
>
>Se recomienda no eliminar campos (aunque no sean útiles) en la tabla de destinatario, ya que esto puede provocar errores en los módulos integrados.

Además, como la tabla de Destinatarios es parte del producto, tanto la tabla como su formulario asociado evolucionan a medida que cambia el producto. Por lo tanto, se necesita un mantenimiento adicional para comprobar que las extensiones siguen siendo válidas al actualizarse.

## Extensión del modelo de datos {#extending-data-model}

Al empezar con Adobe Campaign, debe evaluar el modelo de datos predeterminado para comprobar qué tabla es la más adecuada para almacenar los datos de mercadotecnia.

Si es pertinente, puede utilizar la tabla de Destinatarios predeterminada con los campos predeterminados, como se describe en [esta sección](#default-recipient-table).

Si es necesario, puede ampliarlo con dos mecanismos:

* Extender una tabla existente con campos nuevos. Por ejemplo, puede agregar un nuevo campo &quot;Lealtad&quot; a la tabla de Destinatarios.
* Cree una nueva tabla, por ejemplo una tabla de &quot;Compra&quot; que enumere todas las compras realizadas por cada perfil de la base de datos y vincúlelo a la tabla de Destinatarios.

Para obtener más información sobre la configuración de esquemas de extensión para ampliar el modelo de datos conceptuales, consulte [Acerca de la edición](../../configuration/using/about-schema-edition.md)de esquema.

>[!IMPORTANT]
>
>La ampliación del modelo de datos está reservada para usuarios avanzados.

## Uso de una lista de destinatarios personalizada {#custom-recipient-table}

Al diseñar el modelo de datos de Adobe Campaign, puede utilizar la tabla [de Destinatarios](#default-recipient-table)lista para usar o decidir crear una tabla de destinatarios no estándar para almacenar sus perfiles de mercadotecnia.

De hecho, si el modelo de datos no se ajusta a la estructura centrada en el destinatario, puede configurar otras tablas como la dimensión de segmentación dentro de Adobe Campaign. Por ejemplo, esto puede ser relevante cuando se necesita el destinatario de hogares, cuentas (como teléfonos móviles) y compañías/sitios en lugar de simplemente destinatarios.

>[!NOTE]
>
>En este caso, deberá crear una nueva [asignación de destino](../../configuration/using/target-mapping.md).

Todos los principios y pasos necesarios para utilizar una tabla de destinatario personalizada se detallan en [esta sección](../../configuration/using/about-custom-recipient-table.md).

Las ventajas de utilizar una tabla de Destinatario personalizada son las siguientes:

### Modelo de datos flexible {#flexible-data-model}

La tabla de Destinatarios lista para usar es inútil si no necesita la mayoría de los campos de la tabla de Destinatarios o si el modelo de datos no está centrado en el destinatario.

### Escalabilidad {#scalability}

Los grandes volúmenes requieren una tabla optimizada con pocos campos para un diseño eficiente. La tabla de Destinatarios lista para usar tendría demasiados campos inútiles, lo que podría afectar al rendimiento y la falta de eficiencia.

### Ubicación de datos {#data-location}

Si los datos residen en una base de datos de mercadotecnia existente externa, es posible que sea necesario un esfuerzo excesivo para utilizar la tabla de Destinatarios lista para usar. Crear uno nuevo basado en una estructura existente es más sencillo.

### Fácil migración {#easy-migration}

No se necesita mantenimiento para comprobar que todas las extensiones siguen siendo válidas al actualizar.

>[!IMPORTANT]
>
>El uso de una tabla de destinatario personalizada está reservado para usuarios avanzados y está sujeto a algunas limitaciones. Para obtener más información, consulte [esta sección](../../configuration/using/about-custom-recipient-table.md).
