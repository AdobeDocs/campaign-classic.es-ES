---
product: campaign
title: Creación del esquema de datos para FDA
description: Aprenda a crear el esquema de datos para FDA
feature: Installation, Instance Settings, Federated Data Access
exl-id: 8702499b-1700-4d1f-a0e0-f7a9dfb4b88f
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 47%

---

# Creación del esquema de datos {#creating-the-data-schema}



Para crear un esquema en una base de datos externa:

1. Haga clic en el botón **[!UICONTROL New]** sobre la lista de esquemas de datos y elija **[!UICONTROL Access external data]**.

   ![](assets/wf_new_schema_fda.png)

1. Introduzca una **[!UICONTROL Namespace]** y  **[!UICONTROL Name]** para el esquema y seleccione la **[!UICONTROL External account]** que habilitará la conexión con la base de datos. Esto permite acceder a la lista de tablas disponibles en la base externa.

   ![](assets/wf_new_schema_select_table_fda.png)

1. Desde el **[!UICONTROL Table name]** , seleccione la tabla que contiene los datos que se van a recopilar.

   Con Snowflake, puede seleccionar aquí sus vistas si se han concedido los privilegios correctos al usuario de la base de datos. Tenga en cuenta que cuando utilice vistas, Adobe Campaign no podrá generar automáticamente el esquema XML, tendrá que crearlo usted mismo. Para obtener más información, consulte [Documentación del Snowflake](https://docs.snowflake.com/en/user-guide/views-introduction.html).

   ![](assets/wf_new_schema_select_table_fda.png)

1. Haga clic en **[!UICONTROL OK]** para confirmar. Adobe Campaign detecta automáticamente la estructura de la tabla seleccionada y genera el esquema lógico. Tenga en cuenta que Adobe Campaign no genera enlaces.

1. Haga clic en **[!UICONTROL Save]** para confirmar la creación.

   >[!CAUTION]
   >
   >Con Snowflake, es obligatorio usar una clave principal.

   ![](assets/wf_new_schema_generate_fda.png)

Los índices se crean automáticamente al asignar una tabla (asignación estándar o FDA).
