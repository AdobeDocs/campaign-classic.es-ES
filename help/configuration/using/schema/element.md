---
product: campaign
title: Elementos y atributos
description: Elementos y atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 60f15ae5-b2bd-48f9-aa45-8f795a3071aa
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '2012'
ht-degree: 0%

---

# elemento {#element--element}

## Modelo de contenido {#content-model-4}

element:==(attribute) | compute-string | dbindex | predeterminado | elemento | ayuda | join | clave | sysFilter | translateDefault)

## Atributos {#attributes-4}

_operation (cadena), avanzado (booleano), acumulado (cadena), aplicableIf (cadena), autopk (booleano), perteneceTo (cadena), convDate (cadena), dataPolicy (cadena), dataSource (cadena), dbEnum (cadena), defOnDuplicate (booleano), valor predeterminado (cadena), desc (cadena), displayAsField (booleano), doesNotSupportDiff (boolean), edit (string), emptyKeyValue (string), enum (string), enumImage (string), expandSchemaTarget (string), expr (string), externalJoin (boolean), feature (string), featureDate (boolean), filterPath (string), folderLink (string), folderModel, Process (cadena), fullLoad (booleano), hierarchy (booleano), hierarchyPath (cadena), img (cadena), inout (cadena), integridad (cadena), label (cadena), labelSingular (cadena), length (cadena), localizable (booleano), name (MNTOKEN), noDbIndex (booleano), noKey (booleano), ordenadas (booleano), sobreflexible (booleano), pkSequence (cadena), pkgStatus (cadena), ref (cadena), obligatorio (booleano), revAdvanced (booleano), revCardinality (cadena), revDesc (cadena), revExternalJoin (booleano), revIntegrity (cadena), revLabel (cadena), vLink (cadena), revTarget (cadena), revVisibleIf (cadena), sql (booleano), sqlname (cadena), sqltable (cadena), tableSpace (cadena), tableSpaceIndex (cadena), target (MNTOKEN), template (cadena), interimTable (booleano), translateDefault (cadena), translateExpr), tipo (MNTOKEN), no enlazado (booleano), usuario (booleano), userEnum (cadena), visibleIf (cadena), xml (booleano), xmlChildren (booleano)

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

Existen cuatro tipos de elementos `<element>` en Adobe Campaign:

* Raíz `<element>` : define el nombre de la tabla SQL que coincide con el esquema.
* Estructura `<element>` : define un grupo de `<element>`   o   `<attribute>`    elementos.
* Vínculo `<element>` : define un vínculo. Estos elementos deben incluir el atributo &quot;@type=link&quot;.
* XML `<element>` : define un campo de tipo texto &quot;mData&quot;. Este elemento debe incluir el atributo &quot;@type=xml&quot;.

## Descripción de atributo {#attribute-description-4}

* **_operation (cadena)**: define el tipo de escritura en la base de datos.

   Este atributo se utiliza principalmente al ampliar los esquemas predeterminados.

   Los valores accesibles son:

   * &quot;ninguno&quot;: solo reconciliación. Esto significa que Adobe Campaign recuperará el elemento sin actualizarlo o generando un error si no existe.
   * &quot;insertOrUpdate&quot;: actualizar con inserción. Esto significa que Adobe Campaign actualizará el elemento o lo creará si no existe.
   * &quot;insertar&quot;: inserción. Esto significa que Adobe Campaign insertará el elemento sin comprobar si existe.
   * &quot;actualización&quot;: actualización. Esto significa que Adobe Campaign actualizará el elemento o generará un error si no existe.
   * &quot;eliminar&quot;: eliminación. Esto significa que Adobe Campaign recuperará y eliminará los elementos.

* **avanzado (booleano)**: cuando esta opción está activada (@advanced=&quot;true&quot;), permite ocultar el atributo en la lista de campos disponibles accesibles para configurar una lista en un formulario.
* **acumulado (cadena)**: permite copiar la definición de un  `<element>`  mediante otro esquema. Este atributo recibe una declaración de esquema en forma de &quot;namespace:name&quot;.
* **applyIf (cadena)**: condición para aplicar el índice. Este atributo recibe una expresión XTK.
* **autopk (booleano)**: si esta opción está activada (autopk=&quot;true&quot;), se definirá automáticamente una clave única. Esta opción solo se puede utilizar en el elemento principal del esquema. Advertencia, Adobe Campaign solo garantiza que la clave generada sea única. No se garantiza que los valores clave sean consecutivos e incrementales.
* **dataPolicy (cadena)**: permite especificar restricciones de aprobación en valores permitidos en el campo SQL. Los valores de este atributo son:

   * &quot;ninguno&quot;: sin valor
   * &quot;smartCase&quot;: mayúsculas y minúsculas
   * &quot;lowerCase&quot;: todas las minúsculas
   * &quot;upperCase&quot;: todas las mayúsculas
   * &quot;correo electrónico&quot;: dirección de correo electrónico
   * &quot;phone&quot;: número de teléfono
   * &quot;identificador&quot;: nombre del identificador
   * &quot;resIdentifier&quot;: nombre de archivo

* **dbEnum (cadena)**: recibe el nombre interno de una enumeración &quot;cerrada&quot;. Los valores de enumeración deben definirse en `<srcschema>`.
* **defOnDuplicate (booleano)**: si este atributo está activado, cuando se duplica un registro, el valor predeterminado (definido en @default) se vuelve a aplicar automáticamente al registro.
* **predeterminado (cadena)**: permite definir el comportamiento del elemento (llamada a una función, valor predeterminado). Este atributo recibe una expresión XTK.
* **desc (cadena)**: permite insertar una descripción del elemento. Esta descripción se muestra en la barra de estado de la interfaz.
* **displayAsField (booleano)**: si este atributo está activado, se  `<element>`  mostrará un tipo &quot;vínculo&quot; como campo en la vista de árbol de los esquemas (pestaña &quot;Estructura&quot;). De este modo, es posible mostrar un vínculo como campo local y cambiar su comportamiento durante una consulta. Cuando el elemento se encuentra en el SELECT de una consulta, se utiliza el valor del destino del vínculo. Cuando el elemento se encuentra en el WHERE de una consulta, se utiliza la clave subyacente del vínculo.
* **editar (cadena)**: este atributo especifica el tipo de entrada que se utilizará en el formulario vinculado al esquema.
* **enum (cadena)**: recibe el nombre de la enumeración vinculada al campo. La enumeración puede insertarse en el mismo esquema o en un esquema remoto.
* **expr (cadena)**: este atributo define un campo calculado para el que no se almacena ninguna definición en la tabla. Recibe una expresión Xpath o XTK (cadena).
* **externalJoin (booleano)**: unión externa en un elemento de tipo &quot;vínculo&quot;.
* **característica (cadena)**: define un campo de características: Estos campos se utilizan para ampliar los datos en un cuadro existente, pero con almacenamiento en un cuadro anexo. Los valores aceptados son:

   * &quot;compartido&quot;: el contenido se almacena en una tabla compartida por tipo de datos
   * &quot;dedicada&quot;: el contenido se almacena en una tabla dedicada

   Las tablas de características SQL se crean automáticamente en función del tipo de característica:

   * dedicada: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * shared: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

   Existen dos tipos de campos de características: campos simples en los que se autoriza un valor único en la característica y campos de opción múltiple, en los que la característica está vinculada a un elemento de colección que puede contener varios valores.

   Cuando una característica se define en un esquema, este esquema debe tener una clave principal basada en un solo campo (las claves compuestas no están autorizadas).

* **featureDate (booleano)**: vinculado al campo de características &quot;@feature&quot;. Si su valor es &quot;true&quot;, le permite averiguar cuándo se actualizó por última vez el valor.
* **filterPath (cadena)**: este atributo recibe una Xpath y permite definir un filtro en un campo.
* **folderLink (cadena)**: este atributo recibe el nombre del vínculo que permite recuperar los archivos que contienen entidades.
* **folderModel (cadena)**: define el tipo de carpeta que habilita el almacenamiento de entidades. Este atributo solo se define si &quot;@folderLink&quot; está presente.
* **folderProcess (cadena)**: define el vínculo en el que se almacenan las instancias del modelo de entidad. Este atributo solo se define si &quot;@folderLink&quot; está presente.
* **fullLoad (booleano)**: este atributo fuerza la visualización de todos los registros de una tabla durante la selección de campos en un formulario.
* **img (cadena)**: recibe la ruta de una imagen vinculada a un elemento. El valor de este atributo es del tipo &quot;namespace:image name&quot;. Por ejemplo: img=&quot;cus:myImage.jpg&quot;. Físicamente, la imagen debe importarse al servidor de aplicaciones.
* **integridad (cadena)**: integridad referencial de la aparición de la tabla de origen hacia la tabla de destino.

   Los valores accesibles son:

   * &quot;define&quot;: Adobe Campaign no elimina la entidad si se hace referencia a ella mediante el vínculo
   * &quot;normal&quot;: al eliminar la incidencia de origen, se inicializan las claves del vínculo en la incidencia de destino (modo predeterminado), este tipo de integridad inicializa todas las claves externas
   * &quot;own&quot;: la eliminación de la incidencia de origen déclencheur la eliminación de la incidencia de destino
   * &quot;Descargar copia&quot;: similar a &quot;own&quot; (en caso de eliminación) o a ocurrencias de duplicados (en caso de duplicación)
   * &quot;neutral&quot;: no hace nada

* **label (cadena)**: etiqueta de elemento.
* **labelSingular (cadena)**: etiqueta (forma singular) del elemento utilizado en algunas partes de la interfaz.
* **length (string)**: max. número de caracteres autorizados para un valor del campo SQL de tipo &quot;cadena&quot;.
* **localizable (booleano)**: si está activado, este atributo indica a la herramienta de recopilación que recupere el valor del atributo &quot;@label&quot; para la traducción (uso interno).
* **nombre (MNTOKEN)**: nombre interno del elemento que coincide con el nombre de la tabla. El valor del atributo &quot;@name&quot; debe ser corto, preferiblemente en inglés, y cumplir con las restricciones de nomenclatura vinculadas a XML.

   Cuando se escribe el esquema en la base de datos, Adobe Campaign agrega automáticamente los prefijos al nombre del campo.

   * &quot;i&quot;: para el tipo &quot;integer&quot;.
   * &quot;d&quot;: para el tipo &quot;doble&quot;.
   * &quot;s&quot;: para el tipo de cadena de caracteres.
   * &quot;ts&quot;: para el tipo &quot;fecha&quot;.

   Para definir el nombre de la tabla de forma autónoma, debe utilizar el atributo &quot;@sqltable&quot; en la definición del elemento de esquema principal.

* **noDbIndex (booleano)**: permite especificar que el elemento no se indexe.
* **ordenado (booleano)**: si el atributo está activado (ordered=&quot;true&quot;), Adobe Campaign mantiene la secuencia de declaración de elementos en un elemento de colección XML.
* **pkSequence (cadena)**: recibe el nombre de la secuencia que se utilizará para calcular una clave incremental automática. Este atributo solo se puede utilizar si se define una clave incremental automática en el elemento raíz del esquema.
* **pkgStatus (cadena)**: durante las exportaciones de paquetes, los valores se tienen en cuenta como una función del valor de este atributo:

   * &quot;always&quot;: el elemento siempre estará presente
   * &quot;never&quot;: el elemento nunca estará presente
   * &quot;predeterminado (o nada)&quot;: el elemento se exporta a menos que sea el elemento predeterminado o si no es un campo interno y no sería compatible con otras instancias

* **ref (cadena)**: este atributo define una referencia a un >elemento> elemento compartido por varios esquemas (factorización de definición). La definición no se copia en el esquema actual.
* **obligatorio (booleano)**: si este atributo está activado (@required=&quot;true&quot;), el campo se resalta en la interfaz. La etiqueta del campo aparece en rojo en los formularios.
* **revAdvanced (booleano)**: cuando se activa, este atributo especifica que el vínculo opuesto es un vínculo &quot;avanzado&quot;.
* **revCardinality (cadena)**: este atributo define la cardinalidad de un vínculo entre dos tablas. Se utiliza en un tipo &quot;vínculo&quot; `<element>`.

   Los valores posibles son:

   * &quot;single&quot; : Vínculo de tipo 1-1 simple
   * &quot;unbound&quot;: Vínculo de colección de tipo 1-N

   De forma predeterminada, si no se especifica el atributo durante la creación del vínculo, la cardinalidad será 1-N.

* **revDesc (cadena)**: este atributo recibe una descripción vinculada al vínculo opuesto.
* **revExternalJoin (booleano)**: cuando se activa, este atributo permite forzar la unión externa en el vínculo opuesto.
* **revIntegrity (cadena)**: este atributo define la integridad en el esquema de destino. Se autorizan los mismos valores que el atributo &quot;@integridad&quot;. De forma predeterminada, Adobe Campaign le da el valor &quot;normal&quot; a este atributo.
* **revLabel (cadena)**: etiqueta del vínculo opuesto.
* **revLink (cadena)**: nombre del vínculo opuesto. Si el valor es &quot;_NONE_&quot;, no se creará ningún vínculo opuesto en el esquema de destino.
* **revTarget (cadena)**: objetivo del vínculo opuesto.
* **sql (booleano)**: si este atributo está activado (@sql=&quot;true&quot;), fuerza el almacenamiento del elemento SQL, aunque el elemento tenga la propiedad xml=&quot;true&quot;.
* **sqlname (cadena)**: nombre del campo durante la creación de la tabla. Si no se especifica &quot;@sqlname&quot;, el valor del atributo &quot;@name&quot; se utiliza de forma predeterminada. Al escribir el esquema en la tabla, los prefijos se añaden automáticamente según el tipo de campo.
* **sqltable (cadena)**: para el elemento principal del esquema, este atributo sobrecarga el nombre de la tabla SQL generada de forma predeterminada. Si no se especifica &quot;@sqltable&quot;, el nombre predeterminado se estructurará de esta manera: espacio de nombres (primera letra en mayúsculas) seguido del valor de SrcSchema &quot;@name&quot;.
* **tableSpace (cadena)**: este atributo permite especificar un nuevo tablespace de almacenamiento de datos para una tabla (válido en la raíz  `<element>`).
* **tableSpaceIndex (cadena)**: este atributo permite especificar un nuevo tablespace de almacenamiento de índices para una tabla (válido en la raíz  `<element>`).
* **target (MNTOKEN)**: recibe el nombre del esquema de destino al crear un vínculo entre tablas. Este atributo solo está activo para elementos de tipo &quot;vínculo&quot;.
* **plantilla (cadena)**: este atributo define una referencia a un  `<element>` elemento compartido por varios esquemas. La definición se copia automáticamente en el esquema actual.
* **translateDefault (cadena)**: si se encuentra un atributo &quot;@default&quot;, &quot;@translateDefault&quot; le permitirá redefinir una expresión que coincida con la definida en @default, que la herramienta de traducción (uso interno) recopilará.
* **translateExpr (cadena)**: si se encuentra un atributo &quot;@expr&quot;, el atributo &quot;@translateExpr&quot; permite redefinir una expresión que coincida con la definida en &quot;@expr&quot; y que la herramienta de traducción (uso interno) recopilará.
* **tipo (MNTOKEN)**: define el tipo de datos almacenados en el elemento .

   Lista de tipos disponibles:

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
   * double
   * enum
   * float
   * html
   * int64
   * vínculo
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
* **userEnum (cadena)**: recibe el nombre interno de una enumeración &quot;open&quot;. El usuario puede definir los valores de enumeración en la interfaz.
* **xml (booleano)**: si esta opción está activada, todos los valores definidos en el elemento se almacenan en XML en un campo TEXT type &quot;mData&quot; . Esto significa que no habrá filtrado ni ordenación en estos campos.
* **xmlChildren (booleano)**: fuerza el almacenamiento de cada niño (  `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`
