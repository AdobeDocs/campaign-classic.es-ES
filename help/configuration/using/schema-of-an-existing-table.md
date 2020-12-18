---
solution: Campaign Classic
product: campaign
title: Esquema de una tabla existente
description: Esquema de una tabla existente
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '216'
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

1. Edite el nodo **[!UICONTROL Administration>Configuration>Data schemas]** del árbol de Adobe Campaign y haga clic en **[!UICONTROL New]** .
1. Seleccione la opción **[!UICONTROL Access data from an existing table or an SQL view]** y haga clic en **[!UICONTROL Next]** .

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. Elija la tabla o la vista existente:

   ![](assets/s_ncs_configuration_select_table.png)

1. Adapte el contenido de esquema para adaptarlo a sus necesidades.

   ![](assets/s_ncs_configuration_view_create_schema.png)

   El esquema debe rellenarse con el atributo vista=&quot;true&quot; en el elemento raíz `<srcSchema>` para no generar una secuencia de comandos SQL de creación de tabla.

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

La configuración que se debe llevar a cabo en los esquemas para acceder a los datos de una base de datos externa se detalla en [esta página](../../installation/using/creating-data-schema.md).
