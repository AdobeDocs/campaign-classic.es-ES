---
product: campaign
title: Actualización de la estructura de la base de datos
description: Actualización de la estructura de la base de datos
feature: Configuration
role: Data Engineer, Developer
exl-id: 6c1e061b-8636-4285-8d83-97474544d252
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 8%

---

# Actualización de la estructura de la base de datos{#updating-the-database-structure}



Para aplicar las modificaciones realizadas a los esquemas, inicie el asistente de actualización de bases de datos. Se puede acceder a este asistente a través de **[!UICONTROL Tools > Advanced > Update database structure]** Comprueba si la estructura física de la base de datos coincide con su descripción lógica y ejecuta los scripts de actualización de SQL.

![](assets/d_ncs_integration_schema_update.png)

Los módulos de la base de datos se rellenan y activan automáticamente.

![](assets/d_ncs_integration_schema_update_select.png)

Las opciones **[!UICONTROL Add stored procedures]** y **[!UICONTROL Import initialization data]** se utilizan para iniciar los scripts SQL iniciales y los paquetes de datos que se ejecutan cuando se crea la base de datos.

Puede importar un conjunto de datos desde un paquete de datos externo. Para ello, seleccione **[!UICONTROL Import a package]** e introduzca el archivo XML del paquete.

Siga los pasos y vea el script SQL de actualización de la base de datos:

![](assets/d_ncs_integration_schema_update2.png)

>[!NOTE]
>
>Se encuentra en un campo de edición y se puede modificar para eliminar o agregar código SQL.

A continuación, inicie la actualización de la base de datos:

![](assets/d_ncs_integration_schema_update3.png)
