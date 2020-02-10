---
title: Actualización de la estructura de la base de datos
seo-title: Actualización de la estructura de la base de datos
description: Actualización de la estructura de la base de datos
seo-description: null
page-status-flag: never-activated
uuid: 084dcc7b-f890-4dff-a322-c9a8f1d614b8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: b82ae459-30b5-4a1c-91cc-5c7b8f128333
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Actualización de la estructura de la base de datos{#updating-the-database-structure}

Para aplicar las modificaciones realizadas en los esquemas, inicie el asistente para la actualización de la base de datos. Se puede acceder a este asistente mediante **[!UICONTROL Tools > Advanced > Update database structure]** . Comprueba si la estructura física de la base de datos coincide con su descripción lógica y ejecuta las secuencias de comandos de actualización SQL.

![](assets/d_ncs_integration_schema_update.png)

Los módulos de la base de datos se rellenan y activan automáticamente.

![](assets/d_ncs_integration_schema_update_select.png)

Las opciones **[!UICONTROL Add stored procedures]** y **[!UICONTROL Import initialization data]** se utilizan para iniciar las secuencias de comandos SQL iniciales y los paquetes de datos ejecutados al crear la base de datos.

Puede importar un conjunto de datos desde un paquete de datos externo. Para ello, seleccione **[!UICONTROL Import a package]** e introduzca el archivo XML del paquete.

Siga los pasos y vea el script SQL de actualización de la base de datos:

![](assets/d_ncs_integration_schema_update2.png)

>[!NOTE]
>
>Esto se encuentra en un campo de edición y se puede modificar para eliminar o agregar código SQL.

A continuación, inicie la actualización de la base de datos:

![](assets/d_ncs_integration_schema_update3.png)

