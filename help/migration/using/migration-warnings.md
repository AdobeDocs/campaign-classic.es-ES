---
product: campaign
title: Advertencias de migración
description: Advertencias de migración
audience: migration
content-type: reference
topic-tags: migration-overview
exl-id: 46b46fc9-c7c9-4c74-b5f3-7935d5368520
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 3%

---

# Advertencias de migración{#migration-warnings}

![](../../assets/v7-only.svg)

* El proceso de migración está reservado para usuarios expertos. Debe contar con la asistencia de al menos un experto en bases de datos, un administrador del sistema y un desarrollador de aplicaciones de Adobe Campaign.
* Antes de iniciar la migración, compruebe que los sistemas y los componentes del sistema que utiliza son compatibles con la versión 7. Consulte la [matriz de compatibilidad](../../rn/using/compatibility-matrix.md).
* Si utiliza Adobe Campaign Cloud Messaging (anteriormente intermediario), póngase en contacto con Adobe Campaign antes de iniciar el procedimiento de migración completo.
* Antes de iniciar un proceso de migración, **must** haga una copia de seguridad de sus datos.
* El proceso de migración puede tardar varios días en completarse.
* Adobe Campaign v7 es más estricto que las versiones 5.11 y 6.02 en términos de configuración. Esto sirve principalmente para evitar problemas como la corrupción de datos y para preservar la integridad de los datos en la base de datos. Por consiguiente, es posible que algunas de las funciones ofrecidas en las versiones 5.11 y 6.02 ya no funcionen en la versión 7 y, por tanto, deban adaptarse después de la migración. Antes de poner en producción cualquier cosa, le sugerimos que pruebe sistemáticamente todas las configuraciones, especialmente los flujos de trabajo necesarios para utilizar Adobe Campaign.

>[!NOTE]
>
>También debe consultar la [Antes de iniciar la migración](../../migration/using/before-starting-migration.md) para obtener más información.
