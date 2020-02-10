---
title: Acerca de las encuestas
seo-title: Acerca de las encuestas
description: Acerca de las encuestas
seo-description: null
page-status-flag: never-activated
uuid: 31a07a48-2ebb-4b51-ae24-382f3ce3f04a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: online-surveys
discoiquuid: ef7d9b16-506a-409c-a578-000b88cd17a2
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# Acerca de las encuestas{#about-surveys}

Adobe Campaign incluye un módulo gráfico para definir y publicar aplicaciones web. Se utiliza para crear páginas, como un formulario de edición en una extranet, o formularios de notificación, incluidos datos de la base de datos con tablas, gráficos, formularios de entrada, etc. Esta funcionalidad permite diseñar y enviar páginas web donde los usuarios pueden buscar o introducir información.

El módulo opcional **Encuesta** le permite crear un nuevo tipo de aplicación web para realizar y gestionar cuestionarios en línea, como formularios para añadir o modificar información de perfil, para suscribirse a un servicio de información o un formulario de entrada de competencia. Cuando se hayan recopilado las respuestas, se almacenan en la base de datos o en variables locales. El modelo de datos se puede ampliar de forma dinámica a través de las respuestas a los cuestionarios. Puede ver los resultados en tiempo real, filtrar las respuestas y analizarlas con gráficos especializados.

En este capítulo se detalla el método para crear y gestionar **Encuestas**, gestión de campos y páginas, modos de almacenamiento y registros.

Los pasos para la creación de un formulario web estándar se detallan en [esta sección](../../web/using/about-web-forms.md).

La gestión de la aplicación web se explica en [esta sección](../../web/using/about-web-applications.md). Consulte esta capítulo para obtener más información.

>[!CAUTION]
>
>Por razones de privacidad, recomendamos utilizar HTTPS para todos los recursos externos.

## Ámbito de los estudios de campaña {#campaign-surveys-scope}

En Adobe Campaign, las aplicaciones web en general permiten acceder a las siguientes funcionalidades:

* Creación de formularios de múltiples páginas,
* Gestión de encuestas multilingües con una herramienta de traducción integrada,
* Interfaz de administración de páginas gráficas, diseño de página de varias columnas,
* Renderización de la personalización y la posición del campo,
* Visualización condicional de los campos de encuesta según las respuestas,
* Visualización condicional de la página,
* Comprobación de la información antes de la aprobación, según el tipo de datos esperado (número, dirección de correo electrónico, fechas, etc.) y campos obligatorios,
* Invitaciones y notificaciones por correo electrónico,
* Personalización de mensajes de error y de fin,
* Uso de imágenes, vídeos, enlaces de hipertexto, captcha, etc.

>[!NOTE]
>
>En [esta sección](../../web/using/about-web-forms.md) se describen todas las funciones vinculadas a los formularios web. Consulte este documento para obtener detalles sobre los conceptos y las funcionalidades de los formularios web en Adobe Campaign.

El módulo opcional de creación de encuestas (**Encuesta**) ofrece las siguientes funcionalidades adicionales:

* Ampliación dinámica de la base de datos: creación de respuestas que no forman parte del modelo de datos inicial. Para obtener más información sobre esto, consulte [Almacenamiento de respuestas](../../web/using/managing-answers.md#storing-collected-answers)recopiladas.
* Gestión de la puntuación. For more on this, refer to [Score management](../../web/using/managing-answers.md#score-management).
* Visualización aleatoria de preguntas. For more on this, refer to [Adding questions](../../web/using/building-a-survey.md#adding-questions).
* Seguimiento en tiempo real de las respuestas. For more on this, refer to [Response tracking](../../web/using/publish--track-and-use-collected-data.md#response-tracking).
* Generación de informes específicos. For more on this, refer to [Reports on surveys](../../web/using/publish--track-and-use-collected-data.md#reports-on-surveys).

En comparación con las aplicaciones web, las encuestas tienen una interfaz gráfica simplificada con un número reducido de controles de edición.

## Pasos para la implementación de encuestas {#surveys-implementation-steps}

Realice los pasos siguientes para crear y enviar una encuesta y procesar sus resultados:

1. Cree las páginas de encuestas y su contenido (campos de entrada, listas desplegables, preguntas, etc.).
1. Defina cómo se deben guardar las respuestas.

   Se puede insertar un paso de precarga de datos para que se precargue el formulario con los datos ya existentes en la base de datos. También puede añadir un cuadro de prueba.

1. Publique y luego envíe el estudio a los destinatarios (p. ej., incluya un vínculo en un envío o en un sitio web).
1. Monitorice las respuestas y vea los informes.

Para obtener más información sobre la configuración y secuenciación de estos pasos, consulte [esta sección](../../web/using/about-web-forms.md). En este capítulo solo se detallan las configuraciones específicas de los estudios.

## Configuración de encuestas {#surveys-configuration}

Surveys are stored in the **[!UICONTROL Resources > Online > Web Applications]** node of the Adobe Campaign tree. Las configuraciones se encuentran en las siguientes carpetas:

* **[!UICONTROL Administration > Configuration > Form rendering]**:: contiene las plantillas de procesamiento para la presentación de formularios Web (aplicaciones y estudios).
* **[!UICONTROL Resources > Templates > Web application templates]**:: contiene las plantillas de formulario. Para crear un formulario, debe empezar con una plantilla.

>[!NOTE]
>
>La información de configuración está disponible en [esta sección](../../web/using/about-web-forms.md).

