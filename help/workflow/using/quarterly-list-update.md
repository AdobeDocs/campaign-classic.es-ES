---
product: campaign
title: Actualización de lista trimestral con una consulta incremental
description: En este caso de uso, se utiliza una consulta incremental para actualizar automáticamente una lista de destinatarios
feature: Workflows
hide: true
exl-id: 0d3e7046-313a-42a6-9155-3365e8d60bac
TQID: https://experienceleague.adobe.com/BH9Rd9DTl5ZnTIo17AS6FKEYio-DjbXiOf0Nn1GLXWI
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: id: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 278
ht-degree: 100%

---

# Actualización de lista trimestral con una consulta incremental {#quarterly-list-update}



En el siguiente ejemplo, se utiliza una [consulta incremental](incremental-query.md) para actualizar automáticamente una lista de destinatarios. Estos destinatarios están dirigidos como parte de campañas de marketing de temporada.

Como estas campañas se inician al comienzo de cada temporada para ofrecer actividades de deportes relevantes, estas listas se actualizan cada trimestre. Sin embargo, un destinatario solo debe ser identificado una vez cada 9 meses por esta campaña. Esto le permite espaciar la frecuencia con la que se puede seleccionar a un destinatario y ofrecerle actividades en diferentes estaciones a lo largo de los años.

![](assets/incremental_query_example.png)

1. Añade una consulta incremental así como una actividad de actualización de lista en un nuevo flujo de trabajo.
1. Configure la pestaña **[!UICONTROL Incremental query]** de la actividad según se especifica en [Creación de una consulta](query.md#creating-a-query).
1. Seleccione la pestaña **[!UICONTROL Scheduling & History]** y luego especifique un historial de 270 días. Un destinatario que ya ha sido identificado ya no será objetivo durante un periodo de 270 días o aproximadamente 9 meses.

   A continuación, haga clic en el botón **[!UICONTROL Change...]** .

1. Para asegurarse de que la lista se actualice antes del inicio de cada temporada, seleccione **[!UICONTROL Monthly]**.
1. En la pantalla siguiente, seleccione marzo, junio, septiembre y diciembre. Elija el día 20 del mes y elija a qué hora le gustaría iniciar el flujo de trabajo.
1. Seleccione el periodo de validez de la consulta. Por ejemplo, si desea que esta actividad esté activa de forma permanente, seleccione **[!UICONTROL Permanent validity]**.

   ![](assets/incremental_query_example_2.png)

1. Después de aprobar la consulta incremental, configure la actividad de actualización de lista como se explica en [Actualización de lista](list-update.md).

Por lo tanto, el flujo de trabajo se iniciará automáticamente justo antes del inicio de cada temporada. La lista se actualizará con nuevos destinatarios aptos para recibir las ofertas.
