---
product: campaign
title: Ejemplo de uso
description: Ejemplo de uso
feature: Subscriptions, Email, Data Management
audience: platform
content-type: reference
topic-tags: filtering-data
exl-id: 85ded096-7d27-41b3-8ef2-93f5ca8def82
hide: true
TQID: https://experienceleague.adobe.com/WuZ0tN8noOI48gW8vl4-923lo2aC8-Jcaz6Ph76nlmE
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c5474392-5419-4296-9e41-f6f4ce4f6e9bid: afa4204e-6d08-4e29-bc35-26aafb656d48
topic_v2: id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
subfeature_v2: id: f529d0bd-1401-4c88-9833-43228cc1d40fid: e739ee2b-6228-412e-878f-45de0791417d
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 274
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

   Puede acceder a estos campos para definir las condiciones de filtro en el cuerpo del editor de filtros. Un filtro de aplicación se define exactamente igual que un filtro avanzado. Para obtener más información sobre los filtros, consulte la [documentación de Campaign v8 (consola)](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/audience/create-filters){target=_blank}.


1. Crear un nuevo filtro de suscripciones para mostrar solo las suscripciones con un formato de correo electrónico no definido:

   ![](assets/s_ncs_user_filter_parameters.png)

1. Haga clic en **[!UICONTROL Save]** para añadir un filtro a los filtros predefinidos para este tipo de lista.
1. Ahora puede utilizar este filtro en la pestaña **[!UICONTROL Subscriptions]** del perfil de destinatario; puede acceder al filtro “Formato del correo electrónico desconocido” haciendo clic en el botón **[!UICONTROL Filters]**.

   ![](assets/s_ncs_user_filter_on_events.png)

   El nombre del filtro actual se muestra encima de la lista. Para cancelar el filtro, haga clic en el icono **[!UICONTROL Delete this filter]**.

   ![](assets/s_ncs_user_filter_on_subscriptions.png)
