---
solution: Campaign Classic
product: campaign
title: Publicación de plantilla
description: Publicación de plantilla
audience: message-center
content-type: reference
topic-tags: message-templates
translation-type: tm+mt
source-git-commit: 02dee9c4cc03784ccc20f147f816798248bd10f2
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 67%

---


# Cancelación de publicación de una plantilla{#template-unpublication}

Una vez publicada una plantilla de mensaje en las instancias de ejecución, se puede cancelar su publicación. Para obtener más información sobre el proceso de publicación de la plantilla, consulte [esta sección](../../message-center/using/template-publication.md).

* De hecho, se puede seguir llamando a una plantilla publicada si se activa el evento correspondiente: si ya no utiliza una plantilla de mensaje, se recomienda cancelar la publicación. Esto es para evitar enviar un mensaje transaccional no deseado por error.

   Por ejemplo, ha publicado una plantilla de mensaje que solo utiliza para campañas de Navidad. Tal vez quiera cancelar la publicación después de que termine el período de Navidad y publicarla nuevamente el año que viene.

* Tampoco puede eliminar una plantilla de mensaje transaccional que tenga el estado **[!UICONTROL Published]**. Primero debe cancelar la publicación.

>[!NOTE]
>
>Esta funcionalidad está disponible a partir de la versión 20.2 de Campaign.

Para cancelar la publicación de una plantilla de mensaje transaccional, siga los pasos a continuación.

1. En la instancia de control, vaya a la carpeta **[!UICONTROL Message Center > Transactional message templates]** del árbol.
1. Seleccione la plantilla cuya publicación desea cancelar.
1. Haga clic **[!UICONTROL Unpublish]**.

   <!--1. Fill in the **[!UICONTROL Log of the process]** field.-->

1. Haga clic **[!UICONTROL Start]**.

![](assets/message-center-unpublish.png)

El estado de la plantilla de mensaje transaccional cambia de **[!UICONTROL Published]** a **[!UICONTROL Being edited]**.

Una vez finalizada la cancelación de la publicación:

* Ambas plantillas de mensaje (aplicadas a eventos de tipo por lotes y en tiempo real) se eliminan de cada instancia de ejecución.

   Ya no aparecen en la carpeta **[!UICONTROL Administration > Production > Message Center Execution > Default > Transactional message templates]** (consulte [esta sección](../../message-center/using/template-publication.md)).

* Una vez cancelada la publicación de una plantilla, puede eliminarla de la instancia de control.

   Para ello, selecciónela en la lista y haga clic en el botón **[!UICONTROL Delete]** situado en la parte superior derecha de la pantalla.