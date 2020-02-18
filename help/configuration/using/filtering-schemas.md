---
title: Filtrado de esquemas
seo-title: Filtrado de esquemas
description: Filtrado de esquemas
seo-description: null
page-status-flag: never-activated
uuid: 04a90785-3084-42fd-85af-77bc28687579
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 64d4c5b8-db0b-4287-8d30-4bf09878a401
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# Filtrado de esquemas{#filtering-schemas}

## Filtros del sistema {#system-filters}

Puede filtrar el acceso al esquema para usuarios específicos, según sus permisos. Los filtros del sistema permiten administrar los permisos de lectura y escritura de las entidades detalladas en los esquemas, mediante parámetros **readAccess** y **writeAccess** .

>[!NOTE]
>
>Esta restricción solo se aplica a usuarios no técnicos: un usuario técnico, con permisos relacionados o utilizando un flujo de trabajo, podrá recuperar y actualizar datos.

* **readAccess**: proporciona acceso de solo lectura a los datos de esquema.

   **Advertencia** : Todas las tablas vinculadas deben configurarse con la misma restricción. Esta configuración puede afectar al rendimiento.

* **writeAccess**: proporciona acceso de escritura a los datos de esquema.

Estos filtros se introducen en el nivel de **elemento** principal de los esquemas y, como se muestra en los ejemplos siguientes, se pueden formar para restringir el acceso.

* Restringir permisos de escritura

   Aquí, el filtro se utiliza para no permitir permisos de ESCRITURA en el esquema para operadores sin el permiso de ADMINISTRACIÓN. Esto significa que solo los administradores tendrán permisos de escritura en las entidades descritas en este esquema.

   ```
   <sysFilter name="writeAccess">      
    <condition enabledIf="hasNamedRight('admin')=false" expr="FALSE"/>    
   </sysFilter>
   ```

* Restringir permisos de lectura y escritura:

   Aquí, el filtro se utiliza para no permitir permisos de lectura y escritura en el esquema para todos los operadores. Solo la cuenta **interna** , representada por la expresión &quot;$(loginId)!=0&quot;, tiene estos permisos.

   ```
   <sysFilter name="readAccess"> 
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   
   <sysFilter name="writeAccess">  
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   ```

   Los posibles valores de atributos **expr** utilizados para definir la condición son TRUE o FALSE.

>[!NOTE]
>
>Si no se especifica ningún filtro, todos los operadores tendrán permisos de lectura y escritura en el esquema.

## Protección de esquemas integrados {#protecting-built-in-schemas}

De forma predeterminada, los esquemas integrados solo son accesibles con permisos de ESCRITURA para los operadores con derechos de ADMINISTRACIÓN:

* ncm:publicación
* nl:supervisión
* nms:calendar
* xtk:builder
* xtk:conexiones
* xtk:dbInit
* xtk:entityBackupNew
* xtk:entityBackupOriginal
* xtk:entityOriginal
* xtk:form
* xtk:funcList
* xtk:fusion
* xtk:image
* xtk:javascript
* xtk:jssp
* xtk:jst
* xtk:navtree
* xtk:operatorGroup
* xtk:package
* xtk:queryDef
* xtk:resourceMenu
* xtk:rights
* xtk:esquema
* xtk:scriptContext
* xtk:especificaciónFile
* xtk:sql
* xtk:sqlSchema
* xtk:srcSchema
* xtk:cadenas
* xtk:xslt

>[!IMPORTANT]
>
>Los permisos de lectura y escritura para el esquema **xtk:sessionInfo** solo son accesibles desde la cuenta interna de una instancia de Adobe Campaign.

## Modificación de los filtros de sistema de los esquemas integrados {#modifying-system-filters-of-built-in-schemas}

Aún puede modificar los filtros del sistema de los esquemas predeterminados que están protegidos de forma predeterminada debido a problemas de compatibilidad con versiones anteriores.

>[!NOTE]
>
>Sin embargo, Adobe recomienda no modificar los parámetros predeterminados para garantizar una seguridad óptima.

1. Cree una extensión para el esquema correspondiente o abra una extensión existente.
1. Agregue un elemento secundario **`<sysfilter name="<filter name>" _operation="delete"/>`** en el elemento principal para eliminar la aplicación del filtro en el mismo esquema de origen.
1. Si lo desea, puede agregar un nuevo filtro, como se detalla en los filtros [](#system-filters)del sistema.

