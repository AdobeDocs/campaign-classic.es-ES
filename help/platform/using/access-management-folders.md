---
product: campaign
title: Administración del acceso a las carpetas de Campaign
description: Obtenga información sobre cómo conceder acceso a carpetas de Campaign y crear vistas
badge: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
feature: Application Settings, Permissions
role: User, Admin
level: Beginner
exl-id: 0ba8a3d0-36d7-42f3-b281-0255e49b5fa3
hide: true
hidefromtoc: true
source-git-commit: 354fc8fd5d030ed88e2b279ba1dd3eaf2f314d53
workflow-type: ht
source-wordcount: '517'
ht-degree: 100%

---

# Administración del acceso a las carpetas{#folder-access-management}



Cada carpeta del árbol de navegación de Explorer tiene asociados derechos de acceso de lectura, escritura y eliminación. Para acceder a un archivo, un operador o grupo de operadores debe tener al menos acceso de lectura.

>[!NOTE]
>
>Para obtener más información sobre permisos en carpetas, consulte la [documentación de la versión 8 de Campaign](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/admin/permissions/folder-permissions){target=_blank}.


## Carpetas y vistas {#folders-and-views}

### ¿Qué es una carpeta? {#about-folders}

Las carpetas son nodos del árbol de Adobe Campaign. Estos nodos se crean haciendo clic con el botón derecho en el árbol, a través del menú **[!UICONTROL Add new folder]**. De forma predeterminada, el primer menú permite añadir la carpeta correspondiente al contexto actual.

![](assets/s_ncs_user_add_folder_in_tree.png)

Puede personalizar el árbol de navegación de Explorer. Conozca los pasos de configuración y las prácticas recomendadas [en esta sección](adobe-campaign-workspace.md).

### ¿Qué es una vista? {#about-views}

Además, puede crear vistas para restringir el acceso a los datos y organizar el contenido del árbol para adaptarlo a sus necesidades. A continuación, puede asignar derechos a las vistas.

Una vista es una carpeta que muestra registros almacenados físicamente en una o más carpetas del mismo tipo. Por ejemplo, si se crea una carpeta de campañas que sea una vista, esta muestra todas las campañas contenidas en la base de datos de manera predeterminada, independientemente de su origen. Estos datos se pueden filtrar.

Cuando se convierte una carpeta en una vista, todos los datos correspondientes al tipo de carpeta presentes en la base de datos se muestran en la vista, independientemente de la carpeta en la que se guarde. A continuación, puede filtrarlos para restringir la lista de datos mostrados.

>[!IMPORTANT]
>
>Las vistas contienen datos y permiten el acceso a ellos, pero los datos no se almacenan físicamente en la carpeta de vista. El operador debe tener los derechos adecuados para la acción deseada en las carpetas de origen de los datos (acceso de lectura, como mínimo).
>
>Para conceder acceso a una vista sin conceder acceso a la carpeta de origen, no asigne acceso de lectura al nodo principal de la carpeta de origen.

Para distinguir vistas de carpetas, el nombre de cada vista se muestra en un color diferente (cian oscuro).

![](assets/s_ncs_user_view_name_color.png)

### Adición de carpetas y creación de vistas {#adding-folders-and-creating-views}

>[!IMPORTANT]
>
>Las carpetas predeterminadas no deben marcarse como vistas.


En el ejemplo siguiente, se muestra cómo crear nuevas carpetas para mostrar datos específicos:

1. Cree una nueva carpeta **[!UICONTROL Deliveries]** y asígnele el nombre **entregas Francia**.
1. Haga clic con el botón derecho en esta carpeta y seleccione **[!UICONTROL Properties...]**.

   ![Captura de pantalla que muestra un clic con el botón derecho en las propiedades](assets/s_ncs_user_add_folder_exple.png)

1. En la pestaña **[!UICONTROL Restriction]**, seleccione **[!UICONTROL This folder is a view]**. Eso hace que se muestren todos los envíos de la base de datos.

   ![Pantalla que muestra la selección de la casilla de vista](assets/s_ncs_user_add_folder_exple01.png)

1. Defina los criterios del filtro de entregas desde el editor de consultas en la sección central de la ventana: esto muestra las campañas correspondientes al filtro definido.

   >[!NOTE]
   >
   >El editor de consultas se muestra en [esta sección](../../platform/using/adobe-campaign-workspace.md#about-queries-in-campaign).

   Con las siguientes condiciones de filtro:

![Captura de pantalla que muestra las diferentes condiciones de filtro](assets/s_ncs_user_add_folder_exple00.png)

Los siguientes envíos se muestran en la vista:

![](assets/s_ncs_user_add_folder_exple02.png)

>[!NOTE]
>
>Al administrar eventos [de mensajería transaccional](../../message-center/using/about-transactional-messaging.md), las carpetas **[!UICONTROL Real time events]** o **[!UICONTROL Batch events]** no deben configurarse como vistas en las instancias de ejecución, ya que esto podría generar problemas de derechos de acceso. Para obtener más información sobre la colección de eventos, consulte [esta sección](../../message-center/using/about-event-processing.md#event-collection).

<!--
## Permissions on a folder

### Edit permissions on a folder {#edit-permissions-on-a-folder}

To edit permissions on a specific folder of the tree, follow the steps below:

1. Right-click on the folder and select **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_folder_properties.png)

1. Click the **[!UICONTROL Security]** tab to view authorizations on this folder.

   ![](assets/s_ncs_user_folder_properties_security.png)

### Modify permissions {#modify-permissions}

To modify permissions, you can:

* **Replace a group or an operator**. To do this, click one of the groups (or operators) with rights to the folder, and select a new group (or a new operator) from the drop-down list:

  ![](assets/s_ncs_user_folder_properties_security02.png)

* **Authorize a group or an operator**. To do this, click the **[!UICONTROL Add]** button and select the group or operator to which you want to assign authorizations for this folder.
* **Forbid a group or an operator**. To do this, click **[!UICONTROL Delete]** and select the group or operator from which you want to remove authorization for this folder.
* **Select the rights assigned to a group or an operator**. To do this, click the group or operator concerned, then select the access rights you want to grant and deselect the others.

  ![](assets/s_ncs_user_folder_properties_security03.png)

### Propagate permissions {#propagate-permissions}

You can propagate authorizations and access rights. To do this, select the **[!UICONTROL Propagate]** option in the folder properties.

The authorizations defined in this window will then be applied to all the sub-folders of the current node. You can then overload these authorizations for each of the sub-folders.

>[!NOTE]
>
>Clearing this option for a folder does not automatically clear it for the sub-folders. You must clear it explicitly for each of the sub-folders.

### Grant access to all operators {#grant-access-to-all-operators}

In the **[!UICONTROL Security]** tab, if the **[!UICONTROL System folder]** option is selected, all operators will have access to this data, regardless of their rights. If this option is cleared, you must explicitly add the operator (or their group) to the list of authorizations in order for them to have access.

![](assets/s_ncs_user_folder_properties_security03b.png)
-->