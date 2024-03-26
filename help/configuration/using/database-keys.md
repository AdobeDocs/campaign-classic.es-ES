---
product: campaign
title: Administración de claves en esquemas de datos
description: Comprensión de la administración de claves en esquemas de datos
feature: Configuration, Instance Settings
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
exl-id: faf63c8f-9d10-43c1-a990-91361594af9f
source-git-commit: 46dcd80d5adc31a66b47c6d75e7914b0a686326b
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 7%

---

# Administración de claves en esquemas {#management-of-keys}

Cada tabla asociada con un esquema de datos debe tener al menos una clave para identificar un registro de una tabla.

Se declara una clave a partir del elemento principal del esquema de datos.

```sql
<key name="name_of_key">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

Una clave se conoce como &quot;clave principal&quot; cuando es la primera del esquema que se rellena o si contiene la variable `internal` atributo establecido en &quot;true&quot;.

Las siguientes reglas se aplican a las claves:

* Una clave puede hacer referencia a uno o varios campos de la tabla
* Se declara implícitamente un índice único para cada definición de clave. La creación de un índice en la clave se puede evitar configurando la variable `noDbIndex` atributo a &quot;true&quot;.

>[!NOTE]
>
>* Como estándar, las claves son los elementos declarados a partir del elemento principal del esquema después de definir los índices.
>
>* Las claves se crean durante la asignación de tablas (estándar o FDA), Adobe Campaign encuentra índices únicos.

**Ejemplo**:

* Añadir una clave a la dirección de correo electrónico y a la ciudad:

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <key name="email">
        <keyfield xpath="@email"/> 
        <keyfield xpath="location/@city"/> 
      </key>
  
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
      <element name="location" label="Location">
        <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
      </element>
    </element>
  </srcSchema>
  ```

  El esquema generado:

  ```sql
  <schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
    <element name="recipient" sqltable="CusRecipient">    
     <dbindex name="email" unique="true">      
       <keyfield xpath="@email"/>      
       <keyfield xpath="location/@city"/>    
     </dbindex>    
  
     <key name="email">      
      <keyfield xpath="@email"/>      
      <keyfield xpath="location/@city"/>    
     </key>    
  
     <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
     <element label="Location" name="location">      
       <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
     </element>  
    </element>
  </schema>
  ```

* Adición de una clave principal o interna al campo de nombre &quot;id&quot;:

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <key name="id" internal="true">
        <keyfield xpath="@id"/> 
      </key>
  
      <key name="email" noDbIndex="true">
        <keyfield xpath="@email"/> 
      </key>
  
      <attribute name="id" type="long" label="Identifier"/>
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
    </element>
  </srcSchema>
  ```

  El esquema generado:

  ```sql
  <schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
    <element name="recipient" sqltable="CusRecipient">    
      <key name="email">      
        <keyfield xpath="@email"/>    
      </key>    
  
      <dbindex name="id" unique="true">      
        <keyfield xpath="@id"/>    
      </dbindex>    
  
      <key internal="true" name="id">      
       <keyfield xpath="@id"/>    
      </key>    
  
      <attribute label="Identifier" name="id" sqlname="iRecipientId" type="long"/>    
      <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>  
    </element>
  </schema>
  ```

## Clave de incremento automático {#auto-incremental-key}

La clave principal de la mayoría de las tablas de Adobe Campaign es un entero de 32 bits generado automáticamente por el motor de la base de datos. El cálculo del valor clave depende de una secuencia (de forma predeterminada, la variable **XtkNewId** función SQL) generando un número único en toda la base de datos. El contenido de la clave se introduce automáticamente al insertar el registro.

La ventaja de una clave incremental es que proporciona una clave técnica no modificable para las uniones entre tablas. Además, esta clave no ocupa mucha memoria porque utiliza un entero de doble byte.

Puede especificar en el esquema de origen el nombre de la secuencia que se va a utilizar con el **pkSequence** atributo. Si este atributo no se proporciona en el esquema de origen, la variable **XtkNewId** se utilizará la secuencia predeterminada. La aplicación utiliza secuencias dedicadas para **nms:broadLog** y **nms:trackingLog** esquemas (**NmsBroadLogId** y **NmsTrackingLogId** respectivamente), ya que estas son las tablas que contienen la mayor cantidad de registros.

Desde ACC 18.10, **XtkNewId** ya no es el valor predeterminado para la secuencia en los esquemas predeterminados. Ahora puede crear un esquema o ampliar el esquema existente con una secuencia dedicada.

>[!IMPORTANT]
>
>Al crear un nuevo esquema o durante una extensión de esquema, se debe mantener el mismo valor de secuencia de clave principal (@pkSequence) para todo el conjunto.

Una secuencia a la que se hace referencia en un esquema de Adobe Campaign (**NmsTrackingLogId** por ejemplo) debe asociarse con una función SQL que devuelva el número de ID en los parámetros, separados por comas. Se debe llamar a esta función **GetNew** XXX **ID**, donde **XXX** es el nombre de la secuencia (**GetNewNmsTrackingLogIds** por ejemplo). Ver el **postgres-nms.sql**, **mssql-nms.sql** o **oracle-nms.sql** archivos proporcionados con la aplicación en el **datakit/nms/eng/sql/** para recuperar el ejemplo de la creación de la secuencia &quot;NmsTrackingLogId&quot; para cada motor de base de datos.

Para declarar una clave única, rellene el **autopk** atributo (con valor &quot;true&quot;) en el elemento principal del esquema de datos.

**Ejemplo**:

Declarar una clave incremental en el esquema de origen:

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient" autopk="true">
  ...
  </element>
</srcSchema>
```

El esquema generado:

```sql
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" autopk="true" pkSequence="XtkNewId" sqltable="CusRecipient"> 
    <dbindex name="id" unique="true">
      <keyfield xpath="@id"/>
    </dbindex>

    <key internal="true" name="id">
      <keyfield xpath="@id"/>
    </key>

    <attribute desc="Internal primary key" label="Primary key" name="id" sqlname="iRecipientId" type="long"/>
  </element>
</schema>
```

Además de la definición de la clave y su índice, se ha añadido un campo numérico llamado &quot;id&quot; al esquema ampliado para contener la clave principal generada automáticamente.

>[!IMPORTANT]
>
>Al crear la tabla, se inserta automáticamente un registro con una clave principal establecida en 0. Este registro se utiliza para evitar las uniones externas, que no son efectivas en las tablas de volumen. De forma predeterminada, todas las claves externas se inicializan con el valor 0, de modo que siempre se pueda devolver un resultado en la unión cuando el elemento de datos no se rellena.


## Más información

Examine los siguientes vínculos para obtener más información:

* [Introducción a los esquemas](about-schema-reference.md)
* [Estructura del esquema](schema-structure.md)
* [Asignación de base de datos](database-mapping.md)
* [Administración de vínculos](database-links.md)
* [Modelo de datos de Campaign](about-data-model.md)
