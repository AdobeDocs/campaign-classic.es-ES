---
solution: Campaign Classic
product: campaign
title: Introducción al modelo de datos de Campaign Classic
description: Obtenga información sobre cómo ampliar el modelo de datos de Campaign, editar esquemas, utilizar API y mucho más
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 7%

---


# Introducción al modelo de datos de Campaign {#about-data-model}

El modelo de datos conceptuales de la base de datos de Adobe Campaign consta de un conjunto de tablas integradas y su interacción. Las tablas principales y los conceptos se enumeran en esta página.

## Información general {#data-model-overview}

Adobe Campaign se basa en una base de datos relacional que contiene tablas vinculadas entre sí. La estructura básica del modelo de datos de Adobe Campaign se puede describir de la siguiente manera.

### Tabla de destinatario {#recipient-table}

El modelo de datos se basa en una tabla principal que, de forma predeterminada, es la tabla de Destinatario (**NmsRecipient**). Esta tabla permite almacenar todos los perfiles de mercadotecnia.

Para obtener más información sobre la tabla de Destinatarios, consulte [esta sección](#default-recipient-table).

### Tabla de envío {#delivery-table}

El modelo de datos también incluye una parte dedicada a almacenar todas las actividades de mercadotecnia. Normalmente es la tabla de Envío (**NmsDelivery**). Cada registro de esta tabla representa una acción de envío o una Plantilla de envíos. Contiene todos los parámetros necesarios para realizar envíos como destinatario, contenido, etc.

### Registra tablas {#log-tables}

Otra parte del modelo de datos permite almacenar temporalmente todos los registros asociados con la ejecución de las campañas.

Registros de envío son todos mensajes enviados a destinatarios o dispositivos en todos los canales. La tabla de Registros de envío principal (**NmsBroadLog**) contiene los registros de envío de todos los destinatarios.
La tabla de Registros de seguimiento principal (**NmsTrackingLog**) almacena los registros de seguimiento de todos los destinatarios. Los registros de seguimiento se refieren a las reacciones de destinatarios, como aperturas de correo electrónico y clics. Cada reacción corresponde a un registro de seguimiento.
Los registros de envío y registros de seguimiento se eliminan después de un período determinado, que se especifica en Adobe Campaign y se puede modificar. Por lo tanto, se recomienda encarecidamente exportar los registros periódicamente.

### Tablas técnicas {#technical-tables}

Finalmente, parte del modelo de datos consiste en datos técnicos utilizados para el proceso aplicativo, incluidos los operadores y derechos de usuario (**NmsGroup**), carpetas (**XtkFolder**).

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

Para obtener más información sobre la configuración de esquemas de extensión para ampliar el modelo de datos conceptuales, consulte [Acerca de la edición de esquema](../../configuration/using/about-schema-edition.md).

>[!IMPORTANT]
>
>La ampliación del modelo de datos está reservada para usuarios avanzados.

## Uso de una lista de destinatarios personalizada {#custom-recipient-table}

Al diseñar su modelo de datos de Adobe Campaign, puede utilizar la [tabla de Destinatarios lista para usar](#default-recipient-table) o decidir crear una [tabla de destinatario personalizada](../../configuration/using/about-custom-recipient-table.md) para almacenar sus perfiles de mercadotecnia.

De hecho, si el modelo de datos no se ajusta a la estructura centrada en el destinatario, puede configurar otras tablas como la dimensión de segmentación dentro de Adobe Campaign. Por ejemplo, esto puede ser relevante cuando se necesita el destinatario de hogares, cuentas (como teléfonos móviles) y compañías/sitios en lugar de simplemente destinatarios.

>[!NOTE]
>
>En este caso, deberá crear una nueva [asignación de destino](../../configuration/using/target-mapping.md).

Todos los principios y pasos necesarios para utilizar una tabla de destinatario personalizada se detallan en [esta sección](../../configuration/using/about-custom-recipient-table.md).

Las ventajas de utilizar una tabla de Destinatario personalizada son las siguientes:

* **Modelo**  de datos flexible: la tabla de Destinatarios lista para usar es inútil si no se necesita la mayoría de los campos de la tabla de Destinatarios o si el modelo de datos no se centra en el destinatario.

* **Escalabilidad** : los grandes volúmenes requieren una tabla optimizada con pocos campos para un diseño eficiente. La tabla de Destinatarios lista para usar tendría demasiados campos inútiles, lo que podría afectar al rendimiento y la falta de eficiencia.

* **Ubicación**  de los datos: si los datos residen en una base de datos de marketing existente externa, puede que sea necesario un esfuerzo excesivo para utilizar la tabla de Destinatarios lista para usar. Crear uno nuevo basado en una estructura existente es más sencillo.

* **Fácil migración** : no se necesita mantenimiento para comprobar que todas las extensiones siguen siendo válidas tras la actualización.

>[!IMPORTANT]
>
>El uso de una tabla de destinatario personalizada está reservado para usuarios avanzados y está sujeto a algunas limitaciones. Para obtener más información, consulte [esta sección](../../configuration/using/about-custom-recipient-table.md).

## Temas relacionados

Obtenga más información sobre el modelo de datos de Campaña en estas secciones:

* **Descripción de las tablas**  principales: para obtener más información sobre la descripción del modelo de datos Campaign Classic predeterminado, consulte  [esta sección](../../configuration/using/data-model-description.md).

* **Descripción completa de cada tabla** : para acceder a la descripción completa de cada tabla, vaya a  **[!UICONTROL Admin > Configuration > Data schemas]**, seleccione un recurso de la lista y haga clic en la  **[!UICONTROL Documentation]** ficha.

   ![](assets/data-model_documentation-tab.png)


* **Esquemas**  de campaña: la estructura física y lógica de los datos que se llevan en la aplicación se describe en XML. Obedece a una gramática específica de Adobe Campaign, denominada esquema. Para obtener más información sobre esquemas de Adobe Campaign, lea [esta sección](../../configuration/using/about-schema-reference.md).

* **Prácticas recomendadas**  del modelo de datos: Obtenga información sobre la arquitectura del modelo de datos de Campaña y las prácticas recomendadas relacionadas en  [esta sección](../../configuration/using/data-model-best-practices.md#data-model-architecture).
