---
title: Actualización de lista trimestral con una consulta incremental
description: En este caso de uso,, se utiliza una consulta incremental para actualizar automáticamente una lista de destinatarios.
page-status-flag: never-activated
uuid: 24d322e8-172c-4faa-8a1f-59085b390a76
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 31071cd2-7d97-4a4f-a6cc-5ac5b6178be5
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 100%

---


# Actualización de lista trimestral con una consulta incremental {#quarterly-list-update}

En el siguiente ejemplo, se utiliza una [consulta incremental](../../workflow/using/incremental-query.md) para actualizar automáticamente una lista de destinatarios. Estos destinatarios están dirigidos como parte de campañas de marketing de temporada.

Como estas campañas se inician al comienzo de cada temporada para ofrecer actividades de deportes relevantes, estas listas se actualizan cada trimestre. Sin embargo, un destinatario solo debe ser identificado una vez cada 9 meses por esta campaña. Esto le permite espaciar la frecuencia con la que se puede seleccionar a un destinatario y ofrecerle actividades en diferentes estaciones a lo largo de los años.

![](assets/incremental_query_example.png)

1. Añade una consulta incremental así como una actividad de actualización de lista en un nuevo flujo de trabajo.
1. Configure la pestaña **[!UICONTROL Incremental query]** de la actividad según se especifica en [Creación de una consulta](../../workflow/using/query.md#creating-a-query).
1. Seleccione la pestaña **[!UICONTROL Scheduling & History]** y luego especifique un historial de 270 días. Un destinatario que ya ha sido identificado ya no será objetivo durante un periodo de 270 días o aproximadamente 9 meses.

   A continuación, haga clic en el botón **[!UICONTROL Change...]** .

1. Para asegurarse de que la lista se actualice antes del inicio de cada temporada, seleccione **[!UICONTROL Monthly]**.
1. En la pantalla siguiente, seleccione marzo, junio, septiembre y diciembre. Elija el día 20 del mes y elija a qué hora le gustaría iniciar el flujo de trabajo.
1. Seleccione el periodo de validez de la consulta. Por ejemplo, si desea que esta actividad esté activa de forma permanente, seleccione **[!UICONTROL Permanent validity]**.

   ![](assets/incremental_query_example_2.png)

1. Después de aprobar la consulta incremental, configure la actividad de actualización de lista como se explica en [Actualización de lista](../../workflow/using/list-update.md).

Por lo tanto, el flujo de trabajo se iniciará automáticamente justo antes del inicio de cada temporada. La lista se actualizará con nuevos destinatarios aptos para recibir las ofertas.
