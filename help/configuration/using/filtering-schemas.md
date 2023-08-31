---
product: campaign
title: Filtrado de esquemas
description: Filtrado de esquemas
feature: Custom Resources
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
exl-id: 009bed25-cd35-437c-b789-5b58a6d2d7c6
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 3%

---

# Filtrar esquemas{#filtering-schemas}

## Filtros del sistema {#system-filters}

Puede filtrar el acceso a esquemas a usuarios específicos, según sus permisos. Los filtros del sistema permiten administrar los permisos de lectura y escritura de las entidades detalladas en los esquemas mediante **readAccess** y **writeAccess** parámetros.

>[!NOTE]
>
>Esta restricción se aplica solo a los usuarios no técnicos: un usuario técnico, con permisos relacionados o que utilice un flujo de trabajo, podrá recuperar y actualizar datos.

* **readAccess**: proporciona acceso de solo lectura a los datos del esquema.

  **Advertencia** : todas las tablas vinculadas deben configurarse con la misma restricción. Esta configuración puede afectar al rendimiento.

* **writeAccess**: proporciona acceso de escritura a los datos de esquema.

Estos filtros se introducen en la **elemento** nivel de los esquemas y, como se muestra en los ejemplos siguientes, se puede formar para restringir el acceso.

* Restringir permisos de ESCRITURA

  En este caso, el filtro se utiliza para impedir los permisos de ESCRITURA en el esquema a los operadores sin el permiso ADMINISTRACIÓN. Esto significa que solo los administradores tendrán permisos de escritura en las entidades descritas en este esquema.

  ```
  <sysFilter name="writeAccess">      
   <condition enabledIf="hasNamedRight('admin')=false" expr="FALSE"/>    
  </sysFilter>
  ```

* Restrinja los permisos de LECTURA y ESCRITURA:

  En este caso, el filtro se utiliza para impedir los permisos de LECTURA y ESCRITURA en el esquema para todos los operadores. Solo el **interno** cuenta, representada por la expresión &quot;$(loginId)!=0&quot;, tiene estos permisos.

  ```
  <sysFilter name="readAccess"> 
   <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
  </sysFilter>
  
  <sysFilter name="writeAccess">  
   <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
  </sysFilter>
  ```

  Posible **expr** Los valores de atributo utilizados para definir la condición son TRUE o FALSE.

>[!NOTE]
>
>Si no se especifica ningún filtro, todos los operadores tendrán permisos de lectura y escritura en el esquema.

## Esquemas integrados de Protect {#protecting-built-in-schemas}

De forma predeterminada, solo se puede acceder a los esquemas integrados con permisos de ESCRITURA para operadores con derechos de ADMINISTRACIÓN:

* ncm:publicar
* nl:monitorización
* nms:calendario
* xtk:builder
* xtk:conexiones
* xtk:dbInit
* xtk:entityBackupNew
* xtk:entityBackupOriginal
* xtk:entityOriginal
* xtk:formulario
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
>Permisos de lectura y escritura para **xtk:sessionInfo** solo son accesibles mediante la cuenta interna de una instancia de Adobe Campaign.

## Modificación de los filtros del sistema de los esquemas integrados {#modifying-system-filters-of-built-in-schemas}

Aún puede modificar los filtros del sistema de los esquemas predeterminados que están protegidos de forma predeterminada debido a problemas de compatibilidad con versiones anteriores.

>[!NOTE]
>
>Sin embargo, Adobe recomienda no modificar los parámetros predeterminados para garantizar una seguridad óptima.

1. Cree una extensión para el esquema correspondiente o abra una extensión existente.
1. Añadir un elemento secundario **`<sysfilter name="<filter name>" _operation="delete"/>`** en el elemento principal para eliminar la aplicación del filtro en el mismo en el esquema de origen.
1. Si lo desea, puede agregar un nuevo filtro, tal como se detalla en [Filtros del sistema](#system-filters).
