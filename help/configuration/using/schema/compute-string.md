---
product: campaign
title: 'Elementos y atributos: elemento de cadena de cálculo'
description: elemento de cadena de cálculo
feature: Schema Extension
exl-id: 8a079bb8-3f53-4144-a065-5bd402649cc7
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 5%

---

# elemento de cadena de cálculo {#compute-string--element}

![](../../../assets/v7-only.svg)

## Modelo de contenido {#content-model-1}

compute-string:==EMPTY

## Atributos {#attributes-1}

@expr

## Padres {#parents-1}

`<element>`

## Tareas secundarias {#children-1}

Ninguno

## Descripción {#description-1}

El `<compute-string>` Este elemento permite generar una cadena basada en una expresión XTK para mostrar una etiqueta &quot;creada&quot; en la interfaz basada en varios valores.

## Uso y contexto de uso {#use-and-context-of-use-1}

Cuando no `<compute-string>` se define, a `<compute-string>` element se introduce de forma predeterminada con los valores de la clave principal en el esquema.

## Descripción de atributo {#attribute-description-1}

* **expr (cadena)**: expresión XTK o Xpath

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
