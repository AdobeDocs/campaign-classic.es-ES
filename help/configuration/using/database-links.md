---
product: campaign
title: Asignación de base de datos
description: Asignación de base de datos
feature: Configuration, Instance Settings
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
source-git-commit: 46220dcfdddb8f6f1e7026cafc503aaeecb7e0fa
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 2%

---


# Administración de vínculos {#links--relation-between-tables}

Un vínculo describe la asociación entre una tabla y otra.

A continuación se enumeran los tipos de asociaciones, también conocidas como cardinalidades.

* Cardinality 1-1: una incidencia de la tabla de origen puede tener como máximo una incidencia correspondiente de la tabla de destino.
* Cardinality 1-N: una incidencia de la tabla de origen puede tener varias incidencias correspondientes de la tabla de destino, pero una incidencia de la tabla de destino puede tener como máximo una incidencia correspondiente de la tabla de origen.
* Cardinality N-N: una incidencia de la tabla de origen puede tener varias incidencias correspondientes de la tabla de destino y viceversa.

En la interfaz de usuario, las cardinalidades se representan con un icono específico.

Para relaciones de unión con una tabla o base de datos de campaña:

* ![](assets/join_with_campaign11.png) : Cardinalidad 1-1. Por ejemplo, entre un destinatario y un pedido actual. Un destinatario solo puede estar relacionado con una incidencia de la tabla de pedidos actual a la vez.
* ![](assets/externaljoin11.png) : cardinalidad 1-1, unión externa. Por ejemplo, entre un destinatario y su país. Un destinatario solo puede estar relacionado con una incidencia del país de la tabla. No se guardará el contenido de la lista del país.
* ![](assets/join_with_campaign1n.png) : Cardinalidad 1-N. Por ejemplo, entre un destinatario y la tabla de suscripciones. Un destinatario puede estar relacionado con varias incidencias en la tabla de suscripciones.

Para relaciones de unión mediante el acceso a bases de datos federadas (FDA):

* ![](assets/join_fda_11.png) : Cardinalidad 1-1
* ![](assets/join_fda_1m.png) : Cardinalidad 1-N

Para obtener más información sobre las tablas de FDA, consulte [Acceso a una base de datos externa](../../installation/using/about-fda.md).

Se debe declarar un vínculo en el esquema que contenga la clave externa de la tabla vinculada a través del elemento principal:

```sql
<element name="name_of_link" type="link" target="key_of_destination_schema">
  <join xpath-dst="xpath_of_field1_destination_table" xpath-src="xpath_of_field1_source_table"/>
  <join xpath-dst="xpath_of_field2_destination_table" xpath-src="xpath_of_field2_source_table"/>
  ...
</element>
```

Los vínculos obedecen las siguientes reglas:

* La definición de un vínculo se introduce en una **vincular**-type **`<element>`** con los atributos siguientes:

   * **name**: nombre del vínculo de la tabla de origen
   * **destino**: nombre del esquema de destino
   * **etiqueta**: etiqueta del vínculo
   * **revLink** (opcional): nombre del vínculo inverso del esquema de destinatario (deducido automáticamente de forma predeterminada)
   * **integridad** (opcional): integridad referencial de la incidencia de la tabla de origen a la incidencia de la tabla de destino.
Los valores posibles son:

      * **definir**: es posible eliminar la incidencia de origen si una incidencia de destino ya no hace referencia a ella
      * **normal**: al eliminar la incidencia de origen se inicializan las claves del vínculo a la incidencia de destino (modo predeterminado), este tipo de integridad inicializa todas las claves externas
      * **poseer**: al eliminar la ocurrencia de origen, se elimina la ocurrencia de destino
      * **owncopy**: igual que **poseer** (en caso de eliminación) o duplica las ocurrencias (en caso de duplicación)
      * **neutral**: sin comportamiento específico

   * **revIntegrity** (opcional): integridad en el esquema de destino (opcional, &quot;normal&quot; de forma predeterminada)
   * **revCardinality** (opcional): con el valor &quot;single&quot; rellena la cardinalidad con tipo 1-1 (1-N de forma predeterminada)
   * **externalJoin** (opcional): fuerza la unión externa
   * **revExternalJoin** (opcional): fuerza la unión externa en el vínculo inverso

* Un vínculo hace referencia a uno o varios campos de la tabla de origen a la tabla de destino. Los campos que componen la unión ( `<join>`  ) no es necesario rellenarlos porque se deducen automáticamente de forma predeterminada mediante la clave interna del esquema de destinatario.
* Se agrega automáticamente un índice a la clave externa del vínculo en el esquema ampliado.
* Un vínculo consta de dos semirvínculos, en los que el primero se declara desde el esquema de origen y el segundo se crea automáticamente en el esquema ampliado del esquema de destino.
* Una unión puede ser una unión externa si la variable **externalJoin** se agrega el atributo, con el valor &quot;true&quot; (admitido en PostgreSQL).

>[!NOTE]
>
>Como estándar, los vínculos son los elementos declarados al final del esquema.

## Ejemplo: vínculo inverso {#example-1}

En el ejemplo siguiente, declaramos una relación 1-N con la tabla de esquema &quot;cus:company&quot;:

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    ...
    <element label="Company" name="company" revIntegrity="define" revLabel="Contact" target="cus:company" type="link"/>
  </element>
</srcSchema>
```

El esquema generado:

```sql
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" sqltable="CusRecipient"> 
    <dbindex name="companyId">      
      <keyfield xpath="@company-id"/>    
    </dbindex>
    ...
    <element label="Company" name="company" revLink="recipient" target="cus:company" type="link">      
      <join xpath-dst="@id" xpath-src="@company-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of 'Company' link (field 'id')" name="company-id" sqlname="iCompanyId" type="long"/>
  </element>
</schema>
```

La definición del vínculo se complementa con los campos que conforman la unión, es decir, la clave principal con su XPath (&quot;@id&quot;) en el esquema de destino y la clave externa con su XPath (&quot;@company-id&quot;) en el esquema.

La clave externa se agrega automáticamente en un elemento que utiliza las mismas características que el campo asociado en la tabla de destino, con la siguiente convención de nombres: nombre del esquema de destino seguido del nombre del campo asociado (&quot;company-id&quot; en nuestro ejemplo).

Esquema extendido del destinatario (&quot;cus:company&quot;):

```sql
<schema mappingType="sql" name="company" namespace="cus" xtkschema="xtk:schema">  
  <element name="company" sqltable="CusCompany" autopk="true"> 
    <dbindex name="id" unique="true">     
      <keyfield xpath="@id"/>    
    </dbindex>   
    <key internal="true" name="id">      
      <keyfield xpath="@id"/>    
    </key>
    ...
    <attribute desc="Internal primary key" label="Primary key" name="id" sqlname="iCompanyId" type="long"/>
    ...
    <element belongsTo="cus:recipient" integrity="define" label="Contact" name="recipient" revLink="company" target="nms:recipient" type="link" unbound="true">      
      <join xpath-dst="@company-id" xpath-src="@id"/>    
    </element>
  </element>
</schema>
```

Se ha añadido un vínculo inverso a la tabla &quot;cus:recipient&quot; con los siguientes parámetros:

* **name**: se deduce automáticamente del nombre del esquema de origen (se puede forzar con el atributo &quot;revLink&quot; en la definición del vínculo en el esquema de origen)
* **revLink**: nombre del vínculo inverso
* **destino**: clave del esquema vinculado (esquema &quot;cus:recipient&quot;)
* **libre**: el vínculo se declara como elemento de colección para una cardinalidad 1-N (de forma predeterminada)
* **integridad**: &quot;definir&quot; de forma predeterminada (se puede forzar con el atributo &quot;revIntegrity&quot; en la definición del vínculo en el esquema de origen).

## Ejemplo: vínculo simple {#example-2}

En este ejemplo, declaramos un vínculo hacia la tabla de esquema &quot;nms:address&quot;. La unión es una unión externa y se rellena explícitamente con la dirección de correo electrónico del destinatario y el campo &quot;@address&quot; de la tabla vinculada (&quot;nms:address&quot;).

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient"> 
    ...
    <element integrity="neutral" label="Info about email" name="emailInfo" revIntegrity="neutral" revLink="recipient" target="nms:address" type="link" externalJoin="true">      
      <join xpath-dst="@address" xpath-src="@email"/>
    </element>
  </element>
</srcSchema>
```

## Ejemplo: cardinalidad única {#example-3}

En este ejemplo, creamos una relación 1-1 con la tabla de esquema &quot;cus:extension&quot;:

```sql
<element integrity="own" label="Extension" name="extension" revCardinality="single" revLink="recipient" target="cus:extension" type="link"/>
```

## Ejemplo: vínculo a una carpeta {#example-4}

En este ejemplo, declaramos un vínculo a una carpeta (esquema &quot;xtk:folder&quot;):

```sql
<element default="DefaultFolder('nmsFolder')" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="own" revLabel="Recipients" target="xtk:folder" type="link"/>
```

El valor predeterminado devuelve el identificador del primer archivo de tipo de parámetro elegible introducido en la función &quot;DefaultFolder(&#39;nmsFolder&#39;)&quot;.

## Ejemplo: Creación de una clave en un vínculo {#example-5}

En este ejemplo, creamos una clave en un vínculo (esquema &quot;empresa&quot; a &quot;cus:empresa&quot;) con **xlink** y un campo de la tabla (&quot;correo electrónico&quot;):

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    <key name="companyEmail"> 
      <keyfield xpath="@email"/>
      <keyfield xlink="company"/>
    </key>
    
    <attribute name="email" type="string" length="80" label="Email" desc="Recipient email"/>
    <element label="Company" name="company" revIntegrity="define" revLabel="Contact" target="cus:company" type="link"/>
  </element>
</srcSchema>
```

El esquema generado:

```sql
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" sqltable="CusRecipient"> 
    <dbindex name="companyId">      
      <keyfield xpath="@company-id"/>    
    </dbindex>

    <dbindex name="companyEmail" unique="true">
      <keyfield xpath="@email"/>      
      <keyfield xpath="@company-id"/>    
    </dbindex>    

    <key name="companyEmail">      
      <keyfield xpath="@email"/>      
      <keyfield xpath="@company-id"/>    
    </key>

    <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>
    <element label="Company" name="company" revLink="recipient" target="sfa:company" type="link">      
      <join xpath-dst="@id" xpath-src="@company-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of link 'Company' (field 'id')" name="company-id" sqlname="iCompanyId" type="long"/>
  </element>
</schema>
```

La definición de la clave del nombre &quot;companyEmail&quot; se amplió con la clave externa del vínculo &quot;company&quot;. Esta clave genera un índice único en ambos campos.

## Más información

Examine los siguientes vínculos para obtener más información:

* [Introducción a los esquemas](about-schema-reference.md)
* [Estructura del esquema](schema-structure.md)
* [Asignación de base de datos](database-mapping.md)
* [Administración de claves](database-keys.md)
* [Modelo de datos de Campaign](about-data-model.md)