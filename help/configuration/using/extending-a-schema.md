---
title: Ampliación de un esquema
seo-title: Ampliación de un esquema
description: Ampliación de un esquema
seo-description: null
page-status-flag: never-activated
uuid: 1767b9de-1d72-4ece-aeec-87f83862d81c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 1c9af980-4e6b-44dc-af61-dd284863ec7d
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 12%

---


# Ampliación de un esquema{#extending-a-schema}

>[!IMPORTANT]
>
>Algunos esquemas integrados no deben ampliarse: principalmente aquellos para los que se definen los siguientes ajustes:\
>**dataSource=&quot;file&quot;** y **mappingType=&quot;xmlFile&quot;**.\
>Los siguientes esquemas no deben ampliarse: **xtk:entityBackupNew**, **xtk:entityBackupOriginal**, **xtk:entityOriginal**, **xtk:form**, **xtk:srcSchema**, **ncm:publishing, xtk:entityOriginal**, **xtk:form************************************:remoteTracking, nmsRules:userAgentxtk:builder,xtk:Connectionsxtk, dbxtk:Init, xtk:cList, xtk:fusiónxtk,xtk: jst**, **xtk:navtree**, **xtk:queryDef**, **xtk:resourceMenu**, **xtk:esquema**, **xtk:scriptContext, xtk session, xtk:sqlSchemaAsistente**, ************xtk:cadenasxtk:Presión.
>Esta lista no es exhaustiva.

Existen dos métodos para ampliar un esquema existente:

1. Modificación directa del esquema de origen.
1. Crear otro esquema con el mismo nombre pero con una Área de nombres diferente. La ventaja es que puede extender una tabla sin necesidad de modificar el esquema original.

   El elemento raíz del esquema debe contener el atributo **expandedSchema** con el nombre del esquema que se extenderá como su valor.

   Un esquema de extensión no tiene su propio esquema: el esquema generado a partir del esquema de origen se rellenará con los campos del esquema de extensión.

   >[!IMPORTANT]
   >
   >No se le permite modificar los esquemas integrados de la aplicación, sino el mecanismo de extensión de esquema. De lo contrario, los esquemas modificados no se actualizarán en el momento de futuras actualizaciones de la aplicación. Esto puede provocar fallos de funcionamiento en el uso de Adobe Campaign.

   **Ejemplo**: extensión del esquema **nms:destinatario** .

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   El **esquema ampliado nms:destinatario** se rellena con el campo rellenado en el esquema de extensión:

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   El atributo **Dependencias** del elemento raíz del esquema hace referencia a las dependencias de los esquemas de extensión.

   El atributo **perteneceA** del campo rellena el esquema donde se declara.

>[!IMPORTANT]
>
>Para que las modificaciones se tengan en cuenta, es necesario volver a generar esquemas. For more on this, refer to the [Regenerating schemas](../../configuration/using/regenerating-schemas.md) section.\
>Si las modificaciones afectan a la estructura de la base de datos, debe ejecutar una actualización. Para obtener más información, consulte la sección [Actualización de la estructura de la base de datos](../../configuration/using/updating-the-database-structure.md).

