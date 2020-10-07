---
title: Elementos y atributos
seo-title: Elementos y atributos
description: Elementos y atributos
seo-description: null
page-status-flag: never-activated
uuid: 72b0128a-a453-4646-93e5-b399914abb76
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5e24d94a-f9c1-4642-a881-dfc4b5492f14
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '6022'
ht-degree: 1%

---


# Elementos y atributos {#elements-and-attributes}

Al editar un esquema, hay disponible un sistema de aprobación basado en el esquema de origen (xtk:srcSchema). También se pueden detectar algunos errores al actualizar la base de datos mediante la &quot;actualización de la estructura de la base de datos...&quot;. asistente.

De forma predeterminada, en los esquemas de Adobe Campaign, todos los atributos de tipo booleano son &quot;false&quot;. Para activarlos, debe especificar el atributo en el esquema y establecer su valor en &quot;true&quot;.

## `<attribute>` Elemento {#attribute--element}

### Modelo de contenido {#content-model}

attribute:==help

### Atributos {#attributes}

_operation (string), avanzado (booleano), correspondienteIf (string), autoIncrement (boolean), perteneceTo (string), dataPolicy (string), dbEnum (string), defOnDuplicate (boolean), predeterminado (string), desc (string), edit (string), enum (string), expr (string), feature (string), featureDate Boolean), img (cadena), inout (cadena), label (cadena), length (cadena), localizable (booleano), name (MNTOKEN), notNull (boolean), pkgStatus (cadena), ref (cadena), required (boolean), sql (boolean), sqlDefault (cadena), sqlname (cadena), sqltable (cadena) destinatario (MNTOKEN), plantilla (cadena), translateDefault (cadena), translateExpr (cadena), tipo (MNTOKEN), usuario (booleano), userEnum (cadena), visibleIf (cadena), xml (booleano)

### Padres {#parents}

`<element>`

### Niños {#children}

`<help>`

### Descripción {#description}

`<attribute>` permite definir un campo en la base de datos.

### Uso y contexto de uso {#use-and-context-of-use}

`<attribute>` los elementos deben declararse en un `<element>` elemento.

La secuencia en la que se definen `<attribute>` los elementos en una `<srcschema>` no afecta a la secuencia de creación de campos en la base de datos. La secuencia de creación será alfabética.

### Descripción del atributo {#attribute-description}

* **_operation (string)**: define el tipo de escritura en la base de datos.

   Este atributo se utiliza principalmente al ampliar los esquemas predeterminados.

   Los valores accesibles son:

   * &quot;ninguno&quot;: sólo reconciliación. Esto significa que Adobe Campaign recuperará el elemento sin actualizarlo ni generar un error si no existe.
   * &quot;insertOrUpdate&quot;: actualizar con inserción. Esto significa que Adobe Campaign actualizará el elemento o lo creará si no existe.
   * &quot;insertar&quot;: inserción. Esto significa que Adobe Campaign insertará el elemento sin comprobar si existe.
   * &quot;update&quot;: actualizar. Esto significa que Adobe Campaign actualizará el elemento o generará un error si no existe.
   * &quot;delete&quot;: eliminación. Esto significa que Adobe Campaign recuperará y eliminará los elementos.

* **avanzado (booleano)**: cuando esta opción está activada (@advanced=&quot;true&quot;), permite ocultar el atributo en la lista de los campos disponibles a los que se puede acceder para configurar una lista en un formulario.
* **applyIf (string)**: este atributo permite hacer que los campos sean opcionales. El `<attribute>` elemento se tendrá en cuenta al actualizar la base de datos cuando se cumpla la restricción. &quot;applyIf&quot; recibe una expresión XTK.
* **autoIncrement (booleano)**: si esta opción está activada, el campo se convierte en un contador. Esto le permite incrementar un valor (principalmente ID). (uso externo)
* **existsTo (string)**: toma el nombre y la Área de nombres de la tabla que comparte el campo y rellena el esquema donde se declara el atributo. (utilizado sólo en una `<schema>`).
* **dataPolicy (string)**: permite especificar restricciones de aprobación en los valores permitidos en el campo SQL o XML. Los valores de este atributo son:

   * &quot;ninguno&quot;: sin valor
   * &quot;smartCase&quot;: letras mayúsculas y minúsculas
   * &quot;lowerCase&quot;: todas las minúsculas
   * &quot;topCase&quot;: todas las mayúsculas y minúsculas
   * &quot;email&quot;: dirección de correo electrónico
   * &quot;phone&quot;: número de teléfono
   * &quot;identifier&quot;: nombre de identificador
   * &quot;resIdentifier&quot;: nombre de archivo

* **dbEnum (cadena)**: recibe el nombre interno de una lista desglosada &quot;cerrada&quot;. Los valores de lista desglosada deben definirse en la `<srcschema>`.
* **defOnDuplicate (booleano)**: si se activa este atributo, cuando se duplica un registro, el valor predeterminado (definido en @default) se vuelve a aplicar automáticamente al registro.
* **default (string)**: permite definir el valor del campo predeterminado (llamada a una función, valor predeterminado). Este atributo recibe una expresión XTK.
* **desc (cadena)**: permite insertar una descripción del atributo. Esta descripción se muestra en la barra de estado de la interfaz.
* **edit (cadena)**: este atributo especifica el tipo de entrada que se utilizará en el formulario vinculado al esquema.
* **enum (cadena)**: recibe el nombre de la lista desglosada vinculada al campo. La lista desglosada se puede insertar en el mismo esquema o en un esquema remoto.
* **expr (cadena)**: define una expresión de precálculo de campo. Este atributo recibe una expresión Xpath o XTK.
* **feature (string)**: define un campo de características: Estos campos se utilizan para ampliar los datos en un cuadro existente, pero con almacenamientos en un cuadro anexo. Los valores aceptados son:

   * &quot;compartido&quot;: el contenido se almacena en una tabla compartida por tipo de datos
   * &quot;dedicado&quot;: el contenido se almacena en una tabla dedicada

   Las tablas de características SQL se crean automáticamente según el tipo de característica:

   * dedicado: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * shared: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

   Existen dos tipos de campos de características: campos sencillos¹ en los que se autorice un valor único en la característica y en los campos de opción múltiple, en los que la característica esté vinculada a un elemento de colección que pueda contener varios valores.

   Cuando una característica se define en un esquema, este esquema debe tener una clave principal basada en un solo campo (las claves compuestas no están autorizadas).

* **featureDate (booleano)**: vinculado al campo de características &quot;@feature&quot;. Si su valor es &quot;true&quot;, le permite averiguar cuándo se actualizó por última vez el valor.
* **img (cadena)**: permite definir una ruta de acceso para una imagen vinculada a un campo (Área de nombres + nombre de imagen) (ejemplo: img=&quot;cus:mypicture.jpg&quot;). Físicamente, la imagen debe importarse al servidor de aplicaciones.
* **label (string)**: etiqueta vinculada al campo, principalmente destinada al usuario en la interfaz. Permite evitar restricciones de nombres.
* **length (string)**: máx. número de caracteres para un valor del campo SQL de tipo &quot;cadena&quot;. Si no se especifica el atributo &quot;@length&quot;, Adobe Campaign crea automáticamente un campo para 255 caracteres.
* **localizable (booleano)**: si se activa, este atributo indica a la herramienta de recopilación que recupere el valor del atributo &quot;@label&quot; para traducción (uso interno).
* **name (MNTOKEN)**: nombre del atributo que coincidirá con el nombre del campo en la tabla. El valor del atributo &quot;@name&quot; debe ser corto, preferiblemente en inglés, y cumplir con las restricciones de nombres XML.

   Cuando el esquema se escribe en la base de datos, Adobe Campaign agrega automáticamente prefijos al nombre del campo:

   * &quot;i&quot;: para el tipo &#39;integer&#39;.
   * &quot;d&quot;: para el tipo &#39;doble&#39;.
   * &quot;s&quot;: para el tipo de cadena de caracteres.
   * &quot;ts&quot;: para el tipo &#39;date&#39;.

   Para definir completamente el nombre del campo en la tabla, utilice la opción &quot;@sqlname&quot; al definir un atributo.

* **notNull (boolean)**: permite redefinir el comportamiento de Adobe Campaign con respecto a la administración de registros NULOS en la base de datos. De forma predeterminada, los campos numéricos no son nulos y los campos de cadena y tipo de fecha pueden ser nulos.
* **pkgStatus (string)**: durante las exportaciones de paquetes, los valores se tienen en cuenta en función del valor de &quot;@pkgStatus&quot;:

   * &quot;always&quot;: siempre presente
   * &quot;never&quot;: nunca presente
   * &quot;predeterminado (o nada)&quot;: el valor se exporta excepto si es el valor predeterminado o si no es un campo interno que no sería compatible con otras instancias.

* **ref (cadena)**: este atributo define una referencia a un `<attribute>` elemento compartido por varios esquemas (factorización de definición). La definición no se copia en el esquema actual.
* **requerido (booleano)**: si este atributo está activado (@required=&quot;true&quot;), el campo se resalta en la interfaz. La etiqueta del campo aparecerá en rojo en los formularios.
* **sql (booleano)**: si este atributo está activado (@sql=&quot;true&quot;), fuerza el almacenamiento del atributo SQL, incluso cuando el elemento que contiene el atributo tiene la propiedad xml=&quot;true&quot;.
* **sqlDefault (string)**: este atributo permite definir el valor predeterminado que se tiene en cuenta para actualizar la base de datos si se activa el atributo @notNull. Si este atributo se agrega después de la creación del atributo, el comportamiento de esquema no cambiará ni siquiera para los nuevos registros. Para cambiar el esquema y actualizar el valor de los nuevos registros, debe eliminar y volver a crear el atributo.
* **sqlname (string)**: del campo durante la creación de la tabla. Si no se especifica @sqlname, el valor del atributo &quot;@name&quot; se utiliza de forma predeterminada. Cuando el esquema se escribe en la base de datos, los prefijos se agregan automáticamente en función del tipo de campo.
* **template (string)**: este atributo define una referencia a un `<attribute>` elemento compartido por varios esquemas. La definición se copia automáticamente en el esquema actual.
* **translateDefault (string)**: si se encuentra un atributo &quot;@default&quot;, &quot;@translateDefault&quot; le permitirá redefinir una expresión para que coincida con la definida en @default, que será recopilada por la herramienta de traducción (uso interno).
* **translateExpr (cadena)**: si hay un atributo &quot;@expr&quot; presente, el atributo &quot;@translateExpr&quot; le permite redefinir una expresión para que coincida con la definida en @expr, que será recopilada por la herramienta de traducción (uso interno).
* **type (MNTOKEN)**: tipo de campo.

   Los tipos de campo son genéricos. Según el tipo de base de datos instalada, Adobe Campaign cambia el tipo definido a un valor específico de la base de datos instalada durante la actualización de la estructura.

   Lista de los tipos disponibles:

   * CUALQUIER
   * bin
   * blob
   * booleano
   * byte
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * date
   * doble
   * enum
   * float
   * html
   * int64
   * link
   * long
   * memo
   * MNTOKEN
   * percent
   * primarykey
   * short
   * string
   * tiempo
   * timespan
   * uuid

   Si el atributo &quot;@type&quot; se deja vacío, Adobe Campaign vinculará una cadena de caracteres (STRING) con una longitud de 100 al campo de forma predeterminada.

   Si el campo es de tipo STRING y el nombre del campo no está especificado por la presencia del atributo &quot;@sqlname&quot;, el nombre del campo en la base de datos estará precedido automáticamente por &#39;s&#39;. Este modo operativo será similar a los campos de tipo INTEGER (i), DOBLE (d) y FECHAS (ts).

* **userEnum (string)**: recibe el nombre interno de una lista desglosada &quot;abierta&quot;. El usuario puede definir los valores de la lista desglosada en la interfaz.
* **visibleIf (cadena)**: define una condición en forma de expresión XTK para mostrar u ocultar el atributo.

   >[!IMPORTANT]
   >
   >El atributo está oculto, pero aún se puede acceder a sus datos.

* **xml (booleano)**: si esta opción está activada, los valores del campo no tienen un campo SQL vinculado. Adobe Campaign crea un campo de tipo Texto &quot;mData&quot; para el almacenamiento de registros. Esto significa que no hay filtrado ni ordenación en estos campos.

### Ejemplos {#examples}

Ejemplo de valores de lista desglosada cuyos valores se almacenan en la base de datos:

```
    <enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>

    <element label="Sample" name="Sample">
       <attribute dbEnum="myEnum" length="100" name="Number" required="true" type="string"/>
    </element>     
```

Declaración de un campo XML con &quot;@datapolicy&quot;:

```
<attribute dataPolicy="phone" desc="Mobile number" label="Mobile"
     length="32" name="mobilePhone" sqlname="sMobilePhone" type="string"/>
```

Ejemplo con un &quot;@applyIf&quot;: el atributo &quot;contains&quot; solo se creará si el número de países es bueno a 20.

```
<attribute length="100" name="Continent" type="string" applicableIf="@country > 20"/>
```

Ejemplo con &quot;@feature&quot; de tipo &quot;compartido&quot;:

```
<attribute name="field1" label="Field 1" type="long" feature="shared"/>
<attribute name="field1" label="Field 1" type="long" feature="shared" sqlname="126" sqltable="Ft_Content_Long"/>
```

Ejemplo con &quot;@feature&quot; de tipo &quot;dedicado&quot;:

```
<attribute name="field1" label="Field 1" type="long" feature="dedicated"/>
<attribute name="field1" label="Field 1" type="long" feature="dedicated" sqlname="sField1" sqltable="Ft_recipient_field1"/>
```

## `<compute-string>` Elemento {#compute-string--element}

### Modelo de contenido {#content-model-1}

compute-string:==EMPTY

### Atributos {#attributes-1}

@expr

### Padres {#parents-1}

`<element>`

### Niños {#children-1}

Ninguno

### Descripción {#description-1}

El `<compute-string>` elemento permite generar una cadena basada en una expresión XTK para mostrar una etiqueta &quot;integrada&quot; en la interfaz basada en varios valores.

### Uso y contexto de uso {#use-and-context-of-use-1}

Cuando no `<compute-string>` se define ninguno, se introduce un `<compute-string>` elemento de forma predeterminada con los valores de la clave principal en el esquema.

### Descripción del atributo {#attribute-description-1}

* **expr (cadena)**: Expresión XTK y/o Xpath

### Ejemplos {#examples-1}

```
<compute-string expr="@label + Iif(@code='','', ' (' + [folder/@label] + ')')"/>  
<compute-string expr="ToString([@centralCatalog-id]) + ',' + ToString([@localOrgUnit-id])" />
```

Resultado de la cadena calculada en un destinatario: &quot;John Doe (john.doe@aol.com)&quot;:

```
<element name="recipient">
<compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')'
"/>
...
</element>
```

## `<condition>` Elemento {#condition--element}

### Modelo de contenido {#content-model-2}

condición:==EMPTY

### Atributos {#attributes-2}

* @boolOperator (cadena)
* @enabledIf (cadena)
* @expr (cadena)

### Padres {#parents-2}

`<sysfilter>`

### Niños {#children-2}

Ninguno

### Descripción {#description-2}

Este elemento permite definir una condición de filtrado.

### Uso y contexto de uso {#use-and-context-of-use-2}

Un `<sysfiler>` elemento puede contener varias condiciones de filtrado.

### Descripción del atributo {#attribute-description-2}

* **boolOperator (cadena)**: si hay varios `<conditions>` definidos dentro del mismo `<sysfilter>` elemento, este atributo permite combinarlos. De forma predeterminada, el vínculo lógico está entre `<condition>` los elementos es &quot;AND&quot;. El atributo &quot;@boolOperator&quot; permite combinar vínculos de tipo &quot;O&quot; y &quot;Y&quot;.
* **enabledIf (string)**: prueba de activación de condición.
* **expr (cadena)**: una expresión XTK.

### Ejemplos {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```

## `<dbindex>` Elemento {#dbindex--element}

### Modelo de contenido {#content-model-3}

dbindex:==keyfield

### Atributos {#attributes-3}

* @_operation (string)
* @applyIf (cadena)
* @label (cadena)
* @name (MNTOKEN)
* @unique (booleano)

### Padres {#parents-3}

`<element>`

### Niños {#children-3}

`<keyfield>`

### Descripción {#description-3}

Este elemento permite definir un índice vinculado a una tabla.

### Uso y contexto de uso {#use-and-context-of-use-3}

Es posible definir varios índices. Un índice puede hacer referencia a uno o varios campos de la tabla. La declaración de índice suele seguir la definición del elemento de esquema principal.

El orden de los `<keyfield>` elementos definidos en una `<dbindex>` es muy importante. El primero `<keyfield>` debe ser el criterio de indización en el que se basan principalmente las consultas.

El nombre del índice de la base de datos se calcula concatenando el nombre de la tabla y el nombre del índice. Por ejemplo: Nombre de tabla &quot;Sample&quot;, Área de nombres &quot;Cus&quot;, nombre de índice &quot;MyIndex&quot;-> nombre del campo de índice durante la consulta de creación de índice: &quot;CusSample_myIndex&quot;.

### Descripción del atributo {#attribute-description-3}

* **_operation (string)**: define el tipo de escritura en la base de datos.

   Este atributo se utiliza principalmente al ampliar los esquemas predeterminados.

   Los valores accesibles son:

   * &quot;ninguno&quot;: sólo reconciliación. Esto significa que Adobe Campaign recuperará el elemento sin actualizarlo ni generar un error si no existe.
   * &quot;insertOrUpdate&quot;: actualizar con inserción. Esto significa que Adobe Campaign actualizará el elemento o lo creará si no existe.
   * &quot;insertar&quot;: inserción. Esto significa que Adobe Campaign insertará el elemento sin comprobar si existe.
   * &quot;update&quot;: actualizar. Esto significa que Adobe Campaign actualizará el elemento o generará un error si no existe.
   * &quot;delete&quot;: eliminación. Esto significa que Adobe Campaign recuperará y eliminará los elementos.

* **applyIf (string)**: condición para tener en cuenta el índice: recibe una expresión XTK.
* **label (string)**: etiqueta de índice.
* **name (MNTOKEN)**: nombre de índice único.
* **unique (booleano)**: si esta opción está activada (@unique=&quot;true&quot;), el atributo garantiza la exclusividad del índice en todos sus campos.

### Ejemplos {#examples-3}

Creación de un índice en el campo &quot;id&quot;. (el atributo &quot;@unique&quot; del `<dbindex>` elemento desencadena la adición de la palabra clave SQL &quot;ÚNICA&quot; cuando se crea el índice en la base de datos (consulta)).

```
<element label="Sample" name="Sample">
  <dbindex name="myIndex" label="My index on the ID field" unique="true" applicableIf="HasPackage('nms:social')">
      <keyfield xpath="@id"/>
  </dbindex>
    <attribute name="id" type="long"/>
</element>          
```

```
ALTER TABLE CusSample ADD iSampleId INTEGER;
UPDATE CusSample SET iSampleId = 0;
ALTER TABLE CusSample ALTER COLUMN iSampleId SET Default 0;
ALTER TABLE CusSample ALTER COLUMN iSampleId SET NOT NULL; 
CREATE UNIQUE INDEX CusSample_myIndex ON CusSample(iSampleId);
```

Creación de un índice compuesto en los campos &quot;@mail&quot; y &quot;@phoneNumber&quot;:

```
<element label="NewSchemaUser" name="NewSchemaUser">
  <dbindex name="myIndex" label="My composite index">
         <keyfield xpath="@email"/>
         <keyfield xpath="@phone"/>
  </dbindex>
  
  <attribute name="email" type="string"/>
  <attribute name="phone" type="string"/>
</element>      
```

```
CREATE INDEX DocNewSchemaUser_myIndex ON DocNewSchemaUser(sEmail, sPhone);
```

## `<element>` Elemento {#element--element}

### Modelo de contenido {#content-model-4}

element:==(atributo | compute-string | dbindex | predeterminado | element | ayuda | join | key | sysFilter | translateDefault)

### Atributos {#attributes-4}

_operation (string), avanzado (booleano), acumulado (string), aplicableIf (string), autopk (boolean), perteneceTo (string), convDate (string), dataPolicy (string), dataSource (string), dbEnum (string), defOnDuplicate (boolean), default (string), desc (string), displayAsField (boolean, doesNotSupportDiff (boolean), edit (string), emptyKeyValue (string), enum (string), enumImage (string), expandedSchemaTarget (string), expr (string), externalJoin (boolean), feature (string), featureDate (boolean), filterPath (string), folderLink (string), folderModel (string), Process (string), fullLoad (boolean), hierarchical (boolean), hierarchicalPath (string), img (string), inout (string), integridad (string), label (string), labelSingular (string), length (string), localizable (boolean), name (MNTOKEN), noDbIndex (boolean), noKey (boolean) order (boolean), overflowtable (boolean), pkSequence (string), pkgStatus (string), ref (string), required (boolean), revAdvanced (boolean), revCardinality (string), revDesc (string), revExternalJoin (boolean), revIntegrity (string), revLabel (string), vLink (string), revTarget (string), revVisibleIf (string), sql (boolean), sqlname (string), sqltable (string), tableSpace (string), tableSpaceIndex (string), destinatario (MNTOKEN), template (string), permanentTable (boolean), translateDefault (string), translateExpr cadena), type (MNTOKEN), unbound (booleano), user (boolean), userEnum (string), visibleIf (string), xml (boolean), xmlChildren (boolean)

### Padres {#parents-4}

`<srcschema>`

`<element>`

### Niños {#children-4}

* `<attribute>`
* `<compute-string>`
* `<dbindex>`
* `<default>`
* `<element>`
* `<help>`
* `<join>`
* `<key>`
* `<sysfilter>`
* `<translateddefault>`

### Descripción {#description-4}

Hay cuatro tipos de `<element>` elementos en Adobe Campaign:

* Raíz `<element>` : define el nombre de la tabla SQL que coincide con el esquema.
* Estructura `<element>` : define un grupo de `<element>` o `<attribute>` elementos.
* Vínculo `<element>` : define un vínculo. Estos elementos deben incluir el atributo &quot;@type=link&quot;.
* XML `<element>` : define un campo de tipo de texto &quot;mData&quot;. Este elemento debe incluir el atributo &quot;@type=xml&quot;.

### Descripción del atributo {#attribute-description-4}

* **_operation (string)**: define el tipo de escritura en la base de datos.

   Este atributo se utiliza principalmente al ampliar los esquemas predeterminados.

   Los valores accesibles son:

   * &quot;ninguno&quot;: sólo reconciliación. Esto significa que Adobe Campaign recuperará el elemento sin actualizarlo ni generar un error si no existe.
   * &quot;insertOrUpdate&quot;: actualizar con inserción. Esto significa que Adobe Campaign actualizará el elemento o lo creará si no existe.
   * &quot;insertar&quot;: inserción. Esto significa que Adobe Campaign insertará el elemento sin comprobar si existe.
   * &quot;update&quot;: actualizar. Esto significa que Adobe Campaign actualizará el elemento o generará un error si no existe.
   * &quot;delete&quot;: eliminación. Esto significa que Adobe Campaign recuperará y eliminará los elementos.

* **avanzado (booleano)**: cuando esta opción está activada (@advanced=&quot;true&quot;), permite ocultar el atributo en la lista de los campos disponibles a los que se puede acceder para configurar una lista en un formulario.
* **acumulada (cadena)**: permite copiar la definición de un `<element>` mediante otro esquema. Este atributo recibe una declaración de esquema en forma de &quot;Área de nombres:nombre&quot;.
* **applyIf (string)**: condición para aplicar el índice. Este atributo recibe una expresión XTK.
* **autopk (booleano)**: si esta opción está activada (autopk=&quot;true&quot;), se definirá automáticamente una clave única. Esta opción solo puede utilizarse en el elemento principal del esquema. Advertencia, Adobe Campaign sólo garantiza que la clave generada sea única. No se garantiza que los valores clave sean consecutivos e incrementales.
* **dataPolicy (string)**: permite especificar restricciones de aprobación en los valores permitidos en el campo SQL. Los valores de este atributo son:

   * &quot;ninguno&quot;: sin valor
   * &quot;smartCase&quot;: letras mayúsculas y minúsculas
   * &quot;lowerCase&quot;: todas las minúsculas
   * &quot;topCase&quot;: todas las mayúsculas y minúsculas
   * &quot;email&quot;: dirección de correo electrónico
   * &quot;phone&quot;: número de teléfono
   * &quot;identifier&quot;: nombre de identificador
   * &quot;resIdentifier&quot;: nombre de archivo

* **dbEnum (cadena)**: recibe el nombre interno de una lista desglosada &quot;cerrada&quot;. Los valores de lista desglosada deben definirse en la `<srcschema>`.
* **defOnDuplicate (booleano)**: si se activa este atributo, cuando se duplica un registro, el valor predeterminado (definido en @default) se vuelve a aplicar automáticamente al registro.
* **default (string)**: permite definir el comportamiento del elemento (llamada a una función, valor predeterminado). Este atributo recibe una expresión XTK.
* **desc (cadena)**: permite insertar una descripción del elemento. Esta descripción se muestra en la barra de estado de la interfaz.
* **displayAsField (boolean)**: si se activa este atributo, se mostrará un tipo de &quot;vínculo&quot; `<element>` como campo en la vista de árbol de los esquemas (&quot;Estructura&quot;). De este modo, es posible mostrar un vínculo como campo local y cambiar su comportamiento durante una consulta. Cuando el elemento se encuentra en la SELECCIÓN de una consulta, se utilizará el valor del destinatario del vínculo. Cuando el elemento se encuentra en el WHERE de una consulta, se utilizará la clave subyacente del vínculo.
* **edit (cadena)**: este atributo especifica el tipo de entrada que se utilizará en el formulario vinculado al esquema.
* **enum (cadena)**: recibe el nombre de la lista desglosada vinculada al campo. La lista desglosada se puede insertar en el mismo esquema o en un esquema remoto.
* **expr (cadena)**: este atributo define un campo calculado para el que no se almacena ninguna definición en la tabla. Recibe una expresión Xpath o XTK (cadena).
* **externalJoin (boolean)**: unión externa en un elemento de tipo &quot;vínculo&quot;.
* **feature (string)**: define un campo de características: Estos campos se utilizan para ampliar los datos en un cuadro existente, pero con almacenamientos en un cuadro anexo. Los valores aceptados son:

   * &quot;compartido&quot;: el contenido se almacena en una tabla compartida por tipo de datos
   * &quot;dedicado&quot;: el contenido se almacena en una tabla dedicada

   Las tablas de características SQL se crean automáticamente según el tipo de característica:

   * dedicado: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * shared: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

   Existen dos tipos de campos de características: campos simples en los que se autoriza un valor único en la característica y en los campos de opción múltiple, en los que la característica está vinculada a un elemento de recopilación que puede contener varios valores.

   Cuando una característica se define en un esquema, este esquema debe tener una clave principal basada en un solo campo (las claves compuestas no están autorizadas).

* **featureDate (booleano)**: vinculado al campo de características &quot;@feature&quot;. Si su valor es &quot;true&quot;, le permite averiguar cuándo se actualizó por última vez el valor.
* **filterPath (string)**: este atributo recibe un Xpath y le permite definir un filtro en un campo.
* **folderLink (cadena)**: este atributo recibe el nombre del vínculo que le permite recuperar los archivos que contienen entidades.
* **folderModel (string)**: define el tipo de carpeta que habilita el almacenamiento de la entidad. Este atributo solo se define si &quot;@folderLink&quot; está presente.
* **folderProcess (cadena)**: define el vínculo donde se almacenan las instancias del modelo de entidad. Este atributo solo se define si &quot;@folderLink&quot; está presente.
* **fullLoad (booleano)**: este atributo fuerza la visualización de todos los registros de una tabla durante la selección de campos en un formulario.
* **img (cadena)**: recibe la ruta de una imagen vinculada a un elemento. El valor de este atributo es del tipo &quot;Área de nombres:nombre de imagen&quot;. Por ejemplo: img=&quot;cus:myImage.jpg&quot;. Físicamente, la imagen debe importarse al servidor de aplicaciones.
* **integridad (cadena)**: integridad referencial de la incidencia de la tabla de origen hacia la tabla de destinatario.

   Los valores accesibles son:

   * &quot;define&quot;: Adobe Campaign no elimina la entidad si se hace referencia a ella a través del vínculo
   * &quot;normal&quot;: al eliminar la incidencia de origen se inicializan las claves del vínculo en la incidencia de destinatario (modo predeterminado), este tipo de integridad inicializa todas las claves externas
   * &quot;propio&quot;: la eliminación de la incidencia de origen activa la eliminación de la incidencia de destinatario
   * &quot;downcopy&quot;: similar a &quot;propia&quot; (en caso de eliminación) o ocurrencias de duplicados (en caso de duplicación)
   * &quot;neutral&quot;: no hace nada

* **label (string)**: etiqueta de elemento.
* **labelSingular (cadena)**: etiqueta (forma singular) del elemento utilizado en algunas partes de la interfaz.
* **length (string)**: máx. número de caracteres autorizados para un valor del campo SQL de tipo &quot;cadena&quot;.
* **localizable (booleano)**: si se activa, este atributo indica a la herramienta de recopilación que recupere el valor del atributo &quot;@label&quot; para traducción (uso interno).
* **name (MNTOKEN)**: nombre interno del elemento que coincide con el nombre de la tabla. El valor del atributo &quot;@name&quot; debe ser corto, preferiblemente en inglés, y cumplir con las restricciones de nombres vinculadas a XML.

   Cuando el esquema se escribe en la base de datos, Adobe Campaign agrega automáticamente los prefijos al nombre del campo.

   * &quot;i&quot;: para el tipo &#39;integer&#39;.
   * &quot;d&quot;: para el tipo &#39;doble&#39;.
   * &quot;s&quot;: para el tipo de cadena de caracteres.
   * &quot;ts&quot;: para el tipo &#39;date&#39;.

   Para definir el nombre de la tabla de forma autónoma, debe utilizar el atributo &quot;@sqltable&quot; en la definición del elemento de esquema principal.

* **noDbIndex (boolean)**: permite especificar que el elemento no se indizará.
* **ordered (booleano)**: si el atributo está activado (ordered=&quot;true&quot;), Adobe Campaign mantiene la secuencia de declaraciones de elementos en un elemento de recopilación XML.
* **pkSequence (cadena)**: recibe el nombre de la secuencia que se va a utilizar para calcular una clave de aumento automático. Este atributo solo se puede utilizar si se define una clave de aumento automático en el elemento raíz del esquema.
* **pkgStatus (string)**: durante las exportaciones de paquetes, los valores se tendrán en cuenta como función del valor de este atributo:

   * &quot;always&quot;: el elemento siempre estará presente
   * &quot;never&quot;: el elemento nunca estará presente
   * &quot;predeterminado (o nada)&quot;: el elemento se exporta a menos que sea el elemento predeterminado o si no es un campo interno y no sería compatible con otras instancias

* **ref (cadena)**: este atributo define una referencia a un elemento >element> compartido por varios esquemas (factorización de definición). La definición no se copia en el esquema actual.
* **requerido (booleano)**: si este atributo está activado (@required=&quot;true&quot;), el campo se resalta en la interfaz. La etiqueta del campo aparecerá en rojo en los formularios.
* **revAdvanced (booleano)**: cuando se activa, este atributo especifica que el vínculo opuesto es un vínculo &quot;avanzado&quot;.
* **revCardinality (string)**: este atributo define la cardinalidad de un vínculo entre dos tablas. Se utiliza en un tipo de &quot;vínculo&quot; `<element>`.

   Los valores posibles son:

   * &quot;single&quot; : Vínculo simple de tipo 1-1
   * &quot;sin enlazar&quot;: Vínculo de colección de tipo 1-N

   De forma predeterminada, si el atributo no se especifica durante la creación del vínculo, la cardinalidad será 1-N.

* **revDesc (cadena)**: este atributo recibe una descripción vinculada al vínculo opuesto.
* **revExternalJoin (booleano)**: cuando se activa, este atributo permite forzar la unión externa en el vínculo opuesto.
* **revIntegrity (cadena)**: este atributo define la integridad en el esquema de destinatario. Se autorizan los mismos valores que el atributo &quot;@integridad&quot;. De forma predeterminada, Adobe Campaign proporciona el valor &quot;normal&quot; a este atributo.
* **revLabel (cadena)**: del vínculo opuesto.
* **revLink (cadena)**: nombre del vínculo opuesto. Si el valor es &quot;_NONE_&quot;, no se creará ningún vínculo opuesto en el esquema de destino.
* **revTarget (cadena)**: destinatario del vínculo opuesto.
* **sql (booleano)**: si este atributo está activado (@sql=&quot;true&quot;), fuerza el almacenamiento del elemento SQL, aunque el elemento tenga la propiedad xml=&quot;true&quot;.
* **sqlname (string)**: nombre del campo durante la creación de la tabla. Si no se especifica &quot;@sqlname&quot;, el valor del atributo &quot;@name&quot; se utiliza de forma predeterminada. Al escribir el esquema en la tabla, los prefijos se agregan automáticamente en función del tipo de campo.
* **sqltable (string)**: para el elemento principal del esquema, este atributo sobrecarga el nombre de la tabla SQL generada de forma predeterminada. Si no se especifica &quot;@sqltable&quot;, el nombre predeterminado se estructurará de esta manera: área de nombres (primera letra mayúscula) seguida del valor del SrcSchema &quot;@name&quot;.
* **tableSpace (cadena)**: este atributo permite especificar un nuevo tablespace de almacenamiento de datos para una tabla (válido en la raíz `<element>`).
* **tableSpaceIndex (string)**: este atributo permite especificar un nuevo tablespace de almacenamiento de índice para una tabla (válido en la raíz `<element>`).
* **destinatario (MNTOKEN)**: recibe el nombre del esquema de destinatario al crear un vínculo entre tablas. Este atributo solo está activo para elementos de tipo &quot;link&quot;.
* **template (string)**: este atributo define una referencia a un `<element>` elemento compartido por varios esquemas. La definición se copia automáticamente en el esquema actual.
* **translateDefault (string)**: si se encuentra un atributo &quot;@default&quot;, &quot;@translateDefault&quot; le permitirá redefinir una expresión para que coincida con la definida en @default, que será recopilada por la herramienta de traducción (uso interno).
* **translateExpr (cadena)**: si se encuentra un atributo &quot;@expr&quot;, el atributo &quot;@translateExpr&quot; le permite redefinir una expresión que coincida con la definida en &quot;@expr&quot; y que será recopilada por la herramienta de traducción (uso interno).
* **type (MNTOKEN)**: define el tipo de datos almacenados en el elemento.

   Lista de los tipos disponibles:

   * CUALQUIER
   * bin
   * blob
   * booleano
   * byte
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * date
   * doble
   * enum
   * float
   * html
   * int64
   * link
   * long
   * memo
   * MNTOKEN
   * percent
   * primarykey
   * short
   * string
   * tiempo
   * timespan
   * uuid

* **unbound (booleano)**: si el atributo está activado (unbound=&quot;true&quot;), el vínculo se declara como un elemento de recopilación para una cardinalidad 1-N.
* **userEnum (string)**: recibe el nombre interno de una lista desglosada &quot;abierta&quot;. El usuario puede definir los valores de lista desglosada en la interfaz.
* **xml (booleano)**: si se activa esta opción, todos los valores definidos en el elemento se almacenan en XML en un campo TEXTO de tipo &quot;mData&quot;. Esto significa que no habrá filtrado ni ordenación en estos campos.
* **xmlChildren (booleano)**: fuerza el almacenamiento de cada niño ( `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`

## `<enumeration>` Elemento {#enumeration--element}

### Modelo de contenido {#content-model-5}

lista desglosada:==(ayuda| valor)

### Atributos {#attributes-5}

* @basetype (string)
* @default (cadena)
* @desc (cadena)
* @label (cadena)
* @name (cadena)
* @template (cadena)

### Padres {#parents-5}

`<srcschema>`

### Niños {#children-5}

* `<help>`
* `<value>`

### Descripción {#description-5}

Este elemento nos permite definir una lista desglosada de valor. Una lista desglosada pertenece al esquema en el que está definida, pero se puede acceder a ella a través de otro esquema.

### Uso y contexto de uso {#use-and-context-of-use-4}

Las listas desglosadas se definen en el inicio de un esquema (antes de definir el elemento principal).

### Descripción del atributo {#attribute-description-5}

* **basetype (string)**: tipo de los valores almacenados en la lista desglosada.

   Lista de los tipos disponibles:

   * CUALQUIER
   * bin
   * blob
   * booleano
   * byte
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * date
   * DOMDocument
   * DOMElement
   * doble
   * enum
   * float
   * html
   * int64
   * link
   * long
   * memo
   * MNTOKEN
   * percent
   * primarykey
   * short
   * string
   * tiempo
   * timespan
   * uuid

* **default (string)**: Valor predeterminado. El valor predeterminado también puede ser uno de los valores definidos en la lista desglosada.
* **desc (cadena)**: Descripción de la lista desglosada.
* **label (string)**: Etiqueta de lista desglosada.
* **name (string)**: nombre interno de la lista desglosada.
* **template (string)**: este atributo define una referencia a un `<enumeration>` elemento compartido por varios esquemas. La definición se copia automáticamente en el esquema actual.

### Ejemplos {#examples-4}

Ejemplo de valores de lista desglosada cuyos valores se almacenan en la base de datos:

```
    <enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>

    <element label="Sample" name="Sample">
       <attribute dbEnum="myEnum" length="100" name="Number" required="true" type="string"/>
    </element>
```

Definición de una lista desglosada con un valor predeterminado:

```
 <enumeration basetype="byte" default="email" name="canal">
    <value label="Email" name="email" value="0"/> 
    <value label="Téléphone" name="phone" value="1"/>
    <value label="Call Center" name="callcenter" value="2"/>
 </enumeration>
```

## `<help>` Elemento {#help--element}

### Modelo de contenido {#content-model-6}

help:==EMPTY

### Atributos {#attributes-6}

Ninguno

### Padres {#parents-6}

`<srcschema>`  ,  `<element>`   ,   `<attribute>`    ,    `<enumeration>`     ,     `<value>`      ,     `<param />`,      `<method />`

### Niños {#children-6}

Ninguno

### Descripción {#description-6}

Este elemento permite describir un `<element>` elemento o `<attribute>` elemento. Sólo puede contener texto y se almacena en XML en la base de datos.

### Descripción del atributo {#attribute-description-6}

Este elemento no tiene atributos.

### Ejemplos {#examples-5}

```
<method name="CheckOperation" static="true"
      <helpchecks the validity of a campaign</help
...
</method> 
```

## `<join>` Elemento {#join--element}

### Modelo de contenido {#content-model-7}

join:==EMPTY

### Atributos {#attributes-7}

* @dstFilterExpr (cadena)
* @xpath-dst (cadena)
* @xpath-src (cadena)

### Padres {#parents-7}

`<element>`

### Niños {#children-7}

Ninguno

### Descripción {#description-7}

Permite definir los campos que crean una combinación entre tablas SQL.

### Uso y contexto de uso {#use-and-context-of-use-5}

Un `<join>` elemento solo se puede usar si el `<element>` elemento principal es de tipo &#39;link&#39;. Esto significa que el elemento principal debe tener declarado el atributo &quot;@type=link&quot;.

No es necesario especificar el nombre y la Área de nombres de la tabla remota en el `<join>` elemento. Deben especificarse en el elemento principal `<element>`.

Por convención, los vínculos se definen al final del esquema.

Si no se especifica el `<join>` elemento cuando se define el elemento de tipo de vínculo, el vínculo se colocará automáticamente en las claves principales de ambas tablas.

### Descripción del atributo {#attribute-description-7}

* **dstFilterExpr (cadena)**: este atributo permite restringir el número de valores elegibles en la tabla remota.
* **xpath-dst (string)**: este atributo recibe un atributo Xpath (@name de la tabla remota).
* **xpath-src (string)**: este atributo recibe un atributo Xpath (@name en el esquema actual).

### Ejemplos {#examples-6}

Vínculo entre el campo &#39;correo electrónico&#39; de la tabla actual y el campo &quot;@compagny-id&quot; de la tabla remota:

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

Vínculo filtrado hacia la tabla &quot;cus:Country&quot; basado en el contenido del campo &quot;@country&quot; que debe contener el valor &#39;EN&#39;:

```
<element name="StockEN" type="link" label="MyLink" target="cus:Stock">
   <join xpath-dst="@country" xpath-src="@code" dstFilterExpr="@country = 'EN'"/>
 </element>
```

## `<key>` Elemento {#key--element}

### Modelo de contenido {#content-model-8}

key:==keyfield

### Atributos {#attributes-8}

* @allowEmptyPart (booleano)
* @applyIf (cadena)
* @internal (booleano)
* @label (cadena)
* @name (MNTOKEN)
* @noDbIndex (booleano)

### Padres {#parents-8}

`<element>`

### Niños {#children-8}

`<keyfield>`

### Descripción {#description-8}

Este elemento permite definir una clave para identificar un registro en la tabla.

Una tabla debe tener al menos una clave.

### Uso y contexto de uso {#use-and-context-of-use-6}

Como regla, las claves se declaran después del elemento principal del esquema y los índices.

Una clave se conoce como compuesta si incluye varios campos (es decir, varios `<keyfield>` elementos secundarios). No utilice una clave compuesta para definir una clave principal.

Si el elemento principal del esquema contiene el atributo &quot;@autopk=true&quot;, la clave principal es única. Sólo podemos tener una clave principal por esquema.

Los primeros 1000 identificadores están reservados, por lo que si es necesario definir un rango de valores para las claves, el inicio será 1000.

### Descripción del atributo {#attribute-description-8}

* **allowEmptyPart (boolean)**: en el caso de una clave compuesta, si este atributo está activado, la clave se considera válida si al menos una de sus claves no está vacía. Si este es el caso, el valor de noción vacío es &quot;0&quot; (booleano o para todos los tipos de datos numéricos). De forma predeterminada, es necesario introducir todas las claves que conforman una clave compuesta.
* **applyIf (string)**: este atributo permite hacer que la clave sea opcional. Define la condición según la cual se aplicará la definición de clave. Este atributo recibe una expresión XTK.
* **interno (booleano)**: si se activa, este atributo permite a Adobe Campaign saber que la clave es principal.
* **label (string)**: de la clave.
* **name (MNTOKEN)**: nombre interno de la clave.
* **noDbIndex (boolean)**: si está activado (noDbIndex=&quot;true&quot;), el campo que coincide con la clave no se indexará.

### Ejemplos {#examples-------}

Declaración de una clave compuesta que autoriza el campo &quot;@expr&quot; o &quot;alias&quot; a estar vacío:

```
<key name="node" allowEmptyPart="true">
  <keyfield xpath="@expr"/>
   <keyfield xpath="@alias"/>
 </key>
```

Declaración de una clave principal en el campo &quot;Nombre&quot; del tipo STRING en una consulta SQL `<srcschema>` y la correspondiente:

```
 
<key name="PrimaryKey" internal="true">  
  <keyfield xpath="@name"/>
</key>

CREATE UNIQUE INDEX Schema_PrimaryKey ON Schema(sName);
```

## `<keyfield>` Elemento {#keyfield--element}

### Modelo de contenido {#content-model-9}

keyfield:==EMPTY

### Atributos {#attributes-9}

* @xlink (MNTOKEN)
* @xpath (MNTOKEN)

### Padres {#parents-9}

`<key>`  ,  `<dbindex />`

### Niños {#children-9}

Ninguno

### Descripción {#description-9}

Este elemento define los campos que se integrarán en un índice o una clave.

### Descripción del atributo {#attribute-description-9}

* **xlink (MNTOKEN)**: le permite hacer referencia automáticamente a claves externas definidas en la unión para una tabla de relación (vínculo N-N).
* **xpath (MNTOKEN)**: definición de un índice o una clave en un `<attribute>` elemento. Este atributo recibe un Xpath que define la ruta al atributo esquema que define la clave o el índice.

### Ejemplos {#examples-}

Selección del campo &quot;sName&quot; en un índice con una Xpath en &quot;@name&quot;:

```
<keyfield xpath="@name"/>
```

## `<method>` Elemento {#method--element}

### Modelo de contenido {#content-model-10}

método:==( help | parámetros)

### Atributos {#attributes-10}

* @_operation (string)
* @access (cadena)
* @const (booleano)
* @hidden (booleano)
* @label (cadena)
* @library (cadena)
* @name (MNTOKEN)
* @pkonly (booleano)
* @static (boolean)

### Padres {#parents-10}

`<methods>`  ,  `<interface />`

### Niños {#children-10}

* `<help>`
* `<parameters>`

### Descripción {#description-10}

Este elemento permite definir un método SOAP.

### Uso y contexto de uso {#use-and-context-of-use-7}

Los métodos SOAP habilitan procesos de aplicación.

&quot;@library&quot; es necesario para declarar un nuevo método (no nativo): la Área de nombres y el nombre utilizados para la biblioteca son independientes de la Área de nombres y el nombre del esquema en el que se encuentra la declaración.

### Descripción del atributo {#attribute-description-10}

* **access (cadena)**: este atributo define el control de acceso para utilizar el método. Si falta este atributo, la identificación es obligatoria. Los valores disponibles son: &#39;anónimo&#39;, &#39;admin&#39; y &#39;sql&#39;.
* **const (booleano)**: si se activa, este atributo significa que el método declarado alterará la entidad
* **label (string)**: del método.
* **library (string)**: este método no es nativo de la aplicación. Este atributo toma el valor de la biblioteca de métodos en la que se encuentra la definición de método (nms:mylibrary.js).
* **name (MNTOKEN)**: nombre de método único.
* **static (boolean)**: si este atributo está activado, el método se considera autónomo, se deben especificar todos los parámetros del método cuando se llame a él.

### Ejemplos {#examples-7}

Definición del método &quot;Subscribe&quot; out of box:

```
 
<method name="Subscribe" static="true">
      <help>Creation of update of a recipient's subscription to an information service</help>
      <parameters>
        <param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string"/>
        <param desc="Recipient to subscribe and possibly create" name="recipient"
               type="DOMElement"/>
        <param desc="Create the recipient if they don't exist" name="create" type="boolean"/>
      </parameters>     
    </method>
```

## `<methods>` Elemento {#methods--element}

### Modelo de contenido {#content-model-11}

métodos:==método

### Atributos {#attributes-11}

Ninguno

### Padres {#parents-11}

`<srcschema>`

### Niños {#children-11}

method

### Descripción {#description-11}

Este elemento permite definir un `<method>` elemento. Es obligatorio para declarar un método.

### Descripción del atributo {#attribute-description-11}

Este elemento no tiene atributos.

### Ejemplos {#examples-8}

```
<methods async="true"
...// definition of one or more <method
</methods>
```

## `<param>` Elemento {#param--element}

### Modelo de contenido {#content-model-12}

param:==help

### Atributos {#attributes-12}

* @_operation (string)
* @desc (cadena)
* @enum (cadena)
* @inout (cadena)
* @label (cadena)
* @localizable (cadena)
* @name (MNTOKEN)
* @Área de nombres (MNTOKEN)
* @type (cadena)

### Padres {#parents-12}

`<parameters>`

### Niños {#children-12}

`<help>`

### Descripción {#description-12}

Este elemento permite definir un parámetro para llamar a un método SOAP.

### Descripción del atributo {#attribute-description-12}

* **desc (cadena)**: descripción que afecta al `<param>` elemento.
* **inout (cadena)**: este atributo define si el parámetro se encuentra o no en la entrada (entrada) o salida (salida) de la llamada SOAP. Si no se especifica este atributo, el parámetro predeterminado es input (&quot;@inout=in&quot;).
* **label (string)**: `<param>` label
* **localizable (cadena)**: si se activa, este atributo indica a la herramienta de recopilación que recupere el valor del atributo &quot;@label&quot; para traducción (uso interno).
* **name (MNTOKEN)**: nombre interno del `<param>`
* **type (string)**: este atributo define el tipo de `<param>` elemento

   Lista de los tipos disponibles:

   * CUALQUIER
   * bin
   * blob
   * booleano
   * byte
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * date
   * DOMDocument
   * DOMElement
   * doble
   * enum
   * float
   * html
   * int64
   * link
   * long
   * memo
   * MNTOKEN
   * percent
   * primarykey
   * short
   * string
   * tiempo
   * timespan
   * uuid

### Ejemplos {#examples-9}

Definición de la configuración de entrada &quot;serviceName&quot; del tipo de cadena de caracteres:

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```

## `<parameters>` Elemento {#parameters--element}

### Modelo de contenido {#content-model-13}

parameters:==param

### Atributos {#attributes-13}

Ninguno

### Padres {#parents-13}

`<method>`

### Niños {#children-13}

`<param>`

### Descripción {#description-13}

Este elemento define un grupo de `<parameter>` elementos.

### Uso y contexto de uso {#use-and-context-of-use-8}

Este elemento es obligatorio, incluso para un solo `<param>` elemento secundario del `<method>` elemento.

### Descripción del atributo {#attribute-description-13}

Ninguno

### Ejemplos {#examples-10}

```
<parameters
... //definition of one or more <param
</parameters>
```

## `<srcschema>` Elemento {#srcschema--element}

### Modelo de contenido {#content-model-14}

srcSchema:==(attribute) | createdBy | datos | element | lista desglosada | ayuda | interfaz | métodos | modifiedBy)

### Atributos {#attributes-14}

created (datetime), createdBy-id (long), desc (string), entitySchema (string), expandedSchema (string), img (string), implements (string), label (string), labelSingular (string), lastModified (datetime), library (boolean), mappingType (string), modifiedBy-id (long), name (string), Área de nombres (cadena), useRecycleBin (booleano), vista (booleano), xtkschema (cadena)

### Padres {#parents-14}

Ninguno

### Niños {#children-14}

* `<attribute>`
* `<createdby>`
* `<data>`
* `<element>`
* `<enumeration>`
* `<help>`
* `<interface>`
* `<methods>`
* `<modifiedby>`

### Descripción {#description-14}

El `<srcschema>` es el elemento raíz de un esquema. Es el punto de entrada para la definición del esquema.

### Uso y contexto de uso {#use-and-context-of-use-9}

La presentación de esquema está disponible en [Acerca de la referencia](../../configuration/using/about-schema-reference.md) de esquema y la estructura [de](../../configuration/using/schema-structure.md)Esquema.

### Descripción del atributo {#attribute-description-14}

* **created (datetime)**: este atributo proporciona información sobre la fecha y hora de creación del esquema. Tiene el formulario &quot;Fecha y hora&quot;. Los valores mostrados se toman del servidor. La hora se muestra en formato UTC.
* **createdBy-id (long)**: es el identificador del operador que creó el esquema.
* **desc (cadena)**: Descripción del esquema
* **entitySchema (cadena)**: esquema básico en el que se basan la sintaxis y la aprobación (de forma predeterminada para Adobe Campaign: xtk:srcSchema). Cuando guarde el esquema actual, Adobe Campaign aprobará su gramática con el esquema declarado en el atributo @xtkschema.
* **expandedSchema (cadena)**: recibe el nombre del esquema predeterminado en el que se basa la extensión de esquema actual. El formulario es &quot;Área de nombres:nombre&quot;.
* **img (cadena)**: icono vinculado al esquema (puede definirse en el asistente para la creación de esquemas).
* **label (string)**: Etiqueta de esquema.
* **labelSingular (cadena)**: etiqueta (singular) para mostrar en la interfaz.
* **lastModified (datetime)**: este atributo proporciona información sobre la fecha y hora de la última modificación. Tiene el formulario &quot;Fecha y hora&quot;. Los valores mostrados se toman del servidor. La hora se muestra en formato UTC.
* **library (boolean)**: uso del esquema como biblioteca y no como entidad. Por lo tanto, otros esquemas pueden hacer referencia a este esquema gracias a los atributos &quot;@ref&quot; y &quot;@template&quot;.
* **mappingType (cadena)**:

   * &quot;sql&quot;: asignación de bases de datos
   * &quot;textFile&quot;: asignación de archivos de texto
   * &quot;xmlFile&quot;: Asignación de archivos de texto en formato XML
   * &quot;binaryFile&quot;: asignación de archivos binarios

* **modifiedBy-id (long)**: coincide con el identificador del operador que cambió el esquema.
* **name (string)**: nombre de esquema único.
* **área de nombres (cadena)**: área de nombres del esquema (predeterminado: nms, xtk, nl). Al crear un nuevo esquema para un proyecto, le recomendamos que utilice una Área de nombres dedicada.
* **useRecycleBin (boolean)**: activa la función de papelera en la aplicación. Los registros eliminados se colocarán en la papelera antes de la eliminación final. Esta función solo está disponible en modo &quot;Envío&quot;.
* **vista (booleana)**: si se activa (@vista=&quot;true&quot;), el esquema se utilizará como vista. El asistente para la actualización de la estructura de la base de datos no tendrá en cuenta el esquema. Esta opción se utiliza principalmente para hacer referencia a tablas externas.
* **xtkschema (string)**: nombre del esquema que define la gramática del esquema (xtk:srcSchema de forma predeterminada).

### Ejemplos {#examples-11}

`<srcschema>` del esquema &quot;nms:envío&quot; fuera de la casilla

```
<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```

## `<sysfilter>` Elemento {#sysfilter--element}

### Modelo de contenido {#content-model-15}

sysFilter:==condition

### Atributos {#attributes-15}

Ninguno

### Padres {#parents-15}

`<element>`

### Niños {#children-15}

`<condition>`

### Descripción {#description-15}

Este elemento permite definir un filtro.

### Descripción del atributo {#attribute-description-15}

Este elemento no tiene atributos.

### Ejemplos {#examples-12}

Definición de un filtro con una condición en el atributo @name:

```
<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```

## `<value>` Elemento {#value--element}

### Modelo de contenido {#content-model-16}

value:==help

### Atributos {#attributes-16}

* @applyIf (cadena)
* @desc (cadena)
* @enabledIf (cadena)
* @img (cadena)
* @label (cadena)
* @name (cadena)
* @value (cadena)

### Padres {#parents-16}

`<enumeration>`

### Niños {#children-16}

`<help>`

### Descripción {#description-16}

Este elemento permite definir los valores almacenados en una lista desglosada.

### Descripción del atributo {#attribute-description-16}

* **applyIf (string)**: este atributo le permite convertir un valor de lista desglosada en opcional. Recibe una expresión XTK.
* **desc (cadena)**: descripción del valor de lista desglosada.
* **enabledIf (string)**: condición para activar el valor de lista desglosada.
* **img (cadena)**: imagen vinculada a la lista desglosada en el formulario &quot;Área de nombres:nombre_imagen&quot;. La imagen debe importarse en el servidor de aplicaciones.
* **label (string)**: del valor de lista desglosada.
* **name (string)**: nombre interno del valor de lista desglosada.
* **value (string)**: valor del valor de lista desglosada. El tipo de valor se define en función del tipo de lista desglosada. Si la lista desglosada es del tipo de cadena de caracteres, sólo puede contener valores de tipo de cadena de caracteres.

### Ejemplos {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
