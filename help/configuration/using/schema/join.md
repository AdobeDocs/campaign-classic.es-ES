---
product: campaign
title: Elementos y atributos
description: Elementos y atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: a7ca0300-d250-429c-8ae1-2ae7dee82cf5
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 4%

---

# elemento de unión {#join--element}

![](../../../assets/v7-only.svg)

## Modelo de contenido {#content-model-7}

join:==EMPTY

## Atributos {#attributes-7}

* @dstFilterExpr (cadena)
* @xpath-dst (cadena)
* @xpath-src (cadena)

## Principales {#parents-7}

`<element>`

## Niños {#children-7}

Ninguno

## Descripción {#description-7}

Permite definir los campos que crean un vínculo entre tablas SQL.

## Uso y contexto de uso {#use-and-context-of-use-5}

A `<join>`  solo se puede usar si el elemento principal  `<element>`  es de tipo &quot;vínculo&quot;. Esto significa que el elemento principal debe tener declarado el atributo &quot;@type=link&quot;.

No es necesario especificar el nombre y el área de nombres de la tabla remota en la variable `<join>`  elemento. Deben especificarse en el elemento principal  `<element>`.

Por convención, los vínculos se definen al final del esquema.

Si la variable `<join>` no se especifica cuando se define el elemento de tipo vínculo, el vínculo se coloca automáticamente en las claves principales de ambas tablas.

## Descripción del atributo {#attribute-description-7}

* **dstFilterExpr (cadena)**: este atributo permite restringir el número de valores aptos en la tabla remota.
* **xpath-dst (cadena)**: este atributo recibe un Xpath (@name attribute de la tabla remota).
* **xpath-src (cadena)**: este atributo recibe un atributo Xpath (@name attribute en el esquema actual).

## Ejemplos {#examples-6}

Enlace entre el campo &quot;correo electrónico&quot; de la tabla actual y el campo &quot;@compagny-id&quot; de la tabla remota:

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

Vínculo filtrado hacia la tabla &quot;cus:Country&quot; basado en el contenido del campo &quot;@country&quot; que debe contener el valor &quot;EN&quot;:

```
<element name="StockEN" type="link" label="MyLink" target="cus:Stock">
   <join xpath-dst="@country" xpath-src="@code" dstFilterExpr="@country = 'EN'"/>
 </element>
```
