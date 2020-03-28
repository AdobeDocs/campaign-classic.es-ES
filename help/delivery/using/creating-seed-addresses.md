---
title: Creación de direcciones semilla
seo-title: Creación de direcciones semilla
description: Creación de direcciones semilla
seo-description: null
page-status-flag: never-activated
uuid: 0dae107a-7b53-4096-93c3-9517b402cbc9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: 6dad49af-4818-471b-9df1-057cc6b9a68a
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Creación de direcciones semilla{#creating-seed-addresses}

Las direcciones semilla no se administran a través de perfiles y destinatarios estándar, sino en un nodo dedicado de la jerarquía de Adobe Campaign **[!UICONTROL Resources > Campaign management > Seed addresses]**.

Se pueden crear subcarpetas para organizar las direcciones semilla. Para ello, haga clic con el botón derecho en el nodo **[!UICONTROL Seed addresses]** y seleccione **[!UICONTROL Create a new &#39;Seed addresses&#39; folder]**. Asigne un nombre a la subcarpeta y pulse **[!UICONTROL Enter]** para validar. Ahora puede crear o copiar las direcciones semilla en esta subcarpeta. Para obtener más información, consulte [Definición de direcciones](#defining-addresses).

Adobe Campaign también permite crear plantillas de las direcciones semilla que se importan a las entregas o campañas, adaptándolas a las necesidades específicas de las entregas o campañas correspondientes. Consulte [Creación de plantillas de direcciones semilla](#creating-seed-address-templates).

## Definición de las direcciones {#defining-addresses}

Para crear direcciones semilla, siga los siguientes pasos:

1. Haga clic en el botón **[!UICONTROL New]** situado encima de las direcciones semilla.
1. Introduzca los datos relacionados con la dirección en los campos correspondientes de la pestaña **[!UICONTROL Recipient]**. Los campos disponibles corresponden a los datos fundamentales del perfil de los destinatarios de la entrega (nms:recipientTable): nombre, apellido, correo electrónico, etc.

   >[!NOTE]
   >
   >La etiqueta de la dirección se rellena automáticamente con el apellido y el nombre definidos.
   >
   >Al crear direcciones semilla, no es necesario introducir todos los campos de cada pestaña. Los elementos de personalización que faltan se introducen de forma aleatoria durante la entrega.

   ![](assets/s_ncs_user_seedlist_new_address.png)

1. En la pestaña **[!UICONTROL Seed fields]**, introduzca los valores que se deben insertar en los registros de envío durante la fase de análisis (en la tabla **[!UICONTROL nms:broadLog]**).
1. En la pestaña **[!UICONTROL Additional data]**, introduzca los datos de personalización utilizados para las entregas creadas en los flujos de trabajo de gestión de datos y a los que desea asignar un valor específico.

## Creación de plantillas de la dirección semilla {#creating-seed-address-templates}

Para crear plantillas de las direcciones que más tarde pueda importar y modificar para cada envío, el proceso es el mismo que al definir una nueva dirección semilla. La única diferencia es que las direcciones semilla deben almacenarse en una carpeta de tipo “plantilla”.

Para definir una carpeta de tipo “plantilla”, siga el siguiente proceso:

1. Cree una nueva carpeta de tipo **[!UICONTROL Seed addresses]**, haga clic con el botón derecho en dicha carpeta y seleccione **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_seedlist_template_folder.png)

1. Haga clic en la ficha **[!UICONTROL Restriction]** y añada la siguiente condición de filtrado: **@isModel = true**.

   ![](assets/s_ncs_user_seedlist_folder_is_model.png)

   Ahora, las direcciones almacenadas en esta carpeta pueden utilizarse como plantillas de direcciones. Pueden importarse en envíos o campañas y adaptarse a las necesidades específicas de las entregas o campañas correspondientes (consulte [Adición de direcciones semilla](../../delivery/using/adding-seed-addresses.md)).
