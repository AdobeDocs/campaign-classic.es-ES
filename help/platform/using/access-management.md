---
product: campaign
title: Introducción a los permisos
description: Obtenga información sobre cómo conceder acceso a las funciones de Campaign
badge: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
feature: Access Management, Permissions
exl-id: 9b616715-33cd-43ba-8548-8d96a179408e
source-git-commit: a5bbd2e6c102a8afa4cd5931b77b0c83705a7bfa
workflow-type: ht
source-wordcount: '256'
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

>[!BEGINTABS]

>[!TAB Documentación de permisos]

Para obtener más información sobre los **permisos de Adobe Campaign**, consulte la **[documentación de Campaign v8 (consola)](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/admin/permissions/gs-permissions?lang=es#_blank){target=_blank}**.

[![imagen](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/admin/permissions/gs-permissions?lang=es#_blank){target=_blank}


>[!TAB Administración de permisos en carpetas]

Para obtener más información sobre cómo definir **permisos en carpetas**, consulte la **[documentación de Campaign v8 (consola)](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/admin/permissions/folder-permissions){target=_blank}**.

[![imagen](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/admin/permissions/folder-permissions){target=_blank}


>[!TAB Autenticación nativa]

La autenticación nativa con un nombre de usuario/contraseña sigue estando disponible en la versión 7 de Campaign. Sin embargo, para reforzar la seguridad y el proceso de autenticación, Adobe Campaign recomienda muy especialmente [migrar el modo de autenticación del usuario final](../../technotes/using/ac-ims.md) desde la autenticación nativa al sistema de administración de identidades (IMS) de Adobe. Tenga en cuenta que en Campaign v8 no se permite la conexión con una autenticación nativa. 

[![imagen](../../assets/do-not-localize/learn-more-button.svg)](../../technotes/using/ac-ims.md)


>[!ENDTABS]



<!--
The permissions apply to operator profiles or operator groups.

They are completed by safety parameters linked to the operator's connection mode to Adobe Campaign. For more about security zones in [this page](../../installation/using/security-zones.md).

There are two types of permissions you can grant to a user:

* You can define groups of operators to which you attribute rights, then associate the operators with one or more groups. This enables you to reuse rights and make operator profiles more consistent. It also facilitates the management and maintenance of profiles. Group creation and management are presented in [this section](access-management-groups.md).

* You can attribute named rights directly to users, in some cases to overload the rights allocated via groups. These rights are presented in [this page](access-management-named-rights.md).

>[!NOTE]
>
> * Before starting defining permissions, Adobe recommends you to read the [Security configuration checklist](https://helpx.adobe.com/es/campaign/kb/acc-security.html).
> * To learn more about permissions, please refer to the detailed explanation on the [Campaign v8 documentation](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/admin/permissions/gs-permissions){target=_blank}.

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