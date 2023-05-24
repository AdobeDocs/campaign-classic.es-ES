---
product: campaign
title: 'Elementos y atributos: elemento dbindex'
description: elemento dbindex
exl-id: d7d1e427-12e0-4f07-9e01-d184dbe2ebf1
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 1%

---

# elemento dbindex {#dbindex--element}

![](../../../assets/v7-only.svg)

## Modelo de contenido {#content-model-3}

dbindex:==keyfield

## Atributos {#attributes-3}

* @_operation (cadena)
* @applicableIf (cadena)
* @label (cadena)
* @name (TOKEN MENÚ)
* @unique (booleano)

## Padres {#parents-3}

`<element>`

## Tareas secundarias {#children-3}

`<keyfield>`

## Descripción {#description-3}

Este elemento permite definir un índice vinculado a una tabla.

## Uso y contexto de uso {#use-and-context-of-use-3}

Es posible definir varios índices. Un índice puede hacer referencia a uno o varios campos de la tabla. La declaración de índice suele seguir la definición del elemento de esquema principal.

El orden de los `<keyfield>` elementos definidos en una `<dbindex>` es muy importante. El primero `<keyfield>` debe ser el criterio de indexación en el que se basan principalmente las consultas.

El nombre del índice en la base de datos se calcula concatenando el nombre de la tabla y el nombre del índice. Por ejemplo: Nombre de tabla &quot;Sample&quot;, Espacio de nombres &quot;Cus&quot;, nombre de índice &quot;MyIndex&quot;-> nombre del campo de índice durante la creación del índice que realiza la consulta: &quot;CusSample_myIndex&quot;.

## Descripción de atributo {#attribute-description-3}

* **_operation (cadena)**: define el tipo de escritura en la base de datos.

   Este atributo se utiliza principalmente para ampliar esquemas predeterminados.

   Los valores accesibles son:

   * &quot;ninguno&quot;: reconciliación sola. Esto significa que Adobe Campaign recuperará el elemento sin actualizarlo ni generar un error si no existe.
   * &quot;insertOrUpdate&quot;: actualizar con inserción. Esto significa que Adobe Campaign actualizará el elemento o lo creará si no existe.
   * &quot;insert&quot;: inserción. Esto significa que Adobe Campaign insertará el elemento sin comprobar si existe.
   * &quot;update&quot;: update. Esto significa que Adobe Campaign actualizará el elemento o generará un error si no existe.
   * &quot;eliminar&quot;: eliminación. Esto significa que Adobe Campaign recuperará y eliminará elementos.

* **applyIf (cadena)**: condición para tener en cuenta el índice que recibe una expresión XTK.
* **label (cadena)**: etiqueta de índice.
* **nombre (MNTOKEN)**: nombre de índice único.
* **único (booleano)**: si esta opción está activada (@unique=&quot;true&quot;), el atributo garantiza la exclusividad del índice en todos sus campos.

## Ejemplos {#examples-3}

Creación de un índice en el campo ID. (el atributo &quot;@unique&quot; de la variable `<dbindex>` déclencheur de elementos agregar la palabra clave SQL &quot;UNIQUE&quot; cuando se crea el índice en la base de datos (consulta).

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

Creación de un índice compuesto en los campos @mail y @phoneNumber:

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
