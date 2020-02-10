---
title: Advertencias de migración
seo-title: Advertencias de migración
description: Advertencias de migración
seo-description: null
page-status-flag: never-activated
uuid: 35361471-881c-4aaf-a57b-ed7e89a97eae
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migration-overview
discoiquuid: 1fa1fe0f-c392-413a-9fa0-d1b4e10e2e5e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f460c79a763c6a207656c54351a4c685f2a78a03

---


# Advertencias de migración{#migration-warnings}

* El proceso de migración está reservado para usuarios expertos. Debe contar con la asistencia de al menos un experto en bases de datos, un administrador del sistema y un desarrollador de aplicaciones de Adobe Campaign.
* Antes de iniciar la migración, compruebe que los sistemas y los componentes del sistema que utiliza son compatibles con la versión 7. Consulte la matriz [de](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)compatibilidad.
* Si utiliza la mensajería en la nube de Adobe Campaign (anteriormente de fuentes intermedias), póngase en contacto con Adobe Campaign antes de iniciar el procedimiento de migración completo.
* Antes de iniciar un proceso de migración, **debe** realizar una copia de seguridad de los datos.
* El proceso de migración puede tardar varios días en completarse.
* Adobe Campaign v7 es más estricto que las versiones 5.11 y 6.02 en cuanto a la configuración. Esto sirve principalmente para evitar problemas como la corrupción de datos y para preservar la integridad de los datos en la base de datos. Por consiguiente, es posible que determinadas funciones ofrecidas en las versiones 5.11 y v6.02 ya no funcionen en la versión v7 y que, por lo tanto, deban adaptarse después de la migración. Antes de poner en producción cualquier cosa, le sugerimos que pruebe sistemáticamente todas las configuraciones, especialmente los flujos de trabajo necesarios para utilizar Adobe Campaign.

>[!NOTE]
>
>También debe consultar la sección [Antes de iniciar la migración](../../migration/using/before-starting-migration.md) .

