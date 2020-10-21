---
title: Creación de una lista de perfiles a partir de un flujo de trabajo
description: Aprenda a crear una lista de perfil en un flujo de trabajo
page-status-flag: never-activated
uuid: a30f7217-fe82-4290-b1e6-e7a126a316c1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: ba42c3cf-31fc-4fbc-b230-a2b3982328c5
translation-type: tm+mt
source-git-commit: c2c0609619e0cc81444d089850add6dec5de93fd
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 14%

---


# Creación de una lista de perfiles a partir de un flujo de trabajo{#creating-a-profile-list-with-a-workflow}

Para crear una lista de **[!UICONTROL List]** tipo basada en la nueva tabla de destinatario, debe crear un flujo de trabajo de objetivo que genere la lista.

Para obtener más información sobre listas en Campaña, consulte [esta sección](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

![](assets/do-not-localize/how-to-video.png) [Descubra esta función en vídeo](../../platform/using/creating-and-managing-lists.md#create-list-in-a-wf-video)

Para crear un flujo de trabajo de objetivo y actualizar destinatarios en una tabla de destinatarios personalizada, siga los pasos a continuación:

1. Vaya al **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** nodo del explorador.
1. Cree un nuevo flujo de trabajo de objetivos.
1. Coloque una actividad de **Consulta** seguida de una actividad de actualización **de** Lista.

   ![](assets/mapping_create_list_workflow01.png)

1. Haga clic con el botón doble en la actividad de **Consulta** y, a continuación, haga clic **[!UICONTROL Edit the query]** para elegir una dimensión de segmentación basada en el esquema de la nueva tabla de destinatarios (en nuestro ejemplo: **Individual**). Haga clic en **[!UICONTROL Finish]** para confirmar.

   ![](assets/mapping_create_list_workflow03.png)

1. Haga clic con el doble en la actividad de actualización **de la** Lista y, a continuación, seleccione el **[!UICONTROL Create the list if necessary (Computed name)]** botón de radio.

   ![](assets/mapping_create_list_workflow02.png)

1. Seleccione la carpeta de creación para la nueva lista.
1. Ejecute el flujo de trabajo para crear la lista.
1. Vista el resultado en el nodo del árbol seleccionado durante la **[!UICONTROL List update]** actividad.

   El panel especifica el esquema en el que se basa la lista, como se muestra a continuación:

   ![](assets/mapping_list_view.png)


