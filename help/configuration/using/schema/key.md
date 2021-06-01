---
product: campaign
title: Elementos y atributos
description: Elementos y atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 3d0ef574-27a3-40f2-91a0-70e9583d9980
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 2%

---

# elemento clave {#key--element}

## Modelo de contenido {#content-model-8}

key:==keyfield

## Atributos {#attributes-8}

* @allowEmptyPart (booleano)
* @applyIf (cadena)
* @internal (booleano)
* @label (cadena)
* @name (MNTOKEN)
* @noDbIndex (booleano)

## Padres {#parents-8}

`<element>`

## Niños {#children-8}

`<keyfield>`

## Descripción {#description-8}

Este elemento permite definir una clave para identificar un registro de la tabla.

Una tabla debe tener al menos una clave.

## Uso y contexto de uso {#use-and-context-of-use-6}

Como regla, las claves se declaran después del elemento principal del esquema y los índices.

Una clave se conoce como compuesta si incluye varios campos (es decir, varios `<keyfield>` secundarios). No utilice una clave compuesta para definir una clave principal.

Si el elemento principal del esquema contiene el atributo &quot;@autopk=true&quot;, la clave principal es única. Solo se puede tener una clave principal por esquema.

Los primeros 1000 identificadores están reservados, por lo que si es necesario definir un intervalo de valores para las claves, comience por 1000.

## Descripción de atributo {#attribute-description-8}

* **allowEmptyPart (booleano)**: en el caso de una clave compuesta, si este atributo está activado, la clave se considera válida si al menos una de sus claves no está vacía. Si este es el caso, el valor de noción vacío es &quot;0&quot; (booleano o para todos los tipos de datos numéricos). De forma predeterminada, es necesario introducir todas las claves que componen una clave compuesta.
* **applyIf (cadena)**: este atributo permite hacer que la clave sea opcional. Define la condición según la cual se aplicará la definición de clave. Este atributo recibe una expresión XTK.
* **interno (booleano)**: si está activado, este atributo informa a Adobe Campaign de que la clave es principal.
* **label (cadena)**: etiqueta de la clave.
* **nombre (MNTOKEN)**: nombre interno de la clave.
* **noDbIndex (booleano)**: si está activado (noDbIndex=&quot;true&quot;), el campo que coincide con la clave no se indexará.

## Ejemplos {#examples-------}

Declaración de una clave compuesta que autoriza el campo &quot;@expr&quot; o &quot;alias&quot; a estar vacío:

```
<key name="node" allowEmptyPart="true">
  <keyfield xpath="@expr"/>
   <keyfield xpath="@alias"/>
 </key>
```

Declaración de una clave principal en el campo &quot;Nombre&quot; del tipo STRING en un `<srcschema>` y la consulta SQL coincidente:

```
 
<key name="PrimaryKey" internal="true">  
  <keyfield xpath="@name"/>
</key>

CREATE UNIQUE INDEX Schema_PrimaryKey ON Schema(sName);
```
