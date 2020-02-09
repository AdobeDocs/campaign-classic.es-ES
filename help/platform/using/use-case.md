---
title: Ejemplo de uso
seo-title: Ejemplo de uso
description: Ejemplo de uso
seo-description: null
page-status-flag: never-activated
uuid: d4c76fdf-d562-4151-93ec-08b4f6563440
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: filtering-data
discoiquuid: fbc38e33-60a6-4d21-a598-312293d168fb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 51e4d72abf3a1f48700ca38566dbf06dd24594b8

---


# Ejemplo de uso{#use-case}

## Creación de un filtro sobre el formato de correo electrónico de los suscriptores {#creating-a-filter-on-the-email-format-of-subscribers}

Este ejemplo muestra cómo crear un filtro para ordenar suscripciones de boletín basándose en el formato de correo electrónico del destinatario.

To do this, we need to use a predefined filer: these filters are linked to a document type and are accessed via the **[!UICONTROL Administration > Configuration > Predefined filters]** node. Estos filtros de datos se pueden utilizar para cada tipo de editor (o documento) de la aplicación.

Los filtros de datos se crean de la misma manera que los filtros predefinidos, pero hay un campo adicional para seleccionar el tipo de documento al que se aplica el filtro.

Siga estos pasos:

1. Cree un nuevo filtro a través del **[!UICONTROL Administration > Configuration > Predefined filters]** nodo.
1. Click the **[!UICONTROL Select link]** icon to select the concerned document:

   ![](assets/s_ncs_user_filter_choose_schema.png)

1. Select the subscription schema (nms:subscription) and click **[!UICONTROL OK]**.

   ![](assets/s_ncs_user_filter_select_schema.png)

1. Click **[!UICONTROL Edit link]** to view the fields of the selected document.

   ![](assets/s_ncs_user_filter_edit_schema.png)

   A continuación, puede ver el contenido del documento seleccionado:

   ![](assets/s_ncs_user_filter_view_schema.png)

   Puede acceder a estos campos para definir las condiciones de filtro en el cuerpo del editor de filtros. Un filtro de aplicación se define exactamente igual que un filtro avanzado. See [Creating an advanced filter](../../platform/using/creating-filters.md#creating-an-advanced-filter).

1. Crear un nuevo filtro en las suscripciones para mostrar solo las suscripciones con un formato de correo electrónico no definido:

   ![](assets/s_ncs_user_filter_parameters.png)

1. Click **[!UICONTROL Save]** to add a filter to the pre-defined filters for this type of list.
1. You can now use this filter in the **[!UICONTROL Subscriptions]** tab of the recipient profile; you can access the &quot;Unknown e-mail format&quot; filter by clicking the **[!UICONTROL Filters]** button.

   ![](assets/s_ncs_user_filter_on_events.png)

   El nombre del filtro actual se muestra encima de la lista. Para cancelar el filtro, haga clic en el **[!UICONTROL Delete this filter]** icono .

   ![](assets/s_ncs_user_filter_on_subscriptions.png)

