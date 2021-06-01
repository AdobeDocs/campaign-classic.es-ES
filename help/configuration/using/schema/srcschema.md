---
product: campaign
title: Elementos y atributos
description: Elementos y atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bc4329b4-d272-4d32-bdaa-290cb9912af4
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 1%

---

# elemento srcschema {#srcschema--element}

## Modelo de contenido {#content-model-14}

srcSchema:==(attribute) | createdBy | datos | elemento | enumeración | ayuda | interfaz | métodos | modifiedBy)

## Atributos {#attributes-14}

created (datetime), createdBy-id (long), desc (string), entitySchema (string), ExtendedSchema (string), img (string), implementaciones (string), label (string), labelSingular (string), lastModified (datetime), library (boolean), mappingType (string), modifiedBy-id (long), name (string), namespace string), useRecycleBin (booleano), view (booleano), xtkschema (cadena)

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

La presentación del esquema está disponible en [Acerca de la referencia de esquema](../../../configuration/using/about-schema-reference.md) y [Estructura del esquema](../../../configuration/using/schema-structure.md).

## Descripción de atributo {#attribute-description-14}

* **created (datetime)**: este atributo proporciona información sobre la fecha y hora de creación del esquema. Tiene el formulario &quot;Hora de la fecha&quot;. Los valores mostrados se toman del servidor. La hora se muestra en formato UTC.
* **createdBy-id (long)**: es el identificador del operador que creó el esquema.
* **desc (cadena)**: descripción del esquema
* **entitySchema (cadena)**: esquema básico en el que se basan la sintaxis y la aprobación (de forma predeterminada para Adobe Campaign: xtk:srcSchema). Cuando guarde el esquema actual, Adobe Campaign aprobará su gramática con el esquema declarado en el atributo @xtkschema .
* **ExtendedSchema (cadena)**: recibe el nombre del esquema predeterminado en el que se basa la extensión de esquema actual. El formulario es &quot;namespace:name&quot;.
* **img (cadena)**: icono vinculado al esquema (puede definirse en el asistente de creación de esquemas).
* **label (cadena)**: etiqueta de esquema.
* **labelSingular (cadena)**: etiqueta (singular) para mostrar en la interfaz de .
* **lastModified (datetime)**: este atributo proporciona información sobre la fecha y la hora de la última modificación. Tiene el formulario &quot;Hora de la fecha&quot;. Los valores mostrados se toman del servidor. La hora se muestra en formato UTC.
* **biblioteca (booleano)**: uso del esquema como biblioteca y no como entidad. Por lo tanto, otros esquemas pueden hacer referencia a este esquema gracias a los atributos &quot;@ref&quot; y &quot;@template&quot;.
* **mappingType (cadena)**:

   * &quot;sql&quot;: asignación de base de datos
   * &quot;textFile&quot;: asignación de archivos de texto
   * &quot;xmlFile&quot;: Asignación de archivos de texto en formato XML
   * &quot;binaryFile&quot;: asignación de archivos binarios

* **modifiedBy-id (long)**: coincide con el identificador del operador que ha cambiado el esquema.
* **nombre (cadena)**: nombre de esquema único.
* **namespace (cadena)**: área de nombres del esquema (predeterminado: nms, xtk, nl). Al crear un nuevo esquema para un proyecto, se recomienda utilizar un área de nombres dedicada.
* **useRecycleBin (booleano)**: activa la función papelera en la aplicación. Los registros eliminados se colocarán en la papelera antes de la eliminación final. Esta función solo está disponible en el modo &quot;Envío&quot;.
* **vista (booleano)**: si está activado (@view=&quot;true&quot;), el esquema se utilizará como vista. El asistente de actualización de la estructura de la base de datos no tendrá en cuenta el esquema. Esta opción se utiliza principalmente para hacer referencia a tablas externas.
* **xtkschema (cadena)**: nombre del esquema que define la gramática del esquema (xtk:srcSchema de forma predeterminada).

## Ejemplos {#examples-11}

`<srcschema>` elemento del esquema predeterminado &quot;nms:delivery&quot;

```
<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```
