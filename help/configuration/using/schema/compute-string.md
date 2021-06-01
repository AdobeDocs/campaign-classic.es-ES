---
product: campaign
title: Elementos y atributos
description: Elementos y atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 8a079bb8-3f53-4144-a065-5bd402649cc7
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 10%

---

# elemento compute-string {#compute-string--element}

## Modelo de contenido {#content-model-1}

compute-string:==EMPTY

## Atributos {#attributes-1}

@expr

## Padres {#parents-1}

`<element>`

## Niños {#children-1}

Ninguno

## Descripción {#description-1}

El elemento `<compute-string>` permite generar una cadena basada en una expresión XTK para mostrar una etiqueta &quot;creada&quot; en la interfaz basada en varios valores.

## Uso y contexto de uso {#use-and-context-of-use-1}

Cuando no se define `<compute-string>` , se introduce un elemento `<compute-string>` de forma predeterminada con los valores de la clave principal en el esquema.

## Descripción de atributo {#attribute-description-1}

* **expr (cadena)**: XTK o expresión Xpath

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
