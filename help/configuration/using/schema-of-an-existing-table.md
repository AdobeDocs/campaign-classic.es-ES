---
product: campaign
title: Esquema de una tabla existente
description: Esquema de una tabla existente
feature: Custom Resources
role: Developer
exl-id: 964f1027-627c-4f12-91b5-f258e9ba458b
TQID: https://experienceleague.adobe.com/Vi1DhgY8tGIhq1TtMOGKeGMrqFgGecfJQHrKyFXTSgg
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
subfeature_v2: id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 216
ht-degree: 9%

---

# Esquema de una tabla existente{#schema-of-an-existing-table}

## Información general {#overview}

Cuando la aplicación necesite acceder a los datos de una tabla, una vista SQL o datos de una base de datos remota, cree su esquema en Adobe Campaign con los siguientes datos:

* Nombre de la tabla: introduzca el nombre de la tabla (con su alias cuando se utiliza un dblink) con el atributo &quot;sqltable&quot;,
* clave de esquema: haga referencia a los campos de reconciliación,
* índices: utilizados para generar consultas,
* Los campos y su ubicación en la estructura XML: rellene solo los campos utilizados en la aplicación,
* vínculos: si hay vínculos con otras tablas de la base.

## Implementación {#implementation}

Para crear el esquema correspondiente, aplique las siguientes fases:

1. Edite el nodo **[!UICONTROL Administration>Configuration>Data schemas]** del árbol de Adobe Campaign y haga clic en **[!UICONTROL New]**
1. Seleccione la opción **[!UICONTROL Access data from an existing table or an SQL view]** y haga clic en **[!UICONTROL Next]**

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. Elija la tabla o la vista existente:

   ![](assets/s_ncs_configuration_select_table.png)

1. Adapte el contenido del esquema para adaptarlo a sus necesidades.

   ![](assets/s_ncs_configuration_view_create_schema.png)

   El esquema debe rellenarse con el atributo view=&quot;true&quot; en el elemento raíz `<srcSchema>` para no generar un script SQL de creación de tabla.

**Ejemplo** :

```
<srcSchema name="recipient" namespace="cus" view="true">
  <element name="recipient" sqltable="dbsrv.recipient">
    <key name="email">
      <keyfield xpath="@email"/>
    </key>   
    <attribute name="email" type="string" length="80" sqlname="email"/>
  </element>
</srcSchema>
```

## Acceso a una base de datos externa {#accessing-an-external-database}

La opción **Acceso de datos federado - FDA** le da acceso a los datos almacenados en una base de datos externa.

La configuración que se llevará a cabo en los esquemas para acceder a los datos de una base de datos externa se detalla en [esta página](../../installation/using/creating-data-schema.md).
