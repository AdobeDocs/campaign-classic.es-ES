---
product: campaign
title: Asignación de destino
description: Obtenga información sobre cómo crear una asignación de destino
feature: Application Settings
badge-v7: label="v7" type="Informative" tooltip="Se aplica a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="También se aplica a Campaign v8"
exl-id: 38333669-5598-4811-a121-b677c1413f56
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 3%

---

# Asignación de destino{#target-mapping}



La creación de asignaciones de destino es necesaria en dos casos:

* si utiliza una tabla de destinatarios distinta de la proporcionada por Adobe Campaign,
* si configura una dimensión de filtrado diferente de la dimensión de segmentación estándar en la pantalla asignación de destino.

El asistente de creación de asignaciones de destino le ayudará a crear todos los esquemas necesarios para utilizar la tabla personalizada.

## Creación y configuración de esquemas vinculados a la tabla personalizada {#creating-and-configuring-schemas-linked-to-the-custom-table}

Antes de crear una asignación de destino, son necesarias varias configuraciones para que Adobe Campaign funcione con un nuevo esquema de datos de destinatario.

Para ello, siga los siguientes pasos:

1. Cree un nuevo esquema de datos que integre los campos de la tabla personalizada que desea utilizar.

   Para obtener más información, consulte [Referencia de esquema (xtk:srcSchema)](../../configuration/using/about-schema-reference.md).

   En nuestro ejemplo, crearemos un esquema de cliente, una tabla muy sencilla que contiene los siguientes campos: ID, nombre, apellidos, dirección de correo electrónico, número de teléfono móvil. El objetivo es poder enviar alertas por correo electrónico o SMS a las personas almacenadas en esta tabla.

   Esquema de ejemplo (cus:individual)

   ```
   <srcSchema name="individual" namespace="cus" label="Individuals">
     <element name="individual">
       <key name="id" internal="true">
         <keyfield xpath="@id"/>
       </key>
       <attribute name="id" type="long" length="32"/>
       <attribute name="lastName" type="string" length="100"/>
       <attribute name="firstName" type="string" length="100"/>
       <attribute name="email" type="string" length="100"/>
       <attribute name="mobile" type="string" length="100"/>
     </element>
   </srcSchema>
   ```

1. Declare el esquema como una vista externa utilizando el atributo =&quot;true&quot;. Consulte [Atributo de vista](../../configuration/using/schema-characteristics.md#the-view-attribute).

   ```
    <srcSchema desc="External recipient table" namespace="cus" view="true"....>
      ...
    </srcSchema>
   ```

1. Si necesita añadir una dirección de correo postal, utilice el siguiente tipo de estructura:

   ```
   <element advanced="true" name="postalAddress" template="nms:common:postalAddress">
        <attribute expr="SubString(JuxtWords(Smart([../infos/@firstname]), Upper([../infos/@name])), 1, 80)"
                   name="line1"/>
        <attribute expr="Upper([../address/@line2])" name="line2"/>
        <attribute expr="Upper([../address/@line])" name="line3"/>
        <attribute expr="Upper([../address/@line])" name="line4"/>
        <attribute expr="Upper([../address/@line])" name="line5"/>
        <attribute expr="Upper([../address/@line])" name="line6"/>
        <attribute _operation="delete" name="line7"/>
        <attribute _operation="delete" name="addrErrorCount"/>
        <attribute _operation="delete" name="addrQuality"/>
        <attribute _operation="delete" name="addrLastCheck"/>
        <element expr="@line1+'n'+@line2+'n'+@line3+'n'+@line4+'n'+@line5+'n'+@line6"
                 name="serialized"/>
        <attribute expr="AllNonNull2([../address/@line], [../infos/@name])" name="addrDefined"/>
      </element>
   ```

1. Haga clic en el nodo **[!UICONTROL Administration > Campaign management > Target mappings]**.
1. Haga clic en **Nuevo** para abrir el asistente de creación de asignaciones de destino.
1. Introduzca el **Etiqueta** y seleccione el esquema que acaba de crear en el campo **Dimensión de segmentación** field.

   ![](assets/mapping_diffusion_wizard_1.png)

1. En el **Editar formularios de direcciones** , seleccione los campos del esquema que coinciden con las distintas direcciones de envío. Aquí, podemos asignar el **@email** y **@mobile** campos.

   ![](assets/mapping_diffusion_wizard_2.png)

1. En lo siguiente **Almacenamiento** , introduzca la **Sufijo de los esquemas de extensión** para diferenciar los nuevos esquemas de los esquemas predeterminados que proporciona Adobe Campaign.

   Clic **[!UICONTROL Define new additional fields]** para seleccionar la dimensión de destino en la entrega.

   De forma predeterminada, la administración de exclusiones se almacena en la misma tabla que los mensajes.

   Compruebe la **Generar un esquema de almacenamiento para el seguimiento** si desea configurar el almacenamiento para el seguimiento vinculado a la asignación de destino.

   ![](assets/mapping_diffusion_wizard_3.png)

   >[!IMPORTANT]
   >
   >Adobe Campaign no admite varios esquemas de destinatarios, conocidos como esquemas de segmentación, vinculados a los mismos esquemas de &quot;broadlog&quot; o de &quot;log&quot; de seguimiento. De lo contrario, esto puede provocar anomalías en la reconciliación de datos posteriormente. Para obtener más información, consulte la [Recomendaciones y limitaciones](../../configuration/using/about-custom-recipient-table.md) página.

1. En el **Extensiones** , seleccione los esquemas opcionales que desea generar (la lista de esquemas disponibles depende de los módulos instalados en la plataforma de Adobe Campaign).

   ![](assets/mapping_diffusion_wizard_4.png)

1. Haga clic en **Guardar** para cerrar el asistente.

   El asistente utiliza el esquema de inicio para crear todos los demás esquemas necesarios para que funcione la nueva asignación de destino.

   ![](assets/mapping_schema_list.png)

## Uso de la asignación de destino {#using-target-mapping}

Existen dos formas de utilizar el nuevo esquema como destinatario de un envío:

* Cree una o más plantillas de envío basadas en la asignación
* Seleccione la asignación directamente durante la selección del destino al crear una entrega, como se muestra a continuación:

![](assets/mapping_selection_ciblage.png)
