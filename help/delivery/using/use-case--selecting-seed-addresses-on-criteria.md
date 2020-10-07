---
title: '"Ejemplo de uso: selección de direcciones semilla según ciertos criterios"'
seo-title: '"Ejemplo de uso: selección de direcciones semilla según ciertos criterios"'
description: '"Ejemplo de uso: selección de direcciones semilla según ciertos criterios"'
seo-description: null
page-status-flag: never-activated
uuid: 6af39893-6ef3-4204-8b53-0c16e35bac8f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: fa8aab62-e182-4388-aa23-c255b0dbd42e
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '845'
ht-degree: 79%

---


# Ejemplo de uso: selección de direcciones semilla según ciertos criterios{#use-case-selecting-seed-addresses-on-criteria}

In the framework of a delivery or a campaign, the **[!UICONTROL Edit the dynamic condition...]** link lets you choose seed addresses based on specific selection criteria.

En este ejemplo de uso, al sitio **My online library** le gustaría personalizar sus boletines informativos según los gustos de lectura de sus clientes.

Junto con el departamento de compras, el usuario a cargo de las entregas ha creado un boletín informativo para suscriptores que hayan comprado novelas policiales.

Para compartir el resultado final de su colaboración con ellos, el administrador de envíos decide añadir a sus compañeros del departamento de compras a la entrega como direcciones semilla. El uso de una condición dinámica permite ahorrar tiempo al configurar y actualizar las direcciones.

Para utilizar la condición dinámica, se debe contar con:

* una entrega lista para realizar,
* direcciones semilla que tengan un valor común. Este valor puede ser un campo que ya exista en Adobe Campaign. En este ejemplo, las direcciones semilla comparten el valor “Compras” en el campo “Departamento” que no está presente en la aplicación de forma predeterminada.

## Paso 1: Creación de una entrega {#step-1---creating-a-delivery}

Los pasos para crear una entrega se detallan en la sección [Creación de una entrega por correo electrónico](../../delivery/using/creating-an-email-delivery.md).

En este ejemplo, el administrador de envíos ha creado el boletín informativo y ha seleccionado los destinatarios.

![](assets/dlv_seeds_usecase_01.png)

## Paso 2: Creación de un valor común {#step-2---creating-a-common-value}

Para crear un valor común como el de nuestro ejemplo (departamento de compras), primero debe extender el **esquema de datos** de las direcciones semilla y editar el formulario de entrada asociado.

### Extensión del esquema de datos {#extending-the-data-schema}

Para obtener más información sobre las extensiones de esquema, consulte la [guía de configuración](../../configuration/using/data-schemas.md).

1. En el **[!UICONTROL Administration > Configuration > Data schemas]** nodo, haga clic en el **[!UICONTROL New]** icono .
1. In the **[!UICONTROL Creation of a data schema]** window, select the **[!UICONTROL Extension of a schema]** option and click **[!UICONTROL Next]**.

   ![](assets/dlv_seeds_usecase_09.png)

1. Select the **[!UICONTROL Seed addresses]** source schema, enter **doc** as the **[!UICONTROL Namespace]** and click **[!UICONTROL Ok]**.

   ![](assets/dlv_seeds_usecase_10.png)

1. Haga clic en **[!UICONTROL Save]**.
1. En la ventana de edición del esquema, copie las líneas situadas debajo y péguelas en el área indicada en la captura de pantalla.

   ```
     <element name="common">
       <element label="Recipient" name="custom_nms_recipient">
         <attribute label="Department" length="80" name="workField" template="nms:recipient:recipient/@company"
                    type="string" userEnum="workField"/>
       </element>
     </element>
   ```

   ![](assets/dlv_seeds_usecase_20.png)

   Then copy the following lines and paste them under the **[!UICONTROL Seed to insert in the export files]** element.

   ```
       <element aggregate="doc:seedMember:common">
     </element>
   ```

   ![](assets/dlv_seeds_usecase_29.png)

   In this case, you are specifying that a new enumeration named **[!UICONTROL Department]** has been created in the seed address table, and it is based on the standard **[!UICONTROL @company]** enumeration template (labeled under the name **Company** in the seed address form).

1. Haga clic en **[!UICONTROL Save]**.
1. In the **[!UICONTROL Tools > Advanced]** menu, select the **[!UICONTROL Update database structure]** option.

   ![](assets/dlv_seeds_usecase_12.png)

1. Cuando se muestre el asistente de actualización, haga clic en el botón **[!UICONTROL Next]** para acceder a la ventana Edit tables: los cambios realizados en el esquema de datos de las direcciones semilla requieren una actualización de estructura.

   ![](assets/dlv_seeds_usecase_13.png)

1. Siga el asistente hasta llegar a la página para ejecutar la actualización. Haga clic en el botón **[!UICONTROL Start]**.

   ![](assets/dlv_seeds_usecase_14.png)

   Una vez finalizada la actualización, puede cerrar el asistente.

1. Desconéctese y vuelva a conectarse a Adobe Campaign. Los cambios realizados en el esquema de datos de las direcciones semilla deberían haber surtido efecto. In order for them to be visible from the seed address screen, you must update the associated **[!UICONTROL Input form]**. Consulte la sección [Actualización del formulario de entrada](#updating-the-input-form).

#### Ampliación del esquema de datos desde una tabla vinculada {#extending-the-data-schema-from-a-linked-table}

El esquema de direcciones semilla puede utilizar valores de una tabla vinculada al esquema de datos del destinatario: Destinatario (nms).

Por ejemplo, el usuario desea integrar **[!UICONTROL Internet Extension]** que se encuentra en la tabla de **[!UICONTROL Country]** que está relacionada con el esquema de destinatarios.

![](assets/dlv_seeds_usecase_06.png)

Por lo tanto, deben ampliar el esquema de datos de las direcciones semilla como se detalla en la sección . Sin embargo, las líneas de código que se van a integrar en el **paso 4** son las siguientes:

```
<element name="country">
      <attribute label="Internet Extension" length="2" name="iana" type="string"/>
      <attribute label="Country ISO" length="2" name="countryIsoA2" type="string"/>
    </element>
```

![](assets/dlv_seeds_usecase_11.png)

Indican lo siguiente:

* que el usuario desea crear un elemento nuevo denominado **[!UICONTROL Internet Extension]**,
* que este elemento proviene de la tabla de **[!UICONTROL Country]**.

>[!CAUTION]
>
>En el nombre de tabla vinculada debe especificar la **xpath-dst** de esa tabla vinculada.
>
>Esto se puede encontrar en el elemento **[!UICONTROL Country]** de la tabla de destinatarios.

![](assets/dlv_seeds_usecase_07.png)

The user can then follow from **step 5** of the section, and update the **[!UICONTROL Input form]** of the seed addresses.

Consulte la sección [Actualización del formulario de entrada](#updating-the-input-form).

#### Actualización del formulario de entrada {#updating-the-input-form}

1. In the **[!UICONTROL Administration > Configuration > Input forms]** node, find the seed addresses input form.

   ![](assets/dlv_seeds_usecase_19.png)

1. Edite el formulario e inserte la línea siguiente en el contenedor **[!UICONTROL Recipient]**:

   ```
   <input xpath="@workField"/>
   ```

   ![](assets/dlv_seeds_usecase_21.png)

1. Guarde los cambios.
1. Abra una dirección semilla. The **[!UICONTROL Department]** field appears in the **[!UICONTROL Recipient]** table.

   ![](assets/dlv_seeds_usecase_22.png)

1. Edite las direcciones semilla que desee utilizar para la entrega e introduzca **Purchasing** como valor del campo **[!UICONTROL Department]**.

## Paso 3: Definición de la condición {#step-3---defining-the-condition}

Ahora puede especificar la condición dinámica de las direcciones semilla para la entrega. Para ello:

1. Abra una entrega.

   ![](assets/dlv_seeds_usecase_01.png)

1. Click the **[!UICONTROL To]** link then the **[!UICONTROL Seed addresses]** tab to access the **[!UICONTROL Edit the dynamic condition...]** link.

   ![](assets/dlv_seeds_usecase_02.png)

1. Seleccione la expresión que le permite elegir las direcciones semilla que desee. Here the user selects the **[!UICONTROL Department (@workField)]** expression.

   ![](assets/dlv_seeds_usecase_03.png)

1. Seleccione el valor que desee. En este ejemplo, el usuario selecciona el departamento **Purchasing** de la lista desplegable de valores.

   ![](assets/dlv_seeds_usecase_17.png)

   >[!NOTE]
   >
   >La extensión de esquema creada anteriormente procede del esquema **recipient.** Los valores mostrados en la pantalla superior proceden de una enumeración del esquema **recipient**.

1. Haga clic en **[!UICONTROL Ok]**.

   The query is displayed in the **[!UICONTROL Select target]** window.

   ![](assets/dlv_seeds_usecase_04.png)

1. Haga clic en **[!UICONTROL Ok]** para aprobar la consulta.
1. Analice la entrega y haga clic en la pestaña **[!UICONTROL Delivery]** para acceder a los registros de envío.

   Las direcciones semilla del departamento de compras se muestran como pendientes de envío, al igual que los destinatarios y otras direcciones semilla.

   ![](assets/dlv_seeds_usecase_05.png)

1. Haga clic en el botón **[!UICONTROL Send]** para iniciar la entrega.

   Los miembros del departamento de compras forman parte de las direcciones semilla que reciben la entrega en la bandeja de entrada de su correo electrónico.

   ![](assets/dlv_seeds_usecase_18.png)
