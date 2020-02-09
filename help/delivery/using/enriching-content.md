---
title: Enriquecimiento de contenido
seo-title: Enriquecimiento de contenido
description: Enriquecimiento de contenido
seo-description: null
page-status-flag: never-activated
uuid: 6f1bce9f-88ed-4ad3-987f-79f6c68264d2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: content-management
discoiquuid: 4404c21e-0a89-4762-af20-384ad7071916
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# Enriquecimiento de contenido{#enriching-content}

Los acumuladores le permiten enriquecer el contenido con datos externos. Estos datos proceden de consultas genéricas o tablas vinculadas.

## Consultas genéricas {#generic-queries}

Queries are configured via the publication template in the **[!UICONTROL Aggregator]** tab.

Los datos recuperados enriquecen el documento de salida XML a través de su elemento principal.

Ejemplo de devolución desde una consulta en el esquema del destinatario (**nms:recipient**):

```
<book name="Content Management">
  ...
  <collection-recipient>
    <recipient lastName="Doe" firstName="John" email="john.doe@aolf.com">
    ...
  </collection-recipient>
</book>
```

The **`<collection-recipient>`** element represents the input element of the document resulting from a query. Los datos recuperados se devuelven en este elemento; en nuestro ejemplo, una lista de destinatarios.

### Adición de una consulta {#adding-a-query}

Los parámetros de la consulta se editan mediante un asistente.

1. En la primera página, especifique la etiqueta y el esquema que contiene los datos que se van a recuperar.

   ![](assets/d_ncs_content_query1.png)

   >[!NOTE]
   >
   >El campo de edición **Path** se utiliza para cambiar el nombre del elemento de salida de la consulta.

1. La siguiente página permite seleccionar los datos que se van a recuperar.

   ![](assets/d_ncs_content_query2.png)

1. La siguiente página define la condición de filtro.

   ![](assets/d_ncs_content_query3.png)

1. La última página inicia una previsualización de los datos devueltos por la consulta.

   ![](assets/d_ncs_content_query4.png)

## Tablas vinculadas {#linked-tables}

Los enlaces permiten recuperar datos externos vinculados al contenido.

Hay dos tipos de datos vinculados:

* Enlaces de contenido: modo nativo de gestión del contenido. El contenido del enlace se integra automáticamente en el documento de salida XML.
* Los enlaces a listas externas proporcionan acceso a las demás listas de la base de datos con la limitación de recuperar los datos del enlace seleccionado mediante un acumulador.

### Vinculación a un esquema de contenido {#link-to-a-content-schema}

En el esquema de datos, se define un enlace de contenido de la siguiente manera:

```
<element expandSchemaTarget="cus:chapter" label="Main chapter" name="mainChapter" type="string"/>
```

The definition of the link is populated on a **string**-type **`<element>`**, and the **expandSchemaTarget** attribute references the target schema (&quot;cus:chapter&quot; in our example). El esquema de referencia debe ser de contenido.

The content of the targeted element enriches the link element, i.e. the **`<chapter>`** element in our example schema:

```
<mainChapter computeString="Introduction" id="7011" title="Introduction" xtkschema="cus:chapter">    
  <page>Introduction to input <STRONG>forms</STRONG>.</page>
</mainChapter>
```

>[!NOTE]
>
>La **Compute string** del enlace se presenta desde el atributo **computeString**.

En el formulario de entrada, el control de edición del enlace se declara de la siguiente manera:

```
<input type="articleEdit" xpath="mainChapter"/>
```

![](assets/d_ncs_content_link.png)

The **[!UICONTROL Magnifier]** icon enables you to open the edit form of the linked element.

#### Colección de enlaces {#link-collection}

Para rellenar una colección de enlaces, añada el atributo **unbound=&quot;true&quot;** a la definición del elemento de enlace en el esquema de datos:

```
<element expandSchemaTarget="cus:chapter" label="List of chapters" name="chapter"  ordered="true" unbound="true"/>
```

El contenido del elemento de destino enriquece cada elemento de colección:

```
<chapter computeString="Introduction" id="7011" title="Introduction" xtkschema="cus:chapter">    
  <page>Introduction to input <STRONG>forms</STRONG>.</page>
</chapter>
```

En el formulario de entrada, el control de lista se declara de la siguiente manera:

```
<input editable="false" nolabel="true" toolbarCaption="List of chapters" type="articleList" xpath="chapter" zoom="true"/>
```

![](assets/d_ncs_content_link2.png)

Se muestra una columna predeterminada para ver la **Compute string** de los elementos de destino.

### Enlaces a tablas externas {#links-to-external-tables}

Se declara un enlace a una tabla externa en el esquema de datos de la siguiente manera:

```
<element label="Main contact" name="mainContact" target="nms:recipient" type="link"/>
```

The definition of the link is populated on a **link**-type **`<element>`**, and the **target** attribute references the target schema (&quot;nms:recipient&quot; in our example).

Por norma, los enlaces deben declararse del elemento principal del esquema de datos.

The **Compute string** and the key of the targeted element enrich the **`<name>-id`** and **`<name>-cs`** attributes on the main element.

En nuestro ejemplo, el enlace se rellena en el esquema “cus:book”, el contenido de los datos del enlace se incluye en los atributos “mainContact-id” y “mainContact-cs”:

```
<book computeString="Content management" date="2006/06/08" id="6106" language="en" mainContact-cs="John Doe (john.doe@adobe.com)" mainContact-id="3012" name="Content management" xtkschema="cus:book">
```

El control de edición de enlaces se declara de la siguiente manera:

```
<input xpath="mainContact"/>
```

![](assets/d_ncs_content_link3.png)

You can restrict the choice of target elements by adding the **`<sysfilter>`** element via the link definition in the input form:

```
<input xpath="mainContact">
  <!-- Filter the selection of the link on the Adobe domain -->
  <sysFilter>
    <condition expr="@domain =  'adobe.com '"/>
  </sysFilter>
</input>
```

>[!NOTE]
>
>Esta restricción también se aplica a los enlaces de contenido.

#### Colección de enlaces {#link-collection-1}

La definición de la colección es idéntica a la definición de una lista en los elementos de colección:

```
<element label="List of contacts" name="contact" unbound="true">
  <element label="Recipient" name="recipient" target="nms:recipient" type="link"/>
</element>
```

En el formulario de entrada, el control de lista se declara de la siguiente manera:

```
<input nolabel="true" toolbarCaption="List of contacts" type="list" xpath="contact">
  <input xpath="recipient"/>
</input>
```

![](assets/d_ncs_content_link4.png)

>[!NOTE]
>
>La lista es editable y permite seleccionar el enlace de un control de tipo “enlace” presentado más atrás.

El contenido del elemento de destino enriquece cada elemento de colección en el documento de salida:

```
<contact id="11504978621" recipient-cs="Doe John (john.doe@adobe.com)" recipient-id="3012"/>
<contact id="11504982510" recipient-cs="Martinez Peter (peter.martinez@adobe.com)" recipient-id="3013"/>
```

#### Acumulación de enlaces {#link-aggregation}

El contenido de cada enlace al que se hace referencia se limita a la clave interna y a la **Compute string** del elemento de destino.

Se utiliza un script de JavaScript para enriquecer el contenido de los enlaces mediante consultas SOAP.

**Ejemplo**: Adición del nombre del destinatario al vínculo &quot;mainContact&quot; y a los vínculos de la colección &quot;contact&quot;:

```
// Update <mainContact> link
var mainContactId = content.@['mainContact-id']
var query = xtk.queryDef.create(
    <queryDef schema="nms:recipient" operation="get">
      <select>
        <node expr="@lastName"/>
      </select>
      <where>
        <condition expr={"@id="+mainContactId}/>
      </where>
    </queryDef>)

var recipient = query.ExecuteQuery()
content.mainContact.@lastName = recipient.@lastName

// Update <contact> link collection
for each(var contact in content.contact)
{
  var contactId = contact.@['recipient-id']
  var query = xtk.queryDef.create(
    <queryDef schema="nms:recipient" operation="get">
      <select>
        <node expr="@lastName"/>
      </select>
      <where>
        <condition expr={"@id="+contactId}/>
      </where>
    </queryDef>
  )
  
  var recipient = query.ExecuteQuery()
  contact.@lastName = recipient.@lastName
}
```

El resultado obtenido después de la ejecución del script:

```
<mainContact lastName="Doe"/>

<contact id="11504978621" lastName="Doe" recipient-cs="Doe John (john.doe@adobe.com)" recipient-id="3012"/>  
<contact id="11504982510" lastName="Martinez" recipient-cs="Martinez Peter (peter.martinez@adobe.com)" recipient-id="3013"/> 
```

The content of the JavaScript code is added via the **[!UICONTROL Administration > Configuration > Content management > JavaScript Codes]** folder and must be populated in the publication template for each transformation.

![](assets/d_ncs_content_link5.png)

