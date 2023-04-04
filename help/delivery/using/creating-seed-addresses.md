---
product: campaign
title: Creación de direcciones semilla
description: Aprenda a crear y utilizar direcciones semilla
feature: Seed Address
exl-id: f7dc97f0-3423-4b6f-88e2-08180f9adf8a
source-git-commit: 0065a25250d73c71e7569768a38b5836cccab992
workflow-type: ht
source-wordcount: '413'
ht-degree: 100%

---

# Creación de direcciones semilla{#creating-seed-addresses}

![](../../assets/common.svg)

Las direcciones semilla no se administran a través de perfiles y destinatarios estándar, sino en un nodo dedicado de la jerarquía de Adobe Campaign **[!UICONTROL Resources > Campaign management > Seed addresses]**.

Se pueden crear subcarpetas para organizar las direcciones semilla. Para ello, haga clic con el botón derecho en el nodo **[!UICONTROL Seed addresses]** y seleccione **[!UICONTROL Create a new 'Seed addresses' folder]**. Asigne un nombre a la subcarpeta y pulse **[!UICONTROL Enter]** para validar. Ahora puede crear o copiar las direcciones semilla en esta subcarpeta. Para obtener más información sobre esto, consulte [Definición de direcciones](#defining-addresses).

Adobe Campaign también permite crear plantillas de las direcciones semilla que se importan a los envíos o campañas, adaptándolas a las necesidades específicas de los envíos o campañas correspondientes. Consulte [Creación de plantillas de direcciones semilla](#creating-seed-address-templates).

## Definición de direcciones {#defining-addresses}

Para crear direcciones semilla, avance con los siguientes pasos:

1. Haga clic en el botón **[!UICONTROL New]** situado encima de las direcciones semilla.
1. Introduzca los datos relacionados con la dirección en los campos correspondientes de la pestaña **[!UICONTROL Recipient]**. Los campos disponibles corresponden a los datos fundamentales del perfil de los destinatarios del envío (nms:recipient table): nombre, apellido, correo electrónico, etc.

   >[!NOTE]
   >
   >La etiqueta de la dirección se rellena automáticamente con el apellido y el nombre definidos.
   >
   >No es necesario introducir todos los campos de cada pestaña al crear una dirección semilla. Los elementos de personalización que faltan se introducen de forma aleatoria durante el análisis de envío.

   ![](assets/s_ncs_user_seedlist_new_address.png)

1. En la pestaña **[!UICONTROL Address fields]**, introduzca los valores que se deben insertar en los registros de envío durante la fase de análisis (en la tabla **[!UICONTROL nms:broadLog]**).

1. En la pestaña **[!UICONTROL Additional data]**, introduzca los datos de personalización utilizados para los envíos creados en los flujos de trabajo de gestión de datos y a los que desea asignar un valor específico.

   >[!NOTE]
   >
   >Asegúrese de que se hayan definido datos de destinatario adicionales con un alias que comience por &#39;@&#39; en la actividad **[!UICONTROL Enrichment]**. De lo contrario, no podrá usarlos correctamente con sus direcciones semilla en la actividad de envío.

## Creación de plantillas de la dirección semilla {#creating-seed-address-templates}

Para crear plantillas de las direcciones que más tarde pueda importar y modificar para cada envío, el proceso es el mismo que al definir una nueva dirección semilla. La única diferencia es que las direcciones semilla deben almacenarse en una carpeta de tipo “plantilla”.

Para definir una carpeta de tipo “plantilla”, siga el siguiente proceso:

1. Cree una nueva carpeta de tipo **[!UICONTROL Seed addresses]**, haga clic con el botón derecho en dicha carpeta y seleccione **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_seedlist_template_folder.png)

1. Haga clic en la ficha **[!UICONTROL Restriction]** y añada la siguiente condición de filtrado: **@isModel = true**.

   ![](assets/s_ncs_user_seedlist_folder_is_model.png)

   Ahora, las direcciones almacenadas en esta carpeta pueden utilizarse como plantillas de direcciones. Pueden importarse en envíos o campañas y adaptarse a las necesidades específicas de los envíos o campañas correspondientes (consulte [Adición de direcciones semilla](adding-seed-addresses.md)).
