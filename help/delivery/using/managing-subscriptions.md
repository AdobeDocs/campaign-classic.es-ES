---
title: Administración de suscripciones
seo-title: Administración de suscripciones
description: Administración de suscripciones
seo-description: null
page-status-flag: never-activated
uuid: a2c526fa-3080-4dd5-9628-f0e7040f93cd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: subscriptions-and-referrals
discoiquuid: 9a61fe74-f779-4f23-be25-3d9a8e95704a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Administración de suscripciones{#managing-subscriptions}

## Acerca de los servicios de información {#about-information-services}

Un servicio de información consta de:

* Registro y suscripción (adhesión),
* Cancelación de registro, baja voluntaria (exclusión) o baja automática (servicio por tiempo limitado, por ejemplo, una oferta de versión de prueba),
* Mecanismos de confirmación de suscripción y baja (mecanismos simples con confirmación, doble adhesión, etc.),
* Seguimiento del historial del suscriptor.

Como función predeterminada, estos servicios incluyen informes estadísticos específicos: seguimiento de suscriptores, nivel de lealtad, tendencias de baja, etc.

En los correos electrónicos, los enlaces obligatorios para darse de baja se generan automáticamente y el proceso de adhesión/exclusión está totalmente automatizado, con el seguimiento del historial para garantizar el cumplimiento total de las normas en vigor.

Hay tres modos de suscripción/baja del servicio:

1. manual
1. mediante importación (solo suscripción),
1. a través de un formulario Web

>[!NOTE]
>
>En [esta sección](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in) se adjunta una muestra para crear un formulario de suscripción con doble adhesión.

## Creación de un servicio informativo {#creating-an-information-service}

Puede crear y gestionar suscripciones a los servicios informativos con mensajes de confirmación o envíos automáticos asociados a los suscriptores.

Para acceder al mapa de servicios de información, vaya al **[!UICONTROL Profiles and Targets]** universo y haga clic en el **[!UICONTROL Services and Subscriptions]** vínculo.

![](assets/s_ncs_user_services_new.png)

Para editar un servicio existente, haga clic en su nombre. To create a service, click the **[!UICONTROL Create]** button located above the list.

![](assets/s_ncs_user_services_add.png)

* Enter the name of the service in the **[!UICONTROL Label]** field and select the delivery channel: email, mobile, Facebook, Twitter, or mobile applications.

   >[!NOTE]
   >
   >En [esta sección](../../social/using/about-social-marketing.md) se detallan las suscripciones a Facebook y Twitter. Las suscripciones a aplicaciones móviles se detallan en [Acerca del canal](../../delivery/using/about-mobile-app-channel.md)de aplicaciones móviles.

* Para el servicio de correo electrónico, seleccione el **Delivery mode**. The possible modes are: **[!UICONTROL Newsletter]** or **[!UICONTROL Viral]**.
* Puede enviar **mensajes de confirmación** para una suscripción o darse de baja. To do this, select the delivery templates to be used to create the corresponding deliveries from the **[!UICONTROL Subscription]** and **[!UICONTROL Unsubscription]** fields. These templates must be configured with a **[!UICONTROL Subscription]** type target mapping, without a defined target. Consulte la sección [Acerca del canal](../../delivery/using/about-email-channel.md)de correo electrónico.
* De forma predeterminada, las suscripciones son ilimitadas. You can deselect the **[!UICONTROL Unlimited]** option to define a validity duration for the service. La duración se puede especificar en días (**[!UICONTROL d]** ) o meses (**[!UICONTROL m]** ).

Una vez guardado el servicio, se agrega a la lista Servicios y suscripciones: Haga clic en su nombre para editarlo. Hay varias pestañas disponibles. The **[!UICONTROL Subscriptions]** tab lets you look at the list of subscribers to the information service (**[!UICONTROL Active subscriptions]** tab) or the subscription/unsubscription history (**[!UICONTROL History]** tab). También puede añadir y eliminar suscriptores de esta pestaña. See [Adding and deleting subscribers](#adding-and-deleting-subscribers).

![](assets/s_ncs_user_services_subscriptions.png)

The **[!UICONTROL Detail...]** button lets you look at the subscription properties for the selected recipient.

Puede modificar las características de la suscripción de un destinatario.

![](assets/s_ncs_user_services_modify.png)

En el tablero, haga clic en la ficha **[!UICONTROL Reports]** para realizar el seguimiento de las suscripciones: cambios en los niveles de suscripción, número total de suscriptores, etc. Puede archivar informes y mirar los historiales desde esta ficha.

## Adición y eliminación de suscriptores {#adding-and-deleting-subscribers}

From the **[!UICONTROL Subscriptions]** tab of an information service click **[!UICONTROL Add]** to add subscribers. You can also right-click the list of subscribers and select **[!UICONTROL Add]**. Select the folder in which the profiles to be subscribed are stored, and then select the profiles to subscribe and click **[!UICONTROL OK]** to validate.

To delete subscribers, select them and click **[!UICONTROL Delete]**. You can also right-click the subscriber list and select **[!UICONTROL Delete]**.

In both cases, you can send a confirmation message to the users concerned if a delivery template for unsubscriptions has been attached to the service (see [Creating an information service](#creating-an-information-service)). Una advertencia permite validar o no validar este envío:

![](assets/s_ncs_user_services_update.png)

See [Subscription and unsubscription mechanisms](#subscription-and-unsubscription-mechanisms).

## Realización de un envío a los suscriptores de un servicio {#delivering-to-the-subscribers-of-a-service}

Para realizar un envío a los suscriptores de un servicio informativo, puede dirigirse a los suscriptores del servicio informativo en cuestión, tal y como se muestra en el siguiente ejemplo:

![](assets/s_ncs_user_wizard_target_is_a_service01.png)

>[!CAUTION]
>
>The target mapping must be **[!UICONTROL Subscriptions]**.

Seleccione **[!UICONTROL Subscribers of an information service]** y haga clic en **[!UICONTROL Next]**.

![](assets/s_ncs_user_wizard_target_is_a_service02.png)

Select the targeted information service and click **[!UICONTROL Finish]**.

![](assets/s_ncs_user_wizard_target_is_a_service03.png)

The **[!UICONTROL Preview]** tab lets you view the list of subscribers to the selected information service.

## Mecanismos de suscripción y baja {#subscription-and-unsubscription-mechanisms}

Puede configurar los mecanismos de suscripción y baja para así automatizar los procesos y la gestión de los suscriptores.

>[!NOTE]
>
>Puede enviar un mensaje de confirmación a los nuevos suscriptores.\
>The content of this message is defined in the information service configuration via the **[!UICONTROL Subscription]** or **[!UICONTROL Unsubscription]** fields.
>
>Los mensajes de confirmación se crean mediante las plantillas de envío especificadas en estos campos. These target mappings must be **[!UICONTROL Subscriptions]**.

![](assets/s_ncs_user_subscribe_confirmation.png)

### Suscripción de un destinatario a un servicio {#subscribing-a-recipient-to-a-service}

Para registrar a los destinatarios en un servicio informativo, puede:

* Manually add the service: to do this, from the **[!UICONTROL Subscriptions]** tab of their profile, click **[!UICONTROL Add]** and select the information service concerned.

   Para obtener más información, consulte la sección de edición de perfiles en [esta sección](../../platform/using/editing-a-profile.md).

* Suscribir automáticamente a un conjunto de destinatarios a este servicio. Puede obtener una lista de destinatarios a través de una operación de filtrado, un grupo, una carpeta, una importación o una selección directa usando el ratón. Para suscribir a estos destinatarios, haga clic con el botón derecho del ratón. Seleccione **[!UICONTROL Actions > Subscribe selection to a service...]**, seleccione el servicio en cuestión e inicie la operación.
* Importación de destinatarios y subscripción automática a un servicio informativo. Para ello, seleccione el servicio correspondiente en el último paso del asistente para importar.

   Para obtener más información, consulte [esta sección](../../platform/using/importing-data.md#import-wizard).

* Uso de un formulario web para que los destinatarios puedan suscribirse a un servicio.

   Para obtener más información, consulte [esta sección](../../web/using/about-web-applications.md).

* Creating a targeting workflow and using a **[!UICONTROL Subscription service]** box.

   ![](assets/s_ncs_user_subscribe_from_wf.png)

   En [esta sección](../../workflow/using/about-workflows.md) se describen los flujos de trabajo y cómo utilizarlos.

### Dar de baja a un destinatario de un servicio {#unsubscribing-a-recipient-from-a-service}

#### Baja manual {#manual-unsubscribing}

los envíos de correo electrónico deben contener, por ley, un enlace para darse de baja. Los destinatarios pueden hacer clic en este enlace para actualizar su perfil y darse de baja de posibles envíos futuros.

The default unsubscription link is inserted via the last button in the toolbar of the content editor provided in the delivery wizard (see [About personalization](../../delivery/using/about-personalization.md)). Cuando el destinatario hace clic en este enlace, el perfil pasa a la lista negra (de exclusión), lo que significa que este destinatario ya no forma parte de ninguna acción de envío.

Sin embargo, los destinatarios pueden optar por cancelar la suscripción de un servicio sin cancelar la suscripción de todos los servicios. To allow this, you can use a web form (refer to [this section](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes)) or insert a personalized unsubscription link (see [Personalization blocks](../../delivery/using/personalization-blocks.md)).

También puede anular la suscripción de un destinatario manualmente desde el perfil del destinatario. To do this, click the **[!UICONTROL Subscriptions]** tab of the recipient concerned, select the information service(s) concerned, and click **[!UICONTROL Delete]**.

A través del servicio informativo correspondiente, pueden cancelar la subscripción de uno o más destinatarios. To do this, click the **[!UICONTROL Subscriptions]** tab of the service, select the recipients concerned and click **[!UICONTROL Delete]**.

#### Baja automática {#automatic-unsubscription}

Un servicio informativo puede tener una duración limitada. Una vez que el periodo de validez haya caducado, se da de baja a los destinatarios de forma automática. This period is specified in the **[!UICONTROL Edit]** tab of the service properties. Se muestra en días.

![](assets/s_ncs_user_services_delay.png)

También puede configurar un flujo de trabajo para darse de baja de una población. To do this, follow the same procedure as for a subscription workflow, but select the **[!UICONTROL Unsubscription]** option. See [Subscribing a recipient to a service](#subscribing-a-recipient-to-a-service).

### Seguimiento del suscriptor {#subscriber-tracking}

You can track the changes in subscriptions to the information services using the **[!UICONTROL Reports]** link on the dashboard.

![](assets/s_ncs_user_services_report.png)
