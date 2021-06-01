---
product: campaign
title: Introducción al modelo de datos de Campaign Classic
description: Obtenga información sobre cómo ampliar el modelo de datos de Campaign, editar esquemas, utilizar API y mucho más
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 655b5928-b005-442f-b026-2f1b0c1abb99
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 7%

---

# Introducción al modelo de datos de Campaign {#about-data-model}

El modelo de datos conceptuales de la base de datos de Adobe Campaign consta de un conjunto de tablas integradas y su interacción. En esta página se enumeran las tablas principales y los conceptos.

## Información general {#data-model-overview}

Adobe Campaign se basa en una base de datos relacional que contiene tablas vinculadas. La estructura básica del modelo de datos de Adobe Campaign se puede describir de la siguiente manera.

### Tabla de destinatario {#recipient-table}

El modelo de datos se basa en una tabla principal que, de forma predeterminada, es la tabla de destinatarios (**NmsRecipient**). Esta tabla permite almacenar todos los perfiles de marketing.

Para obtener más información sobre la tabla de destinatarios, consulte [esta sección](#default-recipient-table).

### Tabla de envío {#delivery-table}

El modelo de datos también incluye una parte dedicada a almacenar todas las actividades de marketing. Normalmente es la tabla Delivery (**NmsDelivery**). Cada registro de esta tabla representa una acción de envío o una plantilla de envío. Contiene todos los parámetros necesarios para realizar envíos como destinatario, contenido, etc.

### Registra tablas {#log-tables}

Otra parte del modelo de datos permite almacenar temporalmente todos los registros asociados con la ejecución de las campañas.

Los registros de envío son todos los mensajes enviados a los destinatarios o dispositivos en todos los canales. La tabla principal Delivery logs (**NmsBroadLog**) contiene los registros de envío de todos los destinatarios.
La tabla principal Tracking logs (**NmsTrackingLog**) almacena los registros de seguimiento para todos los destinatarios. Los registros de seguimiento hacen referencia a reacciones de los destinatarios, como aperturas de correo electrónico y clics. Cada reacción corresponde a un registro de seguimiento.
Los registros de envío y los registros de seguimiento se eliminan después de un periodo determinado, que se especifica en Adobe Campaign y se puede modificar. Por lo tanto, es muy recomendable exportar los registros de forma regular.

### Tablas técnicas {#technical-tables}

Finalmente, parte del modelo de datos consta de datos técnicos utilizados para el proceso aplicativo, incluidos operadores y derechos de usuario (**NmsGroup**), carpetas (**XtkFolder**).

## Uso de la tabla de destinatarios predeterminada {#default-recipient-table}

La tabla de destinatarios predeterminada de Adobe Campaign proporciona un buen punto de partida para crear su modelo de datos. Tiene varios campos predefinidos y vínculos de tabla que se pueden ampliar fácilmente. Esto resulta especialmente útil cuando se dirige principalmente a destinatarios, ya que se ajusta a un modelo de datos sencillo centrado en los destinatarios.

Las ventajas de utilizar la tabla de destinatarios estándar son las siguientes:

* Uso de funcionalidades predeterminadas como suscripciones, listas de fuentes, encuestas, redes sociales, etc.
* Proporcionar una base de datos de marketing con un modelo de datos centrado en el destinatario.
* Implementación más rápida.
* Fácil mantenimiento por parte del apoyo y los socios.

Sin embargo, es posible ampliar la tabla Destinatario, pero no reducir el número de campos o vínculos en la tabla.

>[!IMPORTANT]
>
>Se recomienda no eliminar campos (aunque no sean útiles) en la tabla de destinatarios, ya que esto puede provocar errores en los módulos integrados.

Además, como la tabla de destinatarios forma parte del producto, tanto la tabla como su formulario asociado evolucionan a medida que cambia el producto. Por lo tanto, es necesario realizar un mantenimiento adicional para comprobar que las extensiones siguen siendo válidas tras la actualización.

## Extensión del modelo de datos {#extending-data-model}

Al comenzar con Adobe Campaign, debe evaluar el modelo de datos predeterminado para comprobar qué tabla es la más adecuada para almacenar los datos de marketing.

Si es relevante, puede utilizar la tabla de destinatarios predeterminada con los campos predeterminados, como se describe en [esta sección](#default-recipient-table).

Si es necesario, puede ampliarlo con dos mecanismos:

* Ampliar una tabla existente con campos nuevos. Por ejemplo, puede agregar un nuevo campo &quot;Lealtad&quot; a la tabla de destinatarios.
* Cree una nueva tabla, por ejemplo una tabla &quot;Purchase&quot; que enumere todas las compras realizadas por cada perfil de la base de datos y vincúlelo a la tabla Recipient .

Para obtener más información sobre la configuración de esquemas de extensión para ampliar el modelo de datos conceptuales, consulte [Acerca de la edición de esquema](../../configuration/using/about-schema-edition.md).

>[!IMPORTANT]
>
>La ampliación del modelo de datos está reservada para usuarios avanzados.

## Uso de una lista de destinatarios personalizada {#custom-recipient-table}

Al diseñar el modelo de datos de Adobe Campaign, puede utilizar la [tabla de destinatarios predeterminada](#default-recipient-table) o decidir crear una tabla de destinatarios personalizada](../../configuration/using/about-custom-recipient-table.md) para almacenar sus perfiles de marketing.[

De hecho, si el modelo de datos no se ajusta a la estructura centrada en los destinatarios, puede configurar otras tablas como dimensiones de segmentación dentro de Adobe Campaign. Por ejemplo, esto puede ser relevante cuando necesita dirigirse a hogares, cuentas (como teléfonos móviles) y empresas/sitios en lugar de simplemente a destinatarios.

>[!NOTE]
>
>En este caso, deberá crear una nueva [asignación de destino](../../configuration/using/target-mapping.md).

Todos los principios y pasos necesarios al utilizar una tabla de destinatarios personalizada se detallan en [esta sección](../../configuration/using/about-custom-recipient-table.md).

Las ventajas de utilizar una tabla de destinatarios personalizada son las siguientes:

* **Modelo de datos flexible** : la tabla de destinatarios predeterminada no es útil si no necesita la mayoría de los campos de la tabla de destinatarios o si el modelo de datos no está centrado en el destinatario.

* **Escalabilidad** : los volúmenes grandes requieren una tabla optimizada con pocos campos para un diseño eficiente. La tabla de destinatarios predeterminada tendría demasiados campos inútiles, lo que podría afectar al rendimiento y falta de eficiencia.

* **Ubicación de los datos** : si los datos residen en una base de datos de marketing existente externa, puede requerir demasiado esfuerzo para usar la tabla de destinatarios predeterminada. La creación de una nueva basada en una estructura existente es más sencilla.

* **Migración sencilla** : no se requiere mantenimiento para comprobar que todas las extensiones son válidas después de la actualización.

>[!IMPORTANT]
>
>El uso de una tabla de destinatarios personalizada está reservado para usuarios avanzados y está sujeto a algunas limitaciones. Para obtener más información, consulte [esta sección](../../configuration/using/about-custom-recipient-table.md).

## Temas relacionados

Obtenga más información sobre el modelo de datos de Campaign en estas secciones:

* **Descripción de las tablas**  principales: para obtener más información sobre la descripción del modelo de datos del Campaign Classic predeterminado, consulte  [esta sección](../../configuration/using/data-model-description.md).

* **Descripción completa de cada tabla** : para acceder a la descripción completa de cada tabla, vaya a  **[!UICONTROL Admin > Configuration > Data schemas]**, seleccione un recurso de la lista y haga clic en la  **[!UICONTROL Documentation]** pestaña .

   ![](assets/data-model_documentation-tab.png)


* **Esquemas de campaña** : la estructura física y lógica de los datos que se llevan en la aplicación se describe en XML. Obedece a una gramática específica de Adobe Campaign, denominada esquema. Para obtener más información sobre los esquemas de Adobe Campaign, lea [esta sección](../../configuration/using/about-schema-reference.md).

* **Prácticas recomendadas del modelo de datos** : en  [esta sección](../../configuration/using/data-model-best-practices.md#data-model-architecture), conozca la arquitectura del modelo de datos de Campaign y las prácticas recomendadas relacionadas.
