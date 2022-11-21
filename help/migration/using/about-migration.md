---
product: campaign
title: Migración al Campaign Classic
description: Obtenga información sobre cómo migrar a Campaign Classic desde una versión de Campaign anterior
audience: migration
content-type: reference
topic-tags: migration-overview
exl-id: 3050238d-6f77-4ffa-9aef-677ab8009388
source-git-commit: 2594e4943ba24ae65d1fc005da589dc674aa2b0f
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 3%

---

# Introducción a la migración{#about-migration}

![](../../assets/v7-only.svg)

Este documento detalla los requisitos previos para una migración, los pasos para una migración a Adobe Campaign Classic v7. Los pasos y la configuración opcional dependen de la configuración.

El proceso de migración debe llevarse a cabo con cautela, sus efectos deben ser examinados de antemano y el procedimiento debe llevarse a cabo con rigor. Solo debe realizarlo un usuario experto. Recomendamos encarecidamente que nos pongamos en contacto con [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) antes de iniciar cualquier procedimiento de migración.

La migración debe probarse previamente en el entorno de prueba/fase para asegurarse de que se ejecuta sin problemas y sin errores. La migración del entorno de producción solo debe realizarse una vez que el entorno de prueba migrado esté completamente validado.

>[!NOTE]
>
>Las nuevas funciones y mejoras que se proporcionan con Adobe Campaign v7 se detallan en la sección [Notas de la versión](../../rn/using/latest-release.md).


## Requisitos previos

* El proceso de migración debe realizarlo un usuario experto. Debe contar con la asistencia de al menos un experto en bases de datos, un administrador del sistema y un desarrollador de aplicaciones de Adobe Campaign.
* Antes de iniciar la migración, compruebe que los sistemas y los componentes del sistema que utiliza son compatibles con v7. [Más información](../../rn/using/compatibility-matrix.md).
* Si utiliza Adobe Campaign Cloud Messaging (implementación intermediaria), póngase en contacto con el servicio de atención al cliente de Adobe antes de empezar.
* Antes de iniciar un proceso de migración, **must** haga una copia de seguridad de sus datos.
* El proceso de migración puede tardar varios días en completarse.
* Adobe Campaign v7 es una versión más segura que las anteriores: esto afecta a las directrices de configuración para evitar problemas como la corrupción de datos y para preservar la integridad de los datos en la base de datos. Como cliente, es responsable de probar todas las configuraciones, incluidos los flujos de trabajo.

Hay más requisitos previos disponibles en [esta página](../../migration/using/before-starting-migration.md).


## Entorno modernizado {#modernizing-your-environment}

Realizar una migración puede ser una oportunidad para actualizar su entorno (motores de base de datos, sistemas operativos). Adobe Campaign recomienda encarecidamente actualizar los entornos de producción a las versiones más recientes.

>[!CAUTION]
>
>Para obtener más información sobre las versiones compatibles con Adobe Campaign v7, consulte la [Matriz de compatibilidad](../../rn/using/compatibility-matrix.md).

## Pasos clave de migración {#key-migration-steps}

El procedimiento general para migrar a Adobe Campaign v7 se detalla en [esta página](../../migration/using/before-starting-migration.md).


## Configuraciones específicas {#specific-configurations}

Los cambios que produce Adobe Campaign v7 también pueden significar que tiene que adaptar ciertas configuraciones específicas desarrolladas en versiones anteriores. Por lo tanto, puede ser necesario realizar una auditoría de todas las configuraciones antes de la migración: póngase en contacto con Adobe Campaign para obtener ayuda.

Por ejemplo, se debe prestar especial atención a la configuración específica de las aplicaciones web, las extensiones de esquema con SQLdata o la clonación de esquema predeterminada. Para obtener más información, consulte [esta página](../../migration/using/configuring-your-platform.md).

Del mismo modo, para responder al aumento de la seguridad dentro de Adobe Campaign, se han modificado algunos mecanismos internos: debe adaptar estas configuraciones según corresponda.

