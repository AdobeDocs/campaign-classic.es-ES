---
solution: Campaign Classic
product: campaign
title: Actualización de listas
description: Actualización de listas
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 49f3c123cb8e91b3a2a2a1eb6bd593a242b8bbfe
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 100%

---


# Actualización de listas{#list-update}

Una actividad **List update** almacena la población especificada en la transición a una lista de destinatarios.

![](assets/s_user_segmentation_update_group.png)

La lista se puede seleccionar de la lista de grupos existentes.

También se puede crear con las opciones **[!UICONTROL Create the list if necessary (Computed name)]** y **[!UICONTROL Create the list if necessary (Computed Folder and Name)]**. Estas opciones permiten seleccionar la etiqueta que desee para crear una lista y, posteriormente, la carpeta en la que se guardará. La etiqueta también se puede generar automáticamente insertando campos dinámicos o un script. Los distintos campos dinámicos están disponibles en el menú desplegable situado a la derecha de la etiqueta.

![](assets/s_user_segmentation_update_list_calc.png)

Si la lista ya existe, los destinatarios se añaden al contenido existente, a no ser que marque la opción **[!UICONTROL Purge the list if it exists (otherwise add to the list)]**. En este caso, el contenido de la lista se elimina antes de la actualización.

Si desea que la lista creada o actualizada utilice una lista distinta a la del destinatario, marque la opción **[!UICONTROL Create or use a list with its own table]**.

Para utilizar la opción, dichas tablas específicas deben haberse configurado en el entorno de Adobe Campaign.

Por lo general, guardar un destino en una lista indica el final de un flujo de trabajo. De forma predeterminada, la actividad **[!UICONTROL List update]** no tiene una transición saliente. Marque la opción **[!UICONTROL Generate an outbound transition]** para agregar una.

![](assets/do-not-localize/how-to-video.png) [Descubra cómo crear una lista de destinatarios desde el Explorador con este vídeo](#video)

## Ejemplo: Actualización de lista {#example--list-update}

En el ejemplo siguiente, la actividad de actualización de la lista sigue una consulta destinada a los hombres de más de 30 años que viven en Francia. La lista se creará inicialmente a partir de los resultados de la consulta. A continuación, se actualizará cada vez que se inicie desde el flujo de trabajo. Por ejemplo, se puede utilizar con regularidad para ofertas promocionales de objetivos para campañas.

1. Añada una **[!UICONTROL list update activity]** directamente después de una consulta para abrirla y editarla.

   Para obtener más información sobre la creación de una consulta en el flujo de trabajo, consulte [Consulta](../../workflow/using/query.md).

1. Puede seleccionar una etiqueta para la actividad.
1. Seleccione la opción **[!UICONTROL Create the list if necessary (Calculated name)]** para mostrar que la lista se cree una vez que se haya ejecutado el primer flujo de trabajo y se haya actualizado con las siguientes ejecuciones.
1. Seleccione la carpeta en la que desea guardar la lista.
1. Introduzca una etiqueta para la lista. Puede insertar campos dinámicos para generar automáticamente el nombre de la lista. En este ejemplo, la lista tiene el mismo nombre que la consulta para identificar fácilmente su contenido.
1. Deje activada la opción **[!UICONTROL Purge the list if it exists (otherwise add to the list)]** para eliminar destinatarios que no coincidan con los criterios de direccionamiento y para insertar los nuevos en la lista.
1. También deje la opción **[!UICONTROL Create or use a list with its own table]** marcada.
1. Deje la opción **[!UICONTROL Generate an outbound transition]** sin marcar.
1. Haga clic en **[!UICONTROL Ok]** y comience el flujo de trabajo.

   ![](assets/s_user_segmentation_update_list_calc_example.png)

   A continuación, se crea o actualiza la lista de destinatarios coincidentes.

## Parámetros de entrada {#input-parameters}

* tableName
* esquema

Identifique la población que se va a guardar en el grupo.

## Parámetros de salida {#output-parameters}

* groupId: Identificador de grupo.

## Videotutorial {#video}

Este vídeo muestra cómo crear una lista de destinatarios desde el Explorador.

>[!VIDEO](https://video.tv.adobe.com/v/25602/quality=12)

Hay disponibles más vídeos de procedimientos para Campaign Classic [aquí](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=es).
