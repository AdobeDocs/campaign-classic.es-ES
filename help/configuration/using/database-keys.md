---
product: campaign
title: Administración de claves en esquemas de datos
description: Comprensión de la administración de claves en esquemas de datos
feature: Configuration, Instance Settings
role: Developer
exl-id: faf63c8f-9d10-43c1-a990-91361594af9f
TQID: 'https://experienceleague.adobe.com/dErbfzRabMls-5x1S3eRZO94Kqcz9LRh3PaUhVD5zAU'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
    internal-label: Schema extension
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
    internal-label: PI
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: a97306b73a2b577841e6f24536c62b2526e9fda9
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 11%
---
# Administración de claves en esquemas {#management-of-keys}

Cada tabla asociada con un esquema de datos debe tener al menos una clave para identificar un registro de una tabla. En esta página se describe la clave de incremento automático utilizada en las tablas de Campaign Classic v7.

Como parte de la transición de Campaign v7 a v8, el conjunto de documentación de Campaign Classic se ha optimizado y reorganizado. Ahora, las funciones comunes solo están disponibles en el conjunto de documentación de Campaign v8. Para obtener más información acerca de la administración de claves, consulte la [documentación de Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/database-keys){target=_blank}.

[![imagen](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/database-keys){target=_blank}

## Clave de incremento automático {#auto-incremental-key}

La clave principal de la mayoría de las tablas de Adobe Campaign es un entero de 32 bits generado automáticamente por el motor de la base de datos. El cálculo del valor de clave depende de una secuencia (de forma predeterminada, la función SQL **XtkNewId**) que genere un número único en toda la base de datos. El contenido de la clave se introduce automáticamente al insertar el registro.

La ventaja de una clave incremental es que proporciona una clave técnica no modificable para las uniones entre tablas. Además, esta clave no ocupa mucha memoria porque utiliza un entero de doble byte.

Puede especificar en el esquema de origen el nombre de la secuencia que se va a utilizar con el atributo **pkSequence**. Si este atributo no se proporciona en el esquema de origen, se utilizará la secuencia predeterminada **XtkNewId**. La aplicación usa secuencias dedicadas para los esquemas **nms:broadLog** y **nms:trackingLog** (**NmsBroadLogId** y **NmsTrackingLogId** respectivamente) porque estas son las tablas que contienen la mayor cantidad de registros.

A partir de la versión 18.10 de ACC, **XtkNewId** ya no es el valor predeterminado para la secuencia en los esquemas predeterminados. Ahora puede crear un esquema o ampliar el esquema existente con una secuencia dedicada.

>[!IMPORTANT]
>
>Al crear un nuevo esquema o durante una extensión de esquema, se debe mantener el mismo valor de secuencia de clave principal (@pkSequence) para todo el conjunto.

Una secuencia a la que se hace referencia en un esquema de Adobe Campaign (**NmsTrackingLogId**, por ejemplo) debe asociarse con una función SQL que devuelva el número de ID en los parámetros, separados por comas. Esta función debe llamarse **GetNew** XXX **Ids**, donde **XXX** es el nombre de la secuencia (**GetNewNmsTrackingLogIds**, por ejemplo). Vea los archivos **postgres-nms.sql**, **mssql-nms.sql** o **oracle-nms.sql** proporcionados con la aplicación en el directorio **datakit/nms/eng/sql/** para recuperar el ejemplo de creación de secuencia &#39;NmsTrackingLogId&#39; para cada motor de base de datos.

Para declarar una clave única, rellene el atributo **autopk** (con el valor &quot;true&quot;) en el elemento principal del esquema de datos.

**Ejemplo**:

Declarar una clave incremental en el esquema de origen:

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient" autopk="true">
  ...
  </element>
</srcSchema>
```

El esquema generado:

```sql
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" autopk="true" pkSequence="XtkNewId" sqltable="CusRecipient"> 
    <dbindex name="id" unique="true">
      <keyfield xpath="@id"/>
    </dbindex>

    <key internal="true" name="id">
      <keyfield xpath="@id"/>
    </key>

    <attribute desc="Internal primary key" label="Primary key" name="id" sqlname="iRecipientId" type="long"/>
  </element>
</schema>
```

Además de la definición de la clave y su índice, se ha añadido un campo numérico llamado &quot;id&quot; al esquema ampliado para contener la clave principal generada automáticamente.

>[!IMPORTANT]
>
>Al crear la tabla, se inserta automáticamente un registro con una clave principal establecida en 0. Este registro se utiliza para evitar las uniones externas, que no son efectivas en las tablas de volumen. De forma predeterminada, todas las claves externas se inicializan con el valor 0, de modo que siempre se pueda devolver un resultado en la unión cuando el elemento de datos no se rellena.


## Más información

Examine los siguientes vínculos para obtener más información:

* [Introducción a los esquemas](about-schema-reference.md)
* [Estructura del esquema](schema-structure.md)
* [Asignación de base de datos](database-mapping.md)
* [Administración de vínculos](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/database-links){target="_blank"} (documentación de Campaign v8)
* [Modelo de datos de Campaign](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/datamodel){target="_blank"} (documentación de Campaign v8)
