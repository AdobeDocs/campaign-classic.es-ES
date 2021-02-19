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
source-wordcount: '338'
ht-degree: 2%

---


# elemento dbindex {#dbindex--element}

## Modelo de contenido {#content-model-3}

dbindex:==keyfield

## Atributos {#attributes-3}

* @_operation (string)
* @applyIf (cadena)
* @label (cadena)
* @name (MNTOKEN)
* @unique (booleano)

## Padres {#parents-3}

`<element>`

## Niños {#children-3}

`<keyfield>`

## Descripción {#description-3}

Este elemento permite definir un índice vinculado a una tabla.

## Uso y contexto de uso {#use-and-context-of-use-3}

Es posible definir varios índices. Un índice puede hacer referencia a uno o varios campos de la tabla. La declaración de índice suele seguir la definición del elemento de esquema principal.

El orden de los elementos `<keyfield>` definidos en `<dbindex>` es muy importante. El primer `<keyfield>` debe ser el criterio de indización en el que se basan principalmente las consultas.

El nombre del índice de la base de datos se calcula concatenando el nombre de la tabla y el nombre del índice. Por ejemplo: Nombre de tabla &quot;Sample&quot;, Área de nombres &quot;Cus&quot;, nombre de índice &quot;MyIndex&quot;-> nombre del campo de índice durante la consulta de creación de índice: &quot;CusSample_myIndex&quot;.

## Descripción del atributo {#attribute-description-3}

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

## Ejemplos {#examples-3}

Creación de un índice en el campo &quot;id&quot;. (el atributo &quot;@unique&quot; en los déclencheur del elemento `<dbindex>` que agregan la palabra clave SQL &quot;ÚNICA&quot; cuando se crea el índice en la base de datos (consulta)).

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
