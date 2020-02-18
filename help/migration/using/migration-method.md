---
title: Método de migración
seo-title: Método de migración
description: Método de migración
seo-description: null
page-status-flag: never-activated
uuid: 6b954d5b-cfa3-43c6-ac3d-da9185e9e9d1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migration-overview
discoiquuid: 3ac779a7-1f91-4c1c-a439-10d01697326a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9f7cf3d530f141a661df5fcc8cbcf0bb4c8d3e89

---


# Método de migración{#migration-method}

## Modernización del entorno {#modernizing-your-environment}

Realizar una migración puede ser una oportunidad para actualizar su entorno (motores de base de datos, sistemas operativos). Adobe Campaign recomienda encarecidamente actualizar los entornos de producción a las versiones más recientes.

Las bases de datos y los sistemas operativos de la versión de 32 bits siguen siendo compatibles con la versión v7, pero ya no lo serán en futuras versiones de Adobe Campaign. Le recomendamos encarecidamente que actualice su plataforma a 64 bits lo antes posible.

En la versión 6.02, el modo &quot;multizona horaria&quot; solo estaba disponible para los motores de base de datos PostgreSQL. Ahora se ofrece sin importar el tipo de motor de base de datos que se utilice. Le recomendamos encarecidamente que transforme su base en una base &quot;multizona horaria&quot;. Para obtener más información sobre esto, consulte la sección [Husos](../../migration/using/general-configurations.md#time-zones) horarios.

>[!IMPORTANT]
>
>Algunas versiones de software admitidas en Adobe Campaign 5.11 y 6.02 ya no son compatibles con Adobe Campaign v7.
>
>Para obtener más información sobre las versiones compatibles con Adobe Campaign, consulte la matriz [de](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)compatibilidad.

## Pasos de migración clave {#key-migration-steps}

El procedimiento general para migrar a Adobe Campaign v7 se describe en la sección [Antes de iniciar la migración](../../migration/using/before-starting-migration.md) .

Los pasos de implementación para la migración a Adobe Campaign v7 se describen en la sección Requisitos [previos para la migración a Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) .

Las configuraciones requeridas dependen de las configuraciones existentes y de la versión inicial de la plataforma. Estos se describen en la sección Configuraciones [](../../migration/using/general-configurations.md) generales.

## Configuraciones específicas {#specific-configurations}

Los cambios realizados por Adobe Campaign v7 también pueden significar que debe adaptar determinadas configuraciones específicas desarrolladas en versiones anteriores. Por lo tanto, puede que sea necesario realizar una auditoría de todas las configuraciones antes de la migración: póngase en contacto con Adobe Campaign para obtener ayuda.

Por ejemplo, se debe prestar especial atención a la configuración específica de las aplicaciones Web, las extensiones de esquema con SQLdata o la clonación de esquemas predeterminados. Para obtener más información, consulte la sección [Configuración de la plataforma](../../migration/using/configuring-your-platform.md) .

Del mismo modo, para responder a la mayor seguridad dentro de Adobe Campaign, se han modificado algunos mecanismos internos: debe adaptar estas configuraciones correspondientes.
