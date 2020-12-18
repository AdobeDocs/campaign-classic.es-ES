---
solution: Campaign Classic
product: campaign
title: Ampliación de un esquema
description: Aprenda a extender un esquema
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 10%

---


# Ampliación de un esquema{#extending-a-schema}

>[!IMPORTANT]
>
>Algunos esquemas integrados no deben ampliarse: principalmente aquellos para los que se definen los siguientes ajustes:\
>**dataSource=&quot;file&quot;** and  **mappingType=&quot;xmlFile&quot;**.\
>Los siguientes esquemas no deben ampliarse: **xtk:entityBackupNew**, **xtk:entityBackupOriginal**, **xtk:entityOriginal**, **xtk:form**, **xtk:srcSchema**, **>ncm:publishing**, **nl:Monitoring**, **nms:calendar**, **nms:remoteTracking**, **nms:userAgentRules&lt;a111 9/>,** xtk:builder **,** xtk:Connections **,** xtk:dbInit **,** xtk:funcList **, a28/>xtk:fusion**, **xtk: jst**, **xtk:navtree**, **xtk:queryDef**, **xtk:resourceMenu**, **xtk:esquema&lt;a38 39/>,** xtk:scriptContext **,** xtk:session **,** xtk:sqlSchema **,** xtk:strings **.******
>Esta lista no es exhaustiva.

Existen dos métodos para ampliar un esquema existente:

1. Modificación directa del esquema de origen.
1. Crear otro esquema con el mismo nombre pero con una Área de nombres diferente. La ventaja es que puede extender una tabla sin necesidad de modificar el esquema original.

   El elemento raíz del esquema debe contener el atributo **expandedSchema** con el nombre del esquema que se extenderá como su valor.

   Un esquema de extensión no tiene su propio esquema: el esquema generado a partir del esquema de origen se rellenará con los campos del esquema de extensión.

   >[!IMPORTANT]
   >
   >No se le permite modificar los esquemas integrados de la aplicación, sino el mecanismo de extensión de esquema. De lo contrario, los esquemas modificados no se actualizarán en el momento de futuras actualizaciones de la aplicación. Esto puede provocar fallos de funcionamiento en el uso de Adobe Campaign.

   **Ejemplo**: extensión del esquema  **nms:** recipientschema.

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   El esquema extendido **nms:destinatario** se rellena con el campo rellenado en el esquema de extensión:

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   El atributo **Dependencias** del elemento raíz del esquema hace referencia a las dependencias de los esquemas de extensión.

   El atributo **perteneceTo** del campo rellena el esquema donde se declara.

>[!IMPORTANT]
>
>Para que las modificaciones se tengan en cuenta, es necesario volver a generar esquemas. Para obtener más información sobre esto, consulte la sección [Regeneración de esquemas](../../configuration/using/regenerating-schemas.md).\
>Si las modificaciones afectan a la estructura de la base de datos, debe ejecutar una actualización. Para obtener más información, consulte la sección [Actualización de la estructura de la base de datos](../../configuration/using/updating-the-database-structure.md).

