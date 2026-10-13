---
product: campaign
title: Envío, monitorización y seguimiento de SMS
description: Obtenga información sobre cómo enviar, monitorizar y rastrear SMS en Campaign
feature: SMS
role: User
exl-id: 442672ee-5037-49b7-a06f-3a99920ce2b6
TQID: 'https://experienceleague.adobe.com/6N9cEjqk8JrIUMG19Jsc-TQSAuv8qqheg8BFOMgPYKc'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
    internal-label: Campaigns
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
    internal-label: Email messaging
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
    internal-label: Manage deliverability
  - id: b1bd1421-1927-4c59-9bc6-ce292360e43b
    internal-label: SMS Messaging
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
source-git-commit: d7e5f68c0d2e0b94fd5cfdf2981bed29f33d9f62
workflow-type: tm+mt
source-wordcount: '907'
ht-degree: 95%
---
# Configuración adicional{#sms-properties}

Como parte de la transición de Campaign v7 a v8, el conjunto de documentación de Campaign Classic se ha optimizado y reorganizado. Ahora, las funciones comunes solo están disponibles en el conjunto de documentación de Campaign v8. Para obtener más información sobre la configuración de envíos SMS, consulte la [documentación de Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/sms/config-sms/sms-delivery-settings){target=_blank}.

[![imagen](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/sms/config-sms/sms-delivery-settings){target=_blank}

<!--
## Send SMS messages {#sending-sms-messages}

To approve your message and send it to the recipients of the delivery being created, click **[!UICONTROL Send]**.

The detailed process when validating and sending a delivery is presented in the sections below:

* [Validate the delivery](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/validate/delivery-analysis){target="_blank"} (Campaign v8 documentation)
* [Send the delivery](steps-sending-the-delivery.md)
-->

## Parámetros avanzados {#advanced-parameters}

El botón **[!UICONTROL Properties]** proporciona acceso al parámetro de entrega avanzado. Los parámetros específicos de las entregas SMS se encuentran en la sección **[!UICONTROL SMS parameters]** de la pestaña **[!UICONTROL Delivery]**.

Estas son las opciones disponibles:

* **Dirección del remitente**: permite personalizar el nombre del remitente del envío con una cadena de caracteres alfanuméricos limitada a 11 caracteres. El campo no debe estar compuesto exclusivamente por números. Puede definir una condición para mostrar, por ejemplo, nombres distintos según el código de zona del destinatario:

  ```
  <% if( String(recipient.mobilePhone).indexOf("+1") == 0){ %>NeoShopUS<%} else {%>NeoShopWorld<%}%>
  ```

  >[!IMPORTANT]
  >
  >Compruebe la legislación de su país sobre la edición de nombres de remitente. También debe consultar si su operador ofrece esta funcionalidad.

* **Prioridad**: nivel de importancia asignado a un mensaje. La prioridad **[!UICONTROL Normal]** está seleccionada de forma predeterminada. Pregunte al proveedor de servicios el coste de los SMS enviados con la prioridad **[!UICONTROL High]**.
* **Tipo de aplicación**: elija la aplicación que desea asignar a su envío de SMS. La opción **[!UICONTROL Direct Marketing]** está seleccionada de forma predeterminada y es la que se utiliza más comúnmente.

**Parámetros específicos del conector NetSize**

![](assets/s_user_mobile_sms_adv_netsize.png)

* **Utilizar varios SMS para un único mensaje**: esto le permite enviar un mensaje de más de 160 caracteres mediante varios mensajes SMS.

<!--
## Monitor and track SMS {#monitoring-and-tracking-sms-deliveries}

After sending messages, you can monitor and track your deliveries. For more on this, refer to these sections:

* [Monitor a delivery](about-delivery-monitoring.md)
* [Understand delivery failures](delivery-failures-quarantine.md)
* [About message tracking](about-message-tracking.md)
-->

## Procesamiento de mensajes entrantes {#processing-inbound-messages}

El módulo **nlserver sms** consulta al enrutador SMS a intervalos regulares. Esto permite a Adobe Campaign realizar un seguimiento del progreso de las entregas y controlar los informes de estado y las solicitudes de baja de los destinatarios.

* **Informes de estado**: vea los “logs” de envío para comprobar el estado de los mensajes.

  >[!NOTE]
  >
  >Cada SMS enviado se vincula a una cuenta externa con su clave principal. De este modo:
  >
  > * Los informes de estado de una cuenta de SMS externa eliminada no se procesan correctamente.
  > * Una cuenta SMS solo se puede vincular a una cuenta externa única para garantizar que los informes de estado se atribuyen a la cuenta correcta

* **Baja**: los destinatarios que deseen dejar de recibir envíos SMS pueden devolver un mensaje que contenga la palabra STOP. Si su proveedor lo permite en los términos del contrato, puede recuperar mensajes mediante la actividad de flujo de trabajo de los **SMS de entrada** y, a continuación, crear una consulta para activar la opción **No volver a ponerse en contacto con este destinatario** para los destinatarios correspondientes.

## Esquema InSMS {#insms-schema}

El esquema InSMS contiene información relacionada con los SMS entrantes. Una descripción de estos campos está disponible a través del atributo desc.

* **message**: contenido del SMS recibido.
* **origin**: número de móvil de origen del mensaje.
* **providerId**: identificador del mensaje devuelto por el SMSC (centro de mensajes).
* **created**: fecha en la que se insertó el mensaje entrante en Adobe Campaign.
* **extAccount**: Cuenta externa de Adobe Campaign.

  >[!IMPORTANT]
  >
  >Los campos siguientes son específicos de NetSize.
  >
  >Si el operador utilizado no es NetSize, estos campos se consideran vacíos.

* **alias**: alias del mensaje entrante.
* **separator**: separador entre el alias y el cuerpo del mensaje.
* **messageDate**: fecha del mensaje dada por el operador.
* **receivalDate**: fecha en la que se recibió el mensaje del operador en el SMSC (centro de mensajes).
* **deliveryDate**: fecha en la que se envió el mensaje del SMSC (centro de mensajes).
* **largeAccount**: código de cuenta de cliente vinculada al SMS entrante.
* **countryCode**: código de país del operador.
* **operatorCode**: código de red del operador.
* **linkedSmsId**: Identificador de Adobe Campaign (broadlogId) asociado al SMS saliente, donde el SMS es la respuesta.

## Administración de respuestas automáticas (normativa de Estados Unidos) {#managing-automatic-replies--american-regulation-}

Cuando los suscriptores responden a un mensaje SMS enviado a través de Adobe Campaign y utilizan una palabra clave como STOP, HELP o YES, es necesario en el mercado estadounidense configurar los mensajes que se envían automáticamente.

Por ejemplo, si los destinatarios envían la palabra clave STOP, reciben automáticamente un mensaje de confirmación que indica que se han dado de baja.

El nombre del remitente para este tipo de mensaje es un breve código que suele utilizarse para realizar envíos.

>[!IMPORTANT]
>
>El siguiente procedimiento detallado solo es válido para conectores SMPP, excepto para el conector SMPP genérico extendido. Para obtener más información sobre esto, consulte la sección [Creación de una cuenta externa de SMPP](sms-set-up.md#creating-an-smpp-external-account).
>
>Esto forma parte del proceso de certificación llevado a cabo por los operadores estadounidenses para las campañas de marketing en los Estados Unidos. Estas respuestas a mensajes SMS de suscriptores que contienen la palabra clave deben enviarse al suscriptor inmediatamente después de recibir un mensaje de ellos.

1. Crear este tipo de archivo XML:

   ```
   <autoreply>
     <shortcode name="12345">
       <reply keyword="STOP" text="You will not receive SMS anymore" />
       <reply keyword="HELP" text="Powered by Adobe Campaign" />
     </shortcode>
     <shortcode name="43115">
       <reply keyword="STOP" text="Vous ne recevrez plus de SMS" />
       <reply keyword="HELP" text="Service rendu par Adobe Campaign" />
     </shortcode>
     <shortcode name="*">
       <reply keyword="ADOBE" text="This text is replied when you send ADOBE to any short code" />
     </shortcode>
   </autoreply>
   ```

1. Para el atributo **name** de la etiqueta **`<shortcode>`**, especifique el código corto que se debe mostrar en el lugar del nombre del remitente del mensaje.

   En cada etiqueta **`<reply>`**, introduzca el atributo **keyword** con una palabra clave y el atributo **text** con el mensaje que desee enviar para esta palabra clave.

   >[!NOTE]
   >
   >Cada palabra clave debe estar escrita en mayúsculas.

   Si desea enviar el mismo mensaje para varias palabras clave, duplique la línea correspondiente.

   Por ejemplo:

   ```
   <reply keyword="STOP" text="You will not receive SMS anymore" />
   <reply keyword="QUIT" text="You will not receive SMS anymore" />
   ```

1. Una vez finalizado, guarde este archivo con el nombre **smsAutoReply.xml**.

   Tenga en cuenta que el nombre del archivo distingue mayúsculas de minúsculas en Linux.

1. Copie este archivo en el directorio **conf** de Adobe Campaign, en el mismo lugar que el servidor Web.

>[!IMPORTANT]
>
>Estos tipos de mensajes automáticos no conservan un historial. Por lo tanto, no aparecen en el panel de control de envío. [Más información](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}.
>
>Estos mensajes no se tienen en cuenta en las reglas de presión comercial. Consulte la [documentación de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-optimization/pressure-rules.html?lang=es){target="_blank"}.
