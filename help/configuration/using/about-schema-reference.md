---
solution: Campaign Classic
product: campaign
title: Acerca de la referencia de esquema en Adobe Campaign Classic
description: Obtenga información sobre cómo configurar esquemas de extensión para ampliar el modelo de datos conceptuales de la base de datos de Adobe Campaign Classic.
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 7%

---


# Acerca de la referencia de esquema{#about-schema-reference}

En este capítulo se describe cómo configurar esquemas de extensión para ampliar el modelo de datos conceptuales de la base de datos de Adobe Campaign.

Para comprender mejor las tablas integradas de Campaña y su interacción, consulte el [modelo de datos de Campaign Classic](https://helpx.adobe.com/es/campaign/kb/acc-datamodel.html).

La estructura física y lógica de los datos que se llevan en la aplicación se describe en XML. Obedece a una gramática específica de Adobe Campaign, denominada **esquema**.

Un esquema es un documento XML asociado a una tabla de base de datos. Define la estructura de datos y describe la definición SQL de la tabla:

* El nombre de la tabla
* Campos
* Índices
* Vínculos con otras tablas

También describe la estructura XML utilizada para almacenar datos:

* Elementos y atributos
* Jerarquía de elementos
* Tipos de elementos y atributos
* Valores predeterminados
* Etiquetas, descripciones y otras propiedades.

Las esquemas permiten definir una entidad en la base de datos. Hay un esquema para cada entidad.

La siguiente ilustración muestra la ubicación de esquemas en el sistema de datos de Adobe Campaign:

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

Un esquema de datos se identifica por su nombre y su Área de nombres.

Una Área de nombres permite agrupar un conjunto de esquemas por área de interés. Por ejemplo, la Área de nombres **cus** se utiliza para la configuración específica del cliente (**customers**).

>[!IMPORTANT]
>
>Como estándar, el nombre de la Área de nombres debe ser conciso y contener sólo caracteres autorizados de acuerdo con las reglas de nomenclatura XML.
>
>Los identificadores no deben comenzar con caracteres numéricos.

Algunas Áreas de nombres están reservadas para las descripciones de las entidades del sistema necesarias para el funcionamiento de la aplicación Adobe Campaign:

* **xtk**: sobre los datos del sistema de plataforma,
* **nl**: sobre el uso global de la solicitud,
* **nms**: en relación con el envío (destinatario, envío, seguimiento, etc.),
* **ncm**: sobre el gestor de contenido,
* **temp**: reservado para esquemas temporales.

La clave de identificación de un esquema es una cadena creada con la Área de nombres y el nombre separados por dos puntos; por ejemplo: **cus:destinatario**.
