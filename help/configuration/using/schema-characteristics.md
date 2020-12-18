---
solution: Campaign Classic
product: campaign
title: Características del esquema
description: Características del esquema
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 2%

---


# Características del esquema{#schema-characteristics}

Las características de un esquema que hace referencia a una tabla existente son las siguientes:

* Adobe Campaign no debe modificar los objetos SQL en relación con las tablas existentes,
* Los nombres de las tablas y las columnas deben especificarse explícitamente,
* Se deben declarar los índices.

>[!IMPORTANT]
>
>No elimine los campos de la tabla de destinatario estándar, aunque sean inútiles. Esto puede provocar errores de comportamiento en la base de datos de Adobe Campaign.

## El atributo de vista {#the-view-attribute}

Los esquemas de origen aceptan el atributo **vista** para el elemento raíz **srcSchema**. Debe utilizarse cuando Adobe Campaign se manipula en tablas personalizadas. El atributo **vista=&quot;true&quot;** indica al asistente de actualización de la estructura de la base de datos que ignore este esquema. Por lo tanto, se prohíbe a la aplicación sincronizar la tabla, sus columnas y sus índices con el esquema correspondiente.

Cuando este atributo se establece en **true**, el esquema se utiliza solamente para generar consultas SQL para acceder a los datos de esta tabla.

## Nombres de tablas y columnas {#names-of-tables-and-columns}

Cuando el asistente para la actualización de tablas crea tablas, los nombres de las tablas y las columnas se generan automáticamente en función de los nombres de los esquemas y atributos respectivos. Sin embargo, es posible forzar el uso de los nombres SQL introduciendo los atributos siguientes:

* **** sqltabledentro del elemento principal del esquema, para especificar la tabla,
* **nombre** sqlname en cada atributo, para especificar las columnas.

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

En un esquema, es posible rellenar solo una parte de las columnas de una tabla existente. Las columnas no rellenadas no serán accesibles para el usuario.

## Campos indexados {#indexed-fields}

Al ordenar los registros de una lista desde la consola del cliente, se obtiene un mejor rendimiento ordenando los campos indexados. La declaración de un índice en un esquema hace que la consola muestre los campos indexados con una línea roja debajo de la flecha de orden a la izquierda del rótulo de columna, como se muestra a continuación:

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

