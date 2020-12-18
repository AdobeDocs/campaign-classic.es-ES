---
solution: Campaign Classic
product: campaign
title: Método de migración
description: Método de migración
audience: migration
content-type: reference
topic-tags: migration-overview
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 1%

---


# Método de migración{#migration-method}

## Modernización del entorno {#modernizing-your-environment}

Realizar una migración puede ser una oportunidad para actualizar el entorno (motores de base de datos, sistemas operativos). Adobe Campaign recomienda encarecidamente actualizar sus entornos de producción a las versiones más recientes.

Las bases de datos y los sistemas operativos de la versión de 32 bits siguen siendo compatibles con la versión v7, pero ya no lo serán en futuras versiones de Adobe Campaign. Le recomendamos encarecidamente que actualice su plataforma a 64 bits lo antes posible.

En la versión 6.02, el modo &quot;multizona horaria&quot; solo estaba disponible para los motores de base de datos PostgreSQL. Ahora se ofrece sin importar el tipo de motor de base de datos que se utilice. Le recomendamos encarecidamente que transforme su base en una base &quot;multizona horaria&quot;. Para obtener más información sobre esto, consulte la sección [Husos horarios](../../migration/using/general-configurations.md#time-zones).

>[!IMPORTANT]
>
>Algunas versiones de software admitidas en Adobe Campaign 5.11 y 6.02 ya no son compatibles con Adobe Campaign v7.
>
>Para obtener más información sobre las versiones admitidas por Adobe Campaign, consulte la [matriz de compatibilidad](../../rn/using/compatibility-matrix.md).

## Pasos clave de migración {#key-migration-steps}

El procedimiento general para migrar a Adobe Campaign v7 se detalla en la sección [Antes de iniciar la migración](../../migration/using/before-starting-migration.md).

Los pasos de implementación para la migración a Adobe Campaign v7 se detallan en la sección [Requisitos previos para la migración a Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md).

Las configuraciones requeridas dependen de las configuraciones existentes y de la versión inicial de la plataforma. Estos se describen en la sección [Configuraciones generales](../../migration/using/general-configurations.md).

## Configuraciones específicas {#specific-configurations}

Los cambios producidos por Adobe Campaign v7 también pueden significar que debe adaptar determinadas configuraciones específicas desarrolladas en versiones anteriores. Por lo tanto, puede que sea necesario realizar una auditoría de todas las configuraciones antes de la migración: póngase en contacto con Adobe Campaign para obtener ayuda.

Por ejemplo, se debe prestar especial atención a la configuración específica para Aplicaciones web, extensiones de esquema con SQLdata o clonación de esquemas lista para usar. Para obtener más información, consulte la sección [Configuración de la plataforma](../../migration/using/configuring-your-platform.md).

Del mismo modo, para responder al aumento de la seguridad en Adobe Campaign, se han modificado algunos mecanismos internos: debe adaptar estas configuraciones correspondientes.
