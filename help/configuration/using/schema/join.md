---
product: campaign
title: 'Elementos y atributos de esquema: elemento de unión'
description: elemento de unión
exl-id: a7ca0300-d250-429c-8ae1-2ae7dee82cf5
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 2%

---

# elemento de unión {#join--element}

![](../../../assets/v7-only.svg)

## Modelo de contenido {#content-model-7}

unir:==VACÍO

## Atributos {#attributes-7}

* @dstFilterExpr (cadena)
* @xpath-dst (cadena)
* @xpath-src (cadena)

## Padres {#parents-7}

`<element>`

## Tareas secundarias {#children-7}

Ninguno

## Descripción {#description-7}

Permite definir los campos que crean una unión entre tablas SQL.

## Uso y contexto de uso {#use-and-context-of-use-5}

A `<join>`  element solo se puede usar si el elemento principal  `<element>`  es de tipo &quot;vínculo&quot;. Esto significa que el elemento principal debe tener declarado el atributo &quot;@type=link&quot;.

No es necesario especificar el nombre y el área de nombres de la tabla remota en el `<join>`  Elemento. Deben especificarse en el elemento principal  `<element>`.

Por norma, los vínculos se definen al final del esquema.

Si la variable `<join>` no se ha especificado cuando se define el elemento de tipo de vínculo, el vínculo se coloca automáticamente en las claves principales de ambas tablas.

## Descripción de atributo {#attribute-description-7}

* **dstFilterExpr (cadena)**: este atributo permite restringir el número de valores aptos en la tabla remota.
* **xpath-dst (string)**: este atributo recibe un Xpath (atributo @name de la tabla remota).
* **xpath-src (string)**: este atributo recibe un Xpath (atributo @name en el esquema actual).

## Ejemplos {#examples-6}

Vínculo entre el campo &quot;correo electrónico&quot; de la tabla actual y el campo &quot;@compagny-id&quot; de la tabla remota:

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

Vínculo filtrado hacia la tabla &quot;cus:Country&quot; en función del contenido del campo &quot;@country&quot; que debe contener el valor &quot;EN&quot;:

```
<element name="StockEN" type="link" label="MyLink" target="cus:Stock">
   <join xpath-dst="@country" xpath-src="@code" dstFilterExpr="@country = 'EN'"/>
 </element>
```
