---
solution: Campaign Classic
product: campaign
title: Esquemas de datos
description: Esquemas de datos
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 2%

---


# Esquemas de datos{#data-schemas}

## Principios {#principles}

Para editar, crear y configurar los esquemas, haga clic en el **[!UICONTROL Administration > Configuration > Data schemas]** nodo de la consola de cliente de Adobe Campaign.

>[!NOTE]
>
>Los esquemas de datos predeterminados solo pueden eliminarlos los administradores de la consola de Adobe Campaign Classic.

![](assets/d_ncs_integration_schema_navtree.png)

The edit field shows the XML content of the source schema:

![](assets/d_ncs_integration_schema_edition.png)

>[!NOTE]
>
>El control de edición &quot;Nombre&quot; permite introducir la clave de esquema compuesta por el nombre y la Área de nombres. Los atributos &quot;name&quot; y &quot;Área de nombres&quot; del elemento raíz del esquema se actualizan automáticamente en la zona de edición XML del esquema.

La previsualización genera automáticamente el esquema extendido:

![](assets/d_ncs_integration_schema_edition2.png)

>[!NOTE]
>
>Cuando se guarda el esquema de origen, la generación del esquema extendido se inicia automáticamente.

Si necesita comprobar la estructura completa de un esquema, puede utilizar la ficha previsualización. Si el esquema se ha ampliado, podrá visualizar todas sus extensiones. Como complemento, la ficha Documentación muestra todos los atributos y elementos de esquema, así como sus propiedades (Campo SQL, tipo/longitud, etiqueta, descripción). La ficha Documentación solo se aplica a esquemas generados. For more on this, refer to the [Regenerating schemas](../../configuration/using/regenerating-schemas.md) section.

## Ejemplo: creación de una tabla de contrato {#example--creating-a-contract-table}

En el siguiente ejemplo, queremos crear una nueva tabla para **contratos** en el modelo de base de datos de la base de datos de Adobe Campaign. Esta tabla le permite almacenar los nombres y apellidos y las direcciones de correo electrónico de los titulares y cotenedores para cada contrato.

Para ello, debe crear el esquema de la tabla y actualizar la estructura de la base de datos para generar la tabla correspondiente. Siga estos pasos:

1. Edite el **[!UICONTROL Administration > Configuration > Data schemas]** nodo del árbol de Adobe Campaign y haga clic en **[!UICONTROL New]** .
1. Choose the **[!UICONTROL Create a new table in the data model]** option and click **[!UICONTROL Next]** .

   ![](assets/s_ncs_configuration_create_new_schema.png)

1. Especifique un nombre para la tabla y una Área de nombres.

   ![](assets/s_ncs_configuration_create_new_param.png)

   >[!NOTE]
   >
   >De forma predeterminada, los esquemas creados por los usuarios se almacenan en la Área de nombres &#39;cus&#39;. Para obtener más información sobre esto, consulte [Identificación de un esquema](../../configuration/using/about-schema-reference.md#identification-of-a-schema).

1. Cree el contenido de la tabla. Se recomienda utilizar el asistente de entrada para asegurarse de que no falte ninguna configuración. Para ello, haga clic en el **[!UICONTROL Insert]** botón y elija el tipo de configuración que desee agregar.

   ![](assets/s_ncs_configuration_create_new_content.png)

1. Defina la configuración de la tabla de contratos:

   ```
   <srcSchema desc="Active contracts" img="ncm:channels.png" label="Contracts" labelSingular="Contract" mappingType="sql" name="Contracts" namespace="cus" xtkschema="xtk:srcSchema">
     <element desc="Active contracts" img="ncm:channels.png" label="Contracts" labelSingular="Contract"
              name="Contracts" autopk="true">
              <attribute name="holderName" label="Holder last name" type="string"/>
              <attribute name="holderFirstName" label="Holder first name" type="string"/>
              <attribute name="holderEmail" label="Holder email" type="string"/>
              <attribute name="co-holderName" label="Co-holder last name" type="string"/>           
              <attribute name="co-holderFirstName" label="Co-holder first name" type="string"/>           
              <attribute name="co-holderEmail" label="Co-holder email" type="string"/>    
              <attribute name="date" label="Subscription date" type="date"/>     
              <attribute name="noContract" label="Contract number" type="long"/>  
     </element>
   </srcSchema>
   ```

   Añada el tipo de contrato y coloque un índice en el número de contrato.

   ```
   <srcSchema _cs="Contracts (cus)" desc="Active contracts" entitySchema="xtk:srcSchema" img="ncm:channels.png"
              label="Contracts" labelSingular="Contract" name="Contracts" namespace="cus" xtkschema="xtk:srcSchema">
     <enumeration basetype="byte" name="typeContract">
       <value label="Home" name="home" value="0"/>
       <value label="Car" name="car" value="1"/>
       <value label="Health" name="health" value="2"/>
       <value label="Pension fund" name="pension fund" value="2"/>
     </enumeration>
     <element autopk="true" desc="Active contracts" img="ncm:channels.png" label="Contracts"
              labelSingular="Contract" name="Contracts">
       <attribute label="Holder last name" name="holderName" type="string"/>
       <attribute label="Holder first name" name="holderFirstName" type="string"/>
       <attribute label="Holder email" name="holderEmail" type="string"/>
       <attribute label="Co-holder last name" name="co-holderName" type="string"/>
       <attribute label="Co-holder first name" name="co-holderFirstName" type="string"/>
       <attribute label="Co-holder email" name="co-holderEmail" type="string"/>
       <attribute label="Subscription date" name="date" type="date"/>
      <attribute desc="Type of contract" enum="cus:Contracts:typeContract" label="Type of contract"
                  name="type" type="byte"/>
       <attribute label="Contract number" name="noContract" type="long"/>
       <dbindex name="noContract" unique="true">
         <keyfield xpath="@noContract"/>
       </dbindex>
     </element>
   </srcSchema>
   ```

1. Guarde el esquema para generar la estructura:

   ![](assets/s_ncs_configuration_structure.png)

1. Actualice la estructura de la base de datos para crear la tabla a la que se vinculará el esquema. For more on this, refer to [Updating the database structure](../../configuration/using/updating-the-database-structure.md).

