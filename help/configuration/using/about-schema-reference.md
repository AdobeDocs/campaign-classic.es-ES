---
product: campaign
title: Acerca de la referencia de esquema en Adobe Campaign Classic
description: Obtenga información sobre cómo configurar esquemas de extensión para ampliar el modelo de datos conceptuales de la base de datos de Adobe Campaign Classic.
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: f36a1b01-a002-4a21-9255-ea78b5f173fe
source-git-commit: 4a41aea9edfe5e6ca0454049cbb2892449eec153
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 8%

---

# Acerca de la referencia de esquema{#about-schema-reference}

En este capítulo se describe cómo configurar esquemas de extensión para ampliar el modelo de datos conceptuales de la base de datos de Adobe Campaign.

Para comprender mejor las tablas integradas de Campaign y su interacción, consulte el [modelo de datos del Campaign Classic](https://experienceleague.adobe.com/docs/campaign-classic/using/configuring-campaign-classic/data-model/about-data-model.html?lang=es).

La estructura física y lógica de los datos que se llevan en la aplicación se describe en XML. Obedece a una gramática específica de Adobe Campaign, denominada **schema**.

Un esquema es un documento XML asociado a una tabla de base de datos. Define la estructura de datos y describe la definición SQL de la tabla:

* Nombre de la tabla
* Campos
* Índices
* Vínculos con otras tablas

También describe la estructura XML utilizada para almacenar datos:

* Elementos y atributos
* Jerarquía de elementos
* Tipos de elementos y atributos
* Valores predeterminados
* Etiquetas, descripciones y otras propiedades.

Los esquemas permiten definir una entidad en la base de datos. Hay un esquema para cada entidad.

La siguiente ilustración muestra la ubicación de los esquemas en el sistema de datos de Adobe Campaign:

![](assets/reference_schema_intro.png)

## Sintaxis de esquemas {#syntax-of-schemas}

El elemento raíz del esquema es **`<srcschema>`**. Contiene los subelementos **`<element>`** y **`<attribute>`**.

El primer subelemento **`<element>`** coincide con la raíz de la entidad.

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">  
    <attribute name="lastName"/>
    <attribute name="email"/>
    <element name="location">
      <attribute name="city"/>
   </element>
  </element>
</srcSchema>
```

>[!NOTE]
>
>El elemento raíz de la entidad tiene el mismo nombre que el esquema.

![](assets/s_ncs_configuration_schema_and_entity.png)

Las etiquetas **`<element>`** definen los nombres de los elementos de entidad. **`<attribute>`** las etiquetas del esquema definen los nombres de los atributos en las  **`<element>`** etiquetas a las que se han vinculado.

## Identificación de un esquema {#identification-of-a-schema}

Un esquema de datos se identifica con su nombre y área de nombres.

Un área de nombres permite agrupar un conjunto de esquemas por área de interés. Por ejemplo, el espacio de nombres **cus** se utiliza para la configuración específica del cliente (**customers**).

La clave de identificación de un esquema es una cadena creada con el área de nombres y el nombre separado por dos puntos; por ejemplo: **cus:recipient**.

>[!IMPORTANT]
>
>El nombre del área de nombres debe ser conciso y contener solo caracteres autorizados de acuerdo con las reglas de nomenclatura XML.
>
>Los identificadores no deben comenzar con caracteres numéricos.
>
>Las siguientes áreas de nombres están reservadas para descripciones de las entidades del sistema necesarias para el funcionamiento de la aplicación Adobe Campaign y no deben usarse: **xtk**, **nl**, **nms**, **ncm**, **temp**, **ncl**, **crm&lt;a11 3/>,** xxl **.**

