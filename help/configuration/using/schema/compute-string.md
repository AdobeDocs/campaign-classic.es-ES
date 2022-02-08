---
product: campaign
title: Elementos y atributos
description: elemento compute-string
exl-id: 8a079bb8-3f53-4144-a065-5bd402649cc7
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 6%

---

# elemento compute-string {#compute-string--element}

![](../../../assets/v7-only.svg)

## Modelo de contenido {#content-model-1}

compute-string:==EMPTY

## Atributos {#attributes-1}

@expr

## Principales {#parents-1}

`<element>`

## Niños {#children-1}

Ninguno

## Descripción {#description-1}

La variable `<compute-string>` element permite generar una cadena basada en una expresión XTK para mostrar una etiqueta &quot;creada&quot; en la interfaz basada en varios valores.

## Uso y contexto de uso {#use-and-context-of-use-1}

Cuando no `<compute-string>` se define, `<compute-string>` se introduce de forma predeterminada con los valores de la clave principal en el esquema .

## Descripción del atributo {#attribute-description-1}

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
