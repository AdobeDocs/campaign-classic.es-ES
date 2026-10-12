---
title: Migración de operadores de Campaign a Adobe Identity Management System (IMS)
description: Obtenga información sobre cómo migrar operadores de Campaign a Adobe Identity Management System (IMS)
exl-id: f01948c7-b523-492d-a4e8-67f4adde5fc5
TQID: 'https://experienceleague.adobe.com/drpNkA9cj7Prid--GixHMQ48CO7ZC9qqX4w5fnTiD88'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b12f6872-9271-4369-85e5-86969a0b99a2
    internal-label: APIs
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
    internal-label: Integrations
subfeature_v2:
  - id: efa38731-2723-4334-8d8b-a778af834835
    internal-label: Access management
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
    internal-label: Analytics integration
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: 4bc1e76d129c6a6aa15b7e3915232043bd6f4286
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 4%
---
# Migración de operadores de Campaign a Adobe Identity Management System (IMS) {#migrate-users-to-ims}

Como parte del esfuerzo por reforzar la seguridad y el proceso de autenticación, Adobe Campaign recomienda migrar el modo de autenticación del usuario final de la autenticación nativa de inicio de sesión/contraseña a Adobe Identity Management System (IMS). Todos los operadores deben implementar [Adobe Identity Management System (IMS)](https://helpx.adobe.com/es/enterprise/using/identity.html){target="_blank"} para conectarse a Campaign.

Obtenga más información acerca de esta migración en [esta página](ac-ims.md).

## ¿Qué ha cambiado? {#move-to-ims-changes}

Con Campaign Classic, todos los usuarios normales ya pueden conectarse a la consola del cliente de Adobe Campaign con su Adobe ID, a través de Adobe Identity Management System (IMS). Sin embargo, las conexiones de usuario y contraseña siguen estando disponibles. Esto ya no se permitirá con Campaign v8.

Además, como parte del esfuerzo por reforzar la seguridad y el proceso de autenticación, la aplicación cliente de Adobe Campaign ahora llama a las API de Campaign directamente mediante el token de cuenta técnica de IMS. La migración para operadores técnicos se detalla en un artículo dedicado, disponible en [esta página](ims-migration.md).

Este cambio ya se aplica en Campaign Classic v7 y será **obligatorio** para pasar a Campaign v8.

Adobe le apoya en este esfuerzo de migración. Puede encontrar información detallada sobre el contexto y las directrices paso a paso en el siguiente artículo.

## ¿Se ha visto afectado?{#migrate-ims-impacts}

Este procedimiento se aplica a todos los usuarios de Campaign que aún no se hayan conectado a Campaign con su Adobe ID.

Si los operadores de su organización se conectan a la consola del cliente de Campaign mediante su inicio de sesión/contraseña (también conocido como. (autenticación nativa), se ha visto afectado y debe migrar estos operadores a Adobe IMS como se detalla a continuación.

La migración a [Adobe Identity Management System (IMS)](https://helpx.adobe.com/es/enterprise/using/identity.html){target="_blank"} es un imperativo de seguridad para hacer que sus entornos sean seguros y estandarizados, ya que la mayoría de las otras soluciones y aplicaciones de Adobe Experience Cloud ya están en IMS.

Este cambio es aplicable a partir de la versión 7.4.1 de Campaign Classic (y las últimas [versiones compatibles con la migración IMS](ac-ims.md#ims-versions)) y es **obligatorio** para pasar a la versión 8 de Adobe Campaign.

>[!IMPORTANT]
>
>**Impacto del acceso al Panel de control de Campaign**
>
>Una vez migrados los usuarios a IMS, tenga en cuenta que cualquier Perfil de producto de Adobe Admin Console que contenga la palabra &quot;admin&quot; en su nombre (como &quot;Administradores&quot;, &quot;admin&quot;, &quot;administradores&quot;, &quot;administrador de aprobación&quot;, etc.) concederá automáticamente acceso al Panel de control de Campaign de Campaign. Panel de control de Campaign es una herramienta de autoservicio que permite realizar cambios significativos en las instancias de Campaign.
>
>Revise atentamente las convenciones de nomenclatura de Perfil de producto para asegurarse de que solo los usuarios autorizados tengan acceso al Panel de control de Campaign. Obtenga más información acerca de la administración de permisos de Panel de control de Campaign en la [documentación de Panel de control de Campaign](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=es){target="_blank"}.


## Cómo migrar entornos híbridos y locales {#ims-migration-procedure-on-prem}

A continuación se enumeran los pasos clave para esta migración:

1. Actualice sus entornos a Campaign v7.4.1 (o una [versión compatible con la migración IMS](#ims-versions)).
1. Después de la actualización, aún puede crear nuevos usuarios con ambos métodos, como usuario nativo o con IMS.
1. El administrador interno de Campaign debe configurar Adobe IMS como se detalla en [esta sección](../../integrations/using/configuring-ims.md).
1. A continuación, añada correos electrónicos únicos a todos los usuarios nativos en la consola del cliente de Campaign. Este paso se detalla en [esta sección](https://experienceleague.adobe.com/en/docs/campaign/technotes-ac/tn-new/migrate-users-to-ims#ims-migration-id){target="_blank"} (Documentación de Campaign v8).
1. Cree usuarios y perfiles de producto en Adobe Admin Console como se detalla en [Documentación de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/manage-permissions.html){target="_blank"}.
1. Habilite la opción **Conectar con Adobe ID** para todos los operadores.
1. Implemente Adobe IMS para su conexión según se detalla en [esta página](../../integrations/using/implementing-ims.md).

También puede migrar sus operadores técnicos a Adobe Developer Console como se detalla en [esta nota técnica](ims-migration.md).

## Preguntas frecuentes {#ims-migration-faq}

Para obtener respuestas a preguntas comunes sobre la migración (creación de usuarios después de la migración, adición de correos electrónicos para usuarios nativos, inicio de sesión mediante IMS, tiempo de inactividad, organizaciones que ya utilizan IMS, visualización del tipo de autenticación de los operadores), consulte la [nota técnica de Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/technotes-ac/tn-new/migrate-users-to-ims#ims-migration-faq){target=_blank} (documentación de Campaign v8).

>[!MORELIKETHIS]
>
>* [Migración de usuarios técnicos a la consola de Adobe Developer](ims-migration.md)
>* [Notas de la versión de Adobe Campaign Classic v7](../../rn/using/latest-release.md)
>* [Qué es Adobe Identity Management System (IMS)](https://helpx.adobe.com/es/enterprise/using/identity.html){target="_blank"}
