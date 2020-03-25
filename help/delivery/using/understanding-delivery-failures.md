---
title: Comprensión de los errores de envío
seo-title: Comprensión de los errores de envío
description: Comprensión de los errores de envío
seo-description: null
page-status-flag: never-activated
uuid: 03a91f84-77fe-40a9-8be9-a6a35a873ae1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
discoiquuid: 78b58a7a-b387-4d5d-80d5-01c06f83d759
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: ba750d51d31d7783a3fdc5ef6b0bcf4a863c69d4

---


# Comprensión de los errores de envío{#understanding-delivery-failures}

## Acerca de los errores de envío {#about-delivery-failures}

Cuando un mensaje (correo electrónico, SMS, notificación inmediata) no se puede enviar a un perfil, el servidor remoto envía automáticamente un mensaje de error que recoge la plataforma de Adobe Campaign para determinar si la dirección de correo electrónico o el número de teléfono deben ponerse en cuarentena. Consulte Administración [de correo de devolución](#bounce-mail-management).

>[!NOTE]
>
>Los mensajes de error de correo electrónico (o “rechazos”) se clasifican mediante el proceso de inMail. Los mensajes de error de SMS (o “SR”, de “informe de estado”) se clasifican mediante el proceso MTA.

Una vez enviado un mensaje, los “logs” de envío permiten ver el estado de envío de cada perfil y el tipo y el motivo de error asociado.

Los mensajes también se pueden excluir durante la preparación del envío si una dirección está en cuarentena o si un perfil está en la lista negra. Los mensajes excluidos se muestran en el panel de envío.

**Temas relacionados:**

* [“Logs” de envío e historial](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history)
* [Estado de error](../../delivery/using/monitoring-a-delivery.md#failed-status)
* [Tipos y motivos de errores de envío](#delivery-failure-types-and-reasons)

## Tipos y motivos de errores de envío {#delivery-failure-types-and-reasons}

Existen tres tipos de error cuando falla un mensaje. Cada tipo de error determina si una dirección se envía a cuarentena. Para obtener más información sobre esto, consulte [Condiciones para enviar una dirección a la cuarentena](../../delivery/using/understanding-quarantine-management.md#conditions-for-sending-an-address-to-quarantine)

* **Duro**: Un error &quot;duro&quot; indica una dirección no válida. Esto implica un mensaje de error que indica explícitamente que la dirección no es válida, como: &quot;Usuario desconocido&quot;.
* **Suave**: Podría tratarse de un error temporal o uno que no se pudiera categorizar, como: &quot;Dominio inválido&quot; o &quot;Buzón lleno&quot;.
* **Ignorado**: Se trata de un error que se sabe que es temporal, como &quot;Fuera de la oficina&quot;, o un error técnico, por ejemplo, si el tipo de remitente es &quot;maestro de correo&quot;.

Los posibles motivos de un error de envío son:

<table> 
 <tbody> 
  <tr> 
   <td> Etiqueta de error </td> 
   <td> Tipo de error </td> 
   <td> Valor técnico </td> 
   <td> Descripción </td> 
  </tr> 
  <tr> 
   <td> Cuenta deshabilitada </td> 
   <td> Leve/Grave </td> 
   <td> 4 </td> 
   <td> La cuenta vinculada a la dirección no está activa. Cuando el proveedor de acceso a Internet (IAP) detecta un periodo de inactividad prolongado, puede cerrar la cuenta del usuario. A partir de ese momento no se pueden realizar envíos a la cuenta de usuario. Si la cuenta está temporalmente desactivada debido a seis meses de inactividad y todavía se puede activar, se asigna el estado “con errores” y se prueba de nuevo la cuenta hasta que el contador de errores alcance 5. Si el error indica que la cuenta está desactivada de forma permanente, se envía directamente a Cuarentena.<br /> </td> 
  </tr> 
  <tr> 
   <td> Dirección en cuarentena </td> 
   <td> Grave </td> 
   <td> 9 </td> 
   <td> La dirección se envió a cuarentena.<br /> </td> 
  </tr> 
  <tr> 
   <td> Dirección no especificada </td> 
   <td> Grave </td> 
   <td> 7 </td> 
   <td> No se proporciona ninguna dirección para el destinatario.<br /> </td> 
  </tr> 
  <tr> 
   <td> Dirección de baja calidad </td> 
   <td> Ignorado </td> 
   <td> 14 </td> 
   <td> El índice de calidad de esta dirección es demasiado bajo.<br /> </td> 
  </tr> 
  <tr> 
   <td> Dirección en una lista negra </td> 
   <td> Grave </td> 
   <td> 8 </td> 
   <td> La dirección se incluyó en la lista negra en el momento del envío. Este estado se utiliza para importar datos de listas externas y sistemas externos cuando se importan datos a la lista de cuarentena de Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Dirección de control </td> 
   <td> Ignorado </td> 
   <td> 127 </td> 
   <td> La dirección del destinatario forma parte del grupo de control.<br /> </td> 
  </tr> 
  <tr> 
   <td> Duplicada </td> 
   <td> Ignorado </td> 
   <td> 10 </td> 
   <td> La dirección del destinatario ya se encontraba en este envío.<br /> </td> 
  </tr> 
  <tr> 
   <td> Error ignorado </td> 
   <td> No hay error </td> 
   <td> 25 </td> 
   <td> La dirección no está en la lista negra. Por lo tanto, el error se ignora y se envía un correo electrónico.<br /> </td> 
  </tr> 
  <tr> 
   <td> Excluido tras la mediación </td> 
   <td> Ignorado </td> 
   <td> 12 </td> 
   <td> El destinatario se ha excluido mediante las reglas de tipología de campaña de tipo “mediación”.<br /> </td> 
  </tr> 
  <tr> 
   <td> Excluido por una regla SQL </td> 
   <td> Ignorado </td> 
   <td> 11 </td> 
   <td> El destinatario se ha excluido mediante una regla de tipología de campaña de tipo “SQL”.<br /> </td> 
  </tr> 
  <tr> 
   <td> Dominio inválido </td> 
   <td> Leve </td> 
   <td> 2 </td> 
   <td> El dominio de la dirección del correo electrónico es incorrecto o ya no existe. Este perfil se vuelve a seleccionar hasta que el recuento de errores llegue a 5. Después de esto, el registro se pone en estado de cuarentena y no se realiza ningún reintento.<br /> </td> 
  </tr> 
  <tr> 
   <td> Buzón de correo lleno </td> 
   <td> Leve </td> 
   <td> 5 </td> 
   <td> El buzón de este usuario está lleno y no puede aceptar más mensajes. Este perfil se vuelve a seleccionar hasta que el recuento de errores llegue a 5. Después de esto, el registro se pone en estado de cuarentena y no se realiza ningún reintento.<br /> Este tipo de error se administra mediante un proceso de limpieza; la dirección se establece en un estado válido después de 30 días.<br /> Advertencia: para que la dirección se elimine automáticamente de la lista de direcciones en cuarentena, debe iniciarse el flujo de trabajo técnico de limpieza de bases de datos.<br /> </td> 
  </tr> 
  <tr> 
   <td> Sin conexión </td> 
   <td> Ignorado </td> 
   <td> 6 </td> 
   <td> El teléfono móvil del destinatario está apagado o no está conectado a la red cuando al enviar el mensaje.<br /> </td> 
  </tr> 
  <tr> 
   <td> Sin definir </td> 
   <td> Sin definir </td> 
   <td> 0 </td> 
   <td> La dirección se encuentra sin clasificar debido a que aún no se ha sumado el error. Este tipo de error se produce cuando el servidor envía un nuevo mensaje de error: puede tratarse de un error aislado; sin embargo, si vuelve a producirse, el contador de errores aumenta, lo que advierte a los equipos técnicos. They can then carry out message analysis and qualify this error, via the <span class="uicontrol">Administration</span> / <span class="uicontrol">Campaign Management</span> / <span class="uicontrol">Non deliverables Management</span> node in the tree structure.<br /> </td> 
  </tr> 
  <tr> 
   <td> No reúne los requisitos para las ofertas </td> 
   <td> Ignorado </td> 
   <td> 16 </td> 
   <td> El destinatario no reunía los requisitos para las ofertas del envío.<br /> </td> 
  </tr> 
  <tr> 
   <td> Rechazado </td> 
   <td> Leve/Grave </td> 
   <td> 20 </td> 
   <td> La dirección se ha enviado a cuarentena debido a un comentario de seguridad que informa de correo no deseado. Según el error, se vuelve a intentar enviar un correo a la dirección hasta que el contador de errores alcance 5 o se envía directamente a cuarentena.<br /> </td> 
  </tr> 
  <tr> 
   <td> Destinatarios de tamaño limitado </td> 
   <td> Ignorado </td> 
   <td> 17 </td> 
   <td> Se ha alcanzado el tamaño máximo de envío para el destinatario.<br /> </td> 
  </tr> 
  <tr> 
   <td> Dirección no autorizada </td> 
   <td> Ignorado </td> 
   <td> 15 </td> 
   <td> La dirección postal no se ha clasificado.<br /> </td> 
  </tr> 
  <tr> 
   <td> Inaccesible </td> 
   <td> Leve/Grave </td> 
   <td> 3 </td> 
   <td> Se ha producido un error en la cadena de envío de mensajes. Podría ser un incidente en la retransmisión SMTP, un dominio al que no se puede acceder temporalmente, etc. Según el error, se vuelve a intentar enviar un correo a la dirección hasta que el contador de errores llegue a 5 o se envía directamente a cuarentena.<br /> </td> 
  </tr> 
  <tr> 
   <td> Usuario desconocido </td> 
   <td> Grave </td> 
   <td> 1 </td> 
   <td> La dirección no existe. No se intenta realizar envíos adicionales para este perfil.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Reintentos tras un fallo temporal de envío {#retries-after-a-delivery-temporary-failure}

Si un mensaje falla debido a un error **leve** o **ignorado** temporal, los reintentos se realizan durante la duración del envío.

>[!NOTE]
>
>Temporarily undelivered messages can only be related to a **Soft** or **Ignored** error, but not a **Hard** error (see [Delivery failure types and reasons](#delivery-failure-types-and-reasons)).

Para modificar la duración de un envío, vaya a los parámetros avanzados del envío o de la plantilla de envío y especifique la duración deseada en el campo correspondiente. Las propiedades de envío avanzadas se presentan en [esta sección](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period).

La configuración predeterminada permite cinco intentos en intervalos de una hora, seguidos de un reintento diario durante cuatro días. El número de reintentos se puede cambiar a nivel global (póngase en contacto con el administrador técnico de Adobe) o para cada envío o plantilla de envío (consulte [esta sección](../../delivery/using/steps-sending-the-delivery.md#configuring-retries)).

## Errores sincrónicos y asíncronos {#synchronous-and-asynchronous-errors}

Un mensaje puede fallar inmediatamente (error sincrónico), o más tarde, después de enviarlo (error asíncrono).

* Error sincrónico: el servidor de correo remoto contactado mediante el servidor de envío de Adobe Campaign devuelve inmediatamente un mensaje de error y el envío no puede enviarse al servidor del perfil. Adobe Campaign clasifica cada error para determinar si las direcciones de correo electrónico implicadas deben estar en cuarentena o no. Consulte [Rebotar cualificación](#bounce-mail-qualification)de correo.
* Error asíncrono: el servidor receptor reenvía más tarde un correo electrónico de rechazo o una SR. Este correo se carga en un buzón técnico que la aplicación utiliza para etiquetar mensajes con un error. Pueden producirse errores asíncronos hasta una semana después de mandar el envío.

   >[!NOTE]
   >
   >La configuración del buzón de rechazos se detalla en [esta sección](../../installation/using/deploying-an-instance.md#managing-bounced-emails).

   El bucle de comentarios funciona como los correos electrónicos de rechazo. Cuando un usuario clasifica un correo electrónico como correo no deseado, puede configurar las reglas de correo en Adobe Campaign para bloquear todos los envíos a este usuario. Los mensajes enviados a los usuarios que han clasificado un correo electrónico como no deseado se redireccionan automáticamente a una bandeja de correo creada específicamente para este fin. Las direcciones de estos usuarios se incluyen en la lista negra, aunque no hayan hecho clic en el enlace de baja. Las direcciones se incluyen en la lista negra en la tabla de cuarentena (**NmsAddress**) en vez de en la tabla de destinatarios (**NmsRecipient**).

   >[!NOTE]
   >
   >La administración de quejas se detalla en la sección de [administración de envíos](../../delivery/using/about-deliverability.md).

## Gestión de correos rechazados {#bounce-mail-management}

La plataforma Adobe Campaign permite administrar los errores de envío de los correos electrónicos a través de la función de correos rechazados. Cuando un correo electrónico no puede enviarse a un destinatario, el servidor de mensajería instantánea envía automáticamente un mensaje de error (correo rechazado) a una bandeja de entrada técnica diseñada para este fin. La plataforma de Adobe Campaign recopila los mensajes de error y los clasifica mediante el proceso inMail que enriquece la lista de reglas de gestión de los correos electrónicos.

### Clasificación del correo rechazado {#bounce-mail-qualification}

Cuando falla el envío de un correo electrónico, el servidor de envío de Adobe Campaign recibe un mensaje de error del servidor de mensajería o del servidor DNS remoto. La lista de errores se compone de cadenas de caracteres incluidas en el mensaje rechazado por el servidor remoto. Los tipos y los motivos del error se asignan a cada mensaje.

Esta lista está disponible a través del **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]** nodo. Contiene todas las reglas utilizadas por Adobe Campaign para clasificar los errores de envío. No es exhaustiva, Adobe Campaign la actualiza regularmente y también la puede administrar el usuario.

![](assets/tech_quarant_rules_qualif.png)

* The message returned by the remote server on the first occurrence of this error type is displayed in the **[!UICONTROL First text]** column of the **[!UICONTROL Delivery log qualification]** table. If this column is not displayed, click the **[!UICONTROL Configure list]** button at the right bottom of the list to select it.

![](assets/tech_quarant_rules_qualif_text.png)

Adobe Campaign filtros este mensaje para eliminar el contenido de la variable (como ID, fechas, direcciones de correo electrónico, números de teléfono, etc.) y muestra el resultado filtrado en la **[!UICONTROL Text]** columna. The variables are replaced with **`#xxx#`**, except addresses that are replaced with **`*`**.

Este proceso permite reunir todos los errores del mismo tipo y evitar entradas múltiples para errores similares en la tabla de clasificación de “logs” de envíos.

>[!NOTE]
>
>The **[!UICONTROL Number of occurrences]** field displays the number of occurrences of the message in the list. Está limitado a 100 000 incidencias. Si lo desea, puede editar el campo, por ejemplo, para reiniciarlo.

Los correos electrónicos rechazados pueden tener el siguiente estado de clasificación:

* **[!UICONTROL To qualify]** :: no se pudo calificar el correo de devolución. Se debe asignar la clasificación al equipo de Envíos para garantizar una capacidad de envío eficiente de la plataforma. Siempre que no esté clasificado, no se usa el correo rechazado para enriquecer la lista de reglas de gestión de correo electrónico.
* **[!UICONTROL Keep]** : el correo rechazado fue clasificado y el flujo de trabajo de **Refresh for deliverability** lo usa para compararlo con las reglas de gestión de correo electrónico existentes y enriquecer la lista.
* **[!UICONTROL Ignore]** :: el correo de devolución se calificó, pero el flujo de trabajo **Actualizar para la entrega** no lo usará. No se envía a instancias de clientes.

![](assets/deliverability_qualif_status.png)

Para instalaciones hospedadas o híbridas, si ha actualizado a MTA mejorado:

* Las cualificaciones de devolución de la **[!UICONTROL Delivery log qualification]** tabla ya no se utilizan para los mensajes de error de error de envío sincrónico. El MTA mejorado determina el tipo de devolución y la calificación, y devuelve esa información a la Campaña.

* Las devoluciones asincrónicas siguen siendo calificadas por el proceso enMail a través de las **[!UICONTROL Inbound email]** reglas. Para obtener más información sobre esto, consulte Reglas [de administración de](#email-management-rules)correo electrónico.

* En el caso de instancias que utilicen el MTA mejorado sin **Webhooks/EFS**, las **[!UICONTROL Inbound email]** reglas también se utilizarán para procesar los correos electrónicos de devolución sincrónicos procedentes del MTA mejorado, utilizando la misma dirección de correo electrónico que para los correos electrónicos de devolución asincrónicos.

Para obtener más información sobre el MTA mejorado de Adobe Campaign, consulte este [documento](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html).

### Reglas de gestión de correo electrónico {#email-management-rules}

Se accede a las reglas de correo a través del **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** nodo. Las reglas de administración de correo electrónico se muestran en la parte inferior de la ventana.

Estas reglas contienen la lista de cadenas de caracteres que pueden devolver los servidores remotos y que le permiten clasificar el error (**Grave**, **leve** o **ignorado**).

![](assets/tech_quarant_rules.png)

>[!NOTE]
>
>Los parámetros predeterminados de la plataforma se configuran en el asistente de implementación. Para obtener más información, consulte [esta sección](../../installation/using/deploying-an-instance.md).

Las reglas predeterminadas son las siguientes:

* **Correo electrónico entrante**

   Cuando un mensaje de correo electrónico falla, el servidor remoto devuelve un mensaje de rechazo a la dirección especificada en los parámetros de la plataforma.

   Adobe Campaign compara el contenido de cada mensaje de rechazo con las cadenas de la lista de reglas y, a continuación, lo asigna a uno de los tres tipos de error.

   El usuario puede crear sus propias reglas.

   >[!IMPORTANT]
   >
   >Al importar un paquete y al actualizar datos mediante el flujo de trabajo **Refresh for deliverability**, se sobrescriben las reglas creadas por el usuario.

   Para obtener más información sobre la calificación de correo de devolución, consulte [esta sección](#bounce-mail-qualification).

   >[!NOTE]
   >
   >En el caso de instalaciones hospedadas o híbridas, si ha actualizado a la MTA mejorada, las reglas ya no se utilizan para los mensajes de error de envío sincrónico. **[!UICONTROL Inbound email]** For more on this, see [this section](#bounce-mail-qualification).
   >
   >Para obtener más información sobre el MTA mejorado de Adobe Campaign, consulte este [documento](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html).

* **Administración de dominios**

   El servidor de mensajería de Adobe Campaign aplica reglas específicas a los dominios y, a continuación, las reglas para el caso general representado por un asterisco en la lista de reglas.

   Las reglas para los dominios de Hotmail y MSN están disponibles de forma predeterminada en Adobe Campaign.

   Click the **[!UICONTROL Detail]** icon to access rule configuration.

   ![](assets/tech_quarant_domain_rules_02.png)

   Los **parámetros SMTP** actúan como filtros aplicados a una regla de bloqueo.

   * Se puede elegir si activar o no determinadas normas de identificación y claves de cifrado para comprobar el nombre del dominio como, por ejemplo, **ID de remitente**, **DomainKeys**, **DKIM** y **S/MIME**.
   * **SMTP relay**: permite configurar la dirección IP y el puerto de un servidor de transmisión para un dominio determinado. For more on this, see [this section](../../installation/using/configuring-campaign-server.md#smtp-relay).
   Si los mensajes se muestran en Outlook como **[!UICONTROL on behalf of]** con un nombre de dominio diferente, asegúrese de que no firma los correos electrónicos con el ID **del** remitente, que es el estándar de autenticación de correo electrónico exclusivo de Microsoft que está obsoleto. Si la **[!UICONTROL Sender ID]** opción está activada, desmarque la casilla correspondiente y póngase en contacto con el servicio de soporte técnico de Adobe Campaign. La capacidad de entrega no se verá afectada.

   >[!NOTE]
   >
   >En el caso de instalaciones hospedadas o híbridas, si ha actualizado a la MTA mejorada, las **[!UICONTROL Domain management]** reglas ya no se utilizan. **La firma de autenticación por correo electrónico de DKIM (DomainKeys Identified Mail)** se realiza mediante el MTA mejorado para todos los mensajes con todos los dominios. No se firma con **el ID** del remitente, **DomainKeys** o **S/MIME** a menos que se especifique lo contrario en el nivel de MTA mejorado.
   >
   >Para obtener más información sobre el MTA mejorado de Adobe Campaign, consulte este [documento](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html).

* **Administración MX**

   * Las reglas de administración MX se utilizan para regular el flujo de correos electrónicos salientes para un dominio específico. Realizan muestras de los mensajes de rechazo y bloquean el envío a donde corresponda.

   * El servidor de mensajería de Adobe Campaign aplica reglas específicas a los dominios y, a continuación, las reglas para el caso general representado por un asterisco en la lista de reglas.

   * Para configurar las reglas de administración MX, simplemente configure un umbral y seleccione ciertos parámetros SMTP. Un **umbral** es un límite calculado como un porcentaje de error por encima del cual se bloquean todos los mensajes dirigidos a un dominio específico. Por ejemplo, en el caso general, para un mínimo de 300 mensajes, el envío de correos electrónicos se bloquea durante tres horas si la tasa de error alcanza el 90 %.
   Para obtener más información sobre gestión MX, consulte [esta sección](../../installation/using/email-deliverability.md#mx-configuration).

   >[!NOTE]
   >
   >En el caso de instalaciones alojadas o híbridas, si se ha actualizado a la MTA mejorada, ya no se utilizan las reglas de rendimiento de **[!UICONTROL MX management]** envío. El MTA mejorado utiliza sus propias reglas MX que le permiten personalizar el rendimiento por dominio en función de su propia reputación histórica de correo electrónico y de los comentarios en tiempo real procedentes de los dominios a los que envía correos electrónicos.
   >
   >Para obtener más información sobre el MTA mejorado de Adobe Campaign, consulte este [documento](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html).

>[!IMPORTANT]
>
>* El servidor de envío (MTA) debe reiniciarse si los parámetros se han modificado.
>* La modificación o creación de reglas de administración solo es para usuarios expertos.

