---
product: campaign
title: Introducción a los permisos
description: Obtenga información sobre cómo conceder acceso a las funciones de Campaign
badge: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
feature: Access Management, Permissions
exl-id: 9b616715-33cd-43ba-8548-8d96a179408e
source-git-commit: e1a085384fb27ec165c487c112fbc70fe9738d9e
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 75%

---

# Introducción a los permisos{#access-management}


>[!CAUTION]
>
>A partir de la versión 7.3.1 del Campaign Classic, todos los operadores deben utilizar [Adobe Identity Management System (IMS)](https://helpx.adobe.com/es/enterprise/using/identity.html){target="_blank"} para conectarse a Campaign.
>
>Como parte del esfuerzo por reforzar la seguridad y el proceso de autenticación, Adobe Campaign recomienda migrar todos los operadores existentes en modo de autenticación del inicio de sesión/autenticación nativa con contraseña al Sistema Identity Management de Adobe (IMS). Obtenga información sobre cómo migrar los operadores en [esta página](../../technotes/using/migrate-users-to-ims.md).
> 
>Después de esta migración, tenga en cuenta que ya no se aplica la siguiente sección.  Obtenga información sobre cómo configurar permisos con Adobe IMS en [Documentación de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html?lang=es){target="_blank"}.


Adobe Campaign le permite definir y administrar los derechos asignados a los distintos operadores. Se trata de un conjunto de derechos y restricciones que autorizan o niegan:

* Acceso a determinadas funciones (a través de los derechos asignados),
* Acceso a determinados registros,
* Creación, modificación y eliminación de registros (acciones, contactos, campañas, grupos, etc.).

Los permisos se aplican a perfiles de operador o grupos de operadores.

Se completan por parámetros de seguridad vinculados al modo de conexión del operador a Adobe Campaign. Obtenga más información sobre las zonas de seguridad en [esta página](../../installation/using/security-zones.md).

Existen dos tipos de permisos que puede conceder a un usuario:

* Puede definir grupos de operadores a los que desee atribuir derechos y luego asociar los operadores con uno o varios grupos. Esto permite reutilizar derechos y hacer que los perfiles de operador sean más coherentes. También facilita la administración y el mantenimiento de los perfiles. La creación y la gestión de grupos se presentan en [esta sección](access-management-groups.md).

* Puede atribuir los derechos asignados directamente a los usuarios, en algunos casos para sobrecargar los derechos asignados a través de grupos. Estos derechos se presentan en [esta página](access-management-named-rights.md).

>[!NOTE]
>
>Antes de empezar a definir permisos, Adobe recomienda leer la [lista de comprobación de configuración de seguridad](https://helpx.adobe.com/es/campaign/kb/acc-security.html).

Obtenga información sobre cómo conceder acceso y configurar permisos en estas secciones:

* [Creación de operadores](access-management-operators.md)

* [Definición de grupos](access-management-groups.md)

* [Adición de derechos asignados](access-management-named-rights.md)

* [Administración de acceso a carpetas de Campaign](access-management-folders.md)

* [Matriz de derechos de acceso](access-management-named-rights.md#access-rights-matrix)


Asimismo, consulte:

* [Administración de permisos para flujos de trabajo](../../workflow/using/managing-rights.md)
* [Administración de permisos para marketing distribuido](../../distributed/using/about-distributed-marketing.md#operators-and-entities)
* [Administración de permisos para el módulo de interacción](../../interaction/using/operator-profiles.md)
* [Filtro del acceso a los esquemas](../../configuration/using/filtering-schemas.md)
* [Restricción de la vista PI](../../configuration/using/restricting-pii-view.md)
