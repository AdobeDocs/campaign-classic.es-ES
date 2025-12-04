---
product: campaign
title: Canales de comunicación
description: Cree entregas para enviar mensajes personalizados en diferentes canales
feature: Cross Channel Orchestration, Email, SMS, In App, Direct Mail, Push
role: User
exl-id: 92b5e013-b619-4f0b-b0b1-1fc2e653ceac
source-git-commit: 62ab16b206563aa25b8943e606d03a3184eb00db
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 100%

---

# Canales de comunicación{#communication-channels}

Con Adobe Campaign, puede enviar campañas de canales múltiples, incluidos correos electrónicos, SMS, notificaciones push y correo directo, y medir su eficacia mediante varios informes dedicados. Estos mensajes están diseñados y enviados por medio de envíos y pueden personalizarse para cada destinatario.

Las funciones principales incluyen establecimiento de objetivos, definición y personalización de mensajes, ejecución de comunicaciones y los informes operativos asociados.

Como parte de la transición de Campaign v7 a v8, el conjunto de documentación de Campaign Classic se ha optimizado y reorganizado. Ahora, las funciones comunes solo están disponibles en el conjunto de documentación de Campaign v8.

>[!BEGINTABS]

>[!TAB Documentación de canales de comunicación]

Para obtener más información sobre los canales de comunicación, consulte la [documentación de la versión 8 de Campaign](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/gs-message.html?lang=es){target=_blank}.


[![imagen](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/gs-message.html?lang=es){target=_blank}


>[!TAB Contenido y público de envío]

Aprenda los pasos clave relacionados con la creación de envíos, el contenido y el público **en la documentación de la versión 8 de Campaign**:

* [Crear el envío](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=es#create-the-delivery){target="_blank"}: aprenda a crear un envío único con un solo paso.
* [Definir el contenido](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=es#content-of-the-delivery){target="_blank"}: configure el contenido de envío específico para cada canal.
* [Especificar el público](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=es#target-population){target="_blank"}: defina varios tipos de público destinatario: público principal, público destinatario de prueba, direcciones semilla y grupos de control.
* [Trabajar con plantillas de envío](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-templates.html?lang=es){target="_blank"}: aprenda a definir plantillas para facilitar la creación de envíos.





>[!TAB Validación y envío de la entrega]

Consulte estas páginas para obtener información sobre la validación de envíos, el envío y las prácticas recomendadas en **la documentación de Campaign v8**:

* [Validar el envío](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=es#validate-the-delivery){target="_blank"}: aprenda a validar el envío antes de enviarlo al público destinatario principal.
* [Enviar la entrega](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=es#configuring-and-sending-the-delivery){target="_blank"}: configure las opciones de envío y defina cómo enviar los mensajes.
* [Prácticas recomendadas para envíos](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/delivery-best-practices.html?lang=es){target="_blank"}: consulte las prácticas recomendadas relacionadas con las funciones de envío de Campaign.

>[!ENDTABS]

Los siguientes ajustes son específicos de Campaign Classic. Para obtener más información, consulte la [documentación de la versión 8 de Campaign](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/gs-message.html?lang=es){target="_blank"}.

+++ **Análisis de envíos**

**Mejora del rendimiento del análisis de envío**

Para acelerar la preparación del envío, puede marcar la opción **[!UICONTROL Prepare the delivery parts in the database]** antes de iniciar el análisis.

Cuando esta opción está habilitada, la preparación de envíos se realiza directamente en la base de datos, lo que puede acelerar considerablemente el análisis.

Actualmente, esta opción solo está disponible cuando se cumplen las siguientes condiciones:

* El envío debe ser un correo electrónico. Los otros canales no son compatibles por ahora.
* Evite utilizar enrutamiento intermediario o externo, solo el tipo de enrutamiento de envío masivo. Puede comprobar el enrutamiento que se utiliza en la pestaña **[!UICONTROL General]** de la **[!UICONTROL Delivery properties]**.
* No se puede direccionar hacia una población procedente de un archivo externo. Para un solo envío, haga clic en el enlace **[!UICONTROL To]** desde el **[!UICONTROL Email parameters]** y compruebe que la **[!UICONTROL Defined in the database]** opción está seleccionada. Para un envío utilizado en un flujo de trabajo, compruebe que los destinatarios están **[!UICONTROL Specified by the inbound event(s)]** en la pestaña **[!UICONTROL Delivery]**.
* Debe estar utilizando una base de datos PostgreSQL.

**Configuración de la prioridad de análisis**

Cuando la entrega forma parte de una campaña, la pestaña **[!UICONTROL Advanced]** ofrece una opción adicional. Esto permite organizar el orden de procesamiento de los envíos en la misma campaña.

Cada entrega se analiza antes de realizarlo. La duración del análisis depende del archivo de extracción de envíos. Cuanto más significativo sea el tamaño del archivo, más dura el análisis, lo que hace que los siguientes envíos deban esperar.

Las opciones de **[!UICONTROL Message preparation by the scheduler]** permiten priorizar el análisis de envíos en un flujo de trabajo de Campaign.

![](assets/delivery_analysis_priority.png)

Si una entrega es demasiado grande, es mejor asignarle una prioridad baja para evitar ralentizar el análisis de otros envíos del flujo de trabajo.

>[!NOTE]
>
>Para garantizar que los análisis de entrega más grandes no ralenticen el progreso de los flujos de trabajo, se puede programar su ejecución marcando **[!UICONTROL Schedule execution for a time of low activity]**.

+++

+++ **Envío de entregas**

**Configuración de reintentos**

Para los mensajes que no se hayan enviado temporalmente debido a un error **leve** o **ignorado**, se realiza un reintento automático. Los tipos y motivos del error de entrega se presentan en esta [sección](delivery-failures-quarantine.md#delivery-failure-types-and-reasons).

>[!IMPORTANT]
>
>En el caso de instalaciones hospedadas o híbridas, si ha actualizado al [servidor de correo mejorado](sending-with-enhanced-mta.md), la configuración de reintentos de la entrega ya no se utiliza en Campaign. Los reintentos de rechazo temporal y el periodo de tiempo entre ellos están determinados por el servidor de correo mejorado en función del tipo y la gravedad de las respuestas de rechazo procedentes del dominio de correo electrónico del mensaje.

En el caso de instalaciones on-premise e instalaciones hospedadas/híbridas que utilizan el servidor de correo de Campaign heredado, la sección central de la pestaña **[!UICONTROL Delivery]** para parámetros de envío indica cuántos reintentos deben realizarse al día siguiente del envío y el margen mínimo entre reintentos.

![](assets/s_ncs_user_wizard_retry_param.png)

De manera predeterminada, se programan cinco reintentos para el primer día de la entrega con un intervalo mínimo de una hora distribuidos durante las 24 horas del día. Después de ello, se programa un reintento por día hasta la fecha límite de entrega, que se define en la pestaña **[!UICONTROL Validity]**. Consulte la próxima sección.

**Definición del período de validez**

Una vez iniciada la entrega, se pueden enviar los mensajes (y los reintentos) hasta la fecha límite de entrega. Esto se indica en las propiedades de envío a través de la pestaña **[!UICONTROL Validity]**.

![](assets/s_ncs_user_email_del_valid_period.png)

* El campo **[!UICONTROL Delivery duration]** permite introducir el límite de los reintentos de envío global. Esto significa que Adobe Campaign envía los mensajes comenzando en la fecha de inicio y, a continuación, para los mensajes que devuelven solo un error se realizan reintentos normales y configurables hasta que se alcanza el límite de validez.

  Asimismo, puede especificar fechas. Para ello, seleccione **[!UICONTROL Explicitly set validity dates]**. En este caso, las fechas de envío y de límite de validez también permiten especificar el tiempo. El tiempo actual se utiliza de forma predeterminada, pero puede modificarse directamente en el campo de entrada.

  >[!IMPORTANT]
  >
  >En el caso de instalaciones hospedadas o híbridas, si se ha actualizado al [servidor de correo mejorado](sending-with-enhanced-mta.md), la configuración **[!UICONTROL Delivery duration]** en sus envíos de correo electrónico de Campaign se utilizará únicamente si se establece en **3,5 días o menos**. Si define un valor superior a 3,5 días, no se tendrá en cuenta.

* **Límite de validez de los recursos**: El campo **[!UICONTROL Validity limit]** se utiliza para los recursos cargados, principalmente para la página espejo y las imágenes. Los recursos de esta página son válidos durante un tiempo limitado (para ahorrar espacio en el disco).

  Los valores de este campo se pueden expresar en las unidades enumeradas en [esta sección](../../platform/using/adobe-campaign-workspace.md#default-units).

+++

<!--

   Learn how to create a one-shot single delivery. You can create other types of deliveries to build your use cases. 

For more information about the different types of deliveries and how to create them, refer to the [Campaign v8 documentation](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html){target="_blank"}. 

>[!NOTE]
>
>Adobe Campaign offers a set of tools to monitor your deliverability and optimize email sending. Learn more in [this section](about-deliverability.md).

Delivery sending can be automated by preparing a delivery and/or sending it in the process of a workflow. For more on delivery-type activities in workflows, refer to [this section](../../workflow/using/about-action-activities.md).

Adobe Campaign offers the following delivery channels:

1. **Email channel**: email deliveries let you send personalized emails to the target population. Refer to [About email channel](about-email-channel.md).
1. **Direct mail channel**: direct mail deliveries let you generate an extraction file which contains data on the target population. Refer to [About direct mail channel](about-direct-mail-channel.md).
1. **Mobile channel**: deliveries on mobile channels let you send personalized SMS or LINE messages to the target population. Refer to [SMS channel](sms-channel.md).
1. **Mobile application channel**: mobile app deliveries let you send notifications to iOS and Android systems. Refer to the [Mobile app channel](about-mobile-app-channel.md) chapter.

   Other channels are described on [this section](#other-channels).

   >[!NOTE]
   >
   >The number of available channels depends on your contract. Please check your license agreement.

Deliveries can be carried out **online** (via email, one of the mobile channels and push notifications), and **offline** (direct mail channel).

Depending on the channel, delivery modes can be:

* Direct mass delivery via Adobe Campaign (default mode for email channel).
* External delivery via a specialist operator who is given the output file generated by the delivery assistant (default mode for direct mail channel).

External accounts are configured via the **[!UICONTROL Administration > Platform > External accounts]** node. This configuration should be performed by expert users only.

## Email deliveries {#email-deliveries}

The [Email channel](about-email-channel.md) is one of the core channels in Adobe Campaign, allowing you to schedule and send personalized emails to specific targets.

You can send different types of emails:

* Single-send emails: emails that you can send once to a defined target. They are usually used to promote a specific content that would be prepared and sent only once (newsletter, promotional email, etc.).
* Recurring emails: in a campaign, send the same email regularly and aggregate each send and its reports on a periodic basis. The same email is sent, but usually to a different target, based on the eligible target for the day of the send. A common example is a birthday email. For more on this, refer to [Recurring deliveries](../../workflow/using/recurring-delivery.md).
* Transactional emails: unitary emails that are triggered based on your customers' behavior. Refer to [Transactional messaging](../../message-center/using/about-transactional-messaging.md).

To learn about delivery usage and recommendations, consult Campaign [Delivery best practices](delivery-best-practices.md).

For more on the different types of deliveries, refer to [this section](#types-of-deliveries).

## Mobile deliveries {#mobile-deliveries}

Adobe Campaign allows you to deliver [SMS](sms-channel.md) and [LINE](line-channel.md) messages on mobiles.

For SMS messages, you can create, modify, and personalize messages in text format only. You can also preview your SMS messages before they are sent.

For LINE messages, you can send text or images and links.

To deliver SMS or LINE messages to a mobile phone you need:

* An external account configured on the **[!UICONTROL Mobile (SMS)]** channel or on the **[!UICONTROL LINE]** channel. 
* An SMS or LINE delivery template that is correctly linked to this external account.

## Push notifications {#push-notifications}

Adobe Campaign allows you to send personalized and segmented [push notifications](about-mobile-app-channel.md) on iOS and Android mobile devices, through dedicated apps. Once configuration and integration steps have been performed, iOS and Android deliveries can be created and sent. You can also design rich notifications with images or videos.

## Direct mail {#direct-mail}

[Direct mail](about-direct-mail-channel.md) is an offline channel that allows you to personalize and generate the file required by direct mail providers. It gives you the possibility to mix online and offline channels in your customer journeys.

Online channels allow you to create your messages (email, SMS, mobile app delivery, etc.) and send them to your audience directly from Adobe Campaign. With offline channels, it is different. When you prepare a direct mail delivery, Adobe Campaign generates a file including all the targeted profiles and the chosen contact information (postal address for example). You will then be able to send this file to your direct mail provider who will take care of the actual sending.

## Other channels {#other-channels}

Adobe Campaign offers Telephone delivery template, which is used to create external deliveries. Using this channel implies you set up dedicated methodologies to process output files. Configuration steps are the same as for [Direct mail channel](about-direct-mail-channel.md).

>[!NOTE]
>
>The Telephone channel is not available out-of-the-box. Its implementation requires Adobe Consulting or an Adobe Partner to be engaged. Please reach out to your Adobe representative for more information.

In addition, 'Other' type deliveries use a specific technical template which does not execute a process: this lets them manage marketing actions executed outside of the Adobe Campaign platform.

This channel has no specific mechanism. It is a generic channel that has its own external account routing option, delivery template type and campaign workflow activity, just like any other communication channel available in Adobe Campaign.

This channel is designed for descriptive purposes only, for example to define deliveries for which you want to keep a trace of the target of a campaign performed in a tool other than Adobe Campaign.

## Types of deliveries{#types-of-deliveries}

There are three types of delivery objects in Campaign:

### Single delivery {#single-delivery}

A **delivery** is a standalone delivery object that is executed once. It can be duplicated, prepared again, but as long as it is in its final state (canceled, stopped, finished), it cannot be reused.

Deliveries can be created either from the list of deliveries, or within a workflow via a [Delivery](../../workflow/using/delivery.md) activity.

Workflows also provide specific delivery activities according to the type of channel you want to use. For more on these activities, refer to [this section](../../workflow/using/cross-channel-deliveries.md).

### Recurring delivery {#recurring-delivery}

A **recurring delivery** lets you create a new delivery each time the activity is executed. This avoids you having to create a new delivery for recurring tasks.

As an example, if you run this type of activity once a month, you will end up with 12 deliveries after a year.

Recurring deliveries are created within workflows via the [Recurring delivery activity](../../workflow/using/recurring-delivery.md). An example of this activity being used is presented in this section: [Creating a recurring delivery in a targeting workflow](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

### Continuous delivery {#continuous-delivery}

A **continuous delivery** lets you add new recipients to an existing delivery, which avoids having to create a new delivery each time it is executed.

If an information in the delivery changes (content, name, etc.), a new delivery object is created at the delivery execution. If no information was changed, the same delivery object is reused and the delivery and tracking logs are added in the same object.

As an example, if you run this type of activity once a month, you will end up with a single delivery after a year (provided you did not make any change to the delivery).

Continuous deliveries are created within workflows via the [Continuous delivery activity](../../workflow/using/continuous-delivery.md).-->
