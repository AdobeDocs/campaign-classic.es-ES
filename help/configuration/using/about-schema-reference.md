---
product: campaign
title: Acerca de la referencia de esquema en Adobe Campaign Classic
description: Aprenda a configurar esquemas de extensión para ampliar el modelo de datos conceptuales de la base de datos de Adobe Campaign Classic
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
feature: Schema Extension
role: Data Engineer, Developer
exl-id: f36a1b01-a002-4a21-9255-ea78b5f173fe
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 15%

---

# Acerca de la referencia de esquema{#about-schema-reference}

En este capítulo se describe cómo configurar esquemas de extensión para ampliar el modelo de datos conceptuales de la base de datos de Adobe Campaign.

Para comprender mejor las tablas integradas de Campaign y su interacción, consulte la [modelo de datos de Campaign Classic](https://experienceleague.adobe.com/docs/campaign-classic/using/configuring-campaign-classic/data-model/about-data-model.html?lang=es).

La estructura física y lógica de los datos que se llevan en la aplicación se describe en XML. Obedece a una gramática específica de Adobe Campaign, denominada **esquema**.

Un esquema es un documento XML asociado a una tabla de una base de datos. Define la estructura de datos y describe la definición SQL de la tabla:

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

El elemento raíz del esquema es **`<srcschema>`**. Contiene el **`<element>`** y **`<attribute>`** subelementos.

El primero **`<element>`** El subelemento coincide con la raíz de la entidad.

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

El **`<element>`** las etiquetas definen los nombres de los elementos de entidad. **`<attribute>`** Las etiquetas del esquema definen los nombres de los atributos en la variable **`<element>`** etiquetas a las que se han vinculado.

## Identificación de un esquema {#identification-of-a-schema}

Un esquema de datos se identifica con su nombre y área de nombres.

Un área de nombres permite agrupar un conjunto de esquemas por área de interés. Por ejemplo, la variable **cus** el área de nombres se utiliza para la configuración específica del cliente (**clientes**).

La clave de identificación de un esquema es una cadena creada con el área de nombres y el nombre separados por dos puntos; por ejemplo: **cus:destinatario**.

>[!IMPORTANT]
>
>El nombre del área de nombres debe ser conciso y contener solo caracteres autorizados de acuerdo con las reglas de nomenclatura XML.
>
>Los identificadores no deben comenzar con caracteres numéricos.
>
>Las siguientes áreas de nombres están reservadas para las descripciones de las entidades del sistema necesarias para el funcionamiento de la aplicación Adobe Campaign y no se deben utilizar: **xtk**, **nl**, **nms**, **ncm**, **temporal**, **ncl**, **crm**, **xxl**.

