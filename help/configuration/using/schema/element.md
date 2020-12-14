---
solution: Campaign Classic
product: campaign
title: Elementos y atributos
description: Elementos y atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 922257b157f8d76d6e703b0510ff689d1aa4d067
workflow-type: tm+mt
source-wordcount: '2012'
ht-degree: 0%

---


# elemento del elemento {#element--element}

## Modelo de contenido {#content-model-4}

element:==(atributo | compute-string | dbindex | predeterminado | element | ayuda | join | key | sysFilter | translateDefault)

## Atributos {#attributes-4}

_operation (string), avanzado (booleano), acumulado (string), aplicableIf (string), autopk (boolean), perteneceTo (string), convDate (string), dataPolicy (string), dataSource (string), dbEnum (string), defOnDuplicate (boolean), default (string), desc (string), displayAsField (boolean, doesNotSupportDiff (boolean), edit (string), emptyKeyValue (string), enum (string), enumImage (string), expandedSchemaTarget (string), expr (string), externalJoin (boolean), feature (string), featureDate (boolean), filterPath (string), folderLink (string), folderModel (string), Process (string), fullLoad (boolean), hierarchical (boolean), hierarchicalPath (string), img (string), inout (string), integridad (string), label (string), labelSingular (string), length (string), localizable (boolean), name (MNTOKEN), noDbIndex (boolean), noKey (boolean) order (boolean), overflowtable (boolean), pkSequence (string), pkgStatus (string), ref (string), required (boolean), revAdvanced (boolean), revCardinality (string), revDesc (string), revExternalJoin (boolean), revIntegrity (string), revLabel (string), vLink (string), revTarget (string), revVisibleIf (string), sql (boolean), sqlname (string), sqltable (string), tableSpace (string), tableSpaceIndex (string), destinatario (MNTOKEN), template (string), permanentTable (boolean), translateDefault (string), translateExpr cadena), type (MNTOKEN), unbound (booleano), user (boolean), userEnum (string), visibleIf (string), xml (boolean), xmlChildren (boolean)

## Padres {#parents-4}

`<srcschema>`

`<element>`

## Niños {#children-4}

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

## Descripción {#description-4}

Hay cuatro tipos de `<element>` elementos en Adobe Campaign:

* Raíz `<element>` : define el nombre de la tabla SQL que coincide con el esquema.
* Estructura `<element>`: define un grupo de `<element>`   o   `<attribute>`    elementos.
* Vínculo `<element>`: define un vínculo. Estos elementos deben incluir el atributo &quot;@type=link&quot;.
* XML `<element>` : define un campo de tipo de texto &quot;mData&quot;. Este elemento debe incluir el atributo &quot;@type=xml&quot;.

## Descripción del atributo {#attribute-description-4}

* **_operation (string)**: define el tipo de escritura en la base de datos.

   Este atributo se utiliza principalmente al ampliar los esquemas predeterminados.

   Los valores accesibles son:

   * &quot;ninguno&quot;: sólo reconciliación. Esto significa que Adobe Campaign recuperará el elemento sin actualizarlo ni generar un error si no existe.
   * &quot;insertOrUpdate&quot;: actualizar con inserción. Esto significa que Adobe Campaign actualizará el elemento o lo creará si no existe.
   * &quot;insertar&quot;: inserción. Esto significa que Adobe Campaign insertará el elemento sin comprobar si existe.
   * &quot;update&quot;: actualizar. Esto significa que Adobe Campaign actualizará el elemento o generará un error si no existe.
   * &quot;delete&quot;: eliminación. Esto significa que Adobe Campaign recuperará y eliminará los elementos.

* **avanzado (booleano)**: cuando esta opción está activada (@advanced=&quot;true&quot;), permite ocultar el atributo en la lista de los campos disponibles a los que se puede acceder para configurar una lista en un formulario.
* **acumulada (cadena)**: permite copiar la definición de un esquema  `<element>`  mediante otro. Este atributo recibe una declaración de esquema en forma de &quot;Área de nombres:nombre&quot;.
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

* **dbEnum (cadena)**: recibe el nombre interno de una lista desglosada &quot;cerrada&quot;. Los valores de lista desglosada deben definirse en `<srcschema>`.
* **defOnDuplicate (booleano)**: si se activa este atributo, cuando se duplica un registro, el valor predeterminado (definido en @default) se vuelve a aplicar automáticamente al registro.
* **default (string)**: permite definir el comportamiento del elemento (llamada a una función, valor predeterminado). Este atributo recibe una expresión XTK.
* **desc (cadena)**: permite insertar una descripción del elemento. Esta descripción se muestra en la barra de estado de la interfaz.
* **displayAsField (boolean)**: si se activa este atributo, se  `<element>`  mostrará un tipo de &quot;vínculo&quot; como campo en la vista de árbol de la ficha esquemas (&quot;Estructura&quot;). De este modo, es posible mostrar un vínculo como campo local y cambiar su comportamiento durante una consulta. Cuando el elemento se encuentra en la SELECCIÓN de una consulta, se utilizará el valor del destinatario del vínculo. Cuando el elemento se encuentra en el WHERE de una consulta, se utilizará la clave subyacente del vínculo.
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
* **tableSpace (cadena)**: este atributo permite especificar un nuevo tablespace de almacenamiento de datos para una tabla (válido en la raíz  `<element>`).
* **tableSpaceIndex (string)**: este atributo permite especificar un nuevo tablespace de almacenamiento de índice para una tabla (válido en la raíz  `<element>`).
* **destinatario (MNTOKEN)**: recibe el nombre del esquema de destinatario al crear un vínculo entre tablas. Este atributo solo está activo para elementos de tipo &quot;link&quot;.
* **template (string)**: este atributo define una referencia a un  `<element>` elemento compartido por varios esquemas. La definición se copia automáticamente en el esquema actual.
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
* **xmlChildren (booleano)**: fuerza el almacenamiento de cada niño (  `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`
