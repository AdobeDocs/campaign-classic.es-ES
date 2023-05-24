---
product: campaign
title: 'Elementos y atributos: elemento de atributo'
description: Elementos y atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: e4d34f56-b065-4dce-8974-11dc2767873a
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '1555'
ht-degree: 1%

---

# elemento de atributo {#attribute--element}

![](../../../assets/v7-only.svg)

## Modelo de contenido {#content-model}

atributo:==ayuda

## Atributos {#attributes}

_operation (cadena), advanced (booleano), applyIf (cadena), autoIncrement (booleano), belongingTo (cadena), dataPolicy (cadena), dbEnum (cadena), defOnDuplicate (booleano), default (cadena), desc (cadena), edit (cadena), enum (cadena), expr (cadena), feature (cadena), featureDate (booleano), img (cadena), inout (cadena), label (cadena), length (cadena), localizable (booleano), name (MNTOKEN) ), notNull (booleano), pkgStatus (cadena), ref (cadena), obligatorio (booleano), sql (booleano), sqlDefault (cadena), sqlname (cadena), sqltable (cadena), target (MNTOKEN), plantilla (cadena), translatedDefault (cadena), translatedExpr (cadena), type (MNTOKEN), user (booleano), userEnum (cadena), visibleIf (cadena), xml (booleano)

## Padres {#parents}

`<element>`

## Tareas secundarias {#children}

`<help>`

## Descripción {#description}

`<attribute>` Los elementos de permiten definir un campo en la base de datos.

## Uso y contexto de uso {#use-and-context-of-use}

`<attribute>` los elementos deben declararse en un `<element>` Elemento.

La secuencia en la que `<attribute>` Los elementos de se definen en una `<srcschema>` no afecta a la secuencia de creación de campos en la base de datos. La secuencia de creación será alfabética.

## Descripción de atributo {#attribute-description}

* **_operation (cadena)**: define el tipo de escritura en la base de datos.

   Este atributo se utiliza principalmente para ampliar esquemas predeterminados.

   Los valores accesibles son:

   * &quot;ninguno&quot;: reconciliación sola. Esto significa que Adobe Campaign recuperará el elemento sin actualizarlo ni generar un error si no existe.
   * &quot;insertOrUpdate&quot;: actualizar con inserción. Esto significa que Adobe Campaign actualizará el elemento o lo creará si no existe.
   * &quot;insert&quot;: inserción. Esto significa que Adobe Campaign insertará el elemento sin comprobar si existe.
   * &quot;update&quot;: update. Esto significa que Adobe Campaign actualizará el elemento o generará un error si no existe.
   * &quot;eliminar&quot;: eliminación. Esto significa que Adobe Campaign recuperará y eliminará elementos.

* **avanzado (booleano)**: cuando esta opción está activada (@advanced=&quot;true&quot;), permite ocultar el atributo en la lista de campos disponibles a los que se puede acceder para configurar una lista en un formulario.
* **applyIf (cadena)**: este atributo permite hacer que los campos sean opcionales. El `<attribute>` se tendrá en cuenta al actualizar la base de datos cuando se cumpla la restricción. &quot;applyIf&quot; recibe una expresión XTK.
* **autoIncrement (booleano)**: si esta opción está activada, el campo se convierte en un contador. Esto le permite incrementar un valor (principalmente ID). (uso externo)
* **belongingTo (cadena)**: toma el nombre y el área de nombres de la tabla que comparte el campo y rellena el esquema donde se declara el atributo. (se utiliza solo en un `<schema>`).
* **dataPolicy (cadena)**: permite especificar restricciones de aprobación en los valores permitidos en el campo SQL o XML. Los valores de este atributo son:

   * &quot;none&quot;: sin valor
   * &quot;smartCase&quot;: letras mayúsculas
   * &quot;lowerCase&quot;: todo en minúsculas
   * &quot;upperCase&quot;: todas mayúsculas
   * &quot;email&quot;: email address
   * &quot;phone&quot;: número de teléfono
   * &quot;identifier&quot;: nombre del identificador
   * &quot;resIdentifier&quot;: nombre de archivo

* **dbEnum (cadena)**: recibe el nombre interno de una enumeración &quot;cerrada&quot;. Los valores de enumeración deben definirse en la variable `<srcschema>`.
* **defOnDuplicate (booleano)**: si este atributo está activado, cuando se duplica un registro, el valor predeterminado (definido en @default) se vuelve a aplicar automáticamente al registro.
* **default (cadena)**: permite definir el valor del campo predeterminado (llamada a una función, valor predeterminado). Este atributo recibe una expresión XTK.
* **desc (cadena)**: permite insertar una descripción del atributo. Esta descripción se muestra en la barra de estado de la interfaz.
* **edit (cadena)**: este atributo especifica el tipo de entrada que se utilizará en el formulario vinculado al esquema.
* **enum (cadena)**: recibe el nombre de la enumeración vinculada al campo. La enumeración puede insertarse en el mismo esquema o en un esquema remoto.
* **expr (cadena)**: define una expresión de precálculo de campo. Este atributo recibe una expresión Xpath o XTK.
* **característica (cadena)**: define un campo de características: estos campos se utilizan para ampliar los datos de una tabla existente, pero con almacenamiento en una tabla adjunta. Los valores aceptados son:

   * &quot;compartido&quot;: el contenido se almacena en una tabla compartida por tipo de datos
   * &quot;dedicado&quot;: el contenido se almacena en una tabla dedicada

   Las tablas de características SQL se crean automáticamente en función del tipo de característica:

   * dedicado: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * shared: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

   Existen dos tipos de campos de características: campos oà¹ simples en los que se autoriza un solo valor en la característica y campos oà¹ de opción múltiple, en los que la característica está vinculada a un elemento de colección que puede contener varios valores.

   Cuando se define una característica en un esquema, este debe tener una clave principal basada en un único campo (las claves compuestas no están autorizadas).

* **featureDate (booleano)**: atributo vinculado al campo de características @feature. Si su valor es &quot;true&quot;, le permite averiguar cuándo se actualizó el valor por última vez.
* **img (cadena)**: permite definir una ruta para una imagen vinculada a un campo (área de nombres + nombre de imagen) (ejemplo: img=&quot;cus:mypicture.jpg&quot;). Físicamente, la imagen debe importarse al servidor de aplicaciones.
* **label (cadena)**: etiqueta vinculada al campo, destinada principalmente al usuario en la interfaz. Permite evitar restricciones de nomenclatura.
* **length (cadena)**: máx. número de caracteres para un valor del campo SQL de tipo &quot;cadena&quot;. Si no se especifica el atributo &quot;@length&quot;, Adobe Campaign crea automáticamente un campo de 255 caracteres.
* **localizable (booleano)**: si está activado, este atributo indica a la herramienta de recopilación que recupere el valor del atributo &quot;@label&quot; para su traducción (uso interno).
* **nombre (MNTOKEN)**: nombre del atributo que coincidirá con el nombre del campo de la tabla. El valor del atributo &quot;@name&quot; debe ser corto, preferiblemente en inglés, y cumplir con las restricciones de nomenclatura XML.

   Cuando se escribe el esquema en la base de datos, Adobe Campaign agrega automáticamente prefijos al nombre del campo:

   * &quot;i&quot;: prefijo para el tipo &quot;entero&quot;.
   * &quot;d&quot;: prefijo para el tipo &quot;double&quot;.
   * &quot;s&quot;: prefijo del tipo de cadena de caracteres.
   * &quot;ts&quot;: prefijo para el tipo &quot;fecha&quot;.

   Para definir completamente el nombre del campo en la tabla, utilice la opción @sqlname al definir un atributo.

* **notNull (booleano)**: permite redefinir el comportamiento de Adobe Campaign con respecto a la administración de registros NULL en la base de datos. De forma predeterminada, los campos numéricos no son nulos y los campos de cadena y tipo de fecha pueden ser nulos.
* **pkgStatus (cadena)**: durante las exportaciones de paquetes, los valores se tienen en cuenta según el valor de la &quot;@pkgStatus&quot;:

   * &quot;always&quot;: always present
   * &quot;never&quot;: never present
   * &quot;default (or Nothing)&quot;: el valor se exporta excepto si es el valor predeterminado o si no es un campo interno que no sería compatible con otras instancias.

* **ref (cadena)**: este atributo define una referencia a un `<attribute>` elemento compartido por varios esquemas (factorización de definición). La definición no se copia en el esquema actual.
* **obligatorio (booleano)**: si este atributo está activado (@required=&quot;true&quot;), el campo se resalta en la interfaz. La etiqueta del campo será de color rojo en los formularios.
* **sql (booleano)**: si este atributo está activado (@sql=&quot;true&quot;), fuerza el almacenamiento del atributo SQL, incluso cuando el elemento que contiene el atributo tiene la propiedad xml=&quot;true&quot;.
* **sqlDefault (cadena)**: este atributo permite definir el valor predeterminado que se tiene en cuenta para actualizar la base de datos si el atributo @notNull está activado. Si este atributo se agrega después de la creación del atributo, el comportamiento del esquema no cambiará incluso para los registros nuevos. Para cambiar el esquema y actualizar el valor de los registros nuevos, debe eliminar y crear de nuevo el atributo.
* **sqlname (cadena)**: del campo durante la creación de la tabla. Si no se especifica @sqlname, se utiliza el valor del atributo &quot;@name&quot; de forma predeterminada. Cuando se escribe el esquema en la base de datos, los prefijos se agregan automáticamente según el tipo de campo.
* **template (cadena)**: este atributo define una referencia a un `<attribute>` compartido por varios esquemas. La definición se copia automáticamente en el esquema actual.
* **translatedDefault (cadena)**: si se encuentra un atributo &quot;@default&quot;, la &quot;@translatedDefault&quot; permite redefinir una expresión para que coincida con la definida en @default, que debe recopilar la herramienta de traducción (uso interno).
* **translatedExpr (cadena)**: si hay un atributo &quot;@expr&quot; presente, el atributo &quot;@translatedExpr&quot; permite redefinir una expresión para que coincida con la definida en @expr, que recopila la herramienta de traducción (uso interno).
* **Tipo (MNTOKEN)**: tipo de campo.

   Los tipos de campo son genéricos. Según el tipo de base de datos instalada, Adobe Campaign cambia el tipo definido en un valor específico de la base de datos instalada durante la actualización de la estructura.

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
   * date
   * doble
   * enum
   * float
   * html
   * int64
   * vincular
   * largo
   * nota
   * MNTOKEN
   * percent
   * clave principal
   * corto
   * cadena
   * tiempo
   * intervalo de tiempo
   * uuid

   Si se deja vacío el atributo &quot;@type&quot;, Adobe Campaign vinculará al campo de forma predeterminada una cadena de caracteres (STRING) con una longitud de 100.

   Si el campo es de tipo CADENA y el nombre del campo no se especifica mediante la presencia del atributo &quot;@sqlname&quot;, el nombre del campo en la base de datos estará precedido automáticamente por una &quot;s&quot;. Este modo operativo es similar a los campos de tipo INTEGER (i), DOUBLE (d) y DATES (ts).

* **userEnum (cadena)**: recibe el nombre interno de una enumeración &quot;open&quot;. El usuario puede definir los valores de la enumeración en la interfaz.
* **visibleIf (cadena)**: define una condición en forma de expresión XTK para mostrar u ocultar el atributo.

   >[!IMPORTANT]
   >
   >El atributo está oculto, pero se puede acceder a sus datos.

* **xml (booleano)**: si esta opción está activada, los valores del campo no tienen un campo SQL vinculado. Adobe Campaign crea un campo de tipo de texto &quot;mData&quot; para el almacenamiento de registros. Esto significa que no hay filtrado ni ordenación en estos campos.

### Ejemplos {#examples}

Ejemplo de valores de enumeración cuyos valores se almacenan en la base de datos:

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

Ejemplo con un &quot;@applicableIf&quot;: el atributo &quot;contiene&quot; solo se crea si el número de países es bueno que 20.

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
