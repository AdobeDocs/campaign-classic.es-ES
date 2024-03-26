---
product: campaign
title: Introducción al modelo de datos de Campaign Classic
description: Aprenda a ampliar el modelo de datos de Campaign, editar esquemas, utilizar API y mucho más
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
feature: Data Model, Configuration
role: Data Engineer, Developer
exl-id: 655b5928-b005-442f-b026-2f1b0c1abb99
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '987'
ht-degree: 6%

---

# Introducción al modelo de datos de Campaign{#about-data-model}

El modelo de datos conceptuales de la base de datos de Adobe Campaign consta de un conjunto de tablas integradas y su interacción. En esta página se enumeran las tablas y los conceptos principales.

## Información general {#data-model-overview}

Adobe Campaign se basa en una base de datos relacional que contiene tablas vinculadas entre sí. La estructura básica del modelo de datos de Adobe Campaign se puede describir de la siguiente manera.

### Tabla de destinatarios {#recipient-table}

El modelo de datos se basa en una tabla principal que es de forma predeterminada la tabla de destinatarios (**NmsRecipient**). Esta tabla permite almacenar todos los perfiles de marketing.

Para obtener más información sobre la tabla de destinatarios, consulte [esta sección](#default-recipient-table).

### Tabla de envío {#delivery-table}

El modelo de datos también incluye una parte dedicada a almacenar todas las actividades de marketing. Normalmente es la tabla de envío (**NmsDelivery**). Cada registro de esta tabla representa una acción de envío o una plantilla de envío. Contiene todos los parámetros necesarios para realizar envíos como destinatario, contenido, etc.

### Tablas de registros {#log-tables}

Otra parte del modelo de datos permite almacenar temporalmente todos los registros asociados con la ejecución de las campañas.

Los &quot;logs&quot; de entrega son todos los mensajes enviados a los destinatarios o dispositivos a través de todos los canales. La tabla principal de registros de envío (**NmsBroadLog**) contiene los registros de envío de todos los destinatarios.
La tabla principal de registros de seguimiento (**NmsTrackingLog**) almacena los registros de seguimiento de todos los destinatarios. Los registros de seguimiento hacen referencia a reacciones de los destinatarios, como aperturas de correos electrónicos y clics. Cada reacción corresponde a un registro de seguimiento.
Los registros de envío y los registros de seguimiento se eliminan después de un período determinado, que se especifica en Adobe Campaign y se puede modificar. Por lo tanto, es muy recomendable exportar los registros de forma regular.

### Tablas técnicas {#technical-tables}

Por último, parte del modelo de datos consiste en datos técnicos utilizados para el proceso aplicativo, incluidos los operadores y los derechos de usuario (**NmsGroup**), carpetas (**XtkFolder**).

## Uso de la tabla de destinatarios integrada {#default-recipient-table}

La tabla de destinatarios integrada en Adobe Campaign proporciona un buen punto de partida para crear el modelo de datos. Tiene una serie de campos predefinidos y vínculos de tabla que se pueden ampliar fácilmente. Esto resulta particularmente útil cuando se segmenta principalmente a destinatarios, ya que se ajusta a un modelo de datos sencillo centrado en el destinatario.

Las ventajas de utilizar la tabla de destinatarios integrada son las siguientes:

* Uso de funciones integradas como suscripciones, listas semilla y mucho más.
* Proporcionar una base de datos de marketing con un modelo de datos centrado en el destinatario.
* Implementación más rápida.
* Fácil mantenimiento por parte del soporte y los socios.

Sin embargo, es posible ampliar la tabla de destinatarios, pero no reducir el número de campos o vínculos de la tabla.

>[!IMPORTANT]
>
>Se recomienda no eliminar campos (incluso si no son útiles) en la tabla de destinatarios, ya que esto puede provocar errores en los módulos integrados.

Además, como la tabla Destinatario forma parte del producto, tanto la tabla como su formulario asociado evolucionan a medida que cambia el producto. Por lo tanto, se necesita mantenimiento adicional para comprobar que cualquier extensión sigue siendo válida tras la actualización.

## Ampliación del modelo de datos {#extending-data-model}

Al comenzar con Adobe Campaign, debe evaluar el modelo de datos predeterminado para comprobar qué tabla es la más adecuada para almacenar los datos de marketing.

Si es relevante, puede utilizar la tabla de destinatarios predeterminada con los campos predeterminados, como se describe en [esta sección](#default-recipient-table).

Si es necesario, se puede ampliar con dos mecanismos:

* Ampliar una tabla existente con campos nuevos. Por ejemplo, puede agregar un nuevo campo &quot;Fidelidad&quot; a la tabla Destinatario.
* Cree una nueva tabla, por ejemplo una tabla &quot;Purchase&quot; (compra) que enumere todas las compras realizadas por cada perfil de la base de datos y vincule a la tabla Recipient (destinatario).

Para obtener más información sobre la configuración de esquemas de extensión para ampliar el modelo de datos conceptuales, consulte [Acerca de la edición de esquemas](../../configuration/using/about-schema-edition.md).

>[!IMPORTANT]
>
>La ampliación del modelo de datos está reservada para usuarios avanzados.

## Uso de una tabla de destinatarios personalizada {#custom-recipient-table}

Al diseñar el modelo de datos de Adobe Campaign, puede utilizar el [tabla de destinatarios integrada](#default-recipient-table), o decida crear una [tabla de destinatarios personalizada](../../configuration/using/about-custom-recipient-table.md) para almacenar sus perfiles de marketing.

De hecho, si el modelo de datos no se ajusta a la estructura centrada en el destinatario, puede configurar otras tablas como dimensión de segmentación dentro de Adobe Campaign. Por ejemplo, esto puede ser relevante cuando necesita dirigirse a hogares, cuentas (como teléfonos móviles) y empresas/sitios en lugar de simplemente destinatarios.

>[!NOTE]
>
>En este caso, debe crear un nuevo [asignación de destino](../../configuration/using/target-mapping.md).

Todos los principios y pasos necesarios al utilizar una tabla de destinatarios personalizada se detallan en [esta sección](../../configuration/using/about-custom-recipient-table.md).

Las ventajas de utilizar una tabla de destinatarios personalizada son las siguientes:

* **Modelo de datos flexible** : la tabla de destinatarios integrada no sirve si no se necesitan la mayoría de los campos de la tabla de destinatarios o si el modelo de datos no está centrado en el destinatario.

* **Escalabilidad** - Los volúmenes grandes requieren una tabla optimizada con pocos campos para un diseño eficiente. La tabla de destinatarios integrada tendría demasiados campos inútiles, lo que podría afectar al rendimiento y carecer de eficiencia.

* **Ubicación de datos** : Si los datos residen en una base de datos de marketing externa existente, puede requerir demasiado esfuerzo utilizar la tabla de destinatarios integrada. Crear una nueva basada en una estructura existente es más sencillo.

* **Fácil migración** - No se necesita mantenimiento para comprobar que todas las extensiones siguen siendo válidas tras la actualización.

>[!IMPORTANT]
>
>El uso de una tabla de destinatarios personalizada está reservado para usuarios avanzados y está sujeto a algunas limitaciones. Para obtener más información, consulte [esta sección](../../configuration/using/about-custom-recipient-table.md).

## Temas relacionados

Obtenga más información acerca del modelo de datos de Campaign en estas secciones:

* **Descripción de las tablas principales** : Para obtener más información sobre la descripción del modelo de datos del Campaign Classic predeterminado, consulte [esta sección](../../configuration/using/data-model-description.md).

* **Descripción completa de cada tabla** - Para acceder a la descripción completa de cada tabla, vaya a **[!UICONTROL Admin > Configuration > Data schemas]**, seleccione un recurso de la lista y haga clic en **[!UICONTROL Documentation]** pestaña.

  ![](assets/data-model_documentation-tab.png)


* **Esquemas de campaña** : La estructura física y lógica de los datos que se llevan en la aplicación se describe en XML. Obedece a una gramática específica de Adobe Campaign, denominada esquema. Para obtener más información sobre los esquemas de Adobe Campaign, lea [esta sección](../../configuration/using/about-schema-reference.md).

* **Recomendaciones del modelo de datos** : Conozca la arquitectura del modelo de datos de Campaign y las prácticas recomendadas relacionadas, en [esta sección](../../configuration/using/data-model-best-practices.md#data-model-architecture).
