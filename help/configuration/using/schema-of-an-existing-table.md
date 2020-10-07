---
title: Esquema de una tabla existente
seo-title: Esquema de una tabla existente
description: Esquema de una tabla existente
seo-description: null
page-status-flag: never-activated
uuid: cb766259-8ed7-40a1-8df7-75a8a3f9986d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 6877d94d-d6e5-4080-a537-ef1bb6e6f8cf
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 12%

---


# Esquema de una tabla existente{#schema-of-an-existing-table}

## Información general {#overview}

Cuando la aplicación necesite acceder a los datos de una tabla existente, una vista SQL o datos de una base de datos remota, cree su esquema en Adobe Campaign con los siguientes datos:

* Nombre de la tabla: introduzca el nombre de la tabla (con su alias cuando se utiliza un dblink) con el atributo &quot;sqltable&quot;,
* Clave de esquema: hacer referencia a los campos de reconciliación,
* índices: se utiliza para generar consultas,
* Los campos y su ubicación en la estructura XML: rellene únicamente los campos utilizados en la aplicación,
* vínculos: si hay uniones con las demás tablas de la base.

## Implementación {#implementation}

Para crear el esquema correspondiente, aplique las siguientes etapas:

1. Edite el **[!UICONTROL Administration>Configuration>Data schemas]** nodo del árbol de Adobe Campaign y haga clic en **[!UICONTROL New]** .
1. Seleccione la **[!UICONTROL Access data from an existing table or an SQL view]** opción y haga clic en **[!UICONTROL Next]** .

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. Elija la tabla o la vista existente:

   ![](assets/s_ncs_configuration_select_table.png)

1. Adapte el contenido de esquema para adaptarlo a sus necesidades.

   ![](assets/s_ncs_configuration_view_create_schema.png)

   El esquema debe rellenarse con el atributo vista=&quot;true&quot; en el elemento `<srcSchema>` raíz para no generar una secuencia de comandos SQL de creación de tabla.

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

La opción **Acceso de datos federado - FDA** le permite acceder a los datos almacenados en una base de datos externa.

La configuración que se debe llevar a cabo en los esquemas para acceder a los datos de una base de datos externa se detalla en [esta página](../../platform/using/creating-data-schema.md).
