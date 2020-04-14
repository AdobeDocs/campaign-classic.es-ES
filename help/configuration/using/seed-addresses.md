---
title: Direcciones semilla
seo-title: Direcciones semilla
description: Direcciones semilla
seo-description: null
page-status-flag: never-activated
uuid: 0ebdeb73-be67-4c34-9f59-9fd4fb5241ab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: 41338d32-b95c-45ae-bee6-17b2af5bd837
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d5c1732858fd5d079bbd9a755997c04adf5c9d47

---


# Direcciones semilla{#seed-addresses}

Si la tabla de destinatario es una tabla personalizada, se requieren configuraciones adicionales. The **[!UICONTROL nms:seedMember]** schema must be extended. Se agrega una ficha adicional a las direcciones semilla para definir los campos adecuados, como se muestra a continuación:

![](assets/s_ncs_user_seedlist_new_tab.png)

Para obtener más información sobre el uso de direcciones semilla, consulte [esta sección](../../delivery/using/about-seed-addresses.md).

## Implementación {#implementation}

El esquema **nms:semillaMember** y el formulario vinculado que se incluyen de forma predeterminada deben ampliarse para la configuración del cliente, a fin de hacer referencia a todos los campos necesarios. La definición de esquema contiene comentarios que detallan su modo de configuración.

Definición del esquema ampliado del cuadro de destinatarios:

```
<srcSchema label="Person" name="person" namespace="cus">
  <element autopk="true" label="Person" name="person">
      <attribute label="LastName" name="lastname" type="string"/>
      <attribute label="FirstName" name="firstname" type="string"/>
    <element label="Address" name="address">
      <attribute label="Email" name="addrEnv" type="string"/>
    </element>
    <attribute label="Code Offer" name="codeOffer" type="string"/>
  </element>
</srcSchema>
```

Siga estos pasos:

1. Cree una extensión del esquema **nms:semillaMember** . Para obtener más información sobre esto, consulte [Ampliación de un esquema](../../configuration/using/extending-a-schema.md).
1. En esta nueva extensión, agregue un nuevo elemento en la raíz de **[!UICONTROL seedMember]** con los parámetros siguientes:

   ```
   name="custom_customNamespace_customSchema"
   ```

   Este elemento debe contener los campos necesarios para exportar las campañas. Estos campos deben tener el mismo nombre que los campos correspondientes del esquema externo. Por ejemplo, si el esquema es **[!UICONTROL cus:person]** , el **[!UICONTROL nms:seedMember]** esquema debe ampliarse de la siguiente manera:

   ```
     <srcSchema extendedSchema="nms:seedMember" label="Seed addresses" labelSingular="Seed address" name="seedMember" namespace="cus">
     <element name="common">
       <element name="custom_cus_person">
         <attribute name="lastname" template="cus:person:person/@lastname"/>
         <attribute name="firstname" template="cus:person:person/@firstname"/>
         <attribute name="email" sqlname="myEmailField" template="cus:person:person/address/@addrEnv" xml="false"/>
       </element>
     </element>
     <element name="seedMember">
      <element aggregate="cus:seedMember:common"/>
     </element>
   </srcSchema>
   ```

   >[!NOTE]
   >
   >La ampliación del esquema **nms:semillaMember** deberá ajustarse a las estructuras de una campaña y a un envío en Adobe Campaign.

   >[!IMPORTANT]
   >
   >
   >    
   >    
   >    * Durante la extensión, debe especificar un nombre **SQL (@sqlname)** para el campo &#39;email&#39;. El nombre de SQL debe ser distinto al de &#39;sEmail&#39; reservado para el esquema de destinatario.
   >    * Debe actualizar la estructura de la base de datos con el esquema creado al ampliar **nms:inicializaciónMember**.
   >    * En la extensión **nms:inicializaciónMember** , el campo que contiene la dirección de correo electrónico debe tener **name=&quot;email&quot;** como atributo. El nombre SQL debe ser diferente de &#39;sEmail&#39;, que ya se utiliza para el esquema de destinatario. Este atributo debe declararse inmediatamente bajo el **`<element name="custom_cus_person" />`** elemento .


1. Modifique el **[!UICONTROL seedMember]** formulario en consecuencia para definir una nueva ficha &quot;destinatario interno&quot; en la **[!UICONTROL Seed addresses]** ventana. For more on this, refer to [Form structure](../../configuration/using/form-structure.md).

   ```
   <container colcount="2" label="Internal recipient" name="internal"
                xpath="custom_cus_person">
       <input colspan="2" editable="true" nolabel="true" type="treeEdit">
         <container label="Recipient (cus:person)">
           <input xpath="@last name"/>
           <input xpath="@first name"/>
           <input xpath="@email"/>
         </container>
       </input>
     </container>
   ```

Si no se especifican todos los atributos de la dirección de inicialización, Adobe Campaign sustituye automáticamente los perfiles: se introducirán automáticamente durante la personalización mediante datos de un perfil existente.
