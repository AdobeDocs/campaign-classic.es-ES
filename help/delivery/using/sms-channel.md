---
solution: Campaign Classic
product: campaign
title: Canal de SMS
description: Canal de SMS
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
translation-type: tm+mt
source-git-commit: f78fa94fb4fb9236222886a167a46d252497b2aa
workflow-type: tm+mt
source-wordcount: '3131'
ht-degree: 99%

---


# Canal de SMS{#sms-channel}

Adobe Campaign le permite realizar envíos personalizados y masivos de mensajes SMS. Los perfiles de destinatario deben contener al menos un número de teléfono móvil.

>[!NOTE]
>
>Adobe Campaign también permite enviar notificaciones a los terminales móviles a través de su opción **Adobe Campaign Mobile App Channel (NMAC)**.
> 
>Para obtener más información, consulte la sección [Acerca del canal de la aplicación móvil](../../delivery/using/about-mobile-app-channel.md).

Las secciones a continuación proporcionan información específica del canal SMS. Para obtener más información sobre la creación de entregas, consulte [esta sección](../../delivery/using/steps-about-delivery-creation-steps.md).

## Configuración del canal SMS {#setting-up-sms-channel}

Para enviar a un teléfono móvil, necesita:

1. una cuenta externa que especifique un conector y el tipo de mensaje.

   Recuerde que los siguientes conectores quedan obsoletos a partir de la versión 20.2:, Generic SMPP (SMPP versión 3.4 compatible con modo binario), Sybase365 (SAP SMS 365), CLX Communications, Tele2, O2 e iOS. Durante este periodo, las funcionalidades van a seguir disponibles, pero no se van a actualizar, mejorar ni documentar. Para obtener más información, consulte [esta página](https://helpx.adobe.com/es/campaign/kb/deprecated-and-removed-features.html).

1. Una plantilla de envíos en la que se haga referencia a esta cuenta externa.

### Creación de una cuenta externa SMPP {#creating-an-smpp-external-account}

Para enviar un SMS a un teléfono móvil, primero debe crear una cuenta externa SMPP.
Para obtener más información sobre el protocolo y la configuración SMS, consulte esta [página](../../delivery/using/sms-protocol.md).

Para realizar esto, siga los pasos a continuación:

1. En el nodo **[!UICONTROL External accounts]** > **[!UICONTROL Platform]** del árbol, haga clic en el icono **[!UICONTROL New]**.
1. Defina el tipo de cuenta como **Enrutamiento**, el canal como **Móvil (SMS)** y el modo de envío como **Envío masivo**.

   ![](assets/extended_smpp_create_account.png)

1. Marque la casilla **[!UICONTROL Enabled]**.
1. En la pestaña **[!UICONTROL Mobile]**, en la lista desplegable **[!UICONTROL Connector]**, seleccione **[!UICONTROL Extended generic SMPP]**.

   ![](assets/extended_smpp_connector.png)

   >[!CAUTION]
   >
   > A partir de la versión 20.2, los conectores heredados quedan obsoletos y no son compatibles. Se recomienda utilizar el conector **[!UICONTROL Extended generic SMPP]**. Para obtener más información sobre cómo migrar al conector recomendado, consulte esta [página](../../delivery/using/unsupported-connector-migration.md).

1. La opción **[!UICONTROL Enable verbose SMPP traces in the log file]** permite volcar todo el tráfico SMPP en los archivos de registro. Esta opción debe habilitarse para solucionar los problemas del conector y comparar el tráfico que ve el proveedor.

1. Póngase en contacto con el proveedor de servicios de SMS para que le explique cómo rellenar los distintos campos de cuenta externa de la pestaña **[!UICONTROL Connection settings]**.

   A continuación, póngase en contacto con el proveedor, en función del que haya elegido, para que le proporcione el valor que debe introducir en el campo **[!UICONTROL SMSC implementation name]**.

   Puede definir el número de conexiones al proveedor por MTA secundario. De forma predeterminada, se establece en 1.

1. De forma predeterminada, el número de caracteres de un SMS cumple los estándares de GSM.

   Los mensajes SMS con codificación GSM están limitados a 160 caracteres, o a 153 caracteres por SMS en el caso de los mensajes enviados en varias partes.

   >[!NOTE]
   >
   >Algunos caracteres cuentan como dos (llaves, corchetes, símbolo del euro, etc.).
   >
   >A continuación, se presenta la lista de caracteres GSM disponibles.

   Si lo desea, puede autorizar la transliteración de caracteres marcando el cuadro correspondiente.

   ![](assets/extended_smpp_transliteration.png)

   Para obtener más información, consulte [esta sección](#about-character-transliteration).

1. En la pestaña **[!UICONTROL Throughput and delays]**, puede especificar el rendimiento máximo de los mensajes salientes (&quot;MT&quot;, móvil finalizado) en MT por segundo. Si introduce &quot;0&quot; en el campo correspondiente, el rendimiento es ilimitado.

   Los valores de todos los campos correspondientes a las duraciones deben rellenarse en segundos.

1. En la pestaña **[!UICONTROL Mapping of encodings]**, puede definir las codificaciones.

   Para obtener más información, consulte [esta sección](#about-text-encodings).

1. En la pestaña **[!UICONTROL SMSC specificities]**, la opción **[!UICONTROL Send full phone number]** está desactivada de forma predeterminada. No la habilite si desea respetar el protocolo de SMPP y transferir únicamente dígitos al servidor del proveedor de SMS (SMSC).

   Sin embargo, dado que determinados proveedores requieren el uso del prefijo “+”. se recomienda que se ponga en contacto con su proveedor y que este le recomiende si es necesario activar esta opción.

   La casilla de verificación **[!UICONTROL Enable TLS over SMPP]** permite cifrar el tráfico de SMPP. Para obtener más información, consulte [esta página](../../delivery/using/sms-protocol.md).

1. Si está configurando un conector **[!UICONTROL Extended generic SMPP]**, puede configurar respuestas automáticas.

   Para obtener más información, consulte [esta sección](#automatic-reply).

### Acerca de la transliteración de caracteres {#about-character-transliteration}

Las transliteraciones de caracteres se pueden configurar en una cuenta externa de entrega móvil de SMPP, en la pestaña **[!UICONTROL Mobile]**.

La transliteración consiste en reemplazar un carácter de un SMS por otro cuando el estándar GSM no tiene en cuenta dicho carácter.

* Si la transliteración es **[!UICONTROL authorized]**, cada carácter que no se tiene en cuenta se sustituye por un carácter GSM cuando se envía el mensaje. Por ejemplo, la letra &quot;ë&quot; se sustituye por &quot;e&quot;. Por lo tanto, el mensaje se altera ligeramente, pero el límite de caracteres se mantiene.
* Cuando la transliteración es **[!UICONTROL not authorized]**, cada mensaje que contiene caracteres que no se tienen en cuenta se envía en formato binario (Unicode): todos los caracteres se envían tal cual. Sin embargo, los mensajes SMS con Unicode están limitados a 70 caracteres (o 67 caracteres por SMS en el caso de los mensajes enviados en varias partes). Si se supera el número máximo de caracteres, se envían varios mensajes, lo que puede suponer costes adicionales.

>[!IMPORTANT]
>
>La inserción de campos de personalización en el contenido del mensaje SMS puede introducir caracteres que no se tienen en cuenta con la codificación GSM.

De forma predeterminada, la transliteración de caracteres está desactivada. Si desea que todos los caracteres de los mensajes SMS se mantengan tal cual, para, por ejemplo, no modificar los nombres propios, es recomendable que no habilite esta opción.

Sin embargo, si los mensajes SMS contienen muchos caracteres que generan mensajes Unicode, puede optar por activar esta opción para limitar los costes de envío de mensajes.

La siguiente tabla presenta los caracteres que tiene cuenta el estándar GSM. Todos los caracteres insertados en el cuerpo del mensaje que no sean los mencionados abajo convierten todo el mensaje a formato binario (Unicode) y lo limitan a 70 caracteres.

**Caracteres básicos**

<table> 
 <tbody> 
  <tr> 
   <td> @ </td> 
   <td> <img height="21px" src="assets/delta.png" /> </td> 
   <td> SP </td> 
   <td> 0 </td> 
   <td> ¡ </td> 
   <td> P </td> 
   <td> ¿ </td> 
   <td> p </td> 
  </tr> 
  <tr> 
   <td> £ </td> 
   <td> _ </td> 
   <td> ! </td> 
   <td> 1 </td> 
   <td> A </td> 
   <td> Q </td> 
   <td> a </td> 
   <td> q </td> 
  </tr> 
  <tr> 
   <td> $ </td> 
   <td> <img height="21px" src="assets/phi.png" /> </td> 
   <td> " </td> 
   <td> 2 </td> 
   <td> B </td> 
   <td> R </td> 
   <td> b </td> 
   <td> r </td> 
  </tr> 
  <tr> 
   <td> ¥ </td> 
   <td> <img height="21px" src="assets/gamma.png" /> </td> 
   <td> # </td> 
   <td> 3 </td> 
   <td> C </td> 
   <td> S </td> 
   <td> c </td> 
   <td> s </td> 
  </tr> 
  <tr> 
   <td> è </td> 
   <td> <img height="21px" src="assets/delta.png" /> </td> 
   <td> ¤ </td> 
   <td> 4 </td> 
   <td> D </td> 
   <td> T </td> 
   <td> d </td> 
   <td> t </td> 
  </tr> 
  <tr> 
   <td> é </td> 
   <td> <img height="21px" src="assets/omega.png" /> </td> 
   <td> % </td> 
   <td> 5 </td> 
   <td> E </td> 
   <td> U </td> 
   <td> e </td> 
   <td> u </td> 
  </tr> 
  <tr> 
   <td> ù </td> 
   <td> <img height="21px" src="assets/pi.png" /> </td> 
   <td> &amp; </td> 
   <td> 6 </td> 
   <td> F </td> 
   <td> V </td> 
   <td> f </td> 
   <td> v </td> 
  </tr> 
  <tr> 
   <td> ì </td> 
   <td> <img height="21px" src="assets/psi.png" /> </td> 
   <td> ' </td> 
   <td> 7 </td> 
   <td> G </td> 
   <td> W </td> 
   <td> g </td> 
   <td> w </td> 
  </tr> 
  <tr> 
   <td> ò </td> 
   <td> <img height="21px" src="assets/sigma.png" /> </td> 
   <td> ( </td> 
   <td> 8 </td> 
   <td> H </td> 
   <td> X </td> 
   <td> h </td> 
   <td> x </td> 
  </tr> 
  <tr> 
   <td> Ç </td> 
   <td> <img height="21px" src="assets/theta.png" /> </td> 
   <td> ) </td> 
   <td> 9 </td> 
   <td> I </td> 
   <td> Y </td> 
   <td> i </td> 
   <td> y </td> 
  </tr> 
  <tr> 
   <td> LF </td> 
   <td> <img height="21px" src="assets/xi.png" /> </td> 
   <td> * </td> 
   <td> : </td> 
   <td> J </td> 
   <td> Z </td> 
   <td> j </td> 
   <td> z </td> 
  </tr> 
  <tr> 
   <td> Ø </td> 
   <td> ESC </td> 
   <td> + </td> 
   <td> ; </td> 
   <td> K </td> 
   <td> Ä </td> 
   <td> k </td> 
   <td> ä </td> 
  </tr> 
  <tr> 
   <td> ø </td> 
   <td> Æ </td> 
   <td> , </td> 
   <td> &lt; </td> 
   <td> L </td> 
   <td> Ö </td> 
   <td> l </td> 
   <td> ö </td> 
  </tr> 
  <tr> 
   <td> CR </td> 
   <td> æ </td> 
   <td> - </td> 
   <td> = </td> 
   <td> M </td> 
   <td> Ñ </td> 
   <td> m </td> 
   <td> ñ </td> 
  </tr> 
  <tr> 
   <td> Å </td> 
   <td> ß </td> 
   <td> . </td> 
   <td> &gt; </td> 
   <td> N </td> 
   <td> Ü </td> 
   <td> n </td> 
   <td> ü </td> 
  </tr> 
  <tr> 
   <td> å </td> 
   <td> É </td> 
   <td> / </td> 
   <td> ? </td> 
   <td> O </td> 
   <td> § </td> 
   <td> o </td> 
   <td> à </td> 
  </tr> 
 </tbody> 
</table>

SP: Espacio

ESC: Escape

LF: Fuente de línea

CR: Retorno de carro

**Caracteres avanzados (se cuentan dos veces)**

^ { } `[ ~ ]` | €

### Acerca de las codificaciones de texto {#about-text-encodings}

Al enviar un mensaje SMS, Adobe Campaign puede utilizar una o varias codificaciones de texto. Cada codificación tiene su propio conjunto de caracteres específico y determina el número de caracteres que caben en un mensaje SMS.

Al configurar una cuenta externa de entrega móvil de SMPP, puede definir **[!UICONTROL Mapping of encodings]** en la pestaña **[!UICONTROL Mobile]**: el campo **[!UICONTROL data_coding]** permite a Adobe Campaign notificar qué codificación se utiliza al SMSC.

>[!NOTE]
>
>La asignación entre el valor **data_coding** y la codificación utilizada está estandarizada. Sin embargo, ciertos SMSC tienen su propia asignación específica: en este caso, el administrador de **Adobe Campaign** debe declarar esta asignación. Consulte a su proveedor para obtener más información.

Puede declarar **data_codings** y forzar la codificación si es necesario: para ello, especifique una sola codificación en la tabla.

* Cuando no se define ninguna asignación de codificaciones, el conector asume un comportamiento genérico:

   * se intenta utilizar la codificación GSM para asignar el valor **data_coding = 0**.
   * Si la codificación GSM falla, se utiliza la codificación **UCS2** a la que asigna el valor **data_coding = 8**.

* Al definir las codificaciones que desea utilizar y los valores de campo **[!UICONTROL data_coding]** asociados, Adobe Campaign intenta utilizar la primera codificación en la lista, y luego la siguiente si no se puede usar la primera codificación.

>[!IMPORTANT]
>
>El orden de la declaración es importante: se recomienda que coloque la lista en orden ascendente **según el coste** con el fin de priorizar las codificaciones que le permitan introducir tantos caracteres como sea posible en cada mensaje SMS.
>
>Solo declare las codificaciones que desee utilizar. Si algunas de las codificaciones proporcionadas por SMSC no se corresponden con su propósito, no las declare en la lista.

### Respuesta automática {#automatic-reply}

Al configurar un conector SMPP genérico extendido, puede configurar las respuestas automáticas.

Cuando un suscriptor responda a un mensaje SMS enviado a través de Adobe Campaign y su mensaje contenga una palabra clave como &quot;STOP&quot;, puede configurar mensajes que se envíen automáticamente en la sección **[!UICONTROL Automatic reply sent to the MO]**.

>[!NOTE]
>
>Las palabras clave no distinguen entre mayúsculas y minúsculas.

Para cada palabra clave, especifique un código corto, que es un número que suele utilizarse para realizar envíos y sirve como nombre de remitente, e indique el mensaje que se envía al suscriptor.

También puede vincular una acción a su respuesta automática: **[!UICONTROL Send to quarantine]** o **[!UICONTROL Remove from quarantine]**. Por ejemplo, si un destinatario envía la palabra clave &quot;Detener&quot;, se le envía automáticamente una confirmación de baja y se le incluye en la lista negra.

![](assets/extended_smpp_reply.png)

Si asocia la acción **[!UICONTROL Remove from quarantine]** a una respuesta automática, se elimina a los destinatarios que envíen la palabra clave correspondiente de la cuarentena automáticamente.

Los destinatarios se enumeran en la tabla **[!UICONTROL Non deliverables and addresses]**, disponible a través del menú **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]**.

* Para enviar la misma respuesta independientemente del código corto, deje vacía la columna **[!UICONTROL Short code]**.
* Para enviar la misma respuesta independientemente de la palabra clave, deje vacía la columna **[!UICONTROL Keyword]**.
* Para realizar una acción sin enviar una respuesta, deje vacía la columna **[!UICONTROL Response]**. Por ejemplo, esto le permite sacar de cuarentena a un usuario que responda con un mensaje que sea distinto a Detenerse.

Si tiene varias cuentas externas usando el conector SMPP genérico extendido con la misma cuenta de proveedor, puede ocurrir el siguiente problema: al enviar una respuesta a un código corto, puede recibirse en cualquiera de las conexiones de cuenta externa. En consecuencia, la respuesta automática que se envía no puede ser el mensaje esperado.
Para evitarlo, aplique una de las siguientes soluciones, según el proveedor que esté utilizando:

* Cree una cuenta de proveedor para cada cuenta externa.
* Utilice el campo **[!UICONTROL System type]** de la pestaña **[!UICONTROL Mobile]** > **[!UICONTROL Connection settings]** para distinguir cada código corto. Pida a su proveedor un valor diferente para cada cuenta.

   ![](assets/extended_smpp_system-type.png)

Los pasos para configurar una cuenta externa mediante el conector SMPP genérico extendido se detallan en la sección [Creación de una cuenta externa de SMPP](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

### Modificación de la plantilla de envíos {#changing-the-delivery-template}

Adobe Campaign proporciona una plantilla para las entregas a móviles. Esta plantilla está disponible en el nodo **[!UICONTROL Resources > Templates > Delivery templates]**. Para obtener más información, consulte la sección [Acerca de las plantillas](../../delivery/using/about-templates.md).

Para realizar envíos a través del canal SMS, debe crear una plantilla en la que se haga referencia al conector de canal.

Para conservar la plantilla de envíos nativa, recomendamos que la duplique y, a continuación, la configure.

En el siguiente ejemplo, creamos una plantilla para enviar mensajes a través de la cuenta NetSize activada anteriormente. Para ello:

1. Vaya al nodo **[!UICONTROL Delivery templates]**.
1. Haga clic con el botón derecho del ratón en la plantilla **[!UICONTROL Send to mobiles]** y seleccione **[!UICONTROL Duplicate]**.

   ![](assets/s_user_mobile_template_change_01.png)

1. Cambie la etiqueta de la plantilla, por ejemplo, **Enviado a móviles (SMPP)**.

   ![](assets/s_user_mobile_template_change_02.png)

1. Haga clic **[!UICONTROL Properties]**.
1. En la pestaña **[!UICONTROL General]**, seleccione un modo de enrutamiento que corresponda a la cuenta externa creada en los pasos anteriores.

   ![](assets/s_user_mobile_template_change_03.png)

1. Haga clic en **[!UICONTROL Save]** para crear la plantilla.

   ![](assets/s_user_mobile_template_list.png)

Ahora tiene una cuenta externa y una plantilla de envíos que le permiten realizar envíos a través de SMS.

## Creación de una entrega por SMS {#creating-a-sms-delivery}

### Selección del canal de envío {#selecting-the-delivery-channel}

Para diseñar una entrega de SMS nuevo, siga los pasos a continuación:

>[!NOTE]
>
>En [esta sección](../../delivery/using/steps-about-delivery-creation-steps.md) se exponen conceptos globales sobre la creación de envíos.

1. Cree un nuevo envío, por ejemplo, desde el panel Envío.
1. Seleccione la plantilla de envíos **Enviado a móviles (NetSize)** creada anteriormente. Para obtener más información, consulte la sección [Modificación de las plantillas de entrega](#changing-the-delivery-template).

   ![](assets/s_user_mobile_wizard.png)

1. Identifique su entrega con una etiqueta, un código y una descripción. Para obtener más información, consulte [esta sección](../../delivery/using/steps-create-and-identify-the-delivery.md#identifying-the-delivery).
1. Haga clic en **[!UICONTROL Continue]** para confirmar esta información y mostrar la ventana de configuración de mensajes.

## Definición del contenido del SMS {#defining-the-sms-content}

Para crear el contenido del SMS, siga los pasos a continuación:

1. Introduzca el contenido del mensaje en la sección **[!UICONTROL Text content]** del asistente. Los botones de la barra de herramientas permiten importar, guardar o buscar dentro del contenido. El último botón se utiliza para insertar campos de personalización.

   ![](assets/s_ncs_user_wizard_sms01_138.png)

   El uso de los campos de personalización se presenta en la sección [Acerca de la personalización](../../delivery/using/about-personalization.md).

1. Haga clic en **[!UICONTROL Preview]** en la parte inferior de la página para ver la renderización del mensaje con su personalización. Para iniciar la previsualización, seleccione un destinatario con el botón **[!UICONTROL Test personalization]** de la barra de herramientas. Puede seleccionar un destinatario del público objetivo definido o elegir otro destinatario.

   ![](assets/s_ncs_user_wizard_sms01_139.png)

   Puede aprobar el mensaje SMS. También puede ver el contenido del SMS en la pantalla del teléfono móvil que aparece a la derecha del editor de contenido. Haga clic en la pantalla y utilice el ratón para desplazarse por el contenido.

   ![](assets/s_ncs_user_wizard_sms01_140.png)

1. Haga clic en el enlace **[!UICONTROL Data loaded]** para ver la información sobre el destinatario.

   ![](assets/s_user_mobile_wizard_sms_02.png)

   >[!NOTE]
   >
   >Los mensajes SMS se limitan a una longitud de 160 caracteres si se utiliza la página de códigos Latin-1 (ISO-8859-1). Si el mensaje se escribe en Unicode, no debe exceder los 70 caracteres. Algunos caracteres especiales pueden afectar la longitud del mensaje. Para obtener más información sobre la longitud del mensaje, consulte la sección [Acerca de la transliteración de caracteres](#about-character-transliteration).
   >
   >Cuando hay campos de personalización o campos de contenido condicionados, el tamaño del mensaje varía según el destinatario. La longitud del mensaje debe evaluarse cuando se haya realizado la personalización.
   >
   >Al iniciar el análisis, se comprueba la longitud de los mensajes y se muestra una advertencia en caso de contenidos adicionales.

1. Si utiliza el conector NetSize o un conector SMPP, puede personalizar el nombre del remitente de la entrega. Para obtener más información, consulte [Parámetros avanzados](#advanced-parameters).

## Selección de la población objetivo {#selecting-the-target-population}

En [esta sección](../../delivery/using/steps-defining-the-target-population.md) se describe el proceso detallado al seleccionar la población objetivo de una entrega.

Para obtener más información sobre el uso de los campos de personalización, consulte [Acerca de la personalización](../../delivery/using/about-personalization.md)

Para obtener más información sobre la integración de una lista de reasignación, consulte [Acerca de las direcciones semilla](../../delivery/using/about-seed-addresses.md)

## Envío de mensajes SMS {#sending-sms-messages}

Para aprobar el mensaje y enviarlo a los destinatarios de la entrega que está creando, haga clic en **[!UICONTROL Send]**.

El proceso detallado para validar y realizar una entrega se presenta en las siguientes secciones:

* [Validación de la entrega](../../delivery/using/steps-validating-the-delivery.md)
* [Realización de la entrega](../../delivery/using/steps-sending-the-delivery.md)

### Parámetros avanzados {#advanced-parameters}

El botón **[!UICONTROL Properties]** proporciona acceso al parámetro de entrega avanzado. Los parámetros específicos de las entregas SMS se encuentran en la sección **[!UICONTROL SMS parameters]** de la pestaña **[!UICONTROL Delivery]**.

Estas son las opciones disponibles:

* **Dirección del remitente**: permite personalizar el nombre del remitente del envío con una cadena de caracteres alfanuméricos limitada a 11 caracteres. El campo no debe estar compuesto exclusivamente por números. Puede definir una condición para mostrar, por ejemplo, nombres distintos según el código de zona del destinatario:

   ```
   <% if( String(recipient.mobilePhone).indexOf("+1") == 0){ %>NeoShopUS<%} else {%>NeoShopWorld<%}%>
   ```

   >[!IMPORTANT]
   >
   >Compruebe la legislación de su país sobre la edición de nombres de remitente. También debe consultar si su operador ofrece esta funcionalidad.

* **Modo de transmisión**: transmisión de mensaje por SMS.
* **Prioridad**: nivel de importancia asignado a un mensaje. La prioridad **[!UICONTROL Normal]** está seleccionada de forma predeterminada. Pregunte al proveedor de servicios el coste de los SMS enviados con la prioridad **[!UICONTROL High]**.
* **Tipo de aplicación**: elija la aplicación que desea asignar a su envío de SMS. La opción **[!UICONTROL Direct Marketing]** está seleccionada de forma predeterminada y es la que se utiliza más comúnmente.

**Parámetros específicos del conector NetSize**

![](assets/s_user_mobile_sms_adv_netsize.png)

* **Utilizar varios SMS para un único mensaje**: esto le permite enviar un mensaje de más de 160 caracteres mediante varios mensajes SMS.

**Parámetros específicos de un conector SMPP**

![](assets/s_user_mobile_sms_adv_smpp.png)

* **Cantidad máxima de SMS por mensaje**: esta opción le permite establecer la cantidad de SMS que debe utilizar para enviar un mensaje. Si el número se establece en 0, puede utilizar un SMS para enviar el mensaje. Si el número de SMS se establece en 1 o 2 por ejemplo y el mensaje supera este umbral, no se envía.

## Supervisión y seguimiento de las entregas de SMS {#monitoring-and-tracking-sms-deliveries}

Después de enviar mensajes, puede monitorizar y realizar un seguimiento de las entregas. Para obtener más información, consulte estas secciones:

* [Seguimiento de una entrega](../../delivery/using/about-delivery-monitoring.md)
* [Comprensión de los errores de entrega](../../delivery/using/understanding-delivery-failures.md)
* [Acerca del seguimiento de mensajes](../../delivery/using/about-message-tracking.md)

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

   Consulte la guía [Flujos de trabajo](../../workflow/using/architecture.md).

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
>El siguiente procedimiento detallado solo es válido para conectores SMPP, excepto para el conector SMPP genérico extendido. Para obtener más información sobre esto, consulte la sección [Creación de una cuenta externa de SMPP](#creating-an-smpp-external-account).
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
>Estos tipos de mensajes automáticos no conservan un historial. Por lo tanto, no aparecen en el [panel de envío](../../delivery/using/delivery-dashboard.md).
>
>Estos mensajes no se consideran parte de las [reglas de presión comercial](../../campaign/using/pressure-rules.md).
