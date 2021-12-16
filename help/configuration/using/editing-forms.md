---
product: campaign
title: Edición de formularios
description: Edición de formularios
audience: configuration
content-type: reference
topic-tags: input-forms
exl-id: 24604dc9-f675-4e37-a848-f1911be84f3e
source-git-commit: f4b9ac3300094a527b5ec1b932d204f0e8e5ee86
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 4%

---


# Edición de formularios{#editing-forms}

![](../../assets/common.svg)

## Información general

Los especialistas en marketing y los operadores utilizan formularios de entrada para crear, modificar y previsualizar registros. Forms muestra una representación visual de la información.

Puede crear y modificar formularios de entrada:

* Puede modificar los formularios de entrada de fábrica que se envían de forma predeterminada. Los formularios de entrada de fábrica se basan en los esquemas de datos de fábrica.
* Puede crear formularios de entrada personalizados, basados en esquemas de datos definidos.

Forms son entidades de `xtk:form` tipo . Puede ver la estructura del formulario de entrada en el `xtk:form` esquema. Para ver este esquema, elija **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]** del menú . Más información sobre [estructura de formulario](form-structure.md).

Para acceder a los formularios de entrada, seleccione **[!UICONTROL Administration]> [!UICONTROL Configuration] >[!UICONTROL Input forms]** del menú:

![](assets/d_ncs_integration_form_arbo.png)

Para diseñar formularios, edite el contenido XML en el editor XML:

![](assets/d_ncs_integration_form_edit.png)

[Más información](form-structure.md#formatting).

Para obtener una vista previa de un formulario, haga clic en el botón **[!UICONTROL Preview]** pestaña:

![](assets/d_ncs_integration_form_preview.png)

## Tipos de formulario

Puede crear diferentes tipos de formularios de entrada. El tipo de formulario determina cómo navegan los usuarios en el formulario:

* Pantalla de la consola

   Este es el tipo de formulario predeterminado. El formulario consta de una sola página.

   ![](assets/console_screen_form.png)

* Administración de contenido

   Utilice este tipo de formulario para la gestión de contenido. Consulte esta [caso de uso](../../delivery/using/use-case--creating-content-management.md).

   ![](../../delivery/using/assets/d_ncs_content_form13.png)

* Asistente

   Este formulario consta de varias pantallas flotantes que se ordenan en secuencias específicas. Los usuarios navegan de una pantalla a otra. [Más información](form-structure.md#wizards).

* Iconbox

   Este formulario consta de varias páginas. Para desplazarse por el formulario, los usuarios seleccionan iconos a la izquierda del formulario.

   ![](assets/iconbox_form_preview.png)

* Portátil

   Este formulario consta de varias páginas. Para desplazarse por el formulario, los usuarios seleccionan fichas en la parte superior del formulario.

   ![](assets/notebook_form_preview.png)

* Panel vertical

   Este formulario muestra un árbol de navegación.

* Panel horizontal

   Este formulario muestra una lista de elementos.

## Contenedores

En los formularios, puede utilizar contenedores para varios fines:

* Organización del contenido en los formularios
* Definición del acceso a los campos de entrada
* Anidar formularios dentro de otros formularios

[Más información](form-structure.md#containers).

### Organizar contenido

Utilice contenedores para organizar el contenido dentro de los formularios:

* Los campos se pueden agrupar en secciones.
* Puede agregar páginas a formularios de varias páginas.

Para insertar un contenedor, utilice la variable `<container>` elemento. [Más información](form-structure.md#containers).

#### Campos de grupo

Utilice contenedores para agrupar los campos de entrada en secciones organizadas.

Para insertar una sección en un formulario, utilice este elemento: `<container type="frame">`. De forma opcional, para agregar un título de sección, utilice la variable `label` atributo.

Sintaxis: `<container type="frame" label="`*section_title*`"> […] </container>`

En este ejemplo, un contenedor define la variable **Creación** , que incluye el **[!UICONTROL Created by]** y **[!UICONTROL Name]** campos de entrada:

```xml
<form _cs="Coupons (nms)" entitySchema="xtk:form" img="xtk:form.png" label="Coupons"
      name="coupon" namespace="nms" type="default" xtkschema="xtk:form">
  <input xpath="@code"/>
  <input xpath="@type"/>
  <container label="Creation" type="frame">
    <input xpath="createdBy"/>
    <input xpath="createdBy/@name"/>
  </container>
</form>
```

![](assets/console_screen_form.png)

#### Agregar páginas a formularios de varias páginas

Para los formularios de varias páginas, utilice un contenedor para crear una página de formulario.

Este ejemplo muestra los contenedores para la variable **General** y **Detalles** páginas de un formulario:

```xml
<container img="ncm:book.png" label="General">
[…]
</container>
<container img="ncm:detail.png" label="Details">
[…]
</container>
```

### Definición del acceso a los campos

Utilice contenedores para definir qué es visible y para definir el acceso a los campos. Puede activar o desactivar grupos de campos.

### Anidar formularios

Utilice contenedores para anidar formularios dentro de otros formularios. [Más información](#add-pages-to-multipage-forms).

## Referencias a imágenes

Para buscar imágenes, elija **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Images]** del menú .

Para asociar una imagen a un elemento del formulario, por ejemplo, un icono, puede agregar una referencia a una imagen. Utilice la variable `img` , por ejemplo, en la `<container>` elemento.

Sintaxis: `img="`*`namespace`*`:`*`filename`*`.`*`extension`*`"`

Este ejemplo muestra referencias a la variable `book.png` y `detail.png` imágenes de `ncm` namespace:

```xml
<container img="ncm:book.png" label="General">
[…]
</container>
<container img="ncm:detail.png" label="Details">
[…]
</container>
```

Estas imágenes se utilizan para los iconos en los que los usuarios hacen clic para desplazarse por un formulario de varias páginas:

![](assets/nested_forms_preview.png)
