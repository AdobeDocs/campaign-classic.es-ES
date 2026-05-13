---
product: campaign
title: Creación del esquema de datos para FDA
description: Aprenda a crear el esquema de datos para FDA
feature: Installation, Instance Settings, Federated Data Access
exl-id: 8702499b-1700-4d1f-a0e0-f7a9dfb4b88f
TQID: https://experienceleague.adobe.com/eC7jDm92g943ymcfEQjaeevS7qzIJWJR0zCtnP2Ny7o
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
subfeature_v2: id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 189
ht-degree: 46%

---

# Creación del esquema de datos {#creating-the-data-schema}



Para crear un esquema en una base de datos externa:

1. Haga clic en el botón **[!UICONTROL New]** sobre la lista de esquemas de datos y elija **[!UICONTROL Access external data]**.

   ![](assets/wf_new_schema_fda.png)

1. Escriba **[!UICONTROL Namespace]** y **[!UICONTROL Name]** para el esquema y seleccione **[!UICONTROL External account]** que habilitará la conexión con la base de datos. Esto permite acceder a la lista de tablas disponibles en la base externa.

   ![](assets/wf_new_schema_select_table_fda.png)

1. En el campo **[!UICONTROL Table name]**, elija la tabla que contiene los datos que se van a recopilar.

   Con Snowflake, puede seleccionar aquí sus vistas si se han concedido los privilegios correctos al usuario de la base de datos. Tenga en cuenta que cuando utilice vistas, Adobe Campaign no podrá generar automáticamente el esquema XML, tendrá que crearlo usted mismo. Para obtener más información, consulte [Documentación de Snowflake](https://docs.snowflake.com/en/user-guide/views-introduction.html).

   ![](assets/wf_new_schema_select_table_fda.png)

1. Haga clic en **[!UICONTROL OK]** para confirmar. Adobe Campaign detecta automáticamente la estructura de la tabla seleccionada y genera el esquema lógico. Tenga en cuenta que Adobe Campaign no genera enlaces.

1. Haga clic en **[!UICONTROL Save]** para confirmar la creación.

   >[!CAUTION]
   >
   >Con Snowflake, es obligatorio usar una clave principal.

   ![](assets/wf_new_schema_generate_fda.png)

Los índices se crean automáticamente al asignar una tabla (asignación estándar o FDA).
