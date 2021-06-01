---
product: campaign
title: Acceso a una base de datos externa
description: Acceso a una base de datos externa
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 8702499b-1700-4d1f-a0e0-f7a9dfb4b88f
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 100%

---

# Creación del esquema de datos {#creating-the-data-schema}

Para crear un esquema en una base de datos externa:

1. Haga clic en el botón **[!UICONTROL New]** sobre la lista de esquemas de datos y elija **[!UICONTROL Access external data]**.

   ![](assets/wf_new_schema_fda.png)

1. Introduzca un nombre y una descripción para el esquema y seleccione la cuenta externa que activa la conexión con la base de datos. Esto permite acceder a la lista de tablas disponibles en la base externa. Seleccione la tabla que contiene los datos que se van a recopilar.

   ![](assets/wf_new_schema_select_table_fda.png)

1. Haga clic en **[!UICONTROL OK]** para confirmar. Adobe Campaign detecta automáticamente la estructura de la tabla seleccionada y genera el esquema lógico. Tenga en cuenta que Adobe Campaign no genera enlaces.

1. Haga clic en **[!UICONTROL Save]** para confirmar la creación.

   >[!CAUTION]
   >
   >Con Snowflake, es obligatorio usar una clave principal.

   ![](assets/wf_new_schema_generate_fda.png)

Los índices se crean automáticamente al asignar una tabla (asignación estándar o FDA).
