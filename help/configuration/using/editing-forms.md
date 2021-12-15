---
product: campaign
title: Edición de formularios
description: Edición de formularios
audience: configuration
content-type: reference
topic-tags: input-forms
exl-id: 24604dc9-f675-4e37-a848-f1911be84f3e
source-git-commit: 42717f3ef3bcda4108dad6a4c0ece752ada579a2
workflow-type: tm+mt
source-wordcount: '1647'
ht-degree: 2%

---


# Edición de formularios{#editing-forms}

![](../../assets/common.svg)

## Información general

Marketers and operators use input forms to create, modify, and preview records. Forms show a visual representation of information.

You can create and modify input forms:

* You can modify the factory input forms that are delivered by default. The factory input forms are based on the factory data schemas.
* You can create custom input forms, based on data schemas that you define.

`xtk:form` `xtk:form` **[!UICONTROL Administration]****[!UICONTROL Configuration]****[!UICONTROL Data schemas]** [](form-structure.md)

**[!UICONTROL Administration][!UICONTROL Configuration][!UICONTROL Input forms]**

![](assets/d_ncs_integration_form_arbo.png)

To design forms, edit the XML content in the XML editor:

![](assets/d_ncs_integration_form_edit.png)

[Más información](form-structure.md#formatting).

**[!UICONTROL Preview]**

![](assets/d_ncs_integration_form_preview.png)

## Form types

You can create different types of input forms. The form type determines how users navigate the form:

* Console screen

   This is the default form type. The form comprises a single page.

   ![](assets/console_screen_form.png)

* Administración de contenido

   Use this form type for content management. [](../../delivery/using/use-case--creating-content-management.md)

   ![](../../delivery/using/assets/d_ncs_content_form13.png)

* Wizard

   This form comprises multiple floating screens that are ordered in a specific sequences. Users navigate from one screen to the next. [Más información](form-structure.md#wizards).

* Iconbox

   This form comprises multiple pages. To navigate the form, users select icons at the left of the form.

   ![](assets/iconbox_form_preview.png)

* Notebook

   This form comprises multiple pages. To navigate the form, users select tabs at the top of the form.

   ![](assets/notebook_form_preview.png)

* Vertical pane

   This form shows a navigation tree.

* Horizontal pane

   This form shows a list of items.

## Contenedores

In forms, you can use containers for various purposes:

* Organize content within forms
* Define access to input fields
* Nest forms within other forms

[Más información](form-structure.md#containers).

### Organize content

Use containers to organize content within forms:

* You can group fields into sections.
* You can add pages to multipage forms.

`<container>` [Más información](form-structure.md#containers).

#### Group fields

Use containers to group input fields into organized sections.

`<container type="frame">` `label`

`<container type="frame" label="`**`"> […] </container>`

******[!UICONTROL Created by]****[!UICONTROL Name]**

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

#### Add pages to multipage forms

For multipage forms, use a container to create a form page.

********

```xml
<container img="ncm:book.png" label="General">
[…]
</container>
<container img="ncm:detail.png" label="Details">
[…]
</container>
```

### Define access to fields

Use containers to define what is visible and to define access to fields. You can turn on or off groups of fields.

### Nest forms

Use containers to nest forms within other forms. [Más información](#add-pages-to-multipage-forms).

## References to images

**[!UICONTROL Administration]****[!UICONTROL Configuration]****[!UICONTROL Images]**

To associate an image with an element in the form, for example, an icon, you can add a reference to an image. `img``<container>`

Sintaxis: `img="`*`namespace`*`:`*`filename`*`.`*`extension`*`"`

`book.png``detail.png``ncm`

```xml
<container img="ncm:book.png" label="General">
[…]
</container>
<container img="ncm:detail.png" label="Details">
[…]
</container>
```

These images are used for icons that users click to navigate a multipage form:

![](assets/nested_forms_preview.png)

## Create a simple form {#create-simple-form}

To create a form, follow these steps:

1. **[!UICONTROL Administration]****[!UICONTROL Configuration]****[!UICONTROL Input forms]**
1. **[!UICONTROL New]**

   ![](assets/input-form-create-1.png)

1. Specify the form properties:

   * Specify the form name and the namespace.

      The form name and the namespace can match the related data schema.  `cus:order`

      ```xml
      <form entitySchema="xtk:form" img="xtk:form.png" label="Order" name="order" namespace="cus" type="iconbox" xtkschema="xtk:form">
        […]
      </form>
      ```

      `entity-schema`

      ```xml
      <form entity-schema="cus:stockLine" entitySchema="xtk:form" img="xtk:form.png" label="Stock order" name="stockOrder" namespace="cus" xtkschema="xtk:form">
        […]
      </form>
      ```

   * Specify the label to be displayed on the form.
   * Optionally, specify the form type. If you do not specify a form type, the console screen type is used by default.

      ![](assets/input-form-create-2.png)

      `<form>`

1. Haga clic en **[!UICONTROL Save]**.

1. Insert the form elements.

   `<input>` `xpath` [Más información](schema-structure.md#referencing-with-xpath).

   `nms:recipient`

   ```xml
   <input xpath="@firstName"/>
   <input xpath="@lastName"/>
   ```

1. If the form is based on a specific schema type, you can look up the fields for this schema:

   1. Haga clic en **[!UICONTROL Insert]** > **[!UICONTROL Document fields]**.

      ![](assets/input-form-create-4.png)

   1. **[!UICONTROL OK]**

      ![](assets/input-form-create-5.png)

1. Optionally, specify the field editor.

   A default field editor is associated with each data type:
   * For a date-type field, the form shows an input calendar.
   * For an enumeration-type field, the form shows a selection list.

   You can use these field editor types:

   | Field editor | Form attribute |
   | --- | --- |
   | Radio button | `type="radiobutton"` |
   | Checkbox | `type="checkbox"` |
   | Edit tree | `type="tree"` |

   [](form-structure.md#memory-list-controls)

1. Optionally, define access to the fields:

   | Elemento | Atributo | Descripción |
   | --- | --- | --- |
   | `<input>` | `read-only:"true"` | Provides read-only access to a field |
   | `<container>` | `type="visibleGroup" visibleIf="`**`"` | Conditionally displays a group of fields |
   | `<container>` | `type="enabledGroup" enabledIf="`**`"` | Conditionally enables a group of fields |

   Ejemplo:

   ```xml
   <container type="enabledGroup" enabledIf="@gender=1">
     […]
   </container>
   <container type="enabledGroup" enabledIf="@gender=2">
     […]
   </container>
   ```

1. Optionally, use containers to group fields into sections.

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

## Create a multipage form {#create-multipage-form}

You can create multipage forms. You can also nest forms within other forms.

### `iconbox`

`iconbox`

![](assets/iconbox_form_preview.png)

`iconbox`

1. `type``<form>``iconbox`

   ```xml
   <form […] type="iconbox">
   ```

1. Set a container for each form page:

   1. `<container>``<form>`
   1. `label``img`

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
   `type="frame"``<container>`

### Create a notebook form

`notebook`

![](assets/notebook_form_preview.png)

`notebook`

1. `type``<form>``notebook`

   ```xml
   <form […] type="notebook">
   ```

1. Add a container for each form page:

   1. `<container>``<form>`
   1. `label``img`

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

   `type="frame"``<container>`

### Nest forms {#nest-forms}

You can nest forms within other forms. For example, you can nest notebook forms within iconbox forms.

The level of nesting controls navigation. Users can drill down to subforms.

`<container>``type` `<form>`

### Ejemplo

This example shows a complex form:

* The top-level form is an iconbox form. ********

   ******** To access these pages, users click the icons at the left of the form.

* **** ********

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

************

![](assets/nested_forms_preview.png)

## Modify a factory input form {#modify-factory-form}

To modify a factory form, follow these steps:

1. Optionally, extend the related data schema:

   1. **[!UICONTROL Administration]****[!UICONTROL Configuration]****[!UICONTROL Data schemas]**
   1. Select a data schema and extend it. For example, you can add fields. [Más información](extending-a-schema.md).

      >[!CAUTION]
      > Do not modify the original data in a factory namespace, but, instead, extend it in a custom namespace. The reason is that, during software upgrades, all data in the factory namespaces are overwritten. `xtk``ncm``nms` The data in your custom namespaces is not modified.

1. Modify the factory input form:

   1. **[!UICONTROL Administration]****[!UICONTROL Configuration]****[!UICONTROL Input forms]**
   1. Select an input form and modify it.

   You can extend factory data schemas, but you cannot extend factory input forms. We recommend that you modify factory input forms directly without recreating them. During software upgrades, your modifications in the factory input forms are merged with the upgrades. If the automatic merge fails, you can resolve the conflicts. [Más información](../../production/using/upgrading.md#resolving-conflicts).

   For example, if you extend a factory schema with an additional field, you can add this field to the related factory form.

## Validate forms {#validate-forms}

You can include validation controls in forms.

### Grant read-only access to fields

`readOnly="true"` For example, you might want to show the primary key of a record, but with read-only access. [Más información](form-structure.md#non-editable-fields).

`iRecipientId``nms:recipient`

```xml
<value xpath="@iRecipientId" readOnly="true"/>
```

### Check mandatory fields

You can check mandatory information:

* `required="true"`
* `<leave>`

In this example, the email address is required, and an error message is displayed if the user has not provided this information:

```xml
<input xpath="@email" required="true"/>
<leave>
  <check expr="@email!=''">
    <error>The email address is required.</error>
  </check>
</leave>
```

[](form-structure.md#expression-field)[](form-structure.md#context-of-forms)

### Validate values

You can use JavaScript SOAP calls to validate form data from the Console. Use these calls for complex validation, for example, to check a value against a list of authorized values. [Más información](form-structure.md#soap-methods).

1. Create a validation function in a JS file.

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

   `checkValue` `recipient``nms` The value that is being checked is logged. If the value is not valid, then an error message is logged. If the value is valid, then the value 1 is returned.

   You can use the returned value to modify the form.

1. `<soapCall>``<leave>`

   `@valueToCheck`

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

   `checkValue``nms:recipient`

   * The service is the namespace and the data type.
   * The method is the function name. The name is case-sensitive.

   The call is performed synchronously.

   All exceptions are displayed. `<leave>`

This example shows how you can make service calls from within forms:

```xml
<enter>
  <soapCall name="client" service="c4:ybClient">
    <param exprIn="@id" type="string"/>
    <param type="boolean" xpathOut="/tmp/@count"/>
  </soapCall>
</enter>
```

In this example, the input is an ID, which is a primary key. When users fill the form for this ID, a SOAP call is made with this ID as the input parameter. `/tmp/@count` You can use this boolean inside the form. [](form-structure.md#context-of-forms)
