---
product: campaign
title: 'Elementos y atributos de esquema: elemento clave'
description: elemento clave
feature: Schema Extension
exl-id: 3d0ef574-27a3-40f2-91a0-70e9583d9980
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 1%

---

# elemento clave {#key--element}

![](../../../assets/v7-only.svg)

## Modelo de contenido {#content-model-8}

clave:==campoClave

## Atributos {#attributes-8}

* @allowEmptyPart (booleano)
* @applicableIf (cadena)
* @internal (booleano)
* @label (cadena)
* @name (TOKEN MENÚ)
* @noDbIndex (booleano)

## Padres {#parents-8}

`<element>`

## Tareas secundarias {#children-8}

`<keyfield>`

## Descripción {#description-8}

Este elemento permite definir una clave para identificar un registro de la tabla.

Una tabla debe tener al menos una clave.

## Uso y contexto de uso {#use-and-context-of-use-6}

Como regla, las claves se declaran después del elemento principal del esquema y de los índices.

Una clave se conoce como compuesta si incluye varios campos (es decir, varios `<keyfield>` children). No utilice una clave compuesta para definir una clave principal.

Si el elemento principal del esquema contiene el atributo &quot;@autopk=true&quot;, la clave principal es única. Solo podemos tener una clave principal por esquema.

Los primeros 1000 identificadores están reservados, por lo que si es necesario definir un rango de valores para claves, comience en 1000.

## Descripción de atributo {#attribute-description-8}

* **allowEmptyPart (booleano)**: en el caso de una clave compuesta, si este atributo está activado, la clave se considera válida si al menos una de sus claves no está vacía. En este caso, el valor de noción vacío es &quot;0&quot; (booleano o para todos los tipos de datos numéricos). De forma predeterminada, es necesario introducir todas las claves que componen una clave compuesta.
* **applyIf (cadena)**: este atributo permite hacer que la clave sea opcional. Define la condición según la cual se aplicará la definición de clave. Este atributo recibe una expresión XTK.
* **interno (booleano)**: si está activada, este atributo permite a Adobe Campaign saber que la clave es principal.
* **label (cadena)**: etiqueta de la clave.
* **nombre (MNTOKEN)**: nombre interno de la clave.
* **noDbIndex (booleano)**: si está activado (noDbIndex=&quot;true&quot;), el campo que coincida con la clave no se indexará.

## Ejemplos {#examples-------}

Declaración de una clave compuesta que autoriza que el campo &quot;@expr&quot; o &quot;alias&quot; esté vacío:

```
<key name="node" allowEmptyPart="true">
  <keyfield xpath="@expr"/>
   <keyfield xpath="@alias"/>
 </key>
```

Declaración de una clave principal en el campo &quot;Nombre&quot; del tipo CADENA en un `<srcschema>`  y la consulta SQL coincidente:

```
 
<key name="PrimaryKey" internal="true">  
  <keyfield xpath="@name"/>
</key>

CREATE UNIQUE INDEX Schema_PrimaryKey ON Schema(sName);
```
