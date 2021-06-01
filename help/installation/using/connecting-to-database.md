---
product: campaign
title: Acceso a una base de datos externa
description: Obtenga información sobre cómo conectarse a una base de datos externa
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 240d7e11-da3a-4d64-8986-1f1c8ebcea3c
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 98%

---

# Conexión a la base de datos {#connecting-to-the-database}

Para activar una conexión con la base de datos externa, debe indicar los parámetros de conexión, es decir, el origen de datos objetivo y el nombre de la tabla con los datos que sea necesario cargar.

>[!CAUTION]
>
>El usuario de Adobe Campaign necesita derechos específicos para la base de datos externa y el servidor de aplicaciones de Adobe Campaign para procesar datos desde una base de datos externa. Para obtener más información sobre esto, consulte la sección Derechos [de acceso a bases de datos remotas](../../installation/using/remote-database-access-rights.md).
>
>Para evitar errores de funcionamiento, los operadores que accedan a datos compartidos remotos deben trabajar desde espacios independientes.

## Creación de una conexión compartida {#creating-a-shared-connection}

Para activar una conexión con una base de datos externa compartida, siempre y cuando esta conexión esté activa, se puede acceder a la base de datos a través de Adobe Campaign.

1. La configuración se debe definir previamente a través del nodo **[!UICONTROL Administration > Platform > External accounts]** node.
1. Haga clic en el botón **[!UICONTROL New]** y seleccione el tipo **[!UICONTROL External database]**.
1. Defina los parámetros de **[!UICONTROL Connection]** de la base de datos externa.

   Para conexiones con una base de datos de tipo **ODBC**, el campo **[!UICONTROL Server]** debe contener el nombre del origen de datos ODBC y no el nombre del servidor. Además, pueden ser necesarias determinadas configuraciones adicionales según las bases de datos utilizadas. Consulte la sección [Configuraciones específicas por tipo de base de datos](../../installation/using/configure-fda.md).

1. Una vez introducidos los parámetros, haga clic en el botón **[!UICONTROL Test the connection]** para aprobarlos.

   ![](assets/wf-external-account-create.png)

1. Si es necesario, desactive la opción **[!UICONTROL Enabled]** para deshabilitar el acceso a esta base de datos sin eliminar su configuración.
1. Para permitir que Adobe Campaign acceda a esta base de datos, debe implementar las funciones SQL. Hacer clic en la pestaña **[!UICONTROL Parameters]** y luego en el botón **[!UICONTROL Deploy functions]**.

   ![](assets/wf-external-account-functions.png)

Puede definir espacios de trabajo específicos para las tablas y para el índice en la pestaña **[!UICONTROL Parameters]**.

## Creación de una conexión temporal {#creating-a-temporary-connection}

Puede definir directamente una conexión con una base de datos externa desde las actividades de flujo de trabajo. En este caso, se trata de una base de datos externa local, reservada para utilizarse dentro de un flujo de trabajo actual: no se guarda en las cuentas externas. Este tipo de conexión puntual se puede crear en distintas actividades del flujo de trabajo, especialmente **[!UICONTROL Query]**, **[!UICONTROL Data loading (RDBMS)]**, la actividad de **[!UICONTROL Enrichment]** o la actividad de **[!UICONTROL Split]**.

>[!CAUTION]
>
>No se recomienda este tipo de configuración, pero puede utilizarse periódicamente para recopilar datos. Sin embargo, debe crear una cuenta externa, como se muestra en la sección [Creación de una conexión compartida](#creating-a-shared-connection).

Por ejemplo, en la actividad de consulta, los pasos para crear una conexión periódica con una base de datos externa son los siguientes:

1. Hacer clic en **[!UICONTROL Add data...]** y seleccione las opciones de **[!UICONTROL External data]**.
1. Seleccione la opción **[!UICONTROL Locally defining the data source]**.

   ![](assets/wf_add_data_local_external_data.png)

1. Seleccionar el motor de base de datos de objetivo en la lista desplegable. Introducir el nombre del servidor y especificar los parámetros de autenticación.

   Especificar también el nombre de la base de datos externa.

   ![](assets/wf_add_data_local_external_data_param.png)

   Haga clic en el botón **[!UICONTROL Next]**.

1. Seleccionar la tabla en la que se almacenan los datos.

   Puede introducir el nombre de la tabla directamente en el campo correspondiente o hacer clic en el icono de edición para acceder a la lista de las tablas de la base de datos.

   ![](assets/wf_add_data_local_external_data_select_table.png)

1. Hacer clic en el botón **[!UICONTROL Add]** para definir uno o varios campos de reconciliación entre los datos de la base de datos externa y los datos de la base de datos de Adobe Campaign. Los iconos **[!UICONTROL Edit expression]** del **[!UICONTROL Remote field]** y el **[!UICONTROL Local field]** le proporcionan acceso a la lista de campos de cada una de las tablas.

   ![](assets/wf_add_data_local_external_data_join.png)

1. Si es necesario, especifique una condición de filtrado y el modo de clasificación de datos.
1. Seleccione los datos adicionales que se recopilarán en la base de datos externa. Para ello, haga doble clic en los campos que desea añadir para mostrarlos en las **[!UICONTROL Output columns]**.

   ![](assets/wf_add_data_local_external_data_select.png)

   Hacer clic en **[!UICONTROL Finish]** para confirmar esta configuración.

## Conexión segura {#secure-connection}

>[!NOTE]
>
>La conexión segura solo está disponible para PostgreSQL.

Puede proteger el acceso a una base de datos externa al configurar una cuenta externa de FDA.

Para ello, añada “**:ssl**” después de la dirección del servidor y dirección del puerto utilizado. Por ejemplo: **192.168.0.52:4501:ssl**.

A continuación, los datos se envían mediante el protocolo SSL seguro.

## Configuraciones adicionales {#additional-configurations}

Si es necesario, puede crear el esquema para procesar datos en una base de datos externa. Del mismo modo, Adobe Campaign permite definir la asignación en los datos de una tabla externa. Estas configuraciones son generales y no se aplican exclusivamente a flujos de trabajo.

>[!NOTE]
>
>Para obtener más información sobre la creación de esquemas en Adobe Campaign y la definición de una nueva asignación de datos, consulte [esta página](../../configuration/using/about-schema-edition.md).
