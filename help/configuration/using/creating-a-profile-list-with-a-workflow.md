---
product: campaign
title: Creación de una lista de perfiles a partir de un flujo de trabajo
description: Obtenga información sobre cómo crear una lista de perfiles en un flujo de trabajo
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 6b308299-4d07-4c9e-bd2f-a0860c41cf02
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 14%

---

# Creación de una lista de perfiles a partir de un flujo de trabajo{#creating-a-profile-list-with-a-workflow}

![](../../assets/v7-only.svg)

Para crear un **[!UICONTROL List]** en función de la nueva tabla de destinatarios, debe crear un flujo de trabajo de objetivos que genere la lista.

Para obtener más información sobre las listas en Campaign, consulte [esta sección](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

![](assets/do-not-localize/how-to-video.png) [Descubra esta función en vídeo](../../platform/using/creating-and-managing-lists.md#create-list-in-a-wf-video)

Para crear un flujo de trabajo de objetivos y actualizar destinatarios en una tabla de destinatarios personalizada, siga los pasos a continuación:

1. Vaya a la **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** del explorador.
1. Cree un nuevo flujo de trabajo de objetivos.
1. Coloque una **Consulta** actividad seguida de un **Actualización de listas** actividad.

   ![](assets/mapping_create_list_workflow01.png)

1. Haga doble clic en el botón **Consulta** actividad y, a continuación, haga clic en **[!UICONTROL Edit the query]** para elegir una dimensión de segmentación basada en el esquema de la nueva tabla de destinatarios (en nuestro ejemplo: **Individual**). Haga clic en **[!UICONTROL Finish]** para confirmar.

   ![](assets/mapping_create_list_workflow03.png)

1. Haga doble clic en el botón **Actualización de listas** actividad y, a continuación, seleccione la **[!UICONTROL Create the list if necessary (Computed name)]** botón de opción.

   ![](assets/mapping_create_list_workflow02.png)

1. Seleccione la carpeta de creación de la nueva lista.
1. Ejecute el flujo de trabajo para crear la lista.
1. Ver el resultado en el nodo del árbol que seleccionó durante el **[!UICONTROL List update]** actividad.

   El panel especifica el esquema en el que se basa la lista, como se muestra a continuación:

   ![](assets/mapping_list_view.png)
