---
product: campaign
title: Ampliación de un esquema
description: Obtenga información sobre cómo ampliar un esquema
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Schema Extension
exl-id: 6e3e666d-6ab3-4346-93ca-fb0155a4660d
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 9%

---

# Ampliación de un esquema{#extending-a-schema}

>[!IMPORTANT]
>
>Algunos esquemas integrados no deben ampliarse: principalmente aquellos para los que se definen las siguientes configuraciones:\
>**dataSource=&quot;file&quot;** y **mappingType=&quot;xmlFile&quot;**.\
>Los siguientes esquemas no deben ampliarse: **xtk:entityBackupNew**, **xtk:entityBackupOriginal**, **xtk:entityOriginal**, **xtk:form**, **xtk:srcSchema**, **ncm:publishing**, **nl:monitorización**, **nms:calendar**, **nms:remoteTracking**, **nms:userAgentRules**, **xtk:builder**, **xtk:conexiones**, **xtk:dbInit**, **xtk:funcList**, **xtk:fusión**, **xtk: jst**, **xtk:navtree**, **xtk:queryDef**, **xtk:resourceMenu**, **xtk:schema**, **xtk:scriptContext**, **xtk:session**, **xtk:sqlSchema**, **xtk:strings**.
>Esta lista no es exhaustiva.

Existen dos métodos para ampliar un esquema existente:

1. Modificar directamente el esquema de origen.
1. Crear otro esquema con el mismo nombre pero un área de nombres diferente. La ventaja es que puede ampliar una tabla sin necesidad de modificar el esquema original.

   El elemento raíz del esquema debe contener la variable **ExtendedSchema** con el nombre del esquema que se va a ampliar como su valor.

   Un esquema de extensión no tiene su propio esquema: el esquema generado a partir del esquema de origen se rellena con los campos del esquema de extensión.

   >[!IMPORTANT]
   >
   >No se le permite modificar los esquemas integrados de la aplicación, sino el mecanismo de extensión del esquema. De lo contrario, los esquemas modificados no se actualizarán en el momento de futuras actualizaciones de la aplicación. Esto puede provocar un mal funcionamiento en el uso de Adobe Campaign.

   **Ejemplo**: extensión del **nms:recipient** esquema.

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   La variable **nms:recipient** el esquema ampliado se rellena con el campo rellenado en el esquema de extensión:

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   La variable **DependenciasEsquemas** en el elemento raíz del esquema hace referencia a las dependencias en los esquemas de extensión.

   La variable **delegateTo** en el campo rellena el esquema donde se declara.

>[!IMPORTANT]
>
>Para que se tengan en cuenta las modificaciones, es necesario volver a generar los esquemas. Para obtener más información, consulte [esta página](../../configuration/using/regenerating-schemas.md).\
>Si las modificaciones afectan a la estructura de la base de datos, debe ejecutar una actualización. Para obtener más información, consulte [esta página](../../configuration/using/updating-the-database-structure.md).
