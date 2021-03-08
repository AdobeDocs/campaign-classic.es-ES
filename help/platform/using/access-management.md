---
solution: Campaign Classic
product: campaign
title: Introducción a los permisos
description: Obtenga información sobre cómo conceder acceso a las funciones de Campaign
audience: platform
content-type: reference
topic-tags: administration-basics
translation-type: tm+mt
source-git-commit: f7e4f129a96e80ec169428057f661165d8b967c9
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 66%

---


# Introducción a los permisos{#access-management}

Adobe Campaign le permite definir y administrar los derechos asignados a los distintos operadores. Se trata de un conjunto de derechos y restricciones que autorizan o niegan:

* Acceso a determinadas funciones (a través de los derechos asignados),
* Acceso a determinados registros,
* Creación, modificación y eliminación de registros (acciones, contactos, campañas, grupos, etc.).

Los permisos se aplican a perfiles de operador o grupos de operadores.

Se completan por parámetros de seguridad vinculados al modo de conexión del operador a Adobe Campaign. Para obtener más información sobre las zonas de seguridad en [esta página](../../installation/using/configuring-campaign-server.md#defining-security-zones).

Existen dos tipos de permisos que puede conceder a un usuario:

* Puede definir grupos de operadores a los que desee atribuir derechos y luego asociar los operadores con uno o varios grupos. Esto permite reutilizar derechos y hacer que los perfiles de operador sean más coherentes. También facilita la administración y el mantenimiento de los perfiles. La creación y administración de grupos se presentan en [esta sección](access-management-groups.md).

* Puede atribuir los derechos asignados directamente a los usuarios, en algunos casos para sobrecargar los derechos asignados a través de grupos. Estos derechos se presentan en [esta página](access-management-named-rights.md).

>[!NOTE]
>
>Antes de empezar a definir permisos, Adobe recomienda leer la [lista de comprobación de configuración de seguridad](https://helpx.adobe.com/es/campaign/kb/acc-security.html).

Obtenga información sobre cómo conceder acceso y configurar permisos en estas secciones:

* [Crear operadores](access-management-operators.md)

* [Definir grupos](access-management-groups.md)

* [Agregar derechos asignados](access-management-named-rights.md)

* [Administrar acceso a carpetas de Campaign](access-management-folders.md)

* [Matriz de derechos de acceso](access-management-named-rights.md#access-rights-matrix)


Asimismo, consulte lo siguiente:

* [Administración de permisos para flujos de trabajo](../../workflow/using/managing-rights.md)
* [Administrar permisos para marketing distribuido](../../campaign/using/about-distributed-marketing.md#operators-and-entities)
* [Administrar permisos para el módulo de interacción](../../interaction/using/operator-profiles.md)
* [Filtrar el acceso a los esquemas](../../configuration/using/filtering-schemas.md)
* [Restricción de la vista PI](../../configuration/using/restricting-pii-view.md)
