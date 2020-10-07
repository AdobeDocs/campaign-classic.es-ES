---
title: Creación de una lista de perfiles a partir de un flujo de trabajo
seo-title: Creación de una lista de perfiles a partir de un flujo de trabajo
description: Creación de una lista de perfiles a partir de un flujo de trabajo
seo-description: null
page-status-flag: never-activated
uuid: a30f7217-fe82-4290-b1e6-e7a126a316c1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: ba42c3cf-31fc-4fbc-b230-a2b3982328c5
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 24%

---


# Creación de una lista de perfiles a partir de un flujo de trabajo{#creating-a-profile-list-with-a-workflow}

Para crear una lista de **[!UICONTROL List]** tipo basada en la nueva tabla de destinatario, debe crear un flujo de trabajo de objetivo que genere la lista. Para obtener más información sobre listas en Campaña, consulte [esta sección](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

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

>[!NOTE]
>
>También puede consultar el vídeo [Creación de una lista de destinatarios](https://docs.adobe.com/content/help/es-ES/campaign-classic-learn/tutorials/getting-started/creating-a-list-of-recipients.html) .

