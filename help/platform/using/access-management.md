---
title: Gestión de acceso
seo-title: Gestión de acceso
description: Gestión de acceso
seo-description: null
page-status-flag: never-activated
uuid: 3f0cfa8f-1511-4445-9acb-b5be46e78295
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: administration-basics
discoiquuid: c0eb06fd-192c-4ee4-9a38-c9bedbe6aea0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3946d97e786423bf831d17e486186660db403709

---


# Gestión de acceso{#access-management}

## Acerca de los permisos {#about-permissions}

Adobe Campaign le permite definir y administrar los derechos asignados a los distintos operadores. Se trata de un conjunto de derechos y restricciones que autorizan o niegan:

* Acceso a determinadas funciones (a través de los derechos asignados),
* Acceso a determinados registros,
* Creación, modificación y eliminación de registros (acciones, contactos, campañas, grupos, etc.).

Los permisos se aplican a perfiles de operador o grupos de operadores.

Se completan por parámetros de seguridad vinculados al modo de conexión del operador a Adobe Campaign. Para obtener más información, consulte [esta página](../../installation/using/configuring-campaign-server.md#defining-security-zones).

Existen dos tipos de permisos que puede conceder a un usuario:

* Puede definir grupos de operadores a los que desee atribuir derechos y luego asociar los operadores con uno o varios grupos. Esto permite reutilizar derechos y hacer que los perfiles de operador sean más coherentes. También facilita la administración y el mantenimiento de los perfiles. Group creation and management are presented in [Operator groups](#operator-groups).
* Puede atribuir los derechos asignados directamente a los usuarios, en algunos casos para sobrecargar los derechos asignados a través de grupos. Estos derechos se presentan en derechos [](#named-rights)con nombre.

>[!NOTE]
>
>Antes de empezar a definir permisos, Adobe recomienda leer la [lista de comprobación de configuración de seguridad](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html).

## Operadores {#operators}

### Acerca de los operadores {#about-operators}

Un operador es un usuario de Adobe Campaign que tiene permisos para iniciar sesión y realizar acciones.

De forma predeterminada, los operadores se almacenan en el **[!UICONTROL Administration > Access management > Operators]** nodo.

![](assets/s_ncs_user_list_operators.png)

Los operadores se pueden crear manualmente o asignar en un directorio LDAP existente.

En [esta página](#creating-an-operator) se describe el procedimiento completo para crear un operador.

Para más información sobre la integración de Adobe Campaign y LDAP, consulte [esta página](../../installation/using/connecting-through-ldap.md).

>[!CAUTION]
>
>Los operadores deben vincularse a una zona de seguridad para iniciar sesión en una instancia. Para más información sobre las zonas de seguridad en Adobe Campaign, consulte [esta página](../../installation/using/configuring-campaign-server.md#defining-security-zones).

Los usuarios también pueden conectarse directamente a Adobe Campaign utilizando su Adobe ID. Para obtener más información, consulte [esta página](../../integrations/using/about-adobe-id.md).

### Creación de un operador {#creating-an-operator}

Para crear un operador nuevo y conceder permisos, siga los pasos a continuación:

1. Click the **[!UICONTROL New]** button located above the list of operators, and enter the details of the new operator.

   ![](assets/s_ncs_user_operator_new.png)

1. Specify the **[!UICONTROL Identification parameters]** of the user: its login, password and name. El operador utiliza el nombre de inicio de sesión y la contraseña para iniciar sesión en Adobe Campaign. Once the user is logged on, they can change their password via the **[!UICONTROL Tools > Change password]** menu. El correo electrónico del operador es esencial, ya que permite que el operador reciba notificaciones, por ejemplo, cuando se procesan las aprobaciones.

   Esta sección también permite vincular un operador a una entidad de organización. Para obtener más información, consulte [esta página](../../campaign/using/about-distributed-marketing.md).

1. Select the permissions granted to the operator in the **[!UICONTROL Operator access rights]** section.

   To assign rights to the operator, click the **[!UICONTROL Add]** button located above the list of rights, then select a group of operators from the list of available groups:

   ![](assets/s_ncs_user_permissions_operators.png)

   You can also select one or more named rights (refer to [Named rights](#named-rights)). To do this, click the arrow to the right of the **[!UICONTROL Folder]** field, and select **[!UICONTROL Named rights]**:

   ![](assets/s_ncs_user_rights_operators.png)

   Select groups and/or named rights to be assigned and click **[!UICONTROL OK]** to validate.

1. Click **[!UICONTROL Ok]** to create the operator: the profile is added to the list of existing operators.

   ![](assets/operator_profile_new.png)

>[!NOTE]
>
>Puede organizar los operadores según sus necesidades creando nuevas carpetas de operadores. To do this, right-click the operator folder and select **[!UICONTROL Add an 'Operators' folder]**.

Una vez que se ha creado el perfil del operador, puede agregar o actualizar su información. To do this, click the **[!UICONTROL Edit]** tab.

![](assets/operator_edit_profile.png)

>[!NOTE]
>
>The **[!UICONTROL Session timeout]** field lets you adjust the delay before the FDA session timeout. Para obtener más información sobre este tema, consulte [Acerca del acceso](../../platform/using/accessing-an-external-database.md#about-federated-data-access)a datos federados.

### Zona horaria del operador {#time-zone-of-the-operator}

In the **[!UICONTROL General]** tab, you can select the time zone of the operator. De forma predeterminada, los operadores funcionan en la zona horaria del servidor. Sin embargo, es posible seleccionar otra zona horaria con la lista desplegable.

La configuración de las zonas horarias se describe en [esta página](../../installation/using/time-zone-management.md).

>[!NOTE]
>
>Las colaboraciones en diferentes zonas horarias requieren el almacenamiento de fechas en UTC. Las fechas se convierten a la zona horaria apropiada en los siguientes contextos: cuando se muestra una fecha en la zona horaria del usuario, cuando se importan y exportan archivos, cuando se programa un envío de correo electrónico, cuando se programan actividades en un flujo de trabajo (programador, espera, restricción de tiempo, etc.).
>
>Las restricciones y recomendaciones vinculadas a estos contextos se presentan en secciones relacionadas de la documentación de Adobe Campaign.

In addition, the **[!UICONTROL Regional settings]** drop-down list lets you select the format to display dates and numbers.

### Opciones de derechos de acceso {#access-rights-options}

Use the **[!UICONTROL Access rights]** tab to update the groups and named rights linked to the operator.

![](assets/operator_profile_security_options.png)

El **[!UICONTROL Edit the access parameters...]** vínculo le permite acceder a las siguientes opciones:

* The **[!UICONTROL Disable account]** option lets you disable the operator&#39;s account: he will no longer access Adobe Campaign.
* The **[!UICONTROL Forbid access from the rich client]** option lets you restrict the use of Adobe Campaign to [Web access](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) or through APIs: access to the Adobe Campaign client console is no longer available.
* Es posible vincular una zona de seguridad al operador. Para obtener más información, consulte [esta página](../../installation/using/configuring-campaign-server.md#defining-security-zones).
* También puede definir una máscara IP de confianza mediante el enlace apropiado.

   El operador puede conectarse a Adobe Campaign sin introducir su contraseña si su dirección IP está en la lista.

   También se puede especificar un conjunto de direcciones IP autorizado que pueden conectarse sin contraseña, como en el siguiente ejemplo:

   ![](assets/operator_trustip.png)

   >[!NOTE]
   >
   >Para mantener el acceso a su plataforma segura, esta opción debe utilizarse con cuidado.

* The **[!UICONTROL Restrict to information found in sub-folders of:]** option lets you limit the rights attributed to the operator of a folder. El usuario solo puede ver las subcarpetas del nodo especificado en esta opción:

   ![](assets/s_ncs_user_restrictions_operators.png)

   >[!CAUTION]
   >
   >Se trata de una restricción muy estricta y debe utilizarse con precaución. Un operador registrado con este tipo de derechos puede ver el contenido de la carpeta especificada y no tiene acceso a ningún otro nodo del árbol mediante el navegador. Sin embargo, según las funcionalidades a las que tenga acceso (por ejemplo: flujos de trabajo), puede mostrar datos que normalmente se almacenan en nodos que no puede ver.

### Carpetas, aprobación y tareas de un operador {#folders--approval-and-tasks-of-an-operator}

The **[!UICONTROL Audit]** tab lets you view information related to the operator. Las distintas pestañas se añaden automáticamente en función de la configuración definida en el área de intervención del operador.

Puede acceder a:

* La lista de derechos en carpetas vinculadas al operador.

   ![](assets/operator_folder_permissions.png)

   >[!NOTE]
   >
   >Para obtener más información sobre esto, consulte Administración [de acceso a](#folder-access-management)carpetas.

* El registro de aprobaciones del operador.

   ![](assets/operator_profile_validations.png)

* La lista de foros de debate a los que están suscritas.
* Los eventos en el calendario.
* La lista de tareas asignadas a ellas.

### Operadores predeterminados {#default-operators}

Adobe Campaign utiliza operadores técnicos con perfiles configurados de forma predeterminada: Administrador (&#39;admin&#39;), Facturación (&#39;facturación&#39;), Supervisión, Agente de aplicaciones web (&#39;webapp&#39;), etc. Algunas de ellas dependen de las aplicaciones y opciones instaladas en la plataforma: Los operadores &#39;central&#39; y &#39;local&#39;, por ejemplo, solo son visibles si está instalada la opción Marketing distribuido.

>[!CAUTION]
>
>Se notifica a estos operadores técnicos de forma predeterminada cuando la plataforma devuelve mensajes de información. Recomendamos que proporcione un correo electrónico de contacto para ellos.
>
>Para asegurarse de que las aplicaciones Web funcionan correctamente, se recomienda no definir la configuración regional específica para el operador “webapp”.

De forma predeterminada, el operador técnico “webapp” tiene el derecho asignado ADMINISTRACIÓN, que puede generar riesgos de seguridad. Para solucionar este problema, se recomienda eliminar este derecho. Para ello:

1. En el **[!UICONTROL Administration > Access management > Named rights]** nodo, haga clic en **[!UICONTROL New]** para crear un derecho y asígnele un nombre WEBAPP.

   ![](assets/s_ncs_default_operators_webapp_right.png)

   Named rights are detailed in the [Named rights](#named-rights) section.

1. From the **[!UICONTROL Administration > Access management > Operators]** node, select the Web applications agent operator (&#39;webapp&#39;).

   Select the **[!UICONTROL Edit]** tab, then the **[!UICONTROL Access rights]** tab and delete the ADMINISTRATION named right from the list.

   ![](assets/s_ncs_default_operators_webapp_admin_right.png)

   Click **[!UICONTROL Add]** and select the WEBAPP right that you have just created, then save your changes.

   ![](assets/s_ncs_default_operators_webapp_webapp_right.png)

1. Asigne los derechos de acceso a los datos de lectura y escritura del operador “webapp” en las carpetas correspondientes a dicho operador, principalmente en las carpetas de “Destinatario”.

   ![](assets/s_ncs_default_operators_webapp_folder_access.png)

   Modifying rights on tree folders is detailed in the [Folder access management](#folder-access-management) section.

>[!NOTE]
>
>Para obtener más información sobre pautas de seguridad consulte la [Lista de comprobación de configuración de seguridad de Adobe Campaign ](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html).

## Grupos de operadores {#operator-groups}

Operator groups are created via the **[!UICONTROL Administration > Access management > Operator groups]** node in the tree.

### Creación de un grupo de operadores nuevo {#creating-a-new-operator-group}

Para crear un grupo de operadores nuevo siga los siguientes pasos:

1. Click the **[!UICONTROL New]** button to the right of the list of groups or right-click the list and choose **[!UICONTROL New]**.
1. In the section lower window, from the **[!UICONTROL General]** tab, enter the name and a description for this group in the corresponding fields.

   ![](assets/s_ncs_user_create_operator_gp.png)

1. Click the **[!UICONTROL Content]** tab to define authorizations for this group.
1. Click the **[!UICONTROL Add]** button to select an appointed right or an operator to associate to the group.
1. Click the drop-down list or on the folder to the right of the **[!UICONTROL Folder]** field to locate the appointed rights or operators to associate to this group.
1. Select the rights or operators to add and click **[!UICONTROL OK]** to validate.

   ![](assets/s_ncs_user_create_operator_gp03.png)

   Repita esta operación para añadir otros derechos u operadores.

1. Click the **[!UICONTROL Save]** button to add the group to the list.

### Grupos predeterminados {#default-groups}

Los grupos de operadores predeterminados son:

1. Operadores de envío

   Los operadores de este grupo están a cargo de la administración de las envíos: permiten el acceso a los recursos principales necesarios para crear y preparar envíos (tipologías de campaña, asignaciones de envíos, plantillas predeterminadas, bloques de personalización, etc.).

   Este grupo contiene los siguientes derechos asignados:

   * PREPARACIÓN DE ENVÍOS: derecho para crear, editar e iniciar el análisis de envíos,
   * INICIO DE ENVÍOS: derecho para aprobar entregas analizadas anteriormente.

1. Administradores de campañas

   Los operadores de este grupo pueden administrar las campañas de marketing: permite acceder a los objetos vinculados a campañas (planes, programas, flujos de trabajo, presupuestos, etc.).

   Este grupo contiene los siguientes derechos asignados:

   * INSERCIÓN DE CARPETAS: derecho para insertar carpetas en el árbol de Adobe Campaign (siempre que tenga derechos de edición para las ramas correspondientes),
   * FLUJO DE TRABAJO: derecho para utilizar flujos de trabajo.
   >[!NOTE]
   >
   >Este grupo no permite a los operadores iniciar envíos.

1. Contribuidores de contenido

   Los operadores de este grupo pueden acceder a las carpetas de contenido, dentro del marco de **Content management** (módulo opcional de Adobe Campaign). Este grupo no otorga derechos adicionales.

1. Acceso a informes

   Este grupo está reservado para operadores externos, para acceder a los informes de envío a través de un acceso Web.

1. Ejecución del flujo de trabajo

   Este grupo permite asignar a operadores el derecho para administrar los flujos de trabajo que no están relacionados con las campañas.

1. Supervisores de flujo de trabajo

   Los operadores de este grupo reciben una notificación por correo electrónico en caso de alertas relacionadas con los flujos de trabajo de campañas.

1. Administración local/central

   Estos grupos permiten utilizar **Distributed Marketing** (módulo opcional de Adobe Campaign).

## Derechos asignados {#named-rights}

De forma predeterminada, Adobe Campaign propone un conjunto de derechos asignados que permiten definir las autorizaciones asignadas a operadores y grupos de operadores. These rights can be edited from the **[!UICONTROL Administration > Access management > Named rights]** node of the tree.

![](assets/s_ncs_admin_named_rights.png)

Estos derechos son los siguientes:

* ADMINISTRACIÓN: Derecho de administración genérico aplicado a todas las carpetas de la consola.
* ADMINISTRACIÓN DE LA APROBACIÓN: Derecho a asignar revisores.
* CENTRAL: Derecho a la administración central (marketing distribuido).
* ELIMINAR CARPETA: Derecho a eliminar carpetas.
* EDITAR CARPETAS: Derecho a modificar las propiedades de la carpeta: nombre, etiqueta, imagen asociada, etc.
* EXPORTAR: Derecho a exportar datos.
* ACCESO A ARCHIVOS: Derecho a leer y escribir el acceso de los archivos a través de una secuencia de comandos.
* IMPORTAR: Derecho para la importación de datos genéricos.
* INSERTAR CARPETAS: Derecho a insertar carpetas.
* LOCAL: Derecho para la administración local (marketing distribuido).
* COMBINAR: Derecho a combinar registros.
* PREPARAR ENTREGA: Derecho a crear, editar e iniciar el análisis de entrega.
* DATOS DE PRIVACIDAD DERECHOS: Derecho a recopilar y eliminar datos de privacidad. Para obtener más información, consulte [esta página](https://helpx.adobe.com/campaign/kb/acc-privacy.html).
* EJECUCIÓN DEL PROGRAMA: Derecho a ejecutar programas externos.
* IMPORTACIÓN DE DESTINATARIOS: Derecho a importar destinatarios.
* EJECUCIÓN DE SECUENCIAS DE COMANDOS SQL: Derecho a ejecutar secuencias de comandos SQL en la base de datos.
* INICIAR ENTREGA: Derecho a aprobar entregas previamente analizadas.
* USE SQL DATA MANAGEMENT ACTIVITY: Right to write your own SQL scripts using the SQL Data Management activity, in order to create and populate work tables (see [this section](../../workflow/using/sql-data-management.md)).
* FLUJO DE TRABAJO: Derecho a utilizar flujos de trabajo.
* WEBAPP: Derecho a utilizar aplicaciones web.

>[!NOTE]
>
>Esta lista puede variar según los complementos instalados en la plataforma.

## Matriz de derechos de acceso {#access-rights-matrix}

Los grupos predeterminados y los derechos asignados permiten a los operadores acceder a ciertas carpetas de la jerarquía de navegación y conceder permisos de lectura, escritura y eliminación.

La matriz de derechos de acceso a Adobe Campaign está disponible [aquí](/help/platform/using/assets/accessrights.pdf).

## Administración de acceso a carpetas {#folder-access-management}

Cada carpeta del árbol tiene asociados derechos de acceso de lectura, escritura y eliminación. Para acceder a un archivo, un operador o un grupo de operadores debe tener al menos acceso de lectura.

### Edición de permisos en una carpeta {#edit-permissions-on-a-folder}

Para editar los permisos en una carpeta específica del árbol, siga los pasos siguientes:

1. Right-click on the folder and select **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_folder_properties.png)

1. Click the **[!UICONTROL Security]** tab to view authorizations on this folder.

   ![](assets/s_ncs_user_folder_properties_security.png)

### Modificar permisos {#modify-permissions}

Para modificar los permisos, puede:

* **Reemplazar un grupo o un operador**. Para ello, haga clic en uno de los grupos (u operadores) con derechos sobre la carpeta y seleccione un nuevo grupo (o un operador nuevo) en la lista desplegable:

   ![](assets/s_ncs_user_folder_properties_security02.png)

* **Autorizar un grupo o un operador**. To do this, click the **[!UICONTROL Add]** button and select the group or operator to which you want to assign authorizations for this folder.
* **Prohibir un grupo o un operador**. To do this, click **[!UICONTROL Delete]** and select the group or operator from which you want to remove authorization for this folder.
* **Seleccione los derechos asignados a un grupo o a un operador**. Para ello, haga clic en el grupo u operador respectivo y, a continuación, seleccione los derechos de acceso que desee conceder y desmarque los demás.

   ![](assets/s_ncs_user_folder_properties_security03.png)

### Propagación de permisos {#propagate-permissions}

Se puede propagar autorizaciones y derechos de acceso. To do this, select the **[!UICONTROL Propagate]** option in the folder properties.

Las autorizaciones definidas en esta ventana se aplican a todas las subcarpetas del nodo actual. A continuación, se pueden sobrecargar estas autorizaciones para cada una de las subcarpetas.

>[!NOTE]
>
>Borrar esta opción para una carpeta no la borra automáticamente para las subcarpetas. Debe borrarla específicamente en relación con cada una de las subcarpetas.

### Concesión de acceso a todos los operadores {#grant-access-to-all-operators}

In the **[!UICONTROL Security]** tab, if the **[!UICONTROL System folder]** option is selected, all operators will have access to this data, regardless of their rights. Si se borra esta opción, se debe añadir explícitamente el operador (o su grupo) a la lista de autorizaciones para que tengan acceso.

![](assets/s_ncs_user_folder_properties_security03b.png)

## Carpetas y vistas {#folders-and-views}

### Acerca de las carpetas y las vistas {#about-folders-and-views}

Las carpetas son nodos del árbol de Adobe Campaign. These nodes are created by right-clicking the tree, via the **[!UICONTROL Add new folder]** menu. De forma predeterminada, el primer menú permite añadir la carpeta correspondiente al contexto actual.

![](assets/s_ncs_user_add_folder_in_tree.png)

Puede conceder permisos a estas carpetas en todas las demás carpetas del árbol. Consulte Administración [de acceso a carpetas](#folder-access-management).

Además, puede crear vistas para restringir el acceso a los datos y organizar el contenido del árbol para adaptarlo a sus necesidades. A continuación, puede asignar derechos a las vistas.

Una vista es una carpeta que muestra registros almacenados físicamente en una o más carpetas del mismo tipo. Por ejemplo, si se crea una carpeta de campañas que sea una vista, esta muestra todas las campañas contenidas en la base de datos de manera predeterminada, independientemente de su origen. Estos datos se pueden filtrar.

Cuando se convierte una carpeta en una vista, todos los datos correspondientes al tipo de carpeta presentes en la base de datos se muestran en la vista, independientemente de la carpeta en la que se guarde. A continuación, puede filtrarlos para restringir la lista de datos mostrados.

>[!CAUTION]
>
>Las vistas contienen datos y permiten el acceso a ellos, pero los datos no se almacenan físicamente en la carpeta de vista. El operador debe tener los derechos adecuados para la acción deseada en las carpetas de origen de los datos (acceso de lectura, como mínimo).
>
>Para conceder acceso a una vista sin conceder acceso a la carpeta de origen, no asigne acceso de lectura al nodo principal de la carpeta de origen.

### Adición de carpetas y creación de vistas {#adding-folders-and-creating-views}

En el ejemplo siguiente, se muestra cómo crear nuevas carpetas para mostrar datos específicos:

1. Create a new **[!UICONTROL Deliveries]** type folder, and name it **Deliveries France**.
1. Right-click this folder and select **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_add_folder_exple.png)

1. En la **[!UICONTROL Restriction]** ficha, seleccione **[!UICONTROL This folder is a view]**. Eso hace que se muestren todos los envíos de la base de datos.

   ![](assets/s_ncs_user_add_folder_exple01.png)

1. Defina los criterios del filtro de envíos desde el editor de consultas en la sección central de la ventana: esto muestra las campañas correspondientes al filtro definido.

   >[!NOTE]
   >
   >El editor de consultas se muestra en [esta sección](../../platform/using/about-queries-in-campaign.md).

   Con las siguientes condiciones de filtro:

![](assets/s_ncs_user_add_folder_exple00.png)

Los siguientes envíos se muestran en la vista:

![](assets/s_ncs_user_add_folder_exple02.png)

