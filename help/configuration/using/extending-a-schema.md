---
product: campaign
title: Ampliación de un esquema
description: Obtenga información sobre cómo ampliar un esquema
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 6e3e666d-6ab3-4346-93ca-fb0155a4660d
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 10%

---

# Ampliación de un esquema{#extending-a-schema}

>[!IMPORTANT]
>
>Algunos esquemas integrados no deben ampliarse: principalmente aquellos para los que se definen las siguientes configuraciones:\
>**dataSource=&quot;file&quot;** and  **mappingType=&quot;xmlFile&quot;**.\
>Los siguientes esquemas no deben ampliarse: **xtk:entityBackupNew**, **xtk:entityBackupOriginal**, **xtk:entityOriginal**, **xtk:form**, **xtk:srcSchema**, **ncm:publishing**, **nl:monitoring**, **nms:calendar**, **nms:remoteTracking**, **nms:userAgentRules&lt;a11 9/>,** xtk:builder **,** xtk:Connections **,** xtk:dbInit **,** xtk:funcList **, a28/>xtk:fusión**, **xtk: jst**, **xtk:navtree**, **xtk:queryDef**, **xtk:resourceMenu**, **xtk:schema&lt;a33 9/>,** xtk:scriptContext **,** xtk:session **,** xtk:sqlSchema **,** xtk:strings **.******
>Esta lista no es exhaustiva.

Existen dos métodos para ampliar un esquema existente:

1. Modificar directamente el esquema de origen.
1. Crear otro esquema con el mismo nombre pero un área de nombres diferente. La ventaja es que puede ampliar una tabla sin necesidad de modificar el esquema original.

   El elemento raíz del esquema debe contener el atributo **ExtendedSchema** con el nombre del esquema que se ampliará como su valor.

   Un esquema de extensión no tiene su propio esquema: el esquema generado a partir del esquema de origen se rellena con los campos del esquema de extensión.

   >[!IMPORTANT]
   >
   >No se le permite modificar los esquemas integrados de la aplicación, sino el mecanismo de extensión del esquema. De lo contrario, los esquemas modificados no se actualizarán en el momento de futuras actualizaciones de la aplicación. Esto puede provocar un mal funcionamiento en el uso de Adobe Campaign.

   **Ejemplo**: extensión del esquema  **nms:** recipient.

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   El esquema ampliado **nms:recipient** se rellena con el campo rellenado en el esquema de extensión:

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   El atributo **Dependschemas** del elemento raíz del esquema hace referencia a las dependencias de los esquemas de extensión.

   El atributo **perteneceTo** del campo rellena el esquema en el que se declara.

>[!IMPORTANT]
>
>Para que se tengan en cuenta las modificaciones, es necesario volver a generar los esquemas. Para obtener más información, consulte la sección [Regeneración de esquemas](../../configuration/using/regenerating-schemas.md) .\
>Si las modificaciones afectan a la estructura de la base de datos, debe ejecutar una actualización. Para obtener más información, consulte la sección [Actualización de la estructura de la base de datos](../../configuration/using/updating-the-database-structure.md).
