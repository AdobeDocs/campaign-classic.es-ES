---
product: campaign
title: Edición de perfiles
description: Edición de perfiles
feature: Profiles
audience: platform
content-type: reference
topic-tags: profile-management
exl-id: 0f3a5582-5c90-4393-bee8-d9e2f07e5982
hide: true
hidefromtoc: true
source-git-commit: 471018f09e5a14635fcce07aeca1e2cf48d9144f
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 100%

---

# Edición de un perfil{#editing-a-profile}



Para ver información relacionada con un perfil, haga clic en su nombre en la lista de perfiles.

Los detalles del perfil aparecen en una nueva ficha.

![](assets/s_user_recipient_edit.png)

Los datos concernientes a los perfiles se agrupan en fichas.

Las fichas y su contenido dependen de la configuración y de los paquetes instalados.

>[!CAUTION]
>
>Se accede al esquema XML y al formulario pertinente a los campos de la tabla de perfiles mediante el nodo **[!UICONTROL Administration > Configuration > Data schemas]** del árbol de Adobe Campaign. Solo los usuarios expertos pueden realizar cambios en estos esquemas.
>
>Para obtener más información, consulte [esta página](../../configuration/using/about-schema-edition.md).

>[!NOTE]
>
>Para obtener más información sobre cómo editar perfiles y acceder a ellos, consulte la documentación detallada de la [versión 8 de Campaign](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/audience/view-profiles){target=_blank}.



<!--
## General tab {#general-tab}

This screen contains all general data about the selected profile. In particular, it contains the last name, first name, email address, email reception format, etc. It looks like this:

![](assets/s_ncs_user_profile_general_tab.png)

>[!NOTE]
>
>When the **[!UICONTROL No longer contact (by any channel)]** option is selected, this means that the profile is on denylist, i.e. the profile has expressed a wish not to be contacted (for example, by clicking an unsubscription link in a newsletter). They will no longer be targeted by deliveries on any channel (email, direct mail, etc.). For more on this, refer to [this page](../../delivery/using/understanding-quarantine-management.md).

## Contact information tab {#contact-information-tab}

This screen contains the direct mail address of the selected profile. It looks like this:

![](assets/s_ncs_user_profile_details_tab.png)

This screen shows the quality index of the address, as well as how many errors the address contains. This information is used directly by the mail carrier based on the number of errors found during previous deliveries, and is not modifiable manually.

## Other tab {#other-tab}

This screen contains user-defined fields that can be personalized based on requirements. You can also change the names of the fields and define their format, via **[!UICONTROL Field properties...]**, as shown below:

![](assets/s_ncs_user_profile_others_tab.png)

>[!NOTE]
>
>For more on field properties and on adding fields, refer to [this page](../../configuration/using/new-field-wizard.md).

## Lists tab {#lists-tab}

This screen displays the group(s) to which the selected profile belongs. Click **[!UICONTROL Add]** to subscribe the profile to a list. Click **[!UICONTROL Detail]** to display the description and the list of profiles in the selected list.

![](assets/s_ncs_user_profile_groups_tab_details.png)

For more on this, refer to [Create and manage lists](../../platform/using/creating-and-managing-lists.md).

## Subscriptions tab {#subscriptions-tab}

This screen contains the information services to which the profile has subscribed.

![](assets/s_ncs_user_profile_subscript_tab_details.png)

The **[!UICONTROL Detail]** button displays the properties of the selected subscription. The **[!UICONTROL Add]** button is used to add a new subscription manually.

For more on this, refer to [this page](../../delivery/using/managing-subscriptions.md).

## Deliveries tab {#deliveries-tab}

This screen displays the delivery logs for the selected profile. You can also display the labels, dates, and status of the delivery actions addressed to the profile via all channels.

![](assets/s_ncs_user_profile_delivery_tab.png)

## Tracking tab {#tracking-tab}

This screen lets you view the tracking logs for the selected profile. This information is used to track profile behavior following deliveries.

![](assets/s_ncs_user_profile_tracking_tab.png)

This tab shows the cumulative total of all URLs tracked in deliveries.

The list is configurable, and usually contains: the URL clicked, date and time of click, and the document that contained the URL.

>[!NOTE]
>
>For more on tracking functionality, please refer to [this page](../../delivery/using/delivery-dashboard.md).

-->