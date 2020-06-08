---
title: Publicación de plantilla
seo-title: Publicación de plantilla
description: Publicación de plantilla
seo-description: null
page-status-flag: never-activated
uuid: f83dbe5f-762c-4c58-aeed-6ec289eb522f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 43908738-a71a-49be-ac00-175f57a0555c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 71aeeda3edafc64dbe696ce6f344b8b0ccdc43d1
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 3%

---


# Anulación de publicación de plantilla{#template-unpublication}

Una vez publicada una plantilla de mensaje en las instancias de ejecución, se puede cancelar su publicación.

De hecho, todavía se puede llamar a una plantilla publicada. Por lo tanto, si ya no utiliza una plantilla de mensaje, se recomienda cancelar la publicación. Esto es para evitar enviar un mensaje transaccional no deseado por error. Por ejemplo, ha publicado una plantilla de mensaje que solo utiliza para campañas de Navidad. Tal vez quiera cancelar la publicación después de que termine el período de Navidad y publicarla nuevamente el año que viene.

Tampoco puede eliminar una Plantilla de mensaje transaccional que tenga el **[!UICONTROL Published]** estado. Primero debe cancelar la publicación.

Para cancelar la publicación de una Plantilla de mensaje transaccional, siga los pasos a continuación.

1. In the control instance, go to the **[!UICONTROL Message Center > Transactional message templates]** folder of the tree.
1. Seleccione la plantilla que desee cancelar la publicación.
1. Haga clic **[!UICONTROL Unpublish]**.

   <!--1. Fill in the **[!UICONTROL Log of the process]** field.-->

1. Haga clic **[!UICONTROL Start]**.

![](assets/message-center-unpublish.png)

El estado de la Plantilla de mensaje transaccional cambia de **[!UICONTROL Published]** a **[!UICONTROL Being edited]**.

Una vez finalizada la cancelación de la publicación:

* Ambas plantillas de mensaje (aplicadas a eventos de tipo por lotes y en tiempo real) se eliminan de cada instancia de ejecución. Ya no aparecen en la **[!UICONTROL Administration > Production > Message Center Execution > Default > Transactional message templates]** carpeta.

* Una vez cancelada la publicación de una plantilla, puede eliminarla de la instancia de control si es necesario. Para ello, selecciónelo en la lista y haga clic en el **[!UICONTROL Delete]** botón situado en la parte superior derecha de la pantalla.