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
source-wordcount: '210'
ht-degree: 4%

---


# `<join>` Elemento {#join--element}

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

Permite definir los campos que crean una combinación entre tablas SQL.

## Uso y contexto de uso {#use-and-context-of-use-5}

Un elemento `<join>` sólo se puede usar si el elemento principal `<element>` es de tipo &#39;link&#39;. Esto significa que el elemento principal debe tener declarado el atributo &quot;@type=link&quot;.

No es necesario especificar el nombre y la Área de nombres de la tabla remota en el elemento `<join>`. Deben especificarse en el elemento principal `<element>`.

Por convención, los vínculos se definen al final del esquema.

Si no se especifica el elemento `<join>` cuando se define el elemento de tipo de vínculo, el vínculo se colocará automáticamente en las claves principales de ambas tablas.

## Descripción del atributo {#attribute-description-7}

* **dstFilterExpr (cadena)**: este atributo permite restringir el número de valores elegibles en la tabla remota.
* **xpath-dst (string)**: este atributo recibe un atributo Xpath (@name de la tabla remota).
* **xpath-src (string)**: este atributo recibe un atributo Xpath (@name en el esquema actual).

## Ejemplos {#examples-6}

Vínculo entre el campo &#39;correo electrónico&#39; de la tabla actual y el campo &quot;@compagny-id&quot; de la tabla remota:

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

Vínculo filtrado hacia la tabla &quot;cus:Country&quot; basado en el contenido del campo &quot;@country&quot; que debe contener el valor &#39;EN&#39;:

```
<element name="StockEN" type="link" label="MyLink" target="cus:Stock">
   <join xpath-dst="@country" xpath-src="@code" dstFilterExpr="@country = 'EN'"/>
 </element>
```
