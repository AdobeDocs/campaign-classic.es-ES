---
product: campaign
title: Editar formularios
description: Editar formularios
feature: Configuration
role: Developer
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
exl-id: 24604dc9-f675-4e37-a848-f1911be84f3e
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '1707'
ht-degree: 3%

---


# Editar formularios{#editing-forms}

## Información general

Los especialistas en marketing y los operadores utilizan formularios de entrada para crear, modificar y previsualizar registros. Forms muestra una representación visual de la información.

Puede crear y modificar formularios de entrada:

* Puede modificar los formularios de entrada de fábrica que se envían de forma predeterminada. Los formularios de entrada de fábrica se basan en los esquemas de datos de fábrica.
* Puede crear formularios de entrada personalizados basados en esquemas de datos definidos.

Forms son entidades del tipo `xtk:form`. Puede ver la estructura del formulario de entrada en el esquema `xtk:form`. Para ver este esquema, elija **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]** en el menú. Más información sobre [estructura de formulario](form-structure.md).

Para acceder a los formularios de entrada, elija **[!UICONTROL Administration]> [!UICONTROL Configuration] >[!UICONTROL Input forms]** en el menú:

![](assets/d_ncs_integration_form_arbo.png)

Para diseñar formularios, edite el contenido XML en el editor XML:

![](assets/d_ncs_integration_form_edit.png)

[Más información](form-structure.md#formatting).

Para obtener una vista previa de un formulario, haga clic en la ficha **[!UICONTROL Preview]**:

![](assets/d_ncs_integration_form_preview.png)

## Tipos de formularios

Puede crear diferentes tipos de formularios de entrada. El tipo de formulario determina cómo navegan los usuarios por el formulario:

* Pantalla de consola

  Este es el tipo de formulario predeterminado. El formulario consta de una sola página.

  ![](assets/console_screen_form.png)

* Administración de contenido

  Utilice este tipo de formulario para la administración de contenido. Ver este [caso de uso](../../delivery/using/use-case-creating-content-management.md).

  ![](../../delivery/using/assets/d_ncs_content_form13.png)

* Ayudante

  Este formulario consta de varias pantallas flotantes ordenadas en una secuencia específica. Los usuarios navegan de una pantalla a otra. [Más información](form-structure.md#wizards).

* Iconbox

  Este formulario consta de varias páginas. Para desplazarse por el formulario, los usuarios seleccionan iconos en la parte izquierda del formulario.

  ![](assets/iconbox_form_preview.png)

* Notebook

  Este formulario consta de varias páginas. Para desplazarse por el formulario, los usuarios seleccionan pestañas en la parte superior del formulario.

  ![](assets/notebook_form_preview.png)

* Panel vertical

  Este formulario muestra un árbol de navegación.

* Panel horizontal

  Este formulario muestra una lista de elementos.

## Contenedores

En los formularios, puede utilizar contenedores para varios fines:

* Organización del contenido de los formularios
* Definición del acceso a los campos de entrada
* Anidar formularios dentro de otros formularios

[Más información](form-structure.md#containers).

### Organizar contenido

Utilice contenedores para organizar el contenido de los formularios:

* Puede agrupar los campos en secciones.
* Puede agregar páginas a formularios de varias páginas.

Para insertar un contenedor, use el elemento `<container>`. [Más información](form-structure.md#containers).

#### Agrupar campos

Utilice contenedores para agrupar los campos de entrada en secciones organizadas.

Para insertar una sección en un formulario, utilice este elemento: `<container type="frame">`. Opcionalmente, para agregar un título de sección, use el atributo `label`.

Sintaxis: `<container type="frame" label="`*section_title*`"> […] </container>`

En este ejemplo, un contenedor define la sección **Creation**, que comprende los campos de entrada **[!UICONTROL Created by]** y **[!UICONTROL Name]**:

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

Para formularios de varias páginas, utilice un contenedor para crear una página de formulario.

Este ejemplo muestra contenedores para las páginas **General** y **Detalles** de un formulario:

```xml
<container img="ncm:book.png" label="General">
[…]
</container>
<container img="ncm:detail.png" label="Details">
[…]
</container>
```

### Definición del acceso a los campos

Utilice contenedores para definir lo que está visible y para definir el acceso a los campos. Puede activar o desactivar grupos de campos.

### Anidar formularios

Utilice contenedores para anidar formularios dentro de otros formularios. [Más información](#add-pages-to-multipage-forms).

## Referencias a imágenes

Para buscar imágenes, elija **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Images]** en el menú.

Para asociar una imagen con un elemento del formulario, por ejemplo, un icono, puede añadir una referencia a una imagen. Utilice el atributo `img`, por ejemplo, en el elemento `<container>`.

Sintaxis: `img="`*`namespace`*`:`*`filename`*`.`*`extension`*`"`

Este ejemplo muestra referencias a las imágenes `book.png` y `detail.png` del espacio de nombres `ncm`:

```xml
<container img="ncm:book.png" label="General">
[…]
</container>
<container img="ncm:detail.png" label="Details">
[…]
</container>
```

Estas imágenes se utilizan para iconos en los que los usuarios hacen clic para desplazarse por un formulario de varias páginas:

![](assets/nested_forms_preview.png)


## Creación de un formulario simple {#create-simple-form}

Para crear un formulario, siga estos pasos:

1. En el menú, elija **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Input forms]**.
1. Haga clic en el botón **[!UICONTROL New]** en la parte superior derecha de la lista.

   ![](assets/input-form-create-1.png)

1. Especifique las propiedades del formulario:

   * Especifique el nombre del formulario y el área de nombres.

     El nombre del formulario y el área de nombres pueden coincidir con el esquema de datos relacionado.  Este ejemplo muestra un formulario para el esquema de datos `cus:order`:

     ```xml
     <form entitySchema="xtk:form" img="xtk:form.png" label="Order" name="order" namespace="cus" type="iconbox" xtkschema="xtk:form">
       […]
     </form>
     ```

     También puede especificar explícitamente el esquema de datos en el atributo `entity-schema`.

     ```xml
     <form entity-schema="cus:stockLine" entitySchema="xtk:form" img="xtk:form.png" label="Stock order" name="stockOrder" namespace="cus" xtkschema="xtk:form">
       […]
     </form>
     ```

   * Especifique la etiqueta que se mostrará en el formulario.
   * De forma opcional, especifique el tipo de formulario. Si no especifica un tipo de formulario, se utiliza el tipo de pantalla de la consola de forma predeterminada.

     ![](assets/input-form-create-2.png)

     Si está diseñando un formulario de varias páginas, puede omitir el tipo de formulario en el elemento `<form>` y especificar el tipo en un contenedor.

1. Haga clic en **[!UICONTROL Save]**.

1. Inserte los elementos del formulario.

   Por ejemplo, para insertar un campo de entrada, utilice el elemento `<input>`. Establezca el atributo `xpath` en la referencia de campo como una expresión XPath. [Más información](schema-structure.md#referencing-with-xpath).

   Este ejemplo muestra campos de entrada basados en el esquema `nms:recipient`.

   ```xml
   <input xpath="@firstName"/>
   <input xpath="@lastName"/>
   ```

1. Si el formulario se basa en un tipo de esquema específico, puede buscar los campos de este esquema:

   1. Haga clic en **[!UICONTROL Insert]** > **[!UICONTROL Document fields]**.

      ![](assets/input-form-create-4.png)

   1. Seleccione el campo y haga clic en **[!UICONTROL OK]**.

      ![](assets/input-form-create-5.png)

1. De forma opcional, especifique el editor de campos.

   Hay asociado un editor de campos predeterminado con cada tipo de datos:
   * Para un campo de tipo fecha, el formulario muestra un calendario de entrada.
   * Para un campo de tipo lista desglosada, el formulario muestra una lista de selección.

   Puede utilizar estos tipos de editor de campos:

   | Editor de campos | Atributo de formulario |
   | --- | --- |
   | Botón de opción | `type="radiobutton"` |
   | Casilla de verificación | `type="checkbox"` |
   | Editar árbol | `type="tree"` |

   Más información sobre [controles de lista de memoria](form-structure.md#memory-list-controls).

1. De forma opcional, defina el acceso a los campos:

   | Elemento | Atributo | Descripción |
   | --- | --- | --- |
   | `<input>` | `read-only="true"` | Proporciona acceso de solo lectura a un campo |
   | `<container>` | `type="visibleGroup" visibleIf="`*edit-expr*`"` | Muestra condicionalmente un grupo de campos |
   | `<container>` | `type="enabledGroup" enabledIf="`*edit-expr*`"` | Habilita condicionalmente un grupo de campos |

   Ejemplo:

   ```xml
   <container type="enabledGroup" enabledIf="@gender=1">
     […]
   </container>
   <container type="enabledGroup" enabledIf="@gender=2">
     […]
   </container>
   ```

1. De forma opcional, utilice contenedores para agrupar campos en secciones.

   ```xml
   <container type="frame" label="Name">
      <input xpath="@firstName"/>
      <input xpath="@lastName"/>
   </container>
   <container type="frame" label="Contact details">
      <input xpath="@email"/>
      <input xpath="@phone"/>
   </container>
   ```

   ![](assets/input-form-create-3.png)

## Creación de un formulario de varias páginas {#create-multipage-form}

Puede crear formularios de varias páginas. También puede anidar formularios dentro de otros formularios.

### Crear un formulario `iconbox`

Utilice el tipo de formulario `iconbox` para mostrar los iconos a la izquierda del formulario, que llevarán a los usuarios a diferentes páginas del formulario.

![](assets/iconbox_form_preview.png)

Para cambiar el tipo de un formulario existente a `iconbox`, siga estos pasos:

1. Cambiar el atributo `type` del elemento `<form>` a `iconbox`:

   ```xml
   <form […] type="iconbox">
   ```

1. Establezca un contenedor para cada página de formulario:

   1. Agregue un elemento `<container>` como elemento secundario del elemento `<form>`.
   1. Para definir una etiqueta y una imagen para el icono, use los atributos `label` y `img`.

      ```xml
      <form entitySchema="xtk:form" name="Service provider" namespace="nms" type="iconbox" xtkschema="xtk:form">
          <container img="xtk:properties.png" label="General">
              <input xpath="@label"/>
              <input xpath="@name"/>
              […]
          </container>
          <container img="nms:msgfolder.png" label="Details">
              <input xpath="@address"/>
              […]
          </container>
          <container img="nms:supplier.png" label="Services">
              […]
          </container>
      </form>
      ```

   Como alternativa, quite el atributo `type="frame"` de los elementos `<container>` existentes.

### Crear un formulario de bloc de notas

Utilice el tipo de formulario `notebook` para mostrar las fichas en la parte superior del formulario, que llevan a los usuarios a diferentes páginas.

![](assets/notebook_form_preview.png)

Para cambiar el tipo de un formulario existente a `notebook`, siga estos pasos:

1. Cambiar el atributo `type` del elemento `<form>` a `notebook`:

   ```xml
   <form […] type="notebook">
   ```

1. Agregue un contenedor para cada página de formulario:

   1. Agregue un elemento `<container>` como elemento secundario del elemento `<form>`.
   1. Para definir la etiqueta y la imagen para el icono, utilice los atributos `label` y `img`.

   ```xml
     <form entitySchema="xtk:form" name="Service provider" namespace="nms" type="notebook" xtkschema="xtk:form">
         <container label="General">
             <input xpath="@label"/>
             <input xpath="@name"/>
             […]
         </container>
         <container label="Details">
             <input xpath="@address"/>
             […]
         </container>
         <container label="Services">
             […]
         </container>
     </form>
   ```

   Como alternativa, quite el atributo `type="frame"` de los elementos `<container>` existentes.

### Anidar formularios

Puede anidar formularios dentro de otros formularios. Por ejemplo, puede anidar formularios de bloc de notas en formularios de cuadro de iconos.

Nivel de anidación que controla la navegación. Los usuarios pueden explorar en profundidad los subformularios.

Para anidar un formulario dentro de otro formulario, inserte un elemento `<container>` y establezca el atributo `type` en el tipo de formulario. Para el formulario de nivel superior, puede establecer el tipo de formulario en un contenedor externo o en el elemento `<form>`.

### Ejemplo

Este ejemplo muestra un formulario complejo:

* El formulario de nivel superior es un formulario de cuadro de iconos. Este formulario consta de dos contenedores etiquetados como **General** y **Detalles**.

  Como resultado, el formulario externo muestra las páginas **General** y **Detalles** en el nivel superior. Para acceder a estas páginas, los usuarios hacen clic en los iconos de la izquierda del formulario.

* El subformulario es un formulario de bloc de notas anidado en el contenedor **General**. El subformulario consta de dos contenedores con la etiqueta **Name** y **Contact**.

```xml
<form _cs="Profile (nms)" entitySchema="xtk:form" img="xtk:form.png" label="Profile" name="profile" namespace="nms" xtkschema="xtk:form">
  <container type="iconbox">
    <container img="ncm:general.png" label="General">
      <container type="notebook">
        <container label="Name">
          <input xpath="@firstName"/>
          <input xpath="@lastName"/>
        </container>
        <container label="Contact">
          <input xpath="@email"/>
        </container>
      </container>
    </container>
    <container img="ncm:detail.png" label="Details">
      <input xpath="@birthDate"/>
    </container>
  </container>
</form>
```

Como resultado, la página **General** del formulario externo muestra las fichas **Nombre** y **Contacto**.

![](assets/nested_forms_preview.png)

Para anidar un formulario dentro de otro formulario, inserte un elemento `<container>` y establezca el atributo `type` en el tipo de formulario. Para el formulario de nivel superior, puede establecer el tipo de formulario en un contenedor externo o en el elemento `<form>`.

### Ejemplo

Este ejemplo muestra un formulario complejo:

* El formulario de nivel superior es un formulario de cuadro de iconos. Este formulario consta de dos contenedores etiquetados como **General** y **Detalles**.

  Como resultado, el formulario externo muestra las páginas **General** y **Detalles** en el nivel superior. Para acceder a estas páginas, los usuarios hacen clic en los iconos de la izquierda del formulario.

* El subformulario es un formulario de bloc de notas anidado en el contenedor **General**. El subformulario consta de dos contenedores con la etiqueta **Name** y **Contact**.

```xml
<form _cs="Profile (nms)" entitySchema="xtk:form" img="xtk:form.png" label="Profile" name="profile" namespace="nms" xtkschema="xtk:form">
  <container type="iconbox">
    <container img="ncm:general.png" label="General">
      <container type="notebook">
        <container label="Name">
          <input xpath="@firstName"/>
          <input xpath="@lastName"/>
        </container>
        <container label="Contact">
          <input xpath="@email"/>
        </container>
      </container>
    </container>
    <container img="ncm:detail.png" label="Details">
      <input xpath="@birthDate"/>
    </container>
  </container>
</form>
```

Como resultado, la página **General** del formulario externo muestra las fichas **Nombre** y **Contacto**.

![](assets/nested_forms_preview.png)



## Modificación de un formulario de entrada de fábrica {#modify-factory-form}

Para modificar un formulario de fábrica, siga estos pasos:

1. Modifique el formulario de entrada de fábrica:

   1. En el menú, elija **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Input forms]**.
   1. Seleccione un formulario de entrada y modifíquelo.

   Puede ampliar los esquemas de datos de fábrica, pero no puede ampliar los formularios de entrada de fábrica. Se recomienda modificar los formularios de entrada de fábrica directamente sin volver a crearlos. Durante las actualizaciones de software, las modificaciones realizadas en los formularios de entrada de fábrica se combinan con las actualizaciones. Si la combinación automática falla, puede resolver los conflictos. [Más información](../../production/using/upgrading.md#resolving-conflicts).

   Por ejemplo, si amplía un esquema de fábrica con un campo adicional, puede añadir este campo al formulario de fábrica relacionado.

## Validar formularios {#validate-forms}

Puede incluir controles de validación en los formularios.

### Conceder acceso de solo lectura a los campos

Para conceder acceso de sólo lectura a un campo, utilice el atributo `readOnly="true"`. Por ejemplo, es posible que desee mostrar la clave principal de un registro, pero con acceso de sólo lectura. [Más información](form-structure.md#non-editable-fields).

En este ejemplo, la clave principal (`iRecipientId`) del esquema `nms:recipient` se muestra en el acceso de solo lectura:

```xml
<value xpath="@iRecipientId" readOnly="true"/>
```

### Comprobar campos obligatorios

Puede comprobar la información obligatoria:

* Utilice el atributo `required="true"` para los campos obligatorios.
* Utilice el nodo `<leave>` para comprobar estos campos y mostrar mensajes de error.

En este ejemplo, la dirección de correo electrónico es obligatoria y se muestra un mensaje de error si el usuario no ha proporcionado esta información:

```xml
<input xpath="@email" required="true"/>
<leave>
  <check expr="@email!=''">
    <error>The email address is required.</error>
  </check>
</leave>
```

Obtenga más información sobre [campos de expresión](form-structure.md#expression-field) y [contexto de formulario](form-structure.md#context-of-forms).

### Validar valores

Puede utilizar llamadas de JavaScript SOAP para validar datos de formulario desde la consola. Utilice estas llamadas para realizar validaciones complejas, por ejemplo, para comparar un valor con una lista de valores autorizados. [Más información](form-structure.md#soap-methods).

1. Cree una función de validación en un archivo JS.

   Ejemplo:

   ```js
   function nms_recipient_checkValue(value)
   {
     logInfo("checking value " + value)
     if (…)
     {
       logError("Value " + value + " is not valid")
     }
     return 1
   }
   ```

   En este ejemplo, la función se denomina `checkValue`. Esta función se usa para comprobar el tipo de datos `recipient` en el espacio de nombres `nms`. El valor que se está comprobando se registra. Si el valor no es válido, se registra un mensaje de error. Si el valor es válido, se devuelve el valor 1.

   Puede utilizar el valor devuelto para modificar el formulario.

1. En el formulario, agregue el elemento `<soapCall>` al elemento `<leave>`.

   En este ejemplo, se utiliza una llamada de SOAP para validar la cadena `@valueToCheck`:

   ```xml
   <form name="recipient" (…)>
   (…)
     <leave>
       <soapCall name="checkValue" service="nms:recipient">
         <param exprIn="@valueToCheck" type="string"/>
       </soapCall>
     </leave>
   </form>
   ```

   En este ejemplo, se utilizan el método `checkValue` y el servicio `nms:recipient`:

   * El servicio es el área de nombres y el tipo de datos.
   * El método es el nombre de la función. El nombre distingue entre mayúsculas y minúsculas.

   La llamada se realiza sincrónicamente.

   Se muestran todas las excepciones. Si utiliza el elemento `<leave>`, los usuarios no podrán guardar el formulario hasta que se valide la información introducida.

Este ejemplo muestra cómo puede realizar llamadas de servicio desde formularios:

```xml
<enter>
  <soapCall name="client" service="c4:ybClient">
    <param exprIn="@id" type="string"/>
    <param type="boolean" xpathOut="/tmp/@count"/>
  </soapCall>
</enter>
```

En este ejemplo, la entrada es un ID, que es una clave principal. Cuando los usuarios rellenan el formulario de este ID, se realiza una llamada de SOAP con este ID como parámetro de entrada. El resultado es un booleano escrito en este campo: `/tmp/@count`. Puede utilizar este booleano dentro del formulario. Más información sobre [contexto de formulario](form-structure.md#context-of-forms).
