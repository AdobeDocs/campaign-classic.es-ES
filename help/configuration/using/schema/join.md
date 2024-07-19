---
product: campaign
title: 'Elementos y atributos de esquema: elemento de unión'
description: elemento de unión
feature: Schema Extension
exl-id: a7ca0300-d250-429c-8ae1-2ae7dee82cf5
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
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

Un elemento `<join>` solo se puede usar si el elemento principal `<element>` es de tipo &quot;vínculo&quot;. Esto significa que el elemento principal debe tener declarado el atributo &quot;@type=link&quot;.

No es necesario especificar el nombre y el área de nombres de la tabla remota en el elemento `<join>`. Deben especificarse en el elemento principal `<element>`.

Por norma, los vínculos se definen al final del esquema.

Si el elemento `<join>` no se especifica cuando se define el elemento de tipo de vínculo, el vínculo se colocará automáticamente en las claves principales de ambas tablas.

## Descripción de atributo {#attribute-description-7}

* **dstFilterExpr (cadena)**: este atributo le permite restringir el número de valores elegibles en la tabla remota.
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
