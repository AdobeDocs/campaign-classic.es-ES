---
product: campaign
title: Asignación de base de datos
description: Asignación de base de datos
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 728b509f-2755-48df-8b12-449b7044e317
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1974'
ht-degree: 1%

---

# Asignación de base de datos{#database-mapping}

La asignación SQL de nuestro esquema de ejemplo proporciona el siguiente documento XML:

```
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">
  <enumeration basetype="byte" name="gender">    
    <value label="Not specified" name="unknown" value="0"/>    
    <value label="Male" name="male" value="1"/>    
    <value label="Female" name="female" value="2"/> 
  </enumeration>  

  <element name="recipient" sqltable="CusRecipient">    
    <attribute desc="Recipient e-mail address" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
    <attribute default="GetDate()" label="Date of creation" name="created" sqlname="tsCreated" type="datetime"/>    
    <attribute enum="gender" label="Gender" name="gender" sqlname="iGender" type="byte"/>    
    <element label="Location" name="location">      
      <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
    </element>  
  </element>
</schema>
```

## Descripción {#description}

El elemento raíz del esquema ya no es **`<srcschema>`**, sino **`<schema>`**.

Esto nos lleva a otro tipo de documento, que se genera automáticamente a partir del esquema de origen, denominado simplemente esquema. La aplicación Adobe Campaign utilizará este esquema.

Los nombres SQL se determinan automáticamente en función del nombre y tipo del elemento.

Las reglas de nomenclatura SQL son las siguientes:

* tabla: concatenación del área de nombres y nombre del esquema

   En nuestro ejemplo, el nombre de la tabla se introduce mediante el elemento principal del esquema en el atributo **sqltable**:

   ```
   <element name="recipient" sqltable="CusRecipient">
   ```

* campo: nombre del elemento precedido por un prefijo definido según el tipo (&quot;i&quot; para integer, &quot;d&quot; para double, &quot;s&quot; para string, &quot;ts&quot; para dates, etc.)

   El nombre del campo se introduce mediante el atributo **sqlname** para cada **`<attribute>`** y **`<element>`** escritos:

   ```
   <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/> 
   ```

>[!NOTE]
>
>Los nombres SQL se pueden sobrecargar desde el esquema de origen. Para ello, rellene los atributos &quot;sqltable&quot; o &quot;sqlname&quot; en el elemento correspondiente.

La secuencia de comandos SQL para crear la tabla generada a partir del esquema ampliado es la siguiente:

```
CREATE TABLE CusRecipient(
  iGender NUMERIC(3) NOT NULL Default 0,   
  sCity VARCHAR(50),   
  sEmail VARCHAR(80),
  tsCreated TIMESTAMP Default NULL);
```

Las restricciones de campo SQL son las siguientes:

* no hay valores nulos en los campos numérico y de fecha,
* los campos numéricos se inicializan en 0.

## Campos XML {#xml-fields}

De forma predeterminada, cualquier elemento escrito **`<attribute>`** y **`<element>`** se asigna a un campo SQL de la tabla de esquema de datos. Sin embargo, puede hacer referencia a este campo en XML en lugar de SQL, lo que significa que los datos se almacenan en un campo memo (&quot;mData&quot;) de la tabla que contiene los valores de todos los campos XML. El almacenamiento de estos datos es un documento XML que observa la estructura del esquema.

Para rellenar un campo en XML, debe añadir el atributo **xml** con el valor &quot;true&quot; al elemento correspondiente.

**Ejemplo**: aquí hay dos ejemplos de uso de campos XML.

* Campo de comentarios multilínea:

   ```
   <element name="comment" xml="true" type="memo" label="Comment"/>
   ```

* Descripción de los datos en formato HTML:

   ```
   <element name="description" xml="true" type="html" label="Description"/>
   ```

   El tipo &quot;html&quot; permite almacenar el contenido HTML en una etiqueta CDATA y mostrar una comprobación de edición HTML especial en la interfaz del cliente de Adobe Campaign.

El uso de campos XML permite añadir campos sin necesidad de modificar la estructura física de la base de datos. Otra ventaja es que se utilizan menos recursos (tamaño asignado a campos SQL, límite en el número de campos por tabla, etc.).

La principal desventaja es que es imposible indexar o filtrar un campo XML.

## Campos indexados {#indexed-fields}

Los índices permiten optimizar el rendimiento de las consultas SQL utilizadas en la aplicación.

Se declara un índice a partir del elemento principal del esquema de datos.

```
<dbindex name="name_of_index" unique="true/false">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

Los índices obedecen las siguientes reglas:

* Un índice puede hacer referencia a uno o varios campos de la tabla.
* Un índice puede ser único (para evitar duplicados) en todos los campos si el atributo **unique** contiene el valor &quot;true&quot;.
* El nombre SQL del índice se determina a partir del nombre SQL de la tabla y el nombre del índice.

>[!NOTE]
>
>Como estándar, los índices son los primeros elementos declarados del elemento principal del esquema.

>[!NOTE]
>
>Los índices se crean automáticamente durante la asignación de tablas (estándar o FDA).

**Ejemplo**:

* Añadir un índice a la dirección de correo electrónico y a la ciudad:

   ```
   <srcSchema name="recipient" namespace="cus">
     <element name="recipient">
       <dbindex name="email">
         <keyfield xpath="@email"/> 
         <keyfield xpath="location/@city"/> 
       </dbindex>
   
       <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
       <element name="location" label="Location">
         <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
       </element>
     </element>
   </srcSchema>
   ```

* Adición de un índice único al campo de nombre &quot;id&quot;:

   ```
   <srcSchema name="recipient" namespace="cus">
     <element name="recipient">
       <dbindex name="id" unique="true">
         <keyfield xpath="@id"/> 
       </dbindex>
   
       <dbindex name="email">
         <keyfield xpath="@email"/> 
       </dbindex>
   
       <attribute name="id" type="long" label="Identifier"/>
       <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
     </element>
   </srcSchema>
   ```

## Administración de claves {#management-of-keys}

Una tabla debe tener al menos una clave para identificar un registro de la tabla.

Se declara una clave a partir del elemento principal del esquema de datos.

```
<key name="name_of_key">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

Las claves obedecen las siguientes reglas:

* Una clave puede hacer referencia a uno o varios campos de la tabla.
* Una clave se conoce como &#39;primary&#39; (o &#39;priority&#39;) cuando es la primera del esquema que se rellena o si contiene el atributo **internal** con el valor &quot;true&quot;.
* Un índice único se declara implícitamente para cada definición de clave. La creación de un índice en la clave se puede evitar añadiendo el atributo **noDbIndex** con el valor &quot;true&quot;.

>[!NOTE]
>
>Como estándar, las claves son los elementos declarados del elemento principal del esquema después de definir los índices.

>[!NOTE]
>
>Las claves se crean durante la asignación de tablas (estándar o FDA), Adobe Campaign encuentra índices únicos.

**Ejemplo**:

* Adición de una clave a la dirección de correo electrónico y a la ciudad:

   ```
   <srcSchema name="recipient" namespace="cus">
     <element name="recipient">
       <key name="email">
         <keyfield xpath="@email"/> 
         <keyfield xpath="location/@city"/> 
       </key>
   
       <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
       <element name="location" label="Location">
         <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
       </element>
     </element>
   </srcSchema>
   ```

   El esquema generado:

   ```
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
   
      <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
      <element label="Location" name="location">      
        <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
      </element>  
     </element>
   </schema>
   ```

* Adición de una clave principal o interna en el campo de nombre &quot;id&quot;:

   ```
   <srcSchema name="recipient" namespace="cus">
     <element name="recipient">
       <key name="id" internal="true">
         <keyfield xpath="@id"/> 
       </key>
   
       <key name="email" noDbIndex="true">
         <keyfield xpath="@email"/> 
       </key>
   
       <attribute name="id" type="long" label="Identifier"/>
       <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
     </element>
   </srcSchema>
   ```

   El esquema generado:

   ```
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
       <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>  
     </element>
   </schema>
   ```

### Clave incremental automática {#auto-incremental-key}

La clave principal de la mayoría de las tablas de Adobe Campaign es un entero de 32 bits de longitud autogenerado por el motor de base de datos. El cálculo del valor clave depende de una secuencia (de forma predeterminada, la función **XtkNewId** SQL) que genere un número único en toda la base de datos. El contenido de la clave se introduce automáticamente al insertar el registro.

La ventaja de una clave incremental es que proporciona una clave técnica no modificable para las uniones entre tablas. Además, esta clave no ocupa mucha memoria porque utiliza un entero de doble byte.

Puede especificar en el esquema de origen el nombre de la secuencia que se utilizará con el atributo **pkSequence**. Si este atributo no se proporciona en el esquema de origen, se utilizará la secuencia predeterminada **XtkNewId**. La aplicación utiliza secuencias dedicadas para los esquemas **nms:broadLog** y **nms:trackingLog** (**NmsBroadLogId** y **NmsTrackingLogId** respectivamente) porque estas son las tablas que contienen la mayoría de los registros.

Desde ACC 18.10, **XtkNewId** ya no es el valor predeterminado de la secuencia en los esquemas predeterminados. Ahora puede crear un esquema o ampliar el esquema existente con una secuencia dedicada.

>[!IMPORTANT]
>
>Al crear un nuevo esquema o durante una ampliación de esquema, se debe mantener el mismo valor de secuencia de clave principal (@pkSequence) para todo el conjunto.

>[!NOTE]
>
>Una secuencia a la que se hace referencia en un esquema de Adobe Campaign (**NmsTrackingLogId**, por ejemplo) debe asociarse a una función SQL que devuelva el número de ID de los parámetros separados por comas. Esta función debe llamarse **GetNew** XXX **Ids**, donde **XXX** es el nombre de la secuencia (**GetNewNmsTrackingLogIds**, por ejemplo). Vea los archivos **postgres-nms.sql**, **mssql-nms.sql** o **oracle-nms.sql** proporcionados con la aplicación en el directorio **datakit/nms/eng/sql/** para recuperar el ejemplo de un Nms Creación de secuencia de TrackingLogId para cada motor de base de datos.

Para declarar una clave única, rellene el atributo **autopk** (con el valor &quot;true&quot;) en el elemento principal del esquema de datos.

**Ejemplo**:

Declaración de una clave incremental en el esquema de origen:

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient" autopk="true">
  ...
  </element>
</srcSchema>
```

El esquema generado:

```
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

Además de la definición de la clave y su índice, se ha añadido un campo numérico denominado &quot;id&quot; al esquema ampliado para contener la clave principal generada automáticamente.

>[!IMPORTANT]
>
>Un registro con una clave principal establecida en 0 se inserta automáticamente al crear la tabla. Este registro se utiliza para evitar las uniones externas, que no son efectivas en las tablas de volumen. De forma predeterminada, todas las claves externas se inicializan con el valor 0, de modo que siempre se pueda devolver un resultado en la unión cuando el elemento de datos no se rellena.

## Vínculos: relación entre tablas {#links--relation-between-tables}

Un vínculo describe la asociación entre una tabla y otra.

Los distintos tipos de asociaciones (conocidas como &quot;cardinalidades&quot;) son los siguientes:

* Cardinalidad 1-1: una incidencia de la tabla de origen puede tener como máximo una incidencia correspondiente de la tabla de destino.
* Cardinalidad 1-N: una incidencia de la tabla de origen puede tener varias incidencias correspondientes de la tabla de destino, pero una incidencia de la tabla de destino puede tener como máximo una incidencia correspondiente de la tabla de origen.
* Cardinalidad N-N: una incidencia de la tabla de origen puede tener varias incidencias correspondientes de la tabla de destino y viceversa.

En la interfaz, puede distinguir fácilmente los diferentes tipos de relaciones gracias a sus iconos.

Para unir relaciones con una tabla o base de datos de campaña:

* ![](assets/join_with_campaign11.png) : Cardinalidad 1-1. Por ejemplo, entre un destinatario y un pedido actual. Un destinatario solo puede estar relacionado con una incidencia de la tabla de pedidos actual a la vez.
* ![](assets/externaljoin11.png) : Cardinalidad 1-1, unión externa. Por ejemplo, entre un destinatario y su país. Un destinatario puede estar relacionado con una sola aparición del país de la tabla. El contenido de la tabla de país no se guardará.
* ![](assets/join_with_campaign1n.png) : Cardinalidad 1-N. Por ejemplo, entre un destinatario y la tabla de suscripciones. Un destinatario puede estar relacionado con varias apariciones en la tabla de suscripciones.

Para relaciones de unión mediante Federated Database Access:

* ![](assets/join_fda_11.png) : Cardinalidad 1-1
* ![](assets/join_fda_1m.png) : Cardinalidad 1-N

Para obtener más información sobre las tablas FDA, consulte [Acceso a una base de datos externa](../../installation/using/about-fda.md).

Se debe declarar un vínculo en el esquema que contenga la clave externa de la tabla vinculada a través del elemento principal:

```
<element name="name_of_link" type="link" target="key_of_destination_schema">
  <join xpath-dst="xpath_of_field1_destination_table" xpath-src="xpath_of_field1_source_table"/>
  <join xpath-dst="xpath_of_field2_destination_table" xpath-src="xpath_of_field2_source_table"/>
  ...
</element>
```

Los vínculos obedecen a las siguientes reglas:

* La definición de un vínculo se introduce en **link**-type **`<element>`** con los siguientes atributos:

   * **nombre**: nombre del vínculo de la tabla de origen,
   * **target**: nombre del esquema de destino,
   * **etiqueta**: etiqueta del vínculo,
   * **revLink**  (opcional): nombre del vínculo inverso del esquema de destino (deducido automáticamente de forma predeterminada),
   * **integridad**  (opcional): integridad referencial de la aparición de la tabla de origen a la aparición de la tabla de destino. Los valores posibles son los siguientes:

      * **definir**: es posible eliminar la incidencia de origen si ya no se hace referencia a ella en una incidencia de destino,
      * **normal**: al eliminar la ocurrencia de origen, se inicializan las claves del vínculo a la ocurrencia de destino (modo predeterminado), este tipo de integridad inicializa todas las claves externas,
      * **propio**: la eliminación de la ocurrencia de origen conduce a la eliminación de la ocurrencia de destino,
      * **Descargar**: igual que  **own**  (en caso de eliminación) o duplica los sucesos (en caso de duplicación),
      * **neutro**: no hace nada.
   * **revIntegrity**  (opcional): integridad en el esquema de destino (opcional, &quot;normal&quot; de forma predeterminada),
   * **revCardinality**  (opcional): con el valor &quot;simple&quot; rellena la cardinalidad con el tipo 1-1 (1-N de forma predeterminada).
   * **externalJoin**  (opcional): fuerza la unión exterior
   * **revExternalJoin**  (opcional): fuerza la unión exterior en el enlace inverso


* Un vínculo hace referencia a uno o varios campos de la tabla de origen a la tabla de destino. Los campos que componen la unión (elemento `<join>` ) no necesitan rellenarse porque se deducen automáticamente de forma predeterminada mediante la clave interna del esquema de destino.
* Se añade automáticamente un índice a la clave externa del vínculo en el esquema extendido.
* Un vínculo consta de dos vínculos intermedios, donde el primero se declara desde el esquema de origen y el segundo se crea automáticamente en el esquema ampliado del esquema de destino.
* Una unión puede ser una unión externa si se agrega el atributo **externalJoin** con el valor &quot;true&quot; (compatible con PostgreSQL).

>[!NOTE]
>
>Como estándar, los vínculos son los elementos declarados al final del esquema.

### Ejemplo 1 {#example-1}

Relación 1-N con la tabla de esquema &quot;cus:company&quot;:

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    ...
    <element label="Company" name="company" revIntegrity="define" revLabel="Contact" target="cus:company" type="link"/>
  </element>
</srcSchema>
```

El esquema generado:

```
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

La definición del vínculo se completa con los campos que componen la unión, es decir, la clave principal con su XPath (&quot;@id&quot;) en el esquema de destino y la clave externa con su XPath (&quot;@company-id&quot;) en el esquema.

La clave externa se agrega automáticamente en un elemento que utiliza las mismas características que el campo asociado en la tabla de destino, con la siguiente convención de nombres: nombre del esquema de target seguido del nombre del campo asociado (&quot;company-id&quot; en nuestro ejemplo).

Esquema ampliado del objetivo (&quot;cus:company&quot;):

```
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

* **nombre**: deducido automáticamente del nombre del esquema de origen (se puede forzar con el atributo &quot;revLink&quot; en la definición del vínculo en el esquema de origen)
* **revLink**: nombre del vínculo inverso
* **target**: clave del esquema vinculado (&quot;cus:recipient&quot; schema)
* **unbound**: el vínculo se declara como un elemento de recopilación para una cardinalidad 1-N (de forma predeterminada)
* **integridad**: &quot;define&quot; de forma predeterminada (se puede forzar con el atributo &quot;revIntegrity&quot; en la definición del vínculo en el esquema de origen).

### Ejemplo 2 {#example-2}

En este ejemplo, declararemos un vínculo hacia la tabla de esquema &quot;nms:address&quot;. La unión es una unión externa y se rellena explícitamente con la dirección de correo electrónico del destinatario y el campo &quot;@address&quot; de la tabla vinculada (&quot;nms:address&quot;).

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient"> 
    ...
    <element integrity="neutral" label="Info about email" name="emailInfo" revIntegrity="neutral" revLink="recipient" target="nms:address" type="link" externalJoin="true">      
      <join xpath-dst="@address" xpath-src="@email"/>
    </element>
  </element>
</srcSchema>
```

### Ejemplo 3 {#example-3}

Relación 1-1 con la tabla de esquema &quot;cus:extension&quot;:

```
<element integrity="own" label="Extension" name="extension" revCardinality="single" revLink="recipient" target="cus:extension" type="link"/>
```

### Ejemplo 5 {#example-4}

Enlace a una carpeta (esquema &quot;xtk:folder&quot;):

```
<element default="DefaultFolder('nmsFolder')" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="own" revLabel="Recipients" target="xtk:folder" type="link"/>
```

El valor predeterminado devuelve el identificador del primer archivo de tipo de parámetro apto introducido en la función &quot;DefaultFolder(&#39;nmsFolder&#39;)&quot;.

### Ejemplo 4 {#example-5}

En este ejemplo, deseamos crear una clave en un vínculo (&quot;empresa&quot; al esquema &quot;cus:empresa&quot;) con el atributo **xlink** y un campo de la tabla (&quot;correo electrónico&quot;):

```
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

```
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

    <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>
    <element label="Company" name="company" revLink="recipient" target="sfa:company" type="link">      
      <join xpath-dst="@id" xpath-src="@company-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of link 'Company' (field 'id')" name="company-id" sqlname="iCompanyId" type="long"/>
  </element>
</schema>
```

La definición de la clave de nombre &quot;companyEmail&quot; se amplió con la clave externa del vínculo &quot;company&quot;. Esta clave genera un índice único en ambos campos.
