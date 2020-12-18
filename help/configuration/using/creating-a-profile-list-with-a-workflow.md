---
solution: Campaign Classic
product: campaign
title: Creación de una lista de perfiles a partir de un flujo de trabajo
description: Aprenda a crear una lista de perfil en un flujo de trabajo
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 14%

---


# Creación de una lista de perfiles a partir de un flujo de trabajo{#creating-a-profile-list-with-a-workflow}

Para crear una lista de tipo **[!UICONTROL List]** basada en la nueva tabla de destinatario, debe crear un flujo de trabajo de objetivo que genere la lista.

Para obtener más información sobre listas en Campaña, consulte [esta sección](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

![](assets/do-not-localize/how-to-video.png) [Descubra esta función en vídeo](../../platform/using/creating-and-managing-lists.md#create-list-in-a-wf-video)

Para crear un flujo de trabajo de objetivo y actualizar destinatarios en una tabla de destinatarios personalizada, siga los pasos a continuación:

1. Vaya al nodo **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** del explorador.
1. Cree un nuevo flujo de trabajo de objetivos.
1. Coloque una actividad **Consulta** seguida de una actividad **actualización de Lista**.

   ![](assets/mapping_create_list_workflow01.png)

1. Haga clic con el doble en la actividad **Consulta** y luego haga clic en **[!UICONTROL Edit the query]** para elegir una dimensión de segmentación basada en el esquema de la nueva tabla de destinatario (en nuestro ejemplo: **Individual**). Haga clic en **[!UICONTROL Finish]** para confirmar.

   ![](assets/mapping_create_list_workflow03.png)

1. Haga clic con el doble en la actividad **actualización de Lista** y, a continuación, seleccione el botón de opción **[!UICONTROL Create the list if necessary (Computed name)]**.

   ![](assets/mapping_create_list_workflow02.png)

1. Seleccione la carpeta de creación para la nueva lista.
1. Ejecute el flujo de trabajo para crear la lista.
1. Vista el resultado en el nodo del árbol seleccionado durante la actividad **[!UICONTROL List update]**.

   El panel especifica el esquema en el que se basa la lista, como se muestra a continuación:

   ![](assets/mapping_list_view.png)


