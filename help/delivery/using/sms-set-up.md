---
product: campaign
title: Configuración del canal SMS de Campaign
description: Obtenga información sobre cómo configurar el canal SMS en Campaign
feature: SMS
role: User, Developer, Admin
level: Experienced
exl-id: a2783a5e-6d38-41a1-b5c6-24ab489116f8
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: ht
source-wordcount: '1739'
ht-degree: 100%

---

# Configuración del canal SMS en una instancia independiente {#setting-up-sms-channel}

Para enviar a un teléfono móvil, necesita:

1. una cuenta externa que especifique un conector y el tipo de mensaje.

   Tenga en cuenta que los conectores heredados ya no se utilizan. Las funcionalidades van a seguir estando disponibles, pero no se van a mejorar ni admitir. Obtenga más información [en esta página](../../rn/using/deprecated-features.md).

1. Una plantilla de envíos en la que se haga referencia a esta cuenta externa.

>[!NOTE]
>
> Para las entregas SMS, la tipología debe utilizar una afinidad SMS específica creada en **un** contenedor de servidor de aplicaciones dedicado. [Más información](../../installation/using/configure-delivery-settings.md#managing-outbound-smtp-traffic-with-affinities)

## Creación de una cuenta externa SMPP {#creating-an-smpp-external-account}

>[!IMPORTANT]
>
>El uso de la misma cuenta y contraseña para varias cuentas externas de SMS puede provocar conflictos y superposición entre las cuentas. Consulte la [Página de solución de problemas de SMS](troubleshooting-sms.md#external-account-conflict).

Para enviar un SMS a un teléfono móvil, primero debe crear una cuenta externa SMPP.
Para obtener más información sobre el protocolo y la configuración de SMS, consulte esta [página](sms-protocol.md).

Para realizar esto, siga los pasos a continuación:

1. En el nodo **[!UICONTROL External accounts]** > **[!UICONTROL Platform]** del árbol, haga clic en el icono **[!UICONTROL New]**.
1. Defina el tipo de cuenta como **Enrutamiento**, el canal como **Móvil (SMS)** y el modo de envío como **Envío masivo**.

   ![](assets/extended_smpp_create_account.png)

1. Marque la casilla **[!UICONTROL Enabled]**.
1. En la pestaña **[!UICONTROL Mobile]**, en la lista desplegable **[!UICONTROL Connector]**, seleccione **[!UICONTROL Extended generic SMPP]**.

   ![](assets/extended_smpp_connector.png)

   >[!CAUTION]
   >
   > A partir de la versión 20.2, los conectores heredados quedan obsoletos y no son compatibles. Se recomienda utilizar el conector **[!UICONTROL Extended generic SMPP]**. Para obtener más información sobre cómo migrar al conector recomendado, consulte esta [página](unsupported-connector-migration.md).

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

   La casilla de verificación **[!UICONTROL Enable TLS over SMPP]** permite cifrar el tráfico de SMPP. Para obtener más información, consulte esta [página](sms-protocol.md).

1. Si está configurando un conector **[!UICONTROL Extended generic SMPP]**, puede configurar respuestas automáticas.

   Para obtener más información, consulte [esta sección](#automatic-reply).

## Transliteración de caracteres SMS {#about-character-transliteration}

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

## Codificaciones de texto {#about-text-encodings}

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

## Respuesta automática {#automatic-reply}

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

Los pasos para configurar una cuenta externa mediante el conector SMPP genérico extendido se detallan en la sección [Creación de una cuenta externa de SMPP](#creating-an-smpp-external-account).

## Modificación de la plantilla de envíos {#changing-the-delivery-template}

Adobe Campaign proporciona una plantilla para las entregas a móviles. Esta plantilla está disponible en el nodo **[!UICONTROL Resources > Templates > Delivery templates]**. Para obtener más información, consulte la sección [Acerca de las plantillas](about-templates.md).

Para realizar envíos a través del canal SMS, debe crear una plantilla en la que se haga referencia al conector de canal.

Para conservar la plantilla de envíos nativa, recomendamos que la duplique y, a continuación, la configure.

En el siguiente ejemplo, creamos una plantilla para enviar mensajes a través de la cuenta NetSize activada anteriormente. Para ello, haga lo siguiente:

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
