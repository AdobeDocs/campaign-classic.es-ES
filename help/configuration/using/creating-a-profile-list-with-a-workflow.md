---
product: campaign
title: Creación de una lista de perfiles a partir de un flujo de trabajo
description: Obtenga información sobre cómo crear una lista de perfiles en un flujo de trabajo
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
feature: Workflows, Profiles
role: User
exl-id: 6b308299-4d07-4c9e-bd2f-a0860c41cf02
TQID: https://experienceleague.adobe.com/km2D2qnUAdgDCauLUYcWSC-J567twPEyvaZBsLDAOKA
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 194
ht-degree: 18%

---

# Creación de una lista de perfiles a partir de un flujo de trabajo{#creating-a-profile-list-with-a-workflow}


Para crear una lista de tipo **[!UICONTROL List]** basada en la nueva tabla de destinatarios, debe crear un flujo de trabajo de objetivos que genere la lista.

Para obtener más información sobre las listas en Campaign, consulte [esta sección](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

![](assets/do-not-localize/how-to-video.png) [Descubra esta funcionalidad en vídeo](../../platform/using/creating-and-managing-lists.md#create-list-in-a-wf-video)

Para crear un flujo de trabajo de objetivos y actualizar los destinatarios en una tabla de destinatarios personalizada, siga los pasos a continuación:

1. Vaya al nodo **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** del explorador.
1. Cree un nuevo flujo de trabajo de objetivos.
1. Realice una actividad **Query** seguida de una actividad **List update**.

   ![](assets/mapping_create_list_workflow01.png)

1. Haga doble clic en la actividad **Consulta** y, a continuación, haga clic en **[!UICONTROL Edit the query]** para elegir una dimensión de segmentación basada en el esquema de la nueva tabla de destinatarios (en nuestro ejemplo: **Individual**). Haga clic en **[!UICONTROL Finish]** para confirmar.

   ![](assets/mapping_create_list_workflow03.png)

1. Haga doble clic en la actividad **List update** y, a continuación, seleccione el botón de opción **[!UICONTROL Create the list if necessary (Computed name)]**.

   ![](assets/mapping_create_list_workflow02.png)

1. Seleccione la carpeta de creación de la nueva lista.
1. Ejecute el flujo de trabajo para crear la lista.
1. Vea el resultado en el nodo del árbol que seleccionó durante la actividad **[!UICONTROL List update]**.

   El panel especifica el esquema en el que se basa la lista, como se muestra a continuación:

   ![](assets/mapping_list_view.png)
