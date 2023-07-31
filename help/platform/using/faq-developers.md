---
product: campaign
title: Preguntas frecuentes para desarrolladores
description: Preguntas frecuentes para desarrolladores
feature: Troubleshooting, Configuration
badge-v7-only: label="v7" type="Informative" tooltip="Solo se aplica a Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 20552812-5c58-4d48-9636-d5135197685d
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 98%

---

# Preguntas frecuentes para desarrolladores {#dev-faq}



Como solución abierta, Adobe Campaign está listo para la personalización y el desarrollo de aplicaciones avanzadas.

## ¿Qué es el modelo de datos de Campaign? {#what-is-the-campaign-data-model}

El modelo de datos conceptuales de la base de datos de Adobe Campaign consta de un conjunto de tablas integradas y su interacción. La estructura física y lógica de los datos que se llevan en la aplicación se describe en XML. Obedece a una gramática específica de Adobe Campaign, denominada esquema. Para obtener más información sobre Adobe Campaign, [consulte esta sección](../../configuration/using/about-schema-edition.md).

[Haga clic aquí para obtener más información sobre el modelo de datos de Campaign](https://experienceleague.adobe.com/docs/campaign-classic/using/configuring-campaign-classic/data-model/about-data-model.html?lang=es).

Las prácticas recomendadas se enumeran [en este artículo](../../configuration/using/data-model-best-practices.md).

## ¿Cómo se trabaja con los esquemas de Campaign? {#how-to-work-with-campaign-schemas-}

En Adobe Campaign, los esquemas de datos se utilizan para:

* Definir el modo en que los objetos de datos de la aplicación están vinculados a las tablas de bases de datos subyacentes.
* Definir vínculos entre los diferentes objetos de datos dentro de la aplicación de Campaign.
* Definir y describir los campos individuales incluidos en cada objeto.

Lea sobre [Tablas y esquemas](../../configuration/using/about-schema-edition.md) para comprender cómo trabajar con el esquema de datos, ampliar y personalizar Campaign para satisfacer sus necesidades.

## ¿Cómo se utiliza una tabla de destinatarios personalizada? {#how-to-use-a-custom-recipient-table-}

Puede crear e implementar una tabla de destinatarios no estándar en Campaign para enviar los mensajes.

[Haga clic aquí para obtener más información](../../configuration/using/about-custom-recipient-table.md)

## ¿Cuáles son las mejores prácticas para definir las consultas en Campaign?  {#what-are-the-best-practices-to-define-queries-in-campaign-}

El editor de consultas de Adobe Campaign es una herramienta poderosa para explorar datos y crear segmentos.

La herramienta de consulta de Adobe Campaign se encuentra en varios niveles del software: para crear una población objetivo, segmentar clientes, extraer y filtrar logs de seguimiento, crear filtros, etc.

Puede consultar la base de datos de Campaign utilizando el editor de consultas genérico. Se accede a través del menú **Tools > Generic query editor...** Permite extraer información almacenada en una base de datos y organizar, agrupar, ordenar, etc. Por ejemplo, el usuario puede recuperar los destinatarios que han hecho clic un determinado número de veces en el vínculo de un boletín durante un periodo determinado. Esta herramienta le permite recopilar, ordenar y mostrar los resultados según sus necesidades. Esta herramienta combina todas las posibilidades de consultas de Adobe Campaign. Por ejemplo, le permite crear y guardar filtros de restricción. Esto significa que un filtro de usuario creado en el editor de consultas genérico se puede utilizar en el cuadro de consulta de un flujo de trabajo de objetivos, etc.

Las consultas se crean utilizando campos de la tabla seleccionada o utilizando una fórmula. [En esta página](../../platform/using/about-queries-in-campaign.md) se describen los principios principales para crear una consulta en la base de datos de Campaign.

[Haga clic aquí](../../workflow/using/query.md) para descubrir el editor de consultas de Campaign.

## ¿Cómo puedo importar un paquete de datos?  {#how-can-i-import-a-data-package-}

Adobe Campaign permite exportar o importar la configuración y los datos de la plataforma a través de un sistema de paquetes. Los paquetes de datos permiten que las entidades de la base de datos de Adobe Campaign se muestren mediante archivos en formato XML. Cada entidad contenida en un paquete se representa con todos sus datos.

El principio de los paquetes de datos es exportar una configuración de datos e integrarla en otro sistema de Adobe Campaign.

[Haga clic aquí](../../platform/using/working-with-data-packages.md) para aprender a trabajar con paquetes de datos para importar y exportar configuraciones de Campaign.

## ¿Dónde puedo encontrar la lista de las API de Campaign Classic?  {#where-can-i-find-the-list-of-campaign-classic-apis}

Todas las API de Campaign, con su descripción completa, están disponibles en esta [documentación dedicada](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=es).
