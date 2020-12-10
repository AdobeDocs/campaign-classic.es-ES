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
source-wordcount: '88'
ht-degree: 11%

---


# `<compute-string>` Elemento {#compute-string--element}

## Modelo de contenido {#content-model-1}

compute-string:==EMPTY

## Atributos {#attributes-1}

@expr

## Padres {#parents-1}

`<element>`

## Niños {#children-1}

Ninguno

## Descripción {#description-1}

El elemento `<compute-string>` permite generar una cadena basada en una expresión XTK para mostrar una etiqueta &quot;integrada&quot; en la interfaz basada en varios valores.

## Uso y contexto de uso {#use-and-context-of-use-1}

Cuando no se define `<compute-string>`, se introduce un elemento `<compute-string>` de forma predeterminada con los valores de la clave principal en el esquema.

## Descripción del atributo {#attribute-description-1}

* **expr (cadena)**: Expresión XTK y/o Xpath

## Ejemplos {#examples-1}

```
<compute-string expr="@label + Iif(@code='','', ' (' + [folder/@label] + ')')"/>  
<compute-string expr="ToString([@centralCatalog-id]) + ',' + ToString([@localOrgUnit-id])" />
```

Resultado de la cadena calculada en un destinatario: &quot;John Doe (john.doe@aol.com)&quot;:

```
<element name="recipient">
<compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')'
"/>
...
</element>
```
