---
product: campaign
title: Explicación de la estructura de esquemas en Adobe Campaign
description: Estructura del esquema
feature: Custom Resources
role: Developer
audience: configuration
content-type: reference
level: Intermediate, Experienced
topic-tags: schema-reference
exl-id: 3405efb8-a37c-4622-a271-63d7a4148751
TQID: 'https://experienceleague.adobe.com/dFZ38qRKX-4vTEYS9GosS5TdW-XhnoIq8ckbjnNEJmo'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
    internal-label: PI
  - id: a2002dba-5e37-4dff-8e04-1cc3ec73558c
    internal-label: Custom resources
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: a97306b73a2b577841e6f24536c62b2526e9fda9
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 21%
---
# Comprender la estructura de esquema {#schema-structure}

En esta página se muestra cómo se asignan los tipos de datos de Adobe Campaign a los tipos de datos de cada sistema de administración de bases de datos.

Como parte de la transición de Campaign v7 a v8, el conjunto de documentación de Campaign Classic se ha optimizado y reorganizado. Ahora, las funciones comunes solo están disponibles en el conjunto de documentación de Campaign v8. Para obtener más información sobre la estructura de esquemas, consulte la [documentación de Campaign v8](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/developer/schemas-forms/schema-structure){target=_blank}.

[![imagen](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/developer/schemas-forms/schema-structure){target=_blank}

## Asignación de los tipos de datos de Adobe Campaign/DBMS {#mapping-the-types-of-adobe-campaign-dbms-data}

En la tabla siguiente se enumeran las asignaciones para los tipos de datos generados por Adobe Campaign para los distintos sistemas de administración de bases de datos.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Campaign</strong><br /> </td> 
   <td> <strong>PosgreSQL</strong><br /> </td> 
   <td> <strong>Oracle</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Cadena<br /> </td> 
   <td> VARCHAR(255)<br /> </td> 
   <td> VARCHAR2 (NVARCHAR2 si es Unicode)<br /> </td> 
  </tr> 
  <tr> 
   <td> Booleano<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMBER(3)<br /> </td> 
  </tr> 
  <tr> 
   <td> Byte<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMBER(3)<br /> </td> 
  </tr> 
  <tr> 
   <td> Corto<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMBER(5)<br /> </td> 
  </tr> 
  <tr> 
   <td> Doble<br /> </td> 
   <td> PRECISIÓN DOBLE<br /> </td> 
   <td> FLOTANTE<br /> </td> 
  </tr> 
  <tr> 
   <td> Long<br /> </td> 
   <td> ENTERO<br /> </td> 
   <td> NUMBER(10)<br /> </td> 
  </tr> 
  <tr> 
   <td> Int64<br /> </td> 
   <td> BIGINT<br /> </td> 
   <td> NUMBER(20)<br /> </td> 
  </tr> 
  <tr> 
   <td> Fecha<br /> </td> 
   <td> FECHA<br /> </td> 
   <td> FECHA<br /> </td> 
  </tr> 
  <tr> 
   <td> Hora<br /> </td> 
   <td> HORA<br /> </td> 
   <td> FLOTANTE<br /> </td> 
  </tr> 
  <tr> 
   <td> Datetime<br /> </td> 
   <td> MARCA DE TIEMPO <br /> </td> 
   <td> FECHA<br /> </td> 
  </tr> 
  <tr> 
   <td> Datetimenotz<br /> </td> 
   <td> MARCA DE TIEMPO <br /> </td> 
   <td> FECHA<br /> </td> 
  </tr> 
  <tr> 
   <td> Duración <br /> </td> 
   <td> PRECISIÓN DOBLE<br /> </td> 
   <td> FLOTANTE<br /> </td> 
  </tr> 
  <tr> 
   <td> Nota<br /> </td> 
   <td> TEXTO<br /> </td> 
   <td> CLOB (NCLOB si es Unicode)<br /> </td> 
  </tr> 
  <tr> 
   <td> Blob <br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Más información

Examine los siguientes vínculos para obtener más información:

* [Introducción a los esquemas](about-schema-reference.md)
* [Asignación de base de datos](database-mapping.md)
* [Administración de vínculos](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/developer/schemas-forms/database-links){target="_blank"} (documentación de Campaign v8)
* [Administración de claves](database-keys.md)
