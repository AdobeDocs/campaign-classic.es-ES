---
product: campaign
title: 'Elementos y atributos: elemento srcschema'
description: Elementos y atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bc4329b4-d272-4d32-bdaa-290cb9912af4
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 1%

---

# elemento srcschema {#srcschema--element}

![](../../../assets/v7-only.svg)

## Modelo de contenido {#content-model-14}

srcSchema:==(atributo | createdBy | datos | elemento | enumeración | ayuda | interfaz | métodos | modificado por)

## Atributos {#attributes-14}

created (fecha y hora), createdBy-id (long), desc (cadena), entitySchema (cadena), extendedSchema (cadena), img (cadena), implements (cadena), label (cadena), labelSingular (cadena), lastModified (fecha y hora), library (booleano), mappingType (cadena), modifiedBy-id (largo), name (cadena), namespace (cadena), useRecycleBin (booleano), view (booleano), xtkschema (cadena)

## Padres {#parents-14}

Ninguno

## Tareas secundarias {#children-14}

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

La presentación del esquema está disponible en [Acerca de la referencia de esquema](../../../configuration/using/about-schema-reference.md) y [Estructura del esquema](../../../configuration/using/schema-structure.md).

## Descripción de atributo {#attribute-description-14}

* **creado (fecha y hora)**: este atributo proporciona información sobre la fecha y la hora de creación del esquema. Tiene un formulario de &quot;Fecha y hora&quot;. Los valores mostrados se toman del servidor. La hora se muestra en formato UTC.
* **createdBy-id (long)**: es el identificador del operador que creó el esquema.
* **desc (cadena)**: descripción del esquema
* **entitySchema (cadena)**: esquema básico en el que se basan la sintaxis y la aprobación (de forma predeterminada para Adobe Campaign: xtk:srcSchema). Al guardar el esquema actual, Adobe Campaign aprueba su gramática con el esquema declarado en el atributo @xtkschema.
* **extendedSchema (cadena)**: recibe el nombre del esquema predeterminado en el que se basa la extensión de esquema actual. El formato es &quot;área de nombres:nombre&quot;.
* **img (cadena)**: icono vinculado al esquema (puede definirse en el asistente de creación de esquemas).
* **label (cadena)**: etiqueta de esquema.
* **labelSingular (cadena)**: etiqueta (singular) para su visualización en la interfaz.
* **lastModified (fecha y hora)**: este atributo proporciona información sobre la fecha y la hora de la última modificación. Tiene un formulario de &quot;Fecha y hora&quot;. Los valores mostrados se toman del servidor. La hora se muestra en formato UTC.
* **biblioteca (booleano)**: uso del esquema como biblioteca y no como entidad. Por lo tanto, otros esquemas pueden hacer referencia a este esquema gracias a los atributos &quot;@ref&quot; y &quot;@template&quot;.
* **mappingType (cadena)**:

   * &quot;sql&quot;: asignación de base de datos
   * &quot;textFile&quot;: asignación de archivos de texto
   * &quot;xmlFile&quot;: asignación de archivos de texto en formato XML
   * &quot;binaryFile&quot;: asignación de archivos binarios

* **modifiedBy-id (largo)**: coincide con el identificador del operador que cambió el esquema.
* **nombre (cadena)**: nombre de esquema único.
* **namespace (cadena)**: área de nombres del esquema (predeterminado: nms, xtk, nl). Al crear un nuevo esquema para un proyecto, le recomendamos que utilice un área de nombres dedicada.
* **useRecycleBin (booleano)**: activa la función de papelera en la aplicación. Los registros eliminados se colocarán en la papelera antes de la eliminación final. Esta función solo está disponible en el modo &quot;Envío&quot;.
* **vista (booleano)**: si está activado (@view=&quot;true&quot;), el esquema se utilizará como vista. El asistente de actualización de la estructura de la base de datos no tendrá en cuenta el esquema. Esta opción se utiliza principalmente para hacer referencia a tablas externas.
* **xtkschema (cadena)**: nombre del esquema que define la gramática del esquema (xtk:srcSchema de forma predeterminada).

## Ejemplos {#examples-11}

`<srcschema>` del esquema predeterminado &quot;nms:delivery&quot;

```
<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```
