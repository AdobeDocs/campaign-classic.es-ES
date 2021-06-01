---
product: campaign
title: Características del esquema
description: Características del esquema
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 099161b4-b4cb-433c-aed6-71157269a536
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 2%

---

# Características del esquema{#schema-characteristics}

Las características de un esquema que hace referencia a una tabla existente son las siguientes:

* Adobe Campaign no debe modificar los objetos SQL en relación con las tablas existentes,
* Los nombres de las tablas y las columnas deben especificarse explícitamente,
* Los índices deben declararse.

>[!IMPORTANT]
>
>No elimine los campos de la tabla de destinatarios estándar, aunque no sean útiles. Esto puede provocar errores de comportamiento en la base de datos de Adobe Campaign.

## El atributo de vista {#the-view-attribute}

Los esquemas de origen aceptan el atributo **view** para el elemento raíz **srcSchema**. Debe utilizarse cuando Adobe Campaign se manipula en tablas personalizadas. El atributo **view=&quot;true&quot;** indica al asistente de actualización de la estructura de la base de datos que ignore este esquema. Por lo tanto, se prohíbe a la aplicación sincronizar la tabla, sus columnas y sus índices con el esquema correspondiente.

Cuando este atributo se establece en **true**, el esquema solo se utiliza para generar consultas SQL para acceder a los datos de esta tabla.

## Nombres de tablas y columnas {#names-of-tables-and-columns}

Cuando el asistente de actualización de tablas crea tablas, los nombres de las tablas y las columnas se generan automáticamente en función de los nombres de los esquemas y atributos respectivos. Sin embargo, es posible forzar los nombres SQL que se van a utilizar introduciendo los siguientes atributos:

* **** sqltabledentro del elemento principal del esquema, para especificar la tabla,
* **** nombreSQL en cada atributo para especificar las columnas.

**Ejemplo**:

```
<element label="Individual" name="individual" sqltable="individual">
    <key internal="true" name="id">
      <keyfield xpath="@id"/>
    </key> 
    <attribute name="id" type="long" length="32" />
    <attribute name="lastName" type="string" length="100" sqlname="Last_Name"/>
    <attribute name="firstName" type="string" length="100" sqlname="First_Name"/>
    <attribute name="email" type="string" length="100"/>
    <attribute name="mobile" type="string" length="100"/>
</element>
```

En este ejemplo, si los nombres de las tablas y columnas no se hubieran especificado explícitamente, la aplicación habría utilizado **CusIndividual** para la tabla, **lastName** y **firstName** para las columnas.

En un esquema, es posible rellenar solo parte de las columnas de una tabla existente. Las columnas no rellenadas no serán accesibles para el usuario.

## Campos indexados {#indexed-fields}

Al ordenar los registros de una lista desde la consola del cliente, se obtiene un mejor rendimiento ordenando los campos indexados. Declarar un índice en un esquema hace que la consola muestre los campos indexados con una línea roja debajo de la flecha de orden a la izquierda de la etiqueta de columna, como se muestra a continuación:

![](assets/s_ncs_integration_mapping_index.png)

En un esquema, un índice se define de la siguiente manera:

```
<dbindex name="name_of_index" unique="true/false"
  <keyfield xpath="xpath_1st_field"/
  <keyfield xpath="xpath_2nd_field"/
  ...
</dbindex
```

Por eso es importante declarar los índices existentes de la tabla personalizada en el esquema coincidente.

Se declara implícitamente un índice para cada declaración de clave y vínculo del esquema de origen. La declaración de índice se puede evitar especificando el atributo **noDbIndex=&quot;true&quot;**:

**Ejemplo**:

```
<key internal="true" name="customer" noDbIndex="true">
  <keyfield xpath="@customerId"/>
</key>
```
