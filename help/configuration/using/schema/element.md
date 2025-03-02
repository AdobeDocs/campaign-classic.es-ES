---
product: campaign
title: 'Elementos y atributos de esquema: elemento element'
description: elemento
feature: Schema Extension
exl-id: 60f15ae5-b2bd-48f9-aa45-8f795a3071aa
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '2029'
ht-degree: 0%

---

# elemento {#element--element}


## Modelo de contenido {#content-model-4}

element:==(atributo) | compute-string | dbindex | predeterminado | elemento | ayuda | unirse | key | sysFilter | translatedDefault)

## Atributos {#attributes-4}

_operation (cadena), advanced (booleano), aggregate (cadena), applyIf (cadena), autopk (booleano), belongingTo (cadena), convDate (cadena), dataPolicy (cadena), dataSource (cadena), dbEnum (cadena), defOnDuplicate (booleano), default (cadena), desc (cadena), displayAsField (booleano), doesNotSupportDiff (booleano), edit (cadena), emptyKeyValue (cadena), enum (cadena), enumImage (cadena), expandSchemaTarget (cadena), expr (cadena), externalJoin (booleano), feature (cadena), featureDate (booleano), filterPath (cadena), folderLink (cadena), folderModel (cadena), folderProcess (cadena), fullLoad (booleano), jerárquico (booleano), hierarchyPath (cadena), img (cadena), inout (cadena), integridad (cadena), labelSingular (cadena), longitud (cadena), localizable (booleano), nombre (MNTOKEN), noDbIndex (booleano), noKey (booleano), ordenado (booleano), tabla de desbordamiento (booleano), pkSequence (cadena), pkgStatus (cadena), ref (cadena), obligatorio (booleano), revAdvanced (booleano), revCardinality (cadena), revDesc (cadena), revExternalJoin (booleano), revIntegrity (cadena), revLabel (cadena), revTarget (cadena) revVisibleIf (cadena), sql (booleano), sqlname (cadena), sqltable (cadena), tableSpace (cadena), tableSpaceIndex (cadena), target (TOKEN MENÚ), plantilla (cadena), temporaryTable (booleano), translatedDefault (cadena), translatedExpr (cadena), type (TOKEN MENÚ), unbound (booleano), user (cadena), visibleIf (cadena), xml (booleano), xmlChildren (booleano)

## Padres {#parents-4}

`<srcschema>`

`<element>`

## Tareas secundarias {#children-4}

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
* Vínculo `<element>` : define un vínculo. Estos elementos deben incluir el atributo @type=link.
* XML `<element>` : define un campo &quot;mData&quot; de tipo texto. Este elemento debe incluir el atributo @type=xml.

## Descripción de atributo {#attribute-description-4}

* **_operation (cadena)**: define el tipo de escritura en la base de datos.

  Este atributo se utiliza principalmente para ampliar esquemas predeterminados.

  Los valores accesibles son:

   * &quot;ninguno&quot;: reconciliación sola. Esto significa que Adobe Campaign recuperará el elemento sin actualizarlo ni generar un error si no existe.
   * &quot;insertOrUpdate&quot;: actualizar con inserción. Esto significa que Adobe Campaign actualizará el elemento o lo creará si no existe.
   * &quot;insert&quot;: inserción. Esto significa que Adobe Campaign insertará el elemento sin comprobar si existe.
   * &quot;update&quot;: update. Esto significa que Adobe Campaign actualizará el elemento o generará un error si no existe.
   * &quot;eliminar&quot;: eliminación. Esto significa que Adobe Campaign recuperará y eliminará elementos.

* **advanced (boolean)**: cuando esta opción está activada (@advanced=&quot;true&quot;), permite ocultar el atributo en la lista de campos disponibles a los que se puede acceder para configurar una lista en un formulario.
* **aggregate (string)**: permite copiar la definición de un `<element>` a través de otro esquema. Este atributo recibe una declaración de esquema en forma de &quot;namespace:name&quot;.
* **applyIf (string)**: condición para aplicar el índice. Este atributo recibe una expresión XTK.
* **autopk (booleano)**: si esta opción está activada (autopk=&quot;true&quot;), se definirá automáticamente una clave única. Esta opción solo se puede utilizar en el elemento principal del esquema. Advertencia: Adobe Campaign solo garantiza que la clave generada sea única. No se garantiza que los valores clave sean consecutivos e incrementales.
* **dataPolicy (cadena)**: permite especificar restricciones de aprobación en los valores permitidos en el campo SQL. Los valores de este atributo son:

   * &quot;none&quot;: sin valor
   * &quot;smartCase&quot;: letras mayúsculas
   * &quot;lowerCase&quot;: todo en minúsculas
   * &quot;upperCase&quot;: todas mayúsculas
   * &quot;email&quot;: email address
   * &quot;phone&quot;: número de teléfono
   * &quot;identifier&quot;: nombre del identificador
   * &quot;resIdentifier&quot;: nombre de archivo

* **dbEnum (string)**: recibe el nombre interno de una enumeración &quot;cerrada&quot;. Los valores de enumeración deben definirse en `<srcschema>`.
* **defOnDuplicate (booleano)**: si este atributo está activado, cuando se duplica un registro, el valor predeterminado (definido en @default) se vuelve a aplicar automáticamente al registro.
* **default (string)**: permite definir el comportamiento del elemento (llamada a una función, valor predeterminado). Este atributo recibe una expresión XTK.
* **desc (string)**: permite insertar una descripción del elemento. Esta descripción se utiliza para comprender qué es el elemento y para qué se utiliza. Puede mostrarlo en el formulario.
* **displayAsField (booleano)**: si este atributo está activado, se mostrará un tipo de &quot;vínculo&quot; `<element>` como un campo en la vista de árbol de los esquemas (pestaña &quot;Estructura&quot;). De este modo, es posible mostrar un vínculo como un campo local y cambiar su comportamiento durante una consulta. Cuando el elemento se encuentra en la selección de una consulta, se utiliza el valor del destino del vínculo. Cuando el elemento se encuentra en el WHERE de una consulta, se utiliza la clave subyacente del vínculo.
* **edit (string)**: este atributo especifica el tipo de entrada que se utilizará en el formulario vinculado al esquema.
* **enum (string)**: recibe el nombre de la enumeración vinculada al campo. La enumeración puede insertarse en el mismo esquema o en un esquema remoto.
* **expr (cadena)**: este atributo define un campo calculado para el cual no hay ninguna definición almacenada en la tabla. Recibe una expresión Xpath o XTK (cadena).
* **externalJoin (booleano)**: unión externa en un elemento de tipo &quot;vínculo&quot;.
* **feature (string)**: define un campo de características: estos campos se utilizan para ampliar los datos de una tabla existente, pero con almacenamiento en una tabla anexa. Los valores aceptados son:

   * &quot;compartido&quot;: el contenido se almacena en una tabla compartida por tipo de datos
   * &quot;dedicado&quot;: el contenido se almacena en una tabla dedicada

  Las tablas de características SQL se crean automáticamente en función del tipo de característica:

   * dedicado: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * compartido: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

  Existen dos tipos de campos de características: campos simples en los que se autoriza un solo valor en la característica y campos de opción múltiple, en los que la característica está vinculada a un elemento de colección que puede contener varios valores.

  Cuando se define una característica en un esquema, este debe tener una clave principal basada en un único campo (las claves compuestas no están autorizadas).

* **featureDate (booleano)**: atributo vinculado al campo de características &quot;@feature&quot;. Si su valor es &quot;true&quot;, le permite averiguar cuándo se actualizó el valor por última vez.
* **filterPath (string)**: este atributo recibe un Xpath y le permite definir un filtro en un campo.
* **folderLink (string)**: este atributo recibe el nombre del vínculo que le permite recuperar los archivos que contienen entidades.
* **folderModel (string)**: define el tipo de carpeta que habilita el almacenamiento de entidades. Este atributo solo se define si &quot;@folderLink&quot; está presente.
* **folderProcess (cadena)**: define el vínculo donde se almacenan las instancias del modelo de entidad. Este atributo solo se define si &quot;@folderLink&quot; está presente.
* **fullLoad (booleano)**: este atributo fuerza la visualización de todos los registros de una tabla durante la selección de campos en un formulario.
* **img (cadena)**: recibe la ruta de acceso de una imagen vinculada a un elemento. El valor de este atributo es del tipo &quot;área de nombres:nombre de imagen&quot;. Por ejemplo: img=&quot;cus:myImage.jpg&quot;. Físicamente, la imagen debe importarse al servidor de aplicaciones.
* **integridad (cadena)**: integridad referencial de la ocurrencia de la tabla de origen hacia la tabla de destino.

  Los valores accesibles son:

   * &quot;definir&quot;: Adobe Campaign no elimina la entidad si se hace referencia a ella mediante el vínculo
   * &quot;normal&quot;: al eliminar la incidencia de origen, se inicializan las claves del vínculo en la incidencia de destino (modo predeterminado), este tipo de integridad inicializa todas las claves externas
   * &quot;propio&quot;: al eliminar la incidencia de origen, se déclencheur la eliminación de la incidencia de destino
   * &quot;owncopy&quot;: similar a &quot;own&quot; (en caso de eliminación) o duplica ocurrencias (en caso de duplicación)
   * &quot;neutral&quot;: no hace nada

* **label (cadena)**: etiqueta de elemento.
* **labelSingular (cadena)**: etiqueta (forma singular) del elemento utilizado en algunas partes de la interfaz.
* **length (string)**: max. número de caracteres autorizados para un valor del campo SQL de tipo &quot;cadena&quot;.
* **localizable (booleano)**: si está activado, este atributo indica a la herramienta de recopilación que recupere el valor del atributo &quot;@label&quot; para su traducción (uso interno).
* **name (MNTOKEN)**: nombre interno del elemento que coincide con el nombre de la tabla. El valor del atributo &quot;@name&quot; debe ser corto, preferiblemente en inglés, y cumplir con las restricciones de nomenclatura vinculadas a XML.

  Cuando se escribe el esquema en la base de datos, Adobe Campaign agrega automáticamente prefijos al nombre del campo.

   * &quot;i&quot;: prefijo para el tipo &quot;entero&quot;.
   * &quot;d&quot;: prefijo para el tipo &quot;double&quot;.
   * &quot;s&quot;: prefijo del tipo de cadena de caracteres.
   * &quot;ts&quot;: prefijo para el tipo &quot;fecha&quot;.

  Para definir el nombre de la tabla de forma autónoma, debe utilizar el atributo &quot;@sqltable&quot; en la definición del elemento de esquema principal.

* **noDbIndex (booleano)**: permite especificar que el elemento no se va a indizar.
* **ordered (booleano)**: si el atributo está activado (ordered=&quot;true&quot;), Adobe Campaign mantiene la secuencia de declaración del elemento en un elemento de colección XML.
* **pkSequence (string)**: recibe el nombre de la secuencia que se va a utilizar para calcular una clave de incremento automático. Este atributo solo se puede utilizar si se define una clave de incremento automático en el elemento raíz del esquema.
* **pkgStatus (string)**: durante las exportaciones de paquetes, los valores se tendrán en cuenta como una función del valor de este atributo:

   * &quot;always&quot;: el elemento siempre estará presente
   * &quot;never&quot;: el elemento nunca estará presente
   * &quot;default (or Nothing)&quot;: el elemento se exporta a menos que sea el elemento predeterminado o si no es un campo interno y no es compatible con otras instancias

* **ref (string)**: este atributo define una referencia a un elemento >element> compartido por varios esquemas (factorización de definición). La definición no se copia en el esquema actual.
* **obligatorio (booleano)**: si este atributo está activado (@required=&quot;true&quot;), el campo se resalta en la interfaz. La etiqueta del campo será de color rojo en los formularios.
* **revAdvanced (booleano)**: cuando se activa, este atributo especifica que el vínculo opuesto es un vínculo &quot;avanzado&quot;.
* **revCardinality (string)**: este atributo define la cardinalidad de un vínculo entre dos tablas. Se utiliza en un tipo de &quot;vínculo&quot; `<element>`.

  Los valores posibles son:

   * &quot;single&quot; : vínculo de tipo 1-1 simple
   * &quot;unbound&quot;: vínculo de colección de tipo 1-N

  De forma predeterminada, si el atributo no se especifica durante la creación del vínculo, la cardinalidad es 1-N.

* **revDesc (cadena)**: este atributo recibe una descripción vinculada al vínculo opuesto.
* **revExternalJoin (booleano)**: cuando se activa, este atributo permite forzar la unión externa en el vínculo opuesto.
* **revIntegrity (cadena)**: este atributo define la integridad en el esquema de destino. Se autorizan los mismos valores que el atributo @integrity. De forma predeterminada, Adobe Campaign proporciona el valor &quot;normal&quot; a este atributo.
* **revLabel (cadena)**: etiqueta del vínculo opuesto.
* **revLink (cadena)**: nombre del vínculo opuesto. Si el valor es &quot;_NONE_&quot;, no se creará ningún vínculo opuesto en el esquema de destino.
* **revTarget (cadena)**: destino del vínculo opuesto.
* **sql (booleano)**: si este atributo está activado (@sql=&quot;true&quot;), fuerza el almacenamiento del elemento SQL, incluso si el elemento tiene la propiedad xml=&quot;true&quot;.
* **sqlname (string)**: nombre del campo durante la creación de la tabla. Si no se especifica &quot;@sqlname&quot;, se utiliza el valor del atributo &quot;@name&quot; de forma predeterminada. Al escribir el esquema en la tabla, los prefijos se añaden automáticamente según el tipo de campo.
* **sqltable (string)**: para el elemento principal del esquema, este atributo sobrecarga el nombre de la tabla SQL generada de forma predeterminada. Si no se especifica &quot;@sqltable&quot;, el nombre predeterminado se estructurará de esta manera: namespace (primera letra mayúscula) seguido del valor de SrcSchema &quot;@name&quot;.
* **tableSpace (cadena)**: este atributo permite especificar un nuevo espacio de almacenamiento de datos para una tabla (válido en la raíz `<element>`).
* **tableSpaceIndex (cadena)**: este atributo permite especificar un nuevo espacio de tabla de almacenamiento de índice para una tabla (válido en la raíz `<element>`).
* **target (MNTOKEN)**: recibe el nombre del esquema de destino al crear un vínculo entre tablas. Este atributo solo está activo para elementos de tipo &quot;vínculo&quot;.
* **template (string)**: este atributo define una referencia a un elemento `<element>` compartido por varios esquemas. La definición se copia automáticamente en el esquema actual.
* **translatedDefault (string)**: si se encuentra un atributo &quot;@default&quot;, el &quot;@translatedDefault&quot; le permitirá redefinir una expresión para que coincida con la definida en @default, que recopilará la herramienta de traducción (uso interno).
* **translatedExpr (string)**: si se encuentra un atributo &quot;@expr&quot;, el atributo &quot;@translatedExpr&quot; permite redefinir una expresión que coincida con la definida en &quot;@expr&quot; y que recopilará la herramienta de traducción (uso interno).
* **type (MNTOKEN)**: define el tipo de datos almacenados en el elemento.

  Lista de tipos disponibles:

   * CUALQUIERA
   * cubo
   * mancha
   * booleano
   * byte
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * fecha
   * doble
   * enum
   * flotante
   * html
   * int64
   * vincular
   * largo
   * nota
   * MNTOKEN
   * porcentaje
   * clave principal
   * corto
   * cadena
   * tiempo
   * intervalo de tiempo
   * uuid

* **unbound (booleano)**: si el atributo está activado (unbound=&quot;true&quot;), el vínculo se declara como un elemento de colección para una cardinalidad 1-N.
* **userEnum (string)**: recibe el nombre interno de una enumeración &quot;open&quot;. El usuario puede definir los valores de enumeración en la interfaz.
* **xml (booleano)**: si esta opción está activada, todos los valores definidos en el elemento se almacenan en XML en un campo de tipo TEXT &quot;mData&quot;. Esto significa que no habrá filtrado ni ordenación en estos campos.
* **xmlChildren (booleano)**: fuerza el almacenamiento para cada elemento secundario ( `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`
