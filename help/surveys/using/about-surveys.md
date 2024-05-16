---
product: campaign
title: Introducción a las encuestas
description: Introducción a las encuestas de Campaign
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
feature: Surveys
exl-id: 7061a4f1-006f-4f19-8761-918d8930d885
source-git-commit: 8e5a328bee7701adfedec6a533cc21b4ce548187
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 95%

---

# Introducción a las encuestas{#about-surveys}

Adobe Campaign incluye un módulo gráfico para definir y publicar aplicaciones web. Se utiliza para crear páginas, como un formulario de edición en una extranet, o formularios de notificación, incluidos datos de la base de datos con tablas, gráficos, formularios de entrada, etc. Utilice esta capacidad para diseñar y publicar páginas web en las que los usuarios puedan buscar o introducir información.

>[!AVAILABILITY]
>
>La administración de encuestas no está disponible en Campaign v8 en el contexto de una implementación empresarial (FDAC). Obtenga más información en [Documentación de Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/config/architecture/ffda/enterprise-deployment){target="_blank"}.


El complemento opcional **Encuesta** le permite crear un nuevo tipo de aplicación web para realizar y administrar cuestionarios en línea, como formularios para añadir o modificar información del perfil, para suscribirse o cancelar la suscripción a un servicio informativo o un formulario de entrada de competencia. Cuando se hayan recopilado las respuestas, se almacenan en la base de datos o en variables locales. El modelo de datos se puede ampliar de forma dinámica a través de las respuestas a los cuestionarios. Puede ver los resultados en tiempo real, filtrar las respuestas y analizarlas con gráficos especializados.

Este capítulo detalla cómo realizar la creación y la administración **Encuestas**, administración de campos y páginas, modos de almacenamiento y registros.

Aprenda a crear la primera encuesta en [esta página](getting-started-with-surveys.md).

>[!NOTE]
>
>* Los pasos para la creación de un formulario web estándar se detallan en [este documento](../../web/using/about-web-forms.md).
>
>* La administración de la aplicación web se explica en [este documento](../../web/using/about-web-applications.md). Consulte este capítulo para obtener más información.

## Funcionalidad del ámbito {#campaign-surveys-scope}

En Adobe Campaign, utilice las [aplicaciones web](../../web/using/about-web-forms.md) para lo siguiente:

* Crear formularios de varias páginas.
* Administrar formularios multilingües con una herramienta de traducción integrada.
* Administrar la interfaz gráfica, el diseño de página de varias columnas.
* Añadir personalización y definir la posición del campo.
* Visualización condicional de los campos de encuesta según las respuestas.
* Visualización de la página de condición.
* Comprobación de la información antes de la aprobación, según el tipo de datos esperado (número, dirección de correo electrónico, fechas, etc.), y campos obligatorios.
* Enviar invitaciones/notificaciones por correo electrónico.
* Personalización de páginas de error y finalización.
* Agregar imágenes, vídeos, vínculos de hipertexto, captcha, etc., en formularios.

El módulo opcional de creación de encuestas ofrece una IU fácil de usar y las siguientes funcionalidades adicionales:

* Extensión dinámica de la base de datos: creación de respuestas que no forman parte del modelo de datos inicial. [Más información](../../surveys/using/managing-answers.md#storing-collected-answers).
* Gestión de la puntuación. [Más información](../../surveys/using/managing-answers.md#score-management).
* Visualización aleatoria de preguntas. [Más información](../../surveys/using/building-a-survey.md#adding-questions).
* Seguimiento en tiempo real de las respuestas. [Más información](../../surveys/using/publish-track-and-use-collected-data.md#response-tracking).
* Generación de informes específicos. [Más información](../../surveys/using/publish-track-and-use-collected-data.md#reports-on-surveys).


## Pasos de implementación {#surveys-implementation-steps}

Realice los pasos siguientes para crear y enviar una encuesta y procesar sus resultados:

1. Cree las páginas de encuestas y su contenido (campos de entrada, listas desplegables, preguntas, etc.).
1. Defina cómo se deben guardar las respuestas. Se puede insertar un paso de precarga de datos para que se precargue el formulario con los datos ya existentes en la base de datos. También puede añadir un cuadro de prueba.
1. Publique y luego envíe el estudio a los destinatarios (p. ej., incluya un vínculo en una entrega o en un sitio web).
1. Monitorice las respuestas y vea los informes.

Para obtener más información sobre la configuración y secuenciación de estos pasos, consulte [este documento](../../web/using/about-web-forms.md). En este capítulo solo se detallan las configuraciones específicas de las encuestas.

>[!CAUTION]
>
>Por razones de privacidad, recomendamos utilizar HTTPS para todos los recursos externos.

## Configuración {#settings}

De forma predeterminada, las encuestas se almacenan en el **[!UICONTROL Resources > Online > Web Applications]** nodo del árbol de Adobe Campaign.

La configuración se almacena en las siguientes carpetas:

* **[!UICONTROL Administration > Configuration > Form rendering]**: contiene las plantillas de renderización para la presentación de formularios web (aplicaciones y encuestas).
* **[!UICONTROL Resources > Templates > Web application templates]**: contiene las plantillas de formulario. Para crear un formulario, debe empezar con una plantilla.

>[!NOTE]
>
>Los detalles de configuración están disponibles en [este documento](../../web/using/about-web-forms.md).
