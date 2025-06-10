---
product: campaign
title: Introducción a los permisos
description: Obtenga información sobre cómo conceder acceso a las funciones de Campaign
badge: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
feature: Access Management, Permissions
exl-id: 9b616715-33cd-43ba-8548-8d96a179408e
source-git-commit: 42cec0e9bede94a2995a5ad442822512bda14f2b
workflow-type: ht
source-wordcount: '309'
ht-degree: 100%

---

# Introducción a los permisos{#access-management}


>[!CAUTION]
>
>A partir de la version 7.3.1 de Campaign Classic, todos los operadores deben utilizar el [sistema de administración de identidades (IMS) de Adobe](https://helpx.adobe.com/es/enterprise/using/identity.html){target="_blank"} para conectarse a Campaign.
>
>Además, con el objetivo de reforzar la seguridad y el proceso de autenticación, Adobe Campaign recomienda encarecidamente migrar el modo de autenticación de los operadores existentes de la autenticación nativa de inicio de sesión/contraseña a Adobe Identity Management System (IMS). Aprenda a migrar los operadores en [esta página](../../technotes/using/migrate-users-to-ims.md).
> 
>Después de esta migración, tenga en cuenta que ya no se aplica la siguiente sección.  Obtenga información sobre cómo configurar permisos con Adobe IMS en la [documentación de la versión 8 de Campaign](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html?lang=es){target="_blank"}.


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
> * Antes de empezar a definir permisos, Adobe recomienda leer la [lista de comprobación de configuración de seguridad](https://helpx.adobe.com/es/campaign/kb/acc-security.html).
> * Para obtener más información sobre permisos, consulte la explicación detallada en la [documentación de la versión 8 de Campaign](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/admin/permissions/gs-permissions){target=_blank}.

<!--

Learn how to grant access and set up permissions in these sections:

* [Create operators](access-management-operators.md)

* [Define groups](access-management-groups.md)

* [Add Named rights](access-management-named-rights.md)

* [Manage Campaign folder access](access-management-folders.md)

* [Access rights matrix](access-management-named-rights.md#access-rights-matrix)


See also:

* [Manage permissions for workflows](../../workflow/using/managing-rights.md)
* [Manage permissions for distributed marketing](../../distributed/using/about-distributed-marketing.md#operators-and-entities)
* [Manage permissions for the interaction module](../../interaction/using/operator-profiles.md)
* [Filter access to schemas](../../configuration/using/filtering-schemas.md)
* [Restricting PI view](../../configuration/using/restricting-pii-view.md)
-->