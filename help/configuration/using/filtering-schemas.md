---
solution: Campaign Classic
product: campaign
title: Filtrado de esquemas
description: Filtrado de esquemas
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 693e38477b318ee44e0373a04d8524ddf128fe36
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---


# Filtrar esquemas{#filtering-schemas}

## Filtros del sistema {#system-filters}

Puede filtrar el acceso al esquema para usuarios específicos, según sus permisos. Los filtros de sistema permiten administrar los permisos de lectura y escritura de las entidades detalladas en los esquemas mediante parámetros **readAccess** y **writeAccess**.

>[!NOTE]
>
>Esta restricción solo se aplica a usuarios no técnicos: un usuario técnico, con permisos relacionados o utilizando un flujo de trabajo, podrá recuperar y actualizar datos.

* **readAccess**: proporciona acceso de solo lectura a los datos del esquema.

   **Advertencia** : Todas las tablas vinculadas deben configurarse con la misma restricción. Esta configuración puede afectar al rendimiento.

* **writeAccess**: proporciona acceso de escritura a los datos del esquema.

Estos filtros se introducen en el nivel principal **element** de los esquemas y, como se muestra en los ejemplos siguientes, se pueden formar para restringir el acceso.

* Restringir permisos de ESCRITURA

   En este caso, el filtro se utiliza para no permitir permisos WRITE en el esquema para operadores sin el permiso ADMINISTRATION. Esto significa que solo los administradores tendrán permisos de escritura en las entidades descritas por este esquema.

   ```
   <sysFilter name="writeAccess">      
    <condition enabledIf="hasNamedRight('admin')=false" expr="FALSE"/>    
   </sysFilter>
   ```

* Restringir permisos de lectura y escritura:

   En este caso, el filtro se utiliza para no permitir permisos de lectura y escritura en el esquema para todos los operadores. Solo la cuenta **internal**, representada por la expresión &quot;$(loginId)!=0&quot;, tiene estos permisos.

   ```
   <sysFilter name="readAccess"> 
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   
   <sysFilter name="writeAccess">  
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   ```

   Los posibles valores de atributo **expr** utilizados para definir la condición son TRUE o FALSE.

>[!NOTE]
>
>Si no se especifica ningún filtro, todos los operadores tendrán permisos de lectura y escritura en el esquema.

## Proteja los esquemas integrados {#protecting-built-in-schemas}

De forma predeterminada, los esquemas integrados solo son accesibles con permisos WRITE para operadores con derechos de ADMINISTRACIÓN:

* ncm:publishing
* nl:monitorización
* nms:calendar
* xtk:builder
* xtk:conexiones
* xtk:dbInit
* xtk:entityBackupNew
* xtk:entityBackupOriginal
* xtk:entityOriginal
* xtk:form
* xtk:funcList
* xtk:fusión
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
* xtk:schema
* xtk:scriptContext
* xtk:specFile
* xtk:sql
* xtk:sqlSchema
* xtk:srcSchema
* xtk:strings
* xtk:xslt

>[!IMPORTANT]
>
>Los permisos de lectura y escritura para el esquema **xtk:sessionInfo** solo son accesibles desde la cuenta interna de una instancia de Adobe Campaign.

## Modificar filtros del sistema de esquemas integrados {#modifying-system-filters-of-built-in-schemas}

Puede seguir modificando los filtros del sistema de los esquemas predeterminados que están protegidos por defecto debido a problemas de compatibilidad con versiones anteriores.

>[!NOTE]
>
>Sin embargo, Adobe recomienda no modificar los parámetros predeterminados para garantizar una seguridad óptima.

1. Cree una extensión para el esquema correspondiente o abra una extensión existente.
1. Agregue un elemento secundario **`<sysfilter name="<filter name>" _operation="delete"/>`** en el elemento principal para eliminar la aplicación del filtro en el mismo esquema de origen.
1. Si lo desea, puede agregar un nuevo filtro, como se detalla en [Filtros del sistema](#system-filters).

