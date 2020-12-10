---
solution: Campaign Classic
product: campaign
title: Elementos y atributos
description: Elementos y atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 1818bd2aeb60689b2ce0e59cb0bd157f000de513
workflow-type: tm+mt
source-wordcount: '1552'
ht-degree: 0%

---


# `<attribute>` Elemento {#attribute--element}

## Modelo de contenido {#content-model}

attribute:==help

## Atributos {#attributes}

_operation (string), avanzado (booleano), correspondienteIf (string), autoIncrement (boolean), perteneceTo (string), dataPolicy (string), dbEnum (string), defOnDuplicate (boolean), predeterminado (string), desc (string), edit (string), enum (string), expr (string), feature (string), featureDate Boolean), img (cadena), inout (cadena), label (cadena), length (cadena), localizable (booleano), name (MNTOKEN), notNull (boolean), pkgStatus (cadena), ref (cadena), required (boolean), sql (boolean), sqlDefault (cadena), sqlname (cadena), sqltable (cadena) destinatario (MNTOKEN), plantilla (cadena), translateDefault (cadena), translateExpr (cadena), tipo (MNTOKEN), usuario (booleano), userEnum (cadena), visibleIf (cadena), xml (booleano)

## Padres {#parents}

`<element>`

## Niños {#children}

`<help>`

## Descripción {#description}

`<attribute>` permite definir un campo en la base de datos.

## Uso y contexto de uso {#use-and-context-of-use}

`<attribute>` los elementos deben declararse en un  `<element>` elemento.

La secuencia en la que los elementos `<attribute>` se definen en un `<srcschema>` no afecta a la secuencia de creación de campos en la base de datos. La secuencia de creación será alfabética.

## Descripción del atributo {#attribute-description}

* **_operation (string)**: define el tipo de escritura en la base de datos.

   Este atributo se utiliza principalmente al ampliar los esquemas predeterminados.

   Los valores accesibles son:

   * &quot;ninguno&quot;: sólo reconciliación. Esto significa que Adobe Campaign recuperará el elemento sin actualizarlo ni generar un error si no existe.
   * &quot;insertOrUpdate&quot;: actualizar con inserción. Esto significa que Adobe Campaign actualizará el elemento o lo creará si no existe.
   * &quot;insertar&quot;: inserción. Esto significa que Adobe Campaign insertará el elemento sin comprobar si existe.
   * &quot;update&quot;: actualizar. Esto significa que Adobe Campaign actualizará el elemento o generará un error si no existe.
   * &quot;delete&quot;: eliminación. Esto significa que Adobe Campaign recuperará y eliminará los elementos.

* **avanzado (booleano)**: cuando esta opción está activada (@advanced=&quot;true&quot;), permite ocultar el atributo en la lista de los campos disponibles a los que se puede acceder para configurar una lista en un formulario.
* **applyIf (string)**: este atributo permite hacer que los campos sean opcionales. El elemento `<attribute>` se tendrá en cuenta al actualizar la base de datos cuando se cumpla la restricción. &quot;applyIf&quot; recibe una expresión XTK.
* **autoIncrement (booleano)**: si esta opción está activada, el campo se convierte en un contador. Esto le permite incrementar un valor (principalmente ID). (uso externo)
* **existsTo (string)**: toma el nombre y la Área de nombres de la tabla que comparte el campo y rellena el esquema donde se declara el atributo. (se usa solamente en `<schema>`).
* **dataPolicy (string)**: permite especificar restricciones de aprobación en los valores permitidos en el campo SQL o XML. Los valores de este atributo son:

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
* **name (MNTOKEN)**: nombre del atributo que coincidirá con el nombre del campo en la tabla. El valor del atributo &quot;@name&quot; debe ser corto, preferiblemente en inglés, y cumplir con las restricciones de nomenclatura XML.

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

* **ref (cadena)**: este atributo define una referencia a un  `<attribute>` elemento compartido por varios esquemas (factorización de definición). La definición no se copia en el esquema actual.
* **requerido (booleano)**: si este atributo está activado (@required=&quot;true&quot;), el campo se resalta en la interfaz. La etiqueta del campo aparecerá en rojo en los formularios.
* **sql (booleano)**: si este atributo está activado (@sql=&quot;true&quot;), fuerza el almacenamiento del atributo SQL, incluso cuando el elemento que contiene el atributo tiene la propiedad xml=&quot;true&quot;.
* **sqlDefault (string)**: este atributo permite definir el valor predeterminado que se tiene en cuenta para actualizar la base de datos si se activa el atributo @notNull. Si este atributo se agrega después de la creación del atributo, el comportamiento de esquema no cambiará ni siquiera para los nuevos registros. Para cambiar el esquema y actualizar el valor de los nuevos registros, debe eliminar y volver a crear el atributo.
* **sqlname (string)**: del campo durante la creación de la tabla. Si no se especifica @sqlname, el valor del atributo &quot;@name&quot; se utiliza de forma predeterminada. Cuando el esquema se escribe en la base de datos, los prefijos se agregan automáticamente en función del tipo de campo.
* **template (string)**: este atributo define una referencia a un  `<attribute>` elemento compartido por varios esquemas. La definición se copia automáticamente en el esquema actual.
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
