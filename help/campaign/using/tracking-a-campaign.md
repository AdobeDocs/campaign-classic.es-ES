---
title: Seguimiento de una campaña
seo-title: Seguimiento de una campaña
description: Seguimiento de una campaña
seo-description: null
page-status-flag: never-activated
uuid: 66919c81-b22c-4138-a654-ea53154ba718
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: e1f8958d-f036-4635-be6e-ebdbea6ac116
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: eee744eb5bc7a43fd412ffb01f0546385146a978

---


# Seguimiento de una campaña{#tracking-a-campaign}

Los operadores de entidad central pueden rastrear las solicitudes de campaña en la lista de paquetes de campañas.

Esto les permite:

* [Filtración de paquetes](#filter-packages),
* [Editar paquetes](#edit-packages),
* [Cancelar un paquete](#cancel-a-package),
* [Reinicio de un paquete](#reinitializing-a-package).

## Filtración de paquetes {#filter-packages}

From the **[!UICONTROL Campaigns universe]**, you can display the list of **[!UICONTROL Campaign packages]** which regroups all existing Distributed Marketing campaigns. Puede filtrar esta lista para que muestre solo las campañas que se han publicado, que se han retrasado, que están pendientes de aprobación, etc. Para ello, haga clic en los vínculos de la sección superior de esta vista o utilice el **[!UICONTROL Filter list]** vínculo y seleccione el estado del paquete de campaña que desea mostrar.

![](assets/mkg_dist_catalog_filter.png)

## Editar paquetes {#edit-packages}

The **[!UICONTROL Campaign packages]** page lets you view the summary of each package.

Este resumen muestra la siguiente información: etiqueta, tipo de campaña, así como el nombre de la campaña desde la que se creó y la carpeta.

Haga clic en el nombre del paquete para editarlo. También puede ver solicitudes por sus entidades locales y por su estado.

This information is also offered in the **[!UICONTROL Campaign orders]** view which lists all orders.

![](assets/mkg_dist_catalog_op_command_details.png)

El operador central puede editar la solicitud. Hay dos formas de hacerlo:

1. El operador puede hacer clic en el nombre del pedido para editarlo: esto muestra los detalles del pedido.

   ![](assets/mkg_dist_catalog_op_command_edit1.png)

   The **[!UICONTROL Edit > General]** tab lets you view information entered by the local entity when it ordered the campaign.

   ![](assets/mkg_dist_catalog_op_command_edit1a.png)

1. El operador puede hacer clic en la etiqueta del paquete de campaña para editarlo y cambiar ciertas configuraciones.

   ![](assets/mkg_dist_catalog_op_command_edit2.png)

## Cancelar un paquete {#cancel-a-package}

La entidad central puede cancelar un paquete de campaña en cualquier momento.

Haga clic **[!UICONTROL Cancel]** en el paquete de campaña **[!UICONTROL Dashboard]**.

![](assets/mkg_dist_cancel_op_from_dashboard.png)

The **[!UICONTROL Comment]** field lets you justify the cancellation.

Para las **campañas locales**, cancelar un paquete las elimina de la lista de campañas de marketing disponibles.

Para las **campañas de colaboración**, cancelar un paquete activa varias acciones:

1. Todas las solicitudes relacionadas con este paquete se cancelan.

   ![](assets/mkg_dist_mutual_op_cancelled.png)

1. La campaña de referencia se cancela y todos los procesos activos (flujos de trabajo, envíos) se detienen.

   ![](assets/mkg_dist_mutual_op_cancelled1.png)

1. Se envía una notificación a todas las entidades locales correspondientes.

   ![](assets/mkg_dist_mutual_op_cancelled2.png)

La entidad central puede seguir accediendo y reiniciando los paquetes cancelados (consulte a continuación) si es necesario. Solo se ofrecen a las entidades locales una vez aprobadas e iniciadas. A continuación, se muestra el proceso de reinicio de paquetes.

## Reinicio de un paquete {#reinitializing-a-package}

Los paquetes de campañas que ya se han publicado se pueden reiniciar, modificar y ponerlo a disposición de entidades locales.

1. Seleccione el paquete que desee.
1. Haga clic en el **[!UICONTROL Reinitialize the package to reuse it]** vínculo y haga clic en **[!UICONTROL OK]**.

   ![](assets/mkg_dist_mutual_op_reinit.png)

1. Click the **[!UICONTROL Save]** button to approve package re-initialization.

   ![](assets/mkg_dist_mutual_op_reinit2.png)

1. El estado del paquete cambia a **[!UICONTROL Being edited]**. Modifique, apruebe y vuelva a publicarlo para restaurarla en la lista de paquetes de campañas.

>[!NOTE]
>
>También puede reiniciar paquetes de campañas canceladas.

