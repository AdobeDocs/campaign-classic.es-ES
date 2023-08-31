---
product: campaign
title: Acerca de la administración de contenido
description: Introducción al módulo Administrador de contenido de Campaign
badge-v7: label="v7" type="Informative" tooltip="Se aplica a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="También se aplica a Campaign v8"
feature: Landing Pages, Email Design
role: User
exl-id: 87434cc2-1636-4558-ab60-255b7f873c0c
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 100%

---

# Acerca de la administración de contenido{#about-content-management}

El módulo Adobe Campaign Content Manager es un [paquete integrado](../../installation/using/installing-campaign-standard-packages.md) específico de Campaign Classic que puede instalar para crear boletines informativos o sitios web recurrentes. Puede ayudar a crear, validar y publicar los mensajes.

>[!NOTE]
>
>Esta sección hace referencia al módulo de Administración de contenido. Para obtener más información sobre el diseño de contenido de envíos por correo electrónico, consulte [esta sección](defining-the-email-content.md).

El módulo de Administración de contenido incorpora el grupo de trabajo, el flujo de trabajo y la funcionalidad de adición de contenido. Esto permite dar formato automáticamente a un mensaje: correo electrónico, correo, SMS, web, etc.

El uso del gestor de contenido en una entrega permite ofrecer campos de entrada o selección a los operadores de creación de contenido. La presentación y visualización de este contenido, así como los cambios realizados, se administran automáticamente mediante la hoja de estilo.

![](assets/s_ncs_content_create_content_sample.png)

>[!CAUTION]
>
>Todos los cambios realizados en la hoja de estilo se implementan al nivel de la entrega según las plantillas de contenido utilizadas.

El gestor de contenido ofrece las siguientes ventajas:

* Edición de mensajes estructurada mediante interfaces de entrada.
* Separación del contenido de datos y cómo se presenta (generado en formato XML).
* Generación de documentos en varios formatos (HTML, TXT, XML, etc.) basados en hojas de estilo para garantizar la compatibilidad con cartas gráficas.
* Recuperación y agregación automática de flujos de contenido externos.
* Colaboración con flujo de trabajo de validación y verificación de datos.

Sin embargo, este modo de creación de contenido implica varias restricciones, incluidas especialmente:

* Libertad limitada sobre el diseño final del documento.
* El análisis de los requisitos debe ser riguroso para que los usuarios finales no se vean limitados por en caso de que falte una función.
