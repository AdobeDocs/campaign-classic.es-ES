---
product: campaign
title: Ejemplo de uso
description: Ejemplo de uso
feature: Subscriptions, Email, Data Management
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
audience: platform
content-type: reference
topic-tags: filtering-data
exl-id: 85ded096-7d27-41b3-8ef2-93f5ca8def82
hide: true
hidefromtoc: true
source-git-commit: 42cec0e9bede94a2995a5ad442822512bda14f2b
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 100%

---

# Ejemplo de uso{#use-case}



## Creación de un filtro con el formato del correo electrónico de los suscriptores {#creating-a-filter-on-the-email-format-of-subscribers}

Este ejemplo muestra cómo crear un filtro para ordenar suscripciones de newsletter basándose en el formato de correo electrónico del destinatario.

Para ello, es necesario utilizar un filtro predefinido: estos filtros están vinculados a un tipo de documento y se accede a ellos a través del nodo **[!UICONTROL Administration > Configuration > Predefined filters]**. Estos filtros de datos se pueden utilizar para cada tipo de editor (o documento) de la aplicación.

Los filtros de datos se crean de la misma manera que los filtros predefinidos, pero hay un campo adicional para seleccionar el tipo de documento al que se aplica el filtro.

Siga estos pasos:

1. Cree un nuevo filtro a través del nodo **[!UICONTROL Administration > Configuration > Predefined filters]**.
1. Haga clic en el icono **[!UICONTROL Select link]** para seleccionar el documento que le interesa:

   ![](assets/s_ncs_user_filter_choose_schema.png)

1. Seleccione el esquema de suscripción (nms:subscription) y haga clic en **[!UICONTROL OK]**.

   ![](assets/s_ncs_user_filter_select_schema.png)

1. Haga clic en **[!UICONTROL Edit link]** para ver los campos del documento seleccionado.

   ![](assets/s_ncs_user_filter_edit_schema.png)

   A continuación, puede ver el contenido del documento seleccionado:

   ![](assets/s_ncs_user_filter_view_schema.png)

   Puede acceder a estos campos para definir las condiciones de filtro en el cuerpo del editor de filtros. Un filtro de aplicación se define exactamente igual que un filtro avanzado. Consulte [Creación de un filtro avanzado](../../platform/using/creating-filters.md#creating-an-advanced-filter).

1. Crear un nuevo filtro de suscripciones para mostrar solo las suscripciones con un formato de correo electrónico no definido:

   ![](assets/s_ncs_user_filter_parameters.png)

1. Haga clic en **[!UICONTROL Save]** para añadir un filtro a los filtros predefinidos para este tipo de lista.
1. Ahora puede utilizar este filtro en la pestaña **[!UICONTROL Subscriptions]** del perfil de destinatario; puede acceder al filtro “Formato del correo electrónico desconocido” haciendo clic en el botón **[!UICONTROL Filters]**.

   ![](assets/s_ncs_user_filter_on_events.png)

   El nombre del filtro actual se muestra encima de la lista. Para cancelar el filtro, haga clic en el icono **[!UICONTROL Delete this filter]**.

   ![](assets/s_ncs_user_filter_on_subscriptions.png)
