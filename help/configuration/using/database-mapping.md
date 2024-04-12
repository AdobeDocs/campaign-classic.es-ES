---
product: campaign
title: Asignación de base de datos
description: Asignación de base de datos
feature: Configuration, Instance Settings
role: Data Engineer, Developer
exl-id: 728b509f-2755-48df-8b12-449b7044e317
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 4%

---

# Asignación de base de datos{#database-mapping}

La asignación SQL del esquema de ejemplo descrito [en esta página](schema-structure.md) genera el siguiente documento XML:

```sql
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">
  <enumeration basetype="byte" name="gender">    
    <value label="Not specified" name="unknown" value="0"/>    
    <value label="Male" name="male" value="1"/>    
    <value label="Female" name="female" value="2"/> 
  </enumeration>  

  <element name="recipient" sqltable="CusRecipient">    
    <attribute desc="Recipient email address" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
    <attribute default="GetDate()" label="Date of creation" name="created" sqlname="tsCreated" type="datetime"/>    
    <attribute enum="gender" label="Gender" name="gender" sqlname="iGender" type="byte"/>    
    <element label="Location" name="location">      
      <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
    </element>  
  </element>
</schema>
```

El elemento raíz del esquema ha cambiado a **`<srcschema>`** hasta **`<schema>`**.

Este otro tipo de documento se genera automáticamente a partir del esquema de origen y se denomina simplemente esquema.

Los nombres SQL se determinan automáticamente en función del nombre y el tipo del elemento.

Las reglas de nomenclatura SQL son las siguientes:

* **tabla**: concatenación del área de nombres y el nombre del esquema

  En este ejemplo, el nombre de la tabla se introduce mediante el elemento principal del esquema en **sqltable** atributo:

  ```sql
  <element name="recipient" sqltable="CusRecipient">
  ```

* **campo**: nombre del elemento precedido por un prefijo definido según el tipo: &quot;i&quot; para entero, &quot;d&quot; para doble, &quot;s&quot; para cadena, &quot;ts&quot; para fechas, etc.

  El nombre del campo se introduce mediante la variable **sqlname** para cada uno de los **`<attribute>`** y **`<element>`**:

  ```sql
  <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/> 
  ```

>[!NOTE]
>
>Los nombres SQL se pueden sobrecargar desde el esquema de origen. Para ello, rellene los atributos &quot;sqltable&quot; o &quot;sqlname&quot; en el elemento correspondiente.

La secuencia de comandos SQL para crear la tabla generada a partir del esquema ampliado es la siguiente:

```sql
CREATE TABLE CusRecipient(
  iGender NUMERIC(3) NOT NULL Default 0,   
  sCity VARCHAR(50),   
  sEmail VARCHAR(80),
  tsCreated TIMESTAMP Default NULL);
```

Las restricciones de campo SQL son las siguientes:

* no hay valores nulos en los campos numérico y de fecha
* los campos numéricos se inicializan en 0

## Campos XML {#xml-fields}

De forma predeterminada, cualquier  **`<attribute>`** y **`<element>`** El elemento con tipo se asigna a un campo SQL de la tabla de esquema de datos. Sin embargo, puede hacer referencia a este campo en XML en lugar de en SQL, lo que significa que los datos se almacenan en un campo memo (&quot;mData&quot;) de la tabla que contiene los valores de todos los campos XML. El almacenamiento de estos datos es un documento XML que observa la estructura del esquema.

Para rellenar un campo en XML, debe añadir la variable **xml** con el valor &quot;true&quot; al elemento correspondiente.

**Ejemplo**: estos son dos ejemplos de uso de campos XML.

* Campo de comentarios multilínea:

  ```sql
  <element name="comment" xml="true" type="memo" label="Comment"/>
  ```

* Descripción de los datos en formato HTML:

  ```sql
  <element name="description" xml="true" type="html" label="Description"/>
  ```

  El tipo &quot;html&quot; permite almacenar el contenido del HTML en una etiqueta CDATA y mostrar una comprobación especial de edición del HTML en la interfaz de cliente de Adobe Campaign.

Utilice campos XML para añadir nuevos campos sin modificar la estructura física de la base de datos. Otra ventaja es que utiliza menos recursos (tamaño asignado a campos SQL, límite en el número de campos por tabla, etc.). Sin embargo, tenga en cuenta que no puede indexar ni filtrar un campo XML.

## Campos indexados {#indexed-fields}

Los índices permiten optimizar el rendimiento de las consultas SQL utilizadas en la aplicación.

Se declara un índice a partir del elemento principal del esquema de datos.

```sql
<dbindex name="name_of_index" unique="true/false">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

Los índices obedecen las siguientes reglas:

* Un índice puede hacer referencia a uno o varios campos de la tabla
* Un índice puede ser único (para evitar duplicados) en todos los campos si la variable **único** El atributo contiene el valor &quot;true&quot;
* El nombre SQL del índice se determina a partir del nombre SQL de la tabla y el nombre del índice

>[!NOTE]
>
>* Como estándar, los índices son los primeros elementos declarados a partir del elemento principal del esquema.
>
>* Los índices se crean automáticamente durante la asignación de tablas (estándar o FDA).

**Ejemplo**:

* Añadir un índice a la dirección de correo electrónico y a la ciudad:

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <dbindex name="email">
        <keyfield xpath="@email"/> 
        <keyfield xpath="location/@city"/> 
      </dbindex>
  
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
      <element name="location" label="Location">
        <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
      </element>
    </element>
  </srcSchema>
  ```

* Añadir un índice único al campo de nombre &quot;id&quot;:

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <dbindex name="id" unique="true">
        <keyfield xpath="@id"/> 
      </dbindex>
  
      <dbindex name="email">
        <keyfield xpath="@email"/> 
      </dbindex>
  
      <attribute name="id" type="long" label="Identifier"/>
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
    </element>
  </srcSchema>
  ```

## Más información

Examine los siguientes vínculos para obtener más información:

* [Introducción a los esquemas](about-schema-reference.md)
* [Estructura del esquema](schema-structure.md)
* [Administración de claves](database-keys.md)
* [Administración de vínculos](database-links.md)
* [Modelo de datos de Campaign](about-data-model.md)