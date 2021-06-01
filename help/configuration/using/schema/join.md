---
product: campaign
title: Elementos y atributos
description: Elementos y atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: a7ca0300-d250-429c-8ae1-2ae7dee82cf5
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 4%

---

# unir elemento {#join--element}

## Modelo de contenido {#content-model-7}

join:==EMPTY

## Atributos {#attributes-7}

* @dstFilterExpr (cadena)
* @xpath-dst (cadena)
* @xpath-src (cadena)

## Padres {#parents-7}

`<element>`

## Niños {#children-7}

Ninguno

## Descripción {#description-7}

Permite definir los campos que crean un vínculo entre tablas SQL.

## Uso y contexto de uso {#use-and-context-of-use-5}

Un elemento `<join>` solo se puede usar si el elemento principal `<element>` es de tipo &quot;vínculo&quot;. Esto significa que el elemento principal debe tener declarado el atributo &quot;@type=link&quot;.

No es necesario especificar el nombre y el área de nombres de la tabla remota en el elemento `<join>` . Deben especificarse en el `<element>` principal.

Por convención, los vínculos se definen al final del esquema.

Si el elemento `<join>` no se especifica cuando se define el elemento de tipo vínculo, el vínculo se coloca automáticamente en las claves principales de ambas tablas.

## Descripción de atributo {#attribute-description-7}

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
