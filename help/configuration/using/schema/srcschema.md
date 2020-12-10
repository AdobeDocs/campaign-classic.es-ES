---
solution: Campaign Classic
product: campaign
title: Elementos y atributos
description: Elementos y atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: c366326f6a439dabaa42fdd799ec2e55c180a929
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 2%

---


# `<srcschema>` Elemento {#srcschema--element}

## Modelo de contenido {#content-model-14}

srcSchema:==(attribute) | createdBy | datos | element | lista desglosada | ayuda | interfaz | métodos | modifiedBy)

## Atributos {#attributes-14}

created (datetime), createdBy-id (long), desc (string), entitySchema (string), expandedSchema (string), img (string), implements (string), label (string), labelSingular (string), lastModified (datetime), library (boolean), mappingType (string), modifiedBy-id (long), name (string), Área de nombres (cadena), useRecycleBin (booleano), vista (booleano), xtkschema (cadena)

## Padres {#parents-14}

Ninguno

## Niños {#children-14}

* `<attribute>`
* `<createdby>`
* `<data>`
* `<element>`
* `<enumeration>`
* `<help>`
* `<interface>`
* `<methods>`
* `<modifiedby>`

## Descripción {#description-14}

El `<srcschema>` es el elemento raíz de un esquema. Es el punto de entrada para la definición del esquema.

## Uso y contexto de uso {#use-and-context-of-use-9}

La presentación de esquema está disponible en [Acerca de la referencia de esquema](../../../configuration/using/about-schema-reference.md) y [estructura de Esquema](../../../configuration/using/schema-structure.md).

## Descripción del atributo {#attribute-description-14}

* **created (datetime)**: este atributo proporciona información sobre la fecha y hora de creación del esquema. Tiene el formulario &quot;Fecha y hora&quot;. Los valores mostrados se toman del servidor. La hora se muestra en formato UTC.
* **createdBy-id (long)**: es el identificador del operador que creó el esquema.
* **desc (cadena)**: Descripción del esquema
* **entitySchema (cadena)**: esquema básico en el que se basan la sintaxis y la aprobación (de forma predeterminada para Adobe Campaign: xtk:srcSchema). Cuando guarde el esquema actual, Adobe Campaign aprobará su gramática con el esquema declarado en el atributo @xtkschema.
* **expandedSchema (cadena)**: recibe el nombre del esquema predeterminado en el que se basa la extensión de esquema actual. El formulario es &quot;Área de nombres:nombre&quot;.
* **img (cadena)**: icono vinculado al esquema (puede definirse en el asistente para la creación de esquemas).
* **label (string)**: Etiqueta de esquema.
* **labelSingular (cadena)**: etiqueta (singular) para mostrar en la interfaz.
* **lastModified (datetime)**: este atributo proporciona información sobre la fecha y hora de la última modificación. Tiene el formulario &quot;Fecha y hora&quot;. Los valores mostrados se toman del servidor. La hora se muestra en formato UTC.
* **library (boolean)**: uso del esquema como biblioteca y no como entidad. Por lo tanto, otros esquemas pueden hacer referencia a este esquema gracias a los atributos &quot;@ref&quot; y &quot;@template&quot;.
* **mappingType (cadena)**:

   * &quot;sql&quot;: asignación de bases de datos
   * &quot;textFile&quot;: asignación de archivos de texto
   * &quot;xmlFile&quot;: Asignación de archivos de texto en formato XML
   * &quot;binaryFile&quot;: asignación de archivos binarios

* **modifiedBy-id (long)**: coincide con el identificador del operador que cambió el esquema.
* **name (string)**: nombre de esquema único.
* **área de nombres (cadena)**: área de nombres del esquema (predeterminado: nms, xtk, nl). Al crear un nuevo esquema para un proyecto, le recomendamos que utilice una Área de nombres dedicada.
* **useRecycleBin (boolean)**: activa la función de papelera en la aplicación. Los registros eliminados se colocarán en la papelera antes de la eliminación final. Esta función solo está disponible en modo &quot;Envío&quot;.
* **vista (booleana)**: si se activa (@vista=&quot;true&quot;), el esquema se utilizará como vista. El asistente para la actualización de la estructura de la base de datos no tendrá en cuenta el esquema. Esta opción se utiliza principalmente para hacer referencia a tablas externas.
* **xtkschema (string)**: nombre del esquema que define la gramática del esquema (xtk:srcSchema de forma predeterminada).

## Ejemplos {#examples-11}

`<srcschema>` del esquema &quot;nms:envío&quot; fuera de la casilla

```
<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```
