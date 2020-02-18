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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2e18121e4094bc4cb215e5471091810df56b3ef5

---


# Ejemplos de aplicaciones de Facebook{#examples-of-facebook-apps}

Cuando un usuario hace clic en la ficha de una aplicación de Facebook, se muestra en un espacio de 810 píxeles de ancho. Adobe Campaign utiliza una aplicación web de tipo Facebook para permitirle definir y personalizar el contenido mostrado en la aplicación de Facebook, lo que facilita la adquisición de perfiles.

>[!NOTE]
>
>También es posible integrar Adobe Campaign con una aplicación de Facebook desarrollada por un socio. En este caso, no es necesario utilizar la aplicación web de Adobe Campaign para adquirir perfiles de Facebook. For more on this, refer to [Configuring external accounts](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

![](assets/social_webapp_fb_000.png)

>[!IMPORTANT]
>
>Siga los pasos de configuración descritos en [Creación de una aplicación](../../social/using/creating-a-facebook-application.md)de Facebook.

>[!NOTE]
>
>Esta sección detalla los elementos vinculados a las aplicaciones web de tipo Facebook. Todos los elementos compartidos con aplicaciones web estándar se detallan en [esta sección](../../web/using/about-web-applications.md).

Los ejemplos de aplicaciones web de tipo Facebook detallados a continuación son:

* Cómo crear una aplicación de Facebook en 7 pasos. Consulte Inicio [rápido: creación de una aplicación de Facebook en 7 pasos](#quick-start--creating-a-facebook-application-in-7-steps).
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

Para crear esta aplicación, siga los pasos siguientes:

1. Cree una aplicación en Facebook ( [https://developers.facebook.com/apps](https://developers.facebook.com/apps)). Para obtener más información sobre esto, consulte: [Creación de una aplicación](../../social/using/publishing-on-facebook-walls.md#creating-a-facebook-application)de Facebook.

   ![](assets/social_create_facebook_app_002.png)

1. Cree una cuenta externa de **[!UICONTROL Facebook Connect]** tipo e introduzca los parámetros de la aplicación de Facebook. For more on this, refer to: [Configuring external accounts](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

   ![](assets/social_quick_start_2.png)

1. Introduzca los vínculos **[!UICONTROL Terms of service]** y **[!UICONTROL Privacy policy]** que se mostrarán en la pantalla de solicitud de permisos de Facebook. Para obtener más información sobre esto, consulte: [Introducción de los enlaces](../../social/using/creating-a-facebook-application.md#entering-the-terms-of-service-and-privacy-policy-links)de Condiciones de servicio y Política de privacidad.

   ![](assets/social_quick_start_1.png)

1. Cree una aplicación web de tipo Facebook en Adobe Campaign. Para obtener más información sobre esto, consulte: [Creación de una aplicación](../../social/using/creating-a-facebook-application.md#creating-a-facebook-type-web-application)web de tipo Facebook.

   ![](assets/social_webapp_005.png)

1. Edite la aplicación web. En este ejemplo, hemos agregado una **[!UICONTROL Page]** actividad y definido un título para ella.

   ![](assets/social_quick_start_4.png)

1. Implemente la aplicación.

   ![](assets/social_webapp_004.png)

1. Configure la aplicación de Facebook para que se muestre como una ficha en la página de Facebook. For more on this, refer to: [Configuring Facebook tabs](../../social/using/creating-a-facebook-application.md#configuring-facebook-tabs).

   ![](assets/social_quick_start_5.png)

![](assets/social_quick_start_6.png)

Compruebe que la ficha de la aplicación **App01** aparece en la página de Facebook. Al hacer clic en él, se debe llamar a un mensaje de **bienvenida** .

![](assets/social_webapp_042.png)

## ¿Cómo reenviar la configuración a una aplicación de Facebook? {#how-to-forward-settings-to-a-facebook-application-}

>[!IMPORTANT]
>
>Siga los pasos de configuración detallados en [Creación de una aplicación](../../social/using/creating-a-facebook-application.md)de Facebook.

En el ejemplo 1, personalizamos la visualización de la página de Facebook según el valor del **[!UICONTROL Fan of the page]** campo. También es posible procesar el **[!UICONTROL Application settings]** campo. Este campo permite recuperar datos contenidos en un vínculo generado por Adobe Campaign a través de Facebook.

Veamos el ejemplo de una empresa que decide enviar una campaña de correo electrónico. En la entrega, un vínculo apunta a la aplicación Facebook. Este vínculo se personaliza gracias al **[!UICONTROL app_data]** parámetro añadido al final de la dirección URL. El valor de este parámetro podría ser un indicador que refleje la importancia del cliente. En nuestro ejemplo, los valores del **[!UICONTROL app_data]** parámetro son **[!UICONTROL big]** (cliente significativo) y **[!UICONTROL small]** (cliente menos significativo).

Una vez personalizada, la dirección URL tiene este aspecto:

* `http://<path of the Facebook application>&app_data=big` (para un cliente importante)
* `http://<path of the Facebook application>&app_data=small` (para un cliente menos significativo)

Entre los datos anónimos que Facebook envía a Adobe Campaign, se recopila el valor del **[!UICONTROL Application parameters]** campo, lo que permite a Adobe Campaign personalizar la visualización de la aplicación en función de este parámetro.

Si el usuario es un cliente significativo (el valor del **[!UICONTROL app_data]** parámetro es **[!UICONTROL big]**), se muestra la siguiente imagen:

![](assets/social_webapp_017.png)

Si el usuario es un cliente menos significativo (el valor del **[!UICONTROL app_data]** parámetro es **[!UICONTROL small]**), se muestra la siguiente imagen:

![](assets/social_webapp_016.png)

Para volver a crear este caso de uso, hemos creado una aplicación web formada por los siguientes elementos:

* Una **[!UICONTROL Test]** actividad basada en el **[!UICONTROL Application parameter]** campo.
* dos páginas que contienen las imágenes que se van a mostrar según el valor del **[!UICONTROL Application parameter]** campo.

![](assets/social_webapp_018.png)

## ¿Cómo se adquieren los datos del ventilador? {#how-to-acquire-fan-data-}

>[!CAUTION]
>
>Siga los pasos de configuración detallados en [Creación de una aplicación](../../social/using/creating-a-facebook-application.md)de Facebook.

Este ejemplo muestra cómo ponerse en contacto con usuarios de Facebook y ofrecerles que compartan su información de perfil. Veamos el ejemplo de una empresa que quiere adquirir perspectivas y organiza una competencia en su página de Facebook para atraerlos.

Cada vez que un usuario hace clic en la **[!UICONTROL App03]** ficha, le preguntamos si desea participar en la competencia.

![](assets/social_webapp_fb_000.png)

Si deciden participar en el concurso, les ofrecemos compartir su información de perfil.

![](assets/social_webapp_021.png)

Si aceptan compartir su información, se muestra la siguiente pantalla.

![](assets/social_webapp_022.png)

Para crear este caso de uso, hemos creado una aplicación web que incluye los siguientes elementos:

* a **[!UICONTROL Test]** activity
* tres páginas
* una **[!UICONTROL Access control]** actividad
* a **[!UICONTROL Pre-loading]** activity
* a **[!UICONTROL Save]** activity
* una **[!UICONTROL End]** actividad

![](assets/social_webapp_019.png)

### Actividad de prueba {#test-activity}

La **[!UICONTROL Test]** actividad se basa en el **[!UICONTROL ID]** campo y **[!UICONTROL Application parameters]** .

![](assets/social_webapp_023.png)

Se compone de tres ramas:

* **[!UICONTROL identifier (UID) is empty]** :: el identificador solo lo reenvía Facebook si el usuario ya ha aceptado compartir su información. La primera rama de la **[!UICONTROL Test]** actividad le permite poner la competencia a disposición únicamente de los usuarios que nunca han entrado, es decir, aquellos con un ID vacío.
* **[!UICONTROL application parameter equals 'thanks']** :: para evitar un error de visualización vinculado a Facebook, la página final de la aplicación web apunta a la URL de la aplicación Facebook a la que se agrega el **[!UICONTROL app_data]** parámetro mediante el uso del **[!UICONTROL thanks]** valor (para obtener más información sobre esto, consulte: [Finalizar actividad](#end-activity)). La segunda rama le permite averiguar si el usuario proviene de la **[!UICONTROL End]** actividad de la primera rama (y acaba de entrar en la competencia) para mostrar un mensaje de agradecimiento. Para obtener más información sobre el uso de parámetros de URL adicionales, consulte: ¿ [Cómo reenviar la configuración a una aplicación de Facebook?](#how-to-forward-settings-to-a-facebook-application-).
* **[!UICONTROL Default branch]** :: si el usuario ya ha ingresado a la competencia (ID ya ingresado) en una fecha anterior (parámetro de aplicación distinto de **[!UICONTROL thanks]**), se mostrará una página que indicará que ya ha ingresado.

### Página de competencia {#competition-page}

Para evitar el error de visualización vinculado a Facebook, también debe seleccionar **[!UICONTROL Parent window]** o **[!UICONTROL In the top window]** en el campo de la página **[!UICONTROL Window]** de competencia.

![](assets/social_webapp_028.png)

### Actividad de control de acceso {#access-control-activity}

La **[!UICONTROL Access control]** actividad permite mostrar la página de solicitud de permiso de Facebook cuando el usuario entra en la competencia. Si aceptan compartir su información, se recupera durante la precarga. For more on this, refer to: [Pre-loading activity](#pre-loading-activity).

Si previamente ha introducido la cuenta externa al crear la aplicación web (consulte [Creación de una aplicación](../../social/using/creating-a-facebook-application.md#creating-a-facebook-type-web-application)web de tipo Facebook), no es necesario editar la actividad. Si no es así, vaya al **[!UICONTROL Application]** campo y seleccione la cuenta externa vinculada a la aplicación Facebook.

![](assets/social_webapp_024.png)

### Actividad de precarga {#pre-loading-activity}

Seleccione la fuente de datos que se utilizará para la precarga:

* **[!UICONTROL Marketing database]** :: esta opción le permite cargar previamente los datos mediante la base de datos de Adobe Campaign.
* **[!UICONTROL Facebook]** :: esta opción le permite cargar previamente datos mediante Facebook.

![](assets/social_webapp_029.png)

**Base de datos de marketing**

Esta opción le permite recuperar los datos de un perfil que existe en la tabla de visitantes. La verificación se realiza en función del ID de Facebook externo recuperado cuando el usuario hace clic en la ficha de la aplicación de Facebook. Si agrega un formulario después de la **[!UICONTROL Pre-loading]** actividad, los campos que contienen información en la base de datos se cargan previamente.

![](assets/social_webapp_030.png)

>[!NOTE]
>
>Para obtener más información sobre la precarga de datos mediante la base de datos de Adobe Campaign, consulte [esta sección](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data).

**Facebook**

Esta opción permite definir la información de perfil de Facebook que se va a recopilar, entre la que el usuario ha aceptado compartir, para poder guardarla.

![](assets/social_webapp_025.png)

La **[!UICONTROL Database information]** opción le permite recopilar los siguientes datos:

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
>Si marca una o varias casillas en la **[!UICONTROL Private information]** sección, la pantalla de solicitud de permiso de Facebook mostrará automáticamente la solicitud de acceso para estos datos.
>
>Para que pueda recopilar la información seleccionada, el usuario debe aceptar compartirla.
>
>Si desea que ambos tipos de precarga (a través de Adobe Campaign y de Facebook) agreguen dos cuadros de precarga uno tras otro.

### Guardar actividad {#save-activity}

La **[!UICONTROL Save]** actividad permite almacenar la información recopilada durante las fases anteriores en la tabla de visitantes.

Si el perfil ya existe en la tabla de visitantes, sus datos se actualizan con los nuevos datos recopilados.

Si el perfil no existe en la base de datos y se ha recopilado la dirección de correo electrónico del usuario de Facebook, se creará un visitante en la tabla de visitantes.

![](assets/social_webapp_026.png)

1. En el **[!UICONTROL Visitor creation folder]** campo, seleccione la carpeta en la que se creará el perfil. En el caso de una aplicación web de tipo Facebook, la carpeta de creación predeterminada es **[!UICONTROL Visitors]**.
1. En el **[!UICONTROL Reconciliation mode]** campo, seleccione el modo de reconciliación que desee utilizar:

   * **[!UICONTROL Automatic]** :: La reconciliación se realiza por correo electrónico, apellidos, nombre y fecha de nacimiento.
   * **[!UICONTROL Manual]** :: Seleccione una o varias claves de reconciliación.
   * **[!UICONTROL None]** :: No habrá reconciliación.

1. En el **[!UICONTROL Mapping]** campo, seleccione el esquema en el que desea llevar a cabo la reconciliación.

   >[!CAUTION]
   >
   >Asegúrese de que los campos de la **[!UICONTROL Social networks]** ficha se especifican correctamente en la asignación de envío. Se accede a las asignaciones de envío a través del **[!UICONTROL Administration > Campaign management > Target mappings]** nodo.

1. Puede seleccionar una carpeta de búsqueda para la reconciliación y una carpeta de creación para nuevos perfiles. Si los campos están vacíos, se buscarán y crearán perfiles en la carpeta predeterminada del esquema de asignación.

### Actividad final {#end-activity}

Para evitar el error de visualización vinculado a Facebook, debe marcar la **[!UICONTROL Use an external URL]** casilla e introducir la URL de la aplicación Facebook, seguida del **[!UICONTROL app_data]** parámetro y un valor. Este valor se utilizará en la **[!UICONTROL Test]** actividad para detectar si el usuario acaba de entrar en la competencia y para mostrar un mensaje de agradecimiento, si corresponde. For more on this, refer to: [Test activity](#test-activity).

En nuestro ejemplo, el valor utilizado es **gracias**.

![](assets/social_webapp_027.png)

### Pantalla de detalles de un visitante {#details-screen-of-a-visitor}

Igual que para los seguidores de Twitter (consulte: principio [](../../social/using/publishing-on-twitter.md#operating-principle)operativo), los perfiles de Facebook recuperados se almacenan en la tabla de visitantes. Para mostrar la lista de visitantes, vaya al **[!UICONTROL Profiles and Targets > Visitors]** nodo.

Cada posible cliente de Facebook que acepte compartir su información de perfil se agrega a la lista de visitantes. Si la **[!UICONTROL Friends]** casilla está marcada en la **[!UICONTROL Pre-load]** actividad (consulte: actividad [de](#pre-loading-activity)precarga), también se agregan amigos.

![](assets/social_webapp_037.png)

En la **[!UICONTROL Summary]** sección de la ventana de detalles del visitante, hay dos estados posibles para el **[!UICONTROL New Contact]** indicador:

![](assets/social_webapp_038.png)

Si se muestra una marca de verificación verde, significa que el visitante no se reconcilió con ningún destinatario. En este caso, se crea un nuevo perfil en la lista de destinatarios.

![](assets/social_webapp_039.png)

Una cruz roja significa que el visitante se reconcilió con un destinatario. Puede hacer clic en la lupa a la derecha del **[!UICONTROL Recipient]** campo para mostrar el destinatario coincidente.

![](assets/social_webapp_040.png)

Vaya a la ventana de detalles de un destinatario para mostrar el visitante coincidente, si corresponde. Seleccione la **[!UICONTROL Others]** ficha y, a continuación, haga doble clic en el nombre del visitante en la **[!UICONTROL Web identities]** sección .

![](assets/social_webapp_041.png)

La **[!UICONTROL Activities]** pantalla de la página de detalles de un visitante contiene la siguiente información:

* Actividades de abanico de tipo &quot;Open Graph&quot;: música reproducida, videos vistos, artículos leídos e inferral de las aplicaciones instaladas (Deezer, Spotify, Dailymotion, Yahoo News, etc.)

   ![](assets/social_facebook_activities.png)

* &quot;Cantidad de &quot;Me gusta&quot; y comentarios añadidos por el fan después de las entregas enviadas por Adobe Campaign
* páginas a las que les gusta el ventilador
* registros por parte del ventilador

   ![](assets/social_facebook_checkins.png)

   >[!NOTE]
   >
   >Para que Adobe Campaign pueda recopilar los registros de un ventilador, debe hacer clic en el botón **[!UICONTROL Subscribe]** de la pantalla de configuración del servicio. For more on this, refer to [Configuring external accounts](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

## Cómo cargar previamente los campos de un formulario mediante datos de perfil de Facebook {#how-to-pre-load-the-fields-of-a-form-using-facebook-profile-data}

La **[!UICONTROL Social Marketing]** aplicación también permite agregar un botón a un formulario para precargar campos usando información de perfil de Facebook. Esta opción, que está disponible en todas las plantillas de aplicaciones web (**[!UICONTROL Page]** actividades de tipo) se detalla en [esta sección](../../web/using/static-elements-in-a-web-form.md#inserting-html-content).

![](assets/social_webapp_035.png)

>[!NOTE]
>
>Antes de empezar a utilizar esta función, debe crear una aplicación de Facebook y una cuenta **[!UICONTROL Facebook Connect]** externa de tipo. For more on this, refer to [Configuring external accounts](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

