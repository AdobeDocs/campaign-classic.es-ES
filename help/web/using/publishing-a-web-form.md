---
solution: Campaign Classic
product: campaign
title: Publicación de un formulario web
description: Publicación de un formulario web
audience: web
content-type: reference
topic-tags: web-forms
exl-id: 1c66b8e8-7590-4767-9b2f-a9a509df4508
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '995'
ht-degree: 100%

---

# Publicación de un formulario web{#publishing-a-web-form}

## Precarga de los datos del formulario {#pre-loading-the-form-data}

Si desea actualizar los perfiles almacenados en la base de datos mediante un formulario web, puede utilizar una casilla de precarga. La casilla de precarga le permite indicar cómo buscar el registro que se actualiza en la base de datos.

Puede utilizar los siguientes métodos de identificación:

* **[!UICONTROL Adobe Campaign Encryption]**

   Este método de encriptado utiliza el identificador (ID) cifrado de Adobe Campaign. Este método solamente se aplica a un objeto de Adobe Campaign y la ID encriptada solo se puede generar mediante la plataforma de Adobe Campaign.

   Al utilizar este método, es necesario adaptar la URL del formulario para enviar a la dirección de correo electrónico añadiendo el parámetro **`<%=escapeUrl(recipient.cryptedId) %>`**. Para obtener más información, consulte [Envío de un formulario por correo electrónico](#delivering-a-form-via-email).

* **[!UICONTROL DES encryption]**

   ![](assets/s_ncs_admin_survey_preload_methods_001.png)

   Este método de encriptado utiliza un identificador (ID) proporcionado externamente, vinculado a una clave compartida por Adobe Campaign y el proveedor externo. El campo **[!UICONTROL Des key]** permite introducir esta clave de encriptado.

* **[!UICONTROL List of fields]**

   Esta opción le permite elegir entre los campos del contexto actual del formulario, los que se utilizan para encontrar el perfil correspondiente en la base de datos.

   ![](assets/s_ncs_admin_survey_preload_methods_002.png)

   Los campos se pueden añadir a las propiedades del formulario mediante la pestaña **[!UICONTROL Parameters]** (consulte [Adición de parámetros](../../web/using/defining-web-forms-properties.md#adding-parameters)). Se ubican en la dirección URL del formulario o en las zonas de entrada.

   >[!CAUTION]
   >
   >Los datos de los campos seleccionados no están encriptados. No se debe proporcionar en un formulario encriptado, ya que Adobe Campaign no puede descifrarlo si la opción **[!UICONTROL Field list]** está seleccionada.

   En el ejemplo siguiente, la precarga del perfil se basa en la dirección de correo electrónico.

   La dirección URL puede incluir la dirección de correo electrónico sin encriptar, en cuyo caso los usuarios tienen acceso directo a las páginas que les afectan.

   ![](assets/s_ncs_admin_survey_preload_methods_003.png)

   De no ser así, se les pide su contraseña.

   ![](assets/s_ncs_admin_survey_preload_methods_004.png)

   >[!CAUTION]
   >
   >Si se especifican varios campos en la lista, los datos de **TODOS LOS CAMPOS** deben coincidir con los datos almacenados en la base de datos para que se actualice el perfil. De lo contrario, se crea un perfil nuevo.
   > 
   >Esta función es especialmente útil para aplicaciones web, pero no se recomienda para formularios públicos. La opción de control de acceso seleccionada debe ser “Activar control de acceso”.

La opción **[!UICONTROL Skip preloading if no ID]** debe estar seleccionada si no desea actualizar los perfiles. En este caso, cada perfil introducido se añade a la base de datos después de la aprobación del formulario. Esta opción se utiliza, por ejemplo, cuando se publica el formulario en un sitio web.

La opción **[!UICONTROL Auto-load data referenced in the form]** permite precargar de manera automática los datos que coinciden con los campos de entrada y de combinación del formulario. Sin embargo, no afecta a los datos a los que se hace referencia en las actividades **[!UICONTROL Script]** y **[!UICONTROL Test]**. Si esta opción no está seleccionada, debe definir los campos con la opción **[!UICONTROL Load additional data]**.

La opción **[!UICONTROL Load additional data]** permite añadir información que no se utiliza en las páginas del formulario, pero que sí se precarga.

Por ejemplo, se puede precargar el género del destinatario y dirigirlo automáticamente a la página adecuada a través de un cuadro de prueba.

![](assets/s_ncs_admin_survey_preload_ex.png)

## Administración de la entrega y seguimiento de formularios web {#managing-web-forms-delivery-and-tracking}

Una vez que se ha creado, configurado y publicado el formulario, se puede enviar y realizar un seguimiento de las respuestas del usuario.

### Ciclo de vida de un formulario {#life-cycle-of-a-form}

Existen tres fases en el ciclo de vida de un formulario:

1. **Formulario que se está editando**

   Esta es la fase inicial de diseño: Cuando se crea un nuevo formulario, se encuentra en fase de edición. El acceso al formulario, solo para fines de prueba, requiere el uso del parámetro **[!UICONTROL __uuid]** en su dirección URL. Se puede acceder a esta dirección URL desde la subpestaña **[!UICONTROL Preview]**. Consulte [Parámetros de URL del formulario](../../web/using/defining-web-forms-properties.md#form-url-parameters).

   >[!CAUTION]
   >
   >Siempre que se edite el formulario, su dirección URL de acceso es una dirección URL especial.

1. **Formulario en línea**

   Cuando se haya completado la fase de diseño, se puede enviar el formulario. En primer lugar, debe publicarse. Para obtener más información, consulte [Publicación de un formulario](#publishing-a-form).

   El formulario se mantiene en **[!UICONTROL Live]** hasta que caduca.

   >[!CAUTION]
   >
   >Para poder enviarlo, la dirección URL de la encuesta no debe contener el parámetro **[!UICONTROL __uuid]**.

1. **Formulario no disponible**

   Una vez cerrado el formulario, la fase de entrega termina y el formulario deja de estar disponible: ya no es accesible para los usuarios.

   La fecha de caducidad se puede definir en la ventana de propiedades del formulario. Para obtener más información, consulte [Hacer que un formulario esté disponible en línea](#making-a-form-available-online).

El estado de publicación de un formulario se muestra en la lista de formularios.

![](assets/s_ncs_admin_survey_status.png)

### Publicación de un formulario {#publishing-a-form}

Para cambiar el estado de un formulario, debe publicarlo. Para ello, haga clic en el botón **[!UICONTROL Publication]** situado sobre la lista de formularios web y seleccione el estado en la casilla desplegable.

![](assets/webapp_publish_webform.png)

### Disponibilidad de un formulario en línea {#making-a-form-available-online}

Para que los usuarios puedan acceder, el formulario debe estar en producción e iniciado, es decir, dentro de su periodo de validez. Las fechas de validez se introducen mediante el vínculo **[!UICONTROL Properties]** del formulario.

* Utilice los campos de la sección **[!UICONTROL Project]** para introducir las fechas de inicio y finalización del formulario.

   ![](assets/webapp_availability_date.png)

* Haga clic en el vínculo **[!UICONTROL Personalize the message displayed if the form is closed...]** para definir el mensaje de error que se muestra si el usuario intenta acceder al formulario cuando este no es válido.

   Consulte [Accesibilidad del formulario](../../web/using/defining-web-forms-properties.md#accessibility-of-the-form).

### Envío de un formulario por correo electrónico {#delivering-a-form-via-email}

Cuando envía una invitación por correo electrónico, puede utilizar la opción **[!UICONTROL Adobe Campaign Encryption]** para la reconciliación de datos. Para ello, vaya al asistente de envíos y adapte el vínculo al formulario añadiendo el parámetro siguiente:

```
<a href="https://server/webApp/APP264?&id=<%=escapeUrl(recipient.cryptedId) %>">
```

En este caso, la clave de reconciliación para el almacenamiento de datos debe ser el identificador encriptado del destinatario. Para obtener más información, consulte [Precarga de los datos del formulario](#pre-loading-the-form-data).

En este caso, es necesario marcar la opción **[!UICONTROL Update the preloaded record]** en la casilla de registro. Para obtener más información, consulte [Almacenamiento de respuestas de formularios web](../../web/using/web-forms-answers.md#saving-web-forms-answers).

![](assets/s_ncs_admin_survey_save_box_option.png)

### Respuestas al registro {#log-responses}

El seguimiento de respuestas puede activarse en una pestaña específica para controlar el impacto del formulario web. Para ello, haga clic en el vínculo **[!UICONTROL Advanced parameters...]** en la ventana de propiedades del formulario y seleccione la opción **[!UICONTROL Log responses]**.

![](assets/s_ncs_admin_survey_trace.png)

La pestaña **[!UICONTROL Responses]** aparece para mostrarle la identidad de los encuestados.

![](assets/s_ncs_admin_survey_trace_tab.png)

Seleccione un destinatario y haga clic en el botón **[!UICONTROL Detail...]** para ver las respuestas proporcionadas.

![](assets/s_ncs_admin_survey_trace_edit.png)

Puede procesar los “logs” de respuesta proporcionados en las consultas, por ejemplo para dirigirse solo a los no encuestados para enviarles recordatorios o para ofrecer comunicaciones específicas únicamente a los encuestados.

>[!NOTE]
>
>Para obtener un seguimiento completo de las respuestas proporcionadas, exportar las respuestas y ver o crear informes específicos, utilice el módulo opcional de **Encuesta.** Para obtener más información, consulte [esta sección](../../web/using/about-surveys.md).
