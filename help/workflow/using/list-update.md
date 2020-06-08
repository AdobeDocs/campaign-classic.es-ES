---
title: Actualización de listas
seo-title: Actualización de listas
description: Actualización de listas
seo-description: null
page-status-flag: never-activated
uuid: 1446f115-3f64-4b95-8e04-6426ab1b8dab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: ca2cd5bf-78a2-4e43-955d-206f4474d1e0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b1a961822224ab0a9551f51942a5f94cf201c8ee
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 75%

---


# Actualización de listas{#list-update}

Una actividad **List update** almacena la población especificada en la transición a una lista de destinatarios.

![](assets/s_user_segmentation_update_group.png)

La lista se puede seleccionar de la lista de grupos existentes.

También se puede crear con las opciones **[!UICONTROL Create the list if necessary (Computed name)]** y **[!UICONTROL Create the list if necessary (Computed Folder and Name)]** . Estas opciones permiten seleccionar la etiqueta que desee para crear una lista y, posteriormente, la carpeta en la que se guardará. La etiqueta también se puede generar automáticamente insertando campos dinámicos o un script. Los distintos campos dinámicos están disponibles en el menú desplegable situado a la derecha de la etiqueta.

![](assets/s_user_segmentation_update_list_calc.png)

If the list already exists, recipients will be added to the existing content, unless you check the **[!UICONTROL Purge the list if it exists (otherwise add to the list)]** option. En este caso, el contenido de la lista se elimina antes de la actualización.

If you want the created or updated list to use a table other than the recipient table then check the **[!UICONTROL Create or use a list with its own table]** option.

Para utilizar la opción, dichas tablas específicas deben haberse configurado en el entorno de Adobe Campaign.

Por lo general, guardar un destino en una lista indica el final de un flujo de trabajo. De forma predeterminada, la actividad **[!UICONTROL List update]** no tiene una transición saliente. Check the **[!UICONTROL Generate an outbound transition]** option to add one.

## Ejemplo: Actualización de lista {#example--list-update}

En el ejemplo siguiente, la actividad de actualización de la lista sigue una consulta destinada a los hombres de más de 30 años que viven en Francia. La lista se creará inicialmente a partir de los resultados de la consulta. A continuación, se actualizará cada vez que se inicie desde el flujo de trabajo. Por ejemplo, se puede utilizar con regularidad para ofertas promocionales de objetivos para campañas.

1. Añada una **[!UICONTROL list update activity]** directamente después de una consulta para abrirla y editarla.

   Para obtener más información sobre la creación de una consulta en el flujo de trabajo, consulte [Consulta](../../workflow/using/query.md).

1. Puede seleccionar una etiqueta para la actividad.
1. Select the **[!UICONTROL Create the list if necessary (Calculated name)]** option to show that the list will be created once the first workflow has been executed, then updated with the following executions.
1. Seleccione la carpeta en la que desea guardar la lista.
1. Introduzca una etiqueta para la lista. Puede insertar campos dinámicos para generar automáticamente el nombre de la lista. En este ejemplo, la lista tiene el mismo nombre que la consulta para identificar fácilmente su contenido.
1. Leave the **[!UICONTROL Purge the list if it exists (otherwise add to the list)]** option checked to delete recipients that do not match the targeting criteria and to insert the new ones into the list.
1. También deje la **[!UICONTROL Create or use a list with its own table]** opción marcada.
1. Leave the **[!UICONTROL Generate an outbound transition]** option unchecked.
1. Haga clic en **[!UICONTROL Ok]** y comience el flujo de trabajo.

   ![](assets/s_user_segmentation_update_list_calc_example.png)

   A continuación, se crea o actualiza la lista de destinatarios coincidentes.

Para obtener más información sobre esto, consulte el vídeo [Creación de una lista de destinatarios](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html).

## Parámetros de entrada {#input-parameters}

* tableName
* esquema

Identifique la población que se va a guardar en el grupo.

## Parámetros de salida {#output-parameters}

* groupId: Identificador de grupo.
