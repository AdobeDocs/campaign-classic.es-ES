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
source-git-commit: 87966db35779f0e6a4b09a1a3ba1c30d4d002518

---


# Acerca del modelo de datos de Campaign{#about-data-model}

En esta sección se describen los conceptos básicos del modelo de datos de Adobe Campaign Classic para comprender mejor las tablas integradas de Campaign y su interacción.

El modelo de datos conceptuales de la base de datos de Adobe Campaign consta de un conjunto de tablas integradas y su interacción.

Para acceder a la descripción de cada tabla, vaya a **[!UICONTROL Admin > Configuration > Data schemas]**, seleccione un recurso de la lista y haga clic en la **[!UICONTROL Documentation]** ficha.

![](assets/data-model_documentation-tab.png)

Para obtener más información sobre la descripción predeterminada del modelo de datos de Campaign Classic, consulte esta [sección](../../configuration/using/data-model-description.md).

La estructura física y lógica de los datos que se llevan en la aplicación se describe en XML. Obedece a una gramática específica de Adobe Campaign, denominada esquema. Para obtener más información sobre los esquemas de Adobe Campaign, lea esta [sección](../../configuration/using/about-schema-reference.md).

## Información general {#data-model-overview}

Adobe Campaign se basa en una base de datos relacional que contiene tablas vinculadas entre sí. La estructura básica del modelo de datos de Adobe Campaign se puede describir de la siguiente manera.

>[!NOTE]
>
>Para obtener más información sobre la arquitectura del modelo de datos de Campaign y las optimizaciones relacionadas, consulte esta [sección](../../configuration/using/data-model-best-practices.md#data-model-architecture).

### Tabla de destinatarios {#recipient-table}

El modelo de datos se basa en una tabla principal que, de forma predeterminada, es la tabla Destinatario (**NmsRecipient**). Esta tabla permite almacenar todos los perfiles de marketing.

Para obtener más información sobre la tabla Destinatario, consulte esta [sección](#default-recipient-table).

### Tabla de envío {#delivery-table}

El modelo de datos también incluye una parte dedicada a almacenar todas las actividades de marketing. Normalmente es la tabla Entrega (**NmsDelivery**). Cada registro de esta tabla representa una acción de entrega o una plantilla de entrega. Contiene todos los parámetros necesarios para realizar envíos como target, content, etc.

### Registra tablas {#log-tables}

Otra parte del modelo de datos permite almacenar temporalmente todos los registros asociados con la ejecución de las campañas.

Los registros de entrega son todos mensajes enviados a destinatarios o dispositivos en todos los canales. La tabla principal de registros de entrega (**NmsBroadLog**) contiene los registros de entrega de todos los destinatarios.
La tabla de registros de seguimiento principal (**NmsTrackingLog**) almacena los registros de seguimiento de todos los destinatarios. Los registros de seguimiento hacen referencia a reacciones de los destinatarios, como aperturas de correo electrónico y clics. Cada reacción corresponde a un registro de seguimiento.
Los registros de envío y de seguimiento se eliminan después de un período determinado, que se especifica en Adobe Campaign y se puede modificar. Por lo tanto, se recomienda encarecidamente exportar los registros periódicamente.

### Tablas técnicas {#technical-tables}

Finalmente, parte del modelo de datos consiste en datos técnicos utilizados para el proceso aplicativo, incluidos operadores y derechos de usuario (**NmsGroup**), carpetas (**XtkFolder**).

## Uso de la tabla de destinatarios predeterminada {#default-recipient-table}

La tabla Destinatario lista para usar de Adobe Campaign proporciona un buen punto de partida para crear el modelo de datos. Tiene una serie de campos predefinidos y vínculos de tabla que se pueden ampliar fácilmente. Esto resulta especialmente útil cuando se dirige principalmente a destinatarios, ya que se ajusta a un modelo de datos sencillo centrado en el destinatario.

Las ventajas de utilizar la tabla de destinatarios estándar son las siguientes:

* Trabajar de forma predeterminada con funcionalidades como suscripciones, listas de inicio, encuestas, sociales, etc.
* Proporcionar una base de datos de marketing con un modelo de datos centrado en el destinatario.
* Implementación más rápida.
* Fácil mantenimiento por parte del apoyo y los socios.

Sin embargo, es posible ampliar la tabla Destinatario, pero no reducir el número de campos o vínculos en la tabla.

>[!IMPORTANT]
>
>Se recomienda no eliminar campos (aunque no sean útiles) en la tabla del destinatario, ya que esto puede provocar errores en los módulos integrados.

Además, como la tabla Destinatario forma parte del producto, tanto la tabla como el formulario asociado evolucionan a medida que cambia el producto. Por lo tanto, se necesita un mantenimiento adicional para comprobar que las extensiones siguen siendo válidas al actualizarse.

## Ampliación del modelo de datos {#extending-data-model}

Al empezar con Adobe Campaign, debe evaluar el modelo de datos predeterminado para comprobar qué tabla es la más adecuada para almacenar los datos de marketing.

Si es relevante, puede utilizar la tabla Destinatario predeterminada con los campos predeterminados, como se describe en esta [sección](#default-recipient-table).

Si es necesario, puede ampliarlo con dos mecanismos:

* Extender una tabla existente con campos nuevos. Por ejemplo, puede agregar un nuevo campo &quot;Lealtad&quot; a la tabla Destinatario.
* Cree una nueva tabla, por ejemplo una tabla de &quot;Compra&quot; que enumere todas las compras realizadas por cada perfil de la base de datos y vincúlelo a la tabla Destinatario.

Para obtener más información sobre la configuración de esquemas de extensión para ampliar el modelo de datos conceptuales, consulte [Acerca de la edición](../../configuration/using/about-schema-edition.md)de esquemas.

>[!IMPORTANT]
>
>La ampliación del modelo de datos está reservada para usuarios avanzados.

## Uso de una tabla de destinatarios personalizada {#custom-recipient-table}

Al diseñar el modelo de datos de Adobe Campaign, puede utilizar la tabla [Destinatario lista](#default-recipient-table)para usar o decidir crear una tabla de destinatarios no estándar para almacenar sus perfiles de marketing.

De hecho, si el modelo de datos no se ajusta a la estructura centrada en el destinatario, puede configurar otras tablas como dimensión de objetivo dentro de Adobe Campaign. Por ejemplo, esto puede ser relevante cuando necesita dirigirse a hogares, cuentas (como teléfonos móviles) y empresas o sitios en lugar de simplemente destinatarios.

>[!NOTE]
>
>En este caso, deberá crear una nueva asignación [de](../../configuration/using/target-mapping.md)objetivos.

En esta [sección](../../configuration/using/about-custom-recipient-table.md)se detallan todos los principios y pasos necesarios para utilizar una tabla de destinatarios personalizada.

Las ventajas de utilizar una tabla de destinatarios personalizada son las siguientes:

### Modelo de datos flexible {#flexible-data-model}

La tabla Destinatario lista para usar es inútil si no necesita la mayoría de los campos de la tabla Destinatario o si el modelo de datos no está centrado en el destinatario.

### Escalabilidad {#scalability}

Los grandes volúmenes requieren una tabla optimizada con pocos campos para un diseño eficiente. La tabla Destinatario lista para usar tendría demasiados campos inútiles, lo que podría afectar al rendimiento y a la falta de eficiencia.

### Ubicación de datos {#data-location}

Si los datos residen en una base de datos de mercadotecnia existente externa, es posible que sea necesario realizar demasiado esfuerzo para utilizar la tabla de destinatarios lista para usar. Crear uno nuevo basado en una estructura existente es más sencillo.

### Fácil migración {#easy-migration}

No se necesita mantenimiento para comprobar que todas las extensiones siguen siendo válidas al actualizar.

>[!IMPORTANT]
>
>El uso de una tabla de destinatarios personalizada está reservada para usuarios avanzados y está sujeto a algunas limitaciones. Para obtener más información sobre esto, consulte esta sección.
