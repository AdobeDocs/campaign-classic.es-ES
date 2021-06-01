---
product: campaign
title: Elementos y atributos
description: Elementos y atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: e4d34f56-b065-4dce-8974-11dc2767873a
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1553'
ht-degree: 0%

---

# elemento de atributo {#attribute--element}

## Modelo de contenido {#content-model}

attribute:==help

## Atributos {#attributes}

_operation (cadena), avanzado (booleano), aplicableIf (cadena), autoIncrement (booleano), perteneceTo (cadena), dataPolicy (cadena), dbEnum (cadena), defOnDuplicate (booleano), predeterminado (cadena), desc (cadena), editar (cadena), enum (cadena), expr (cadena), característica (cadena), featureDate), img (cadena), inout (cadena), label (cadena), length (cadena), localizable (booleano), name (MNTOKEN), notNull (booleano), pkgStatus (cadena), ref (cadena), required (booleano), sql (booleano), sqlDefault (cadena), sqlname (cadena), sqltable (cadena) target (MNTOKEN), template (string), translateDefault (string), translateExpr (string), type (MNTOKEN), user (boolean), userEnum (string), visibleIf (string), xml (booleano)

## Principales {#parents}

`<element>`

## Niños {#children}

`<help>`

## Descripción {#description}

`<attribute>` los elementos permiten definir un campo en la base de datos.

## Uso y contexto de uso {#use-and-context-of-use}

`<attribute>` Los elementos deben declararse en un  `<element>` elemento.

La secuencia en la que se definen los elementos `<attribute>` en un `<srcschema>` no afecta a la secuencia de creación de campos en la base de datos. La secuencia de creación será alfabética.

## Descripción de atributo {#attribute-description}

* **_operation (cadena)**: define el tipo de escritura en la base de datos.

   Este atributo se utiliza principalmente al ampliar los esquemas predeterminados.

   Los valores accesibles son:

   * &quot;ninguno&quot;: solo reconciliación. Esto significa que Adobe Campaign recuperará el elemento sin actualizarlo o generando un error si no existe.
   * &quot;insertOrUpdate&quot;: actualizar con inserción. Esto significa que Adobe Campaign actualizará el elemento o lo creará si no existe.
   * &quot;insertar&quot;: inserción. Esto significa que Adobe Campaign insertará el elemento sin comprobar si existe.
   * &quot;actualización&quot;: actualización. Esto significa que Adobe Campaign actualizará el elemento o generará un error si no existe.
   * &quot;eliminar&quot;: eliminación. Esto significa que Adobe Campaign recuperará y eliminará los elementos.

* **avanzado (booleano)**: cuando esta opción está activada (@advanced=&quot;true&quot;), permite ocultar el atributo en la lista de campos disponibles accesibles para configurar una lista en un formulario.
* **applyIf (cadena)**: este atributo permite hacer que los campos sean opcionales. El elemento `<attribute>` se tendrá en cuenta al actualizar la base de datos cuando se cumpla la restricción. &quot;applyIf&quot; recibe una expresión XTK.
* **autoIncrement (booleano)**: si esta opción está activada, el campo se convierte en contador. Esto le permite incrementar un valor (principalmente ID). (uso externo)
* **perteneceTo (cadena)**: toma el nombre y el área de nombres de la tabla que comparte el campo y rellena el esquema donde se declara el atributo. (usado solo en un `<schema>`).
* **dataPolicy (cadena)**: permite especificar restricciones de aprobación en valores permitidos en el campo SQL o XML. Los valores de este atributo son:

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
* **predeterminado (cadena)**: permite definir el valor del campo predeterminado (llamada a una función, valor predeterminado). Este atributo recibe una expresión XTK.
* **desc (cadena)**: permite insertar una descripción del atributo. Esta descripción se muestra en la barra de estado de la interfaz.
* **editar (cadena)**: este atributo especifica el tipo de entrada que se utilizará en el formulario vinculado al esquema.
* **enum (cadena)**: recibe el nombre de la enumeración vinculada al campo. La enumeración puede insertarse en el mismo esquema o en un esquema remoto.
* **expr (cadena)**: define una expresión de precálculo de campo. Este atributo recibe una expresión Xpath o XTK.
* **característica (cadena)**: define un campo de características: Estos campos se utilizan para ampliar los datos en un cuadro existente, pero con almacenamiento en un cuadro anexo. Los valores aceptados son:

   * &quot;compartido&quot;: el contenido se almacena en una tabla compartida por tipo de datos
   * &quot;dedicada&quot;: el contenido se almacena en una tabla dedicada

   Las tablas de características SQL se crean automáticamente en función del tipo de característica:

   * dedicada: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * shared: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

   Existen dos tipos de campos de características: campos simples de oà¹ en los que se autoriza un valor único en la característica y campos de opción múltiple de oà¹, en los que la característica esté vinculada a un elemento de colección que pueda contener varios valores.

   Cuando una característica se define en un esquema, este esquema debe tener una clave principal basada en un solo campo (las claves compuestas no están autorizadas).

* **featureDate (booleano)**: vinculado al campo de características &quot;@feature&quot;. Si su valor es &quot;true&quot;, le permite averiguar cuándo se actualizó por última vez el valor.
* **img (cadena)**: permite definir una ruta para una imagen vinculada a un campo (espacio de nombres + nombre de imagen) (ejemplo: img=&quot;cus:mypicture.jpg&quot;). Físicamente, la imagen debe importarse al servidor de aplicaciones.
* **label (cadena)**: etiqueta vinculada al campo, principalmente destinada al usuario en la interfaz de . Permite evitar restricciones de nombres.
* **length (string)**: max. número de caracteres para un valor del campo SQL de tipo &quot;cadena&quot;. Si no se especifica el atributo &quot;@length&quot;, Adobe Campaign crea automáticamente un campo para 255 caracteres.
* **localizable (booleano)**: si está activado, este atributo indica a la herramienta de recopilación que recupere el valor del atributo &quot;@label&quot; para la traducción (uso interno).
* **nombre (MNTOKEN)**: nombre del atributo que coincidirá con el nombre del campo de la tabla. El valor del atributo &quot;@name&quot; debe ser corto, preferiblemente en inglés, y cumplir con las restricciones de nomenclatura XML.

   Cuando se escribe el esquema en la base de datos, Adobe Campaign agrega automáticamente los prefijos al nombre del campo:

   * &quot;i&quot;: para el tipo &quot;integer&quot;.
   * &quot;d&quot;: para el tipo &quot;doble&quot;.
   * &quot;s&quot;: para el tipo de cadena de caracteres.
   * &quot;ts&quot;: para el tipo &quot;fecha&quot;.

   Para definir completamente el nombre del campo en la tabla, utilice la opción &quot;@sqlname&quot; al definir un atributo.

* **notNull (booleano)**: permite redefinir el comportamiento de Adobe Campaign con respecto a la administración de registros NULL en la base de datos. De forma predeterminada, los campos numéricos no son nulos y los campos de cadena y fecha pueden ser nulos.
* **pkgStatus (cadena)**: durante las exportaciones de paquetes, se tienen en cuenta los valores según el valor de &quot;@pkgStatus&quot;:

   * &quot;always&quot;: siempre presente
   * &quot;never&quot;: nunca presente
   * &quot;predeterminado (o nada)&quot;: el valor se exporta excepto si es el valor predeterminado o si no es un campo interno que no sea compatible con otras instancias.

* **ref (cadena)**: este atributo define una referencia a un  `<attribute>` elemento compartido por varios esquemas (factorización de definición). La definición no se copia en el esquema actual.
* **obligatorio (booleano)**: si este atributo está activado (@required=&quot;true&quot;), el campo se resalta en la interfaz. La etiqueta del campo aparece en rojo en los formularios.
* **sql (booleano)**: si este atributo está activado (@sql=&quot;true&quot;), fuerza el almacenamiento del atributo SQL, incluso cuando el elemento que contiene el atributo tiene la propiedad xml=&quot;true&quot;.
* **sqlDefault (cadena)**: este atributo permite definir el valor predeterminado que se tiene en cuenta para actualizar la base de datos si el atributo @notNull está activado. Si este atributo se agrega después de la creación del atributo, el comportamiento del esquema no cambiará ni siquiera para los nuevos registros. Para cambiar el esquema y actualizar el valor de los registros nuevos, debe eliminar y volver a crear el atributo.
* **sqlname (cadena)**: del campo durante la creación de la tabla. Si no se especifica @sqlname, el valor del atributo &quot;@name&quot; se utiliza de forma predeterminada. Cuando se escribe el esquema en la base de datos, los prefijos se añaden automáticamente según el tipo de campo.
* **plantilla (cadena)**: este atributo define una referencia a un  `<attribute>` elemento compartido por varios esquemas. La definición se copia automáticamente en el esquema actual.
* **translateDefault (cadena)**: si se encuentra un atributo &quot;@default&quot;, &quot;@translateDefault&quot; le permitirá redefinir una expresión que coincida con la definida en @default, que la herramienta de traducción (uso interno) recopilará.
* **translateExpr (cadena)**: si hay un atributo &quot;@expr&quot; presente, el atributo &quot;@translateExpr&quot; le permite redefinir una expresión que coincida con la definida en @expr, que la herramienta de traducción (uso interno) recopilará.
* **tipo (MNTOKEN)**: tipo de campo.

   Los tipos de campo son genéricos. Según el tipo de base de datos instalada, Adobe Campaign cambia el tipo definido a un valor específico de la base de datos instalada durante la actualización de estructura.

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

   Si el atributo &quot;@type&quot; se deja vacío, Adobe Campaign vinculará una cadena de caracteres (STRING) con una longitud de 100 al campo de forma predeterminada.

   Si el campo es de tipo STRING y el nombre del campo no se especifica por la presencia del atributo &quot;@sqlname&quot;, el nombre del campo en la base de datos estará precedido automáticamente por &#39;s&#39;. Este modo operativo será similar a los campos de tipo ENTERO (i), DOBLE (d) y FECHAS (ts).

* **userEnum (cadena)**: recibe el nombre interno de una enumeración &quot;open&quot;. El usuario puede definir los valores de la enumeración en la interfaz .
* **visibleIf (cadena)**: define una condición en forma de expresión XTK para mostrar u ocultar el atributo.

   >[!IMPORTANT]
   >
   >El atributo está oculto, pero se puede acceder a sus datos.

* **xml (booleano)**: si esta opción está activada, los valores del campo no tienen un campo SQL vinculado. Adobe Campaign crea un campo de tipo Texto &quot;mData&quot; para el almacenamiento de registros. Esto significa que no hay filtrado ni ordenación en estos campos.

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

Ejemplo con &quot;@applyIf&quot;: el atributo &quot;contiene&quot; solo se creará si el número de países es bueno a 20.

```
<attribute length="100" name="Continent" type="string" applicableIf="@country > 20"/>
```

Ejemplo con &quot;@feature&quot; de tipo &quot;shared&quot;:

```
<attribute name="field1" label="Field 1" type="long" feature="shared"/>
<attribute name="field1" label="Field 1" type="long" feature="shared" sqlname="126" sqltable="Ft_Content_Long"/>
```

Ejemplo con &quot;@feature&quot; de tipo &quot;dedicado&quot;:

```
<attribute name="field1" label="Field 1" type="long" feature="dedicated"/>
<attribute name="field1" label="Field 1" type="long" feature="dedicated" sqlname="sField1" sqltable="Ft_recipient_field1"/>
```
