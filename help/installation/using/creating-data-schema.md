---
product: campaign
title: Acceso a una base de datos externa
description: Acceso a una base de datos externa
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 8702499b-1700-4d1f-a0e0-f7a9dfb4b88f
source-git-commit: d2d0ff575edbee18febb5ec895fcec1e0ae34de7
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 52%

---

# Creación del esquema de datos {#creating-the-data-schema}

![](../../assets/v7-only.svg)

Para crear un esquema en una base de datos externa:

1. Haga clic en el botón **[!UICONTROL New]** sobre la lista de esquemas de datos y elija **[!UICONTROL Access external data]**.

   ![](assets/wf_new_schema_fda.png)

1. Escriba un **[!UICONTROL Namespace]** y  **[!UICONTROL Name]** para el esquema y seleccione el **[!UICONTROL External account]** que habilitará la conexión a la base de datos. Esto permite acceder a la lista de tablas disponibles en la base externa.

   ![](assets/wf_new_schema_select_table_fda.png)

1. En el **[!UICONTROL Table name]** , seleccione la tabla que contiene los datos que se van a recopilar.

   Con Snowflake, puede seleccionar aquí sus vistas si al usuario de la base de datos se le han otorgado los privilegios correctos. Tenga en cuenta que al utilizar las vistas, Adobe Campaign no podrá generar automáticamente el esquema XML, por lo que deberá crearlo usted mismo. Para obtener más información sobre las vistas, consulte [documentación del Snowflake](https://docs.snowflake.com/en/user-guide/views-introduction.html).

   ![](assets/wf_new_schema_select_table_fda.png)

1. Haga clic en **[!UICONTROL OK]** para confirmar. Adobe Campaign detecta automáticamente la estructura de la tabla seleccionada y genera el esquema lógico. Tenga en cuenta que Adobe Campaign no genera enlaces.

1. Haga clic en **[!UICONTROL Save]** para confirmar la creación.

   >[!CAUTION]
   >
   >Con Snowflake, es obligatorio usar una clave principal.

   ![](assets/wf_new_schema_generate_fda.png)

Los índices se crean automáticamente al asignar una tabla (asignación estándar o FDA).
