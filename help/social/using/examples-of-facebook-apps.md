---
title: Ejemplos de aplicaciones de Facebook
seo-title: Ejemplos de aplicaciones de Facebook
description: Ejemplos de aplicaciones de Facebook
seo-description: null
page-status-flag: never-activated
uuid: 336f4006-3545-4b04-959d-61cd0446af27
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: annexes
discoiquuid: 07be1d3c-b038-48ca-be37-a33adb8e0fc0
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1985'
ht-degree: 61%

---


# Ejemplos de aplicaciones de Facebook{#examples-of-facebook-apps}

Cuando un usuario hace clic en la ficha de una aplicación de Facebook, se muestra en un espacio de 810 píxeles de ancho. Adobe Campaign utiliza una aplicación web de tipo Facebook para permitirle definir y personalizar el contenido mostrado en la aplicación de Facebook, lo que facilita la adquisición de perfiles.

>[!NOTE]
>
>También es posible integrar Adobe Campaign con una aplicación de Facebook desarrollada por un socio. En este caso, no es necesario utilizar la aplicación web de Adobe Campaign para adquirir perfiles de Facebook. Para más información, consulte [Configuración de cuentas externas](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

![](assets/social_webapp_fb_000.png)

>[!IMPORTANT]
>
>Siga los pasos de configuración descritos en [Creación de una aplicación de Facebook](../../social/using/creating-a-facebook-application.md).

>[!NOTE]
>
>Esta sección detalla los elementos vinculados a las aplicaciones web de tipo Facebook. Todos los elementos compartidos con aplicaciones web estándar se detallan en [esta sección](../../web/using/about-web-applications.md).

Los ejemplos de aplicaciones web de tipo Facebook detallados a continuación son:

* Cómo crear una aplicación de Facebook en 7 pasos. Consulte [Inicio rápido: creación de una aplicación de Facebook en 7 pasos](#quick-start--creating-a-facebook-application-in-7-steps).
* Cómo reenviar la configuración a una aplicación de Facebook. Consulte [¿Cómo reenviar la configuración a una aplicación de Facebook?](#how-to-forward-settings-to-a-facebook-application-).
* Cómo adquirir datos de seguidores. Consulte [¿Cómo adquirir datos de seguidores?](#how-to-acquire-fan-data-).

>[!IMPORTANT]
>
>Estos casos de uso sencillo se proporcionan como ejemplos para ilustrar las funcionalidades de las aplicaciones web de tipo Facebook.

## Recomendaciones {#recommendations}

Las siguientes limitaciones están vinculadas directamente a Facebook:

* Debe crear todas las aplicaciones web en HTTPS.
* Una aplicación de Facebook que se muestra mediante una ficha tiene una anchura de 810 píxeles.

## Inicio rápido: creación de una aplicación de Facebook en 7 pasos {#quick-start--creating-a-facebook-application-in-7-steps}

Este ejemplo proporciona un proceso paso a paso de cómo mostrar una aplicación creada por Adobe Campaign en Facebook. En este caso, deseamos crear una aplicación que le permita mostrar el mensaje de **bienvenida** cuando el usuario haga clic en la ficha de la aplicación (**App01**).

Para crear esta aplicación, aplique los pasos siguientes:

1. Cree una aplicación en Facebook ([https://developers.facebook.com/apps](https://developers.facebook.com/apps)). Para más información, consulte [Creación de una aplicación de Facebook](../../social/using/publishing-on-facebook-walls.md#creating-a-facebook-application).

   ![](assets/social_create_facebook_app_002.png)

1. Create a **[!UICONTROL Facebook Connect]** type external account and enter the parameters of the Facebook application. Para más información, consulte [Configuración de cuentas externas](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

   ![](assets/social_quick_start_2.png)

1. Introduzca los vínculos **[!UICONTROL Terms of service]** y **[!UICONTROL Privacy policy]** que se mostrarán en la pantalla de solicitud de permisos de Facebook. Para obtener más información, consulte: [Introducción de los vínculos de condiciones de servicio y política de privacidad](../../social/using/creating-a-facebook-application.md#entering-the-terms-of-service-and-privacy-policy-links).

   ![](assets/social_quick_start_1.png)

1. Cree una aplicación web de tipo Facebook en Adobe Campaign. Para obtener más información, consulte: [Creación de una aplicación web de tipo Facebook](../../social/using/creating-a-facebook-application.md#creating-a-facebook-type-web-application).

   ![](assets/social_webapp_005.png)

1. Edite la aplicación web. In this example, we have added a **[!UICONTROL Page]** activity and defined a title for it.

   ![](assets/social_quick_start_4.png)

1. Implemente la aplicación.

   ![](assets/social_webapp_004.png)

1. Configure la aplicación de Facebook para que se muestre como una ficha en la página de Facebook. Para más información, consulte [Configuración de pestañas de Facebook](../../social/using/creating-a-facebook-application.md#configuring-facebook-tabs).

   ![](assets/social_quick_start_5.png)

![](assets/social_quick_start_6.png)

Compruebe que la ficha de la aplicación **App01** aparece en la página de Facebook. Al hacer clic en él, se debe llamar a un mensaje de **Bienvenida**.

![](assets/social_webapp_042.png)

## ¿Cómo reenviar la configuración a una aplicación de Facebook? {#how-to-forward-settings-to-a-facebook-application-}

>[!IMPORTANT]
>
>Siga los pasos de configuración detallados en [Creación de una aplicación de Facebook](../../social/using/creating-a-facebook-application.md).

In example 1, we personalized the display of the Facebook page according to the value in the **[!UICONTROL Fan of the page]** field. It is also possible to process the **[!UICONTROL Application settings]** field. Este campo permite recuperar datos contenidos en un vínculo generado por Adobe Campaign a través de Facebook.

Veamos el ejemplo de una empresa que decide enviar una campaña de correo electrónico. En la entrega, un vínculo apunta a la aplicación Facebook. This link is personalized thanks to the **[!UICONTROL app_data]** parameter added at the end of the URL. El valor de este parámetro podría ser un indicador que refleje la importancia del cliente. In our example, the values of the **[!UICONTROL app_data]** parameter are **[!UICONTROL big]** (significant customer) and **[!UICONTROL small]** (less significant customer).

Una vez personalizada, la dirección URL tiene este aspecto:

* `http://<path of the Facebook application>&app_data=big` (para un cliente importante)
* `http://<path of the Facebook application>&app_data=small` (para un cliente menos significativo)

Among the anonymous data forwarded to Adobe Campaign by Facebook, the value of the **[!UICONTROL Application parameters]** field is collected, thus enabling Adobe Campaign to personalize application display based on this parameter.

If the user is a significant customer (the value of the **[!UICONTROL app_data]** parameter is **[!UICONTROL big]**), the following image is displayed:

![](assets/social_webapp_017.png)

If the user is a less significant customer (the value of the **[!UICONTROL app_data]** parameter is **[!UICONTROL small]**), the following image is displayed:

![](assets/social_webapp_016.png)

Para recrear este ejemplo de uso, se ha creado una aplicación web compuesta por los siguientes elementos:

* Una **[!UICONTROL Test]** actividad basada en el **[!UICONTROL Application parameter]** campo.
* two pages which contain the images to display according to the value of the **[!UICONTROL Application parameter]** field.

![](assets/social_webapp_018.png)

## ¿Cómo se adquieren los datos del ventilador? {#how-to-acquire-fan-data-}

>[!CAUTION]
>
>Siga los pasos de configuración detallados en [Creación de una aplicación de Facebook](../../social/using/creating-a-facebook-application.md).

Este ejemplo muestra cómo ponerse en contacto con usuarios de Facebook y ofrecerles que compartan su información de perfil. Veamos el ejemplo de una empresa que quiere adquirir perspectivas y organiza una competencia en su página de Facebook para atraerlos.

Cada vez que un usuario hace clic en la ficha **[!UICONTROL App03]**, le preguntamos si desea participar en la competencia.

![](assets/social_webapp_fb_000.png)

Si deciden participar en el concurso, les ofrecemos compartir su información de perfil.

![](assets/social_webapp_021.png)

Si aceptan compartir su información, se muestra la siguiente pantalla.

![](assets/social_webapp_022.png)

Para crear este ejemplo de uso, se ha creado una aplicación web compuesta por los siguientes elementos:

* una actividad **[!UICONTROL Test]**
* tres páginas
* una actividad **[!UICONTROL Access control]**
* una actividad **[!UICONTROL Pre-loading]**
* una actividad **[!UICONTROL Save]**
* una actividad **[!UICONTROL End]**

![](assets/social_webapp_019.png)

### Actividad de prueba {#test-activity}

La **[!UICONTROL Test]** actividad se basa en el **[!UICONTROL ID]** campo y **[!UICONTROL Application parameters]** .

![](assets/social_webapp_023.png)

Están formadas por varias ramas:

* **[!UICONTROL identifier (UID) is empty]** :: el identificador solo lo reenvía Facebook si el usuario ya ha aceptado compartir su información. The first branch of the **[!UICONTROL Test]** activity lets you make the competition available only to users who have never entered, i.e. those with an empty ID.
* **[!UICONTROL application parameter equals 'thanks']** :: para evitar un error de visualización vinculado a Facebook, la página final de la aplicación web apunta a la URL de la aplicación Facebook a la que se agrega el **[!UICONTROL app_data]** parámetro mediante el uso del **[!UICONTROL thanks]** valor (para obtener más información sobre esto, consulte: [Actividad](#end-activity)final). The second branch lets you find out whether the user comes from the **[!UICONTROL End]** activity of the first branch (and has just entered the competition) to display a thank you message. Para obtener más información sobre el uso de parámetros de URL adicionales, consulte: [¿Cómo reenviar la configuración a una aplicación de Facebook?](#how-to-forward-settings-to-a-facebook-application-).
* **[!UICONTROL Default branch]** :: si el usuario ya ha ingresado a la competencia (ID ya ingresado) en una fecha anterior (parámetro de aplicación distinto de **[!UICONTROL thanks]**), se mostrará una página que indicará que ya ha ingresado.

### Página de competencia {#competition-page}

Para evitar el error de visualización vinculado a Facebook, también debe seleccionar **[!UICONTROL Parent window]** o **[!UICONTROL In the top window]** en el campo de la página **[!UICONTROL Window]** de competencia.

![](assets/social_webapp_028.png)

### Actividad de control de acceso {#access-control-activity}

The **[!UICONTROL Access control]** activity lets you display the Facebook permission request page when the user enters the competition. Si aceptan compartir su información, se recupera durante la precarga. Para obtener más información, consulte [Actividad de precarga](#pre-loading-activity).

Si previamente ha introducido la cuenta externa al crear la aplicación web (consulte [Creación de una aplicación](../../social/using/creating-a-facebook-application.md#creating-a-facebook-type-web-application) web de tipo Facebook), no es necesario editar la actividad. If not, go to the **[!UICONTROL Application]** field and select the external account linked to the Facebook application.

![](assets/social_webapp_024.png)

### Actividad de precarga {#pre-loading-activity}

Seleccione la fuente de datos que se utilizará para la precarga:

* **[!UICONTROL Marketing database]** :: esta opción le permite cargar previamente los datos mediante la base de datos de Adobe Campaign.
* **[!UICONTROL Facebook]**: esta opción le permite cargar previamente datos mediante Facebook.

![](assets/social_webapp_029.png)

**Base de datos de marketing**

Esta opción le permite recuperar los datos de un perfil que existe en la tabla de visitantes. La verificación se realiza en función del ID de Facebook externo recuperado cuando el usuario hace clic en la ficha de la aplicación de Facebook. If you add a form after the **[!UICONTROL Pre-loading]** activity, the fields which contain information in the database are pre-loaded.

![](assets/social_webapp_030.png)

>[!NOTE]
>
>Para obtener más información sobre la precarga de datos mediante la base de datos de Adobe Campaign, consulte [esta sección](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data).

**Facebook**

Esta opción permite definir la información de perfil de Facebook que se va a recopilar, entre la que el usuario ha aceptado compartir, para poder guardarla.

![](assets/social_webapp_025.png)

The **[!UICONTROL Database information]** option lets you collect the following data:

* **[!UICONTROL External ID]**:: ID de usuario
* **[!UICONTROL Gender]**:: sexo del usuario
* **[!UICONTROL Verified]** :: este campo especifica si el usuario tiene o no una cuenta de Facebook verificada.
* **[!UICONTROL Full name]**:: nombre completo del usuario
* **[!UICONTROL First name]**:: nombre del usuario
* **[!UICONTROL Last name]**:: apellido del usuario
* **[!UICONTROL Language]**:: idioma del usuario

También puede decidir recopilar la foto del perfil, la lista de amigos, la dirección de correo electrónico, la fecha de nacimiento, los intereses y la ubicación marcando las casillas correspondientes.

Antes de hacer clic **[!UICONTROL Ok]**, marque la **[!UICONTROL I agree to comply with Facebook conditions of use]** casilla.

>[!NOTE]
>
>If you check one or more boxes in the **[!UICONTROL Private information]** section, the Facebook permission request screen will automatically display the access request for this data.
>
>Para que pueda recopilar la información seleccionada, el usuario debe aceptar compartirla.
>
>Si desea que ambos tipos de precarga (a través de Adobe Campaign y de Facebook) agreguen dos cuadros de precarga uno tras otro.

### Guardar actividad {#save-activity}

The **[!UICONTROL Save]** activity lets you store the information collected during the previous stages in the visitors&#39; table.

Si el perfil ya existe en la tabla de visitantes, sus datos se actualizan con los nuevos datos recopilados.

Si el perfil no existe en la base de datos y se ha recopilado la dirección de correo electrónico del usuario de Facebook, se creará un visitante en la tabla de visitantes.

![](assets/social_webapp_026.png)

1. In the **[!UICONTROL Visitor creation folder]** field, select the folder which the profile will be created in. In case of a Facebook type web application, the default creation folder is **[!UICONTROL Visitors]**.
1. In the **[!UICONTROL Reconciliation mode]** field, select the reconciliation mode you want to use:

   * **[!UICONTROL Automatic]** :: La reconciliación se realiza por correo electrónico, apellidos, nombre y fecha de nacimiento.
   * **[!UICONTROL Manual]**: Seleccione una o varias claves de reconciliación.
   * **[!UICONTROL None]** :: No habrá reconciliación.

1. In the **[!UICONTROL Mapping]** field, select the schema which you want to carry out the reconciliation on.

   >[!CAUTION]
   >
   >Make sure the fields of the **[!UICONTROL Social networks]** tab are correctly entered in the delivery mapping. Se accede a las asignaciones de envío a través del **[!UICONTROL Administration > Campaign management > Target mappings]** nodo.

1. Puede seleccionar una carpeta de búsqueda para la reconciliación y una carpeta de creación de nuevos perfiles. Si los campos están vacíos, se buscarán y crearán perfiles en la carpeta predeterminada del esquema de asignación.

### Actividad final {#end-activity}

To sidestep the display error linked to Facebook, you need to check the **[!UICONTROL Use an external URL]** box and enter the URL of the Facebook application, followed by the **[!UICONTROL app_data]** parameter and a value. This value will be used in the **[!UICONTROL Test]** activity to detect whether or not the user has just entered the competition, and to display a thank you message if applicable. Para obtener más información, consulte [Actividad de prueba](#test-activity).

En nuestro ejemplo, el valor utilizado es **gracias**.

![](assets/social_webapp_027.png)

### Pantalla de detalles de un visitante {#details-screen-of-a-visitor}

Igual que para los seguidores de Twitter (consulte: [Principio de operación](../../social/using/publishing-on-twitter.md#operating-principle)), los perfiles de Facebook recuperados se almacenan en la tabla de visitantes. To display the list of visitors, go to the **[!UICONTROL Profiles and Targets > Visitors]** node.

Cada posible cliente de Facebook que acepte compartir su información de perfil se agrega a la lista de visitantes. If the **[!UICONTROL Friends]** box is checked in the **[!UICONTROL Pre-load]** activity (refer to: [Pre-loading activity](#pre-loading-activity)), friends are also added.

![](assets/social_webapp_037.png)

In the **[!UICONTROL Summary]** section of the visitor detail window, there are two possible states for the **[!UICONTROL New Contact]** indicator:

![](assets/social_webapp_038.png)

Si se muestra una marca de verificación verde, significa que el visitante no se reconcilió con ningún destinatario. En este caso, se crea un nuevo perfil en la lista de destinatarios.

![](assets/social_webapp_039.png)

Una cruz roja significa que el visitante se reconcilió con un destinatario. You can click the magnifier to the right of the **[!UICONTROL Recipient]** field to display the matching recipient.

![](assets/social_webapp_040.png)

Vaya a la ventana de detalles de un destinatario para mostrar el visitante coincidente, si corresponde. Select the **[!UICONTROL Others]** tab, then double-click the name of the visitor in the **[!UICONTROL Web identities]** section.

![](assets/social_webapp_041.png)

The **[!UICONTROL Activities]** screen of a visitor&#39;s details page contains the following information:

* Actividades de abanico de tipo &quot;Open Graph&quot;: música reproducida, videos vistos, artículos leídos e inferencias de las aplicaciones instaladas (Deezer, Spotify, Dailymotion, Yahoo News, etc.)

   ![](assets/social_facebook_activities.png)

* &quot;Me gusta&quot; y comentarios añadidos por el seguidor después de las entregas enviadas por Adobe Campaign
* páginas a las que les gusta el seguidor
* registros por parte del seguidor

   ![](assets/social_facebook_checkins.png)

   >[!NOTE]
   >
   >In order for Adobe Campaign to collect a fan&#39;s check-ins, you need to click the **[!UICONTROL Subscribe]** button on the service configuration screen. Para más información, consulte [Configuración de cuentas externas](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

## Cómo cargar previamente los campos de un formulario mediante datos de perfil de Facebook {#how-to-pre-load-the-fields-of-a-form-using-facebook-profile-data}

La aplicación **[!UICONTROL Social Marketing]** también permite agregar un botón a un formulario para precargar campos usando información de perfil de Facebook. This option, which is available in all web application templates (**[!UICONTROL Page]** type activities) is detailed in [this section](../../web/using/static-elements-in-a-web-form.md#inserting-html-content).

![](assets/social_webapp_035.png)

>[!NOTE]
>
>Antes de empezar a utilizar esta función, debe crear una aplicación de Facebook y una cuenta externa de tipo **[!UICONTROL Facebook Connect]**. Para más información, consulte [Configuración de cuentas externas](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

