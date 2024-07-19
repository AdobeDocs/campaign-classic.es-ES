---
product: campaign
title: Implementación de una instancia
description: Más información sobre el Asistente de implementación de Campaign
feature: Installation, Instance Settings, Deployment
badge-v7-prem: label="On-premise/híbrido solo" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 8b07447c-9a86-4b56-8d29-e0b01357a6ec
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '3389'
ht-degree: 4%

---

# Implementación de una instancia{#deploying-an-instance}

>[!NOTE]
>
>Las configuraciones del lado del servidor solo se pueden realizar mediante el Adobe para implementaciones alojadas por el Adobe. Para obtener más información sobre las diferentes implementaciones, consulte la sección [Modelos de alojamiento](../../installation/using/hosting-models.md) o [esta página](../../installation/using/capability-matrix.md).

## Asistente de implementación {#deployment-wizard}

Adobe Campaign proporciona un asistente gráfico, disponible en la consola del cliente de Adobe Campaign, para definir los parámetros de la instancia a la que se va a conectar.

Para iniciar el asistente de implementación, seleccione **Herramientas > Avanzadas > Asistente de implementación**.

![](assets/s_ncs_install_deployment_wiz_01.png)

Los pasos de configuración son los siguientes:

1. [Parámetros generales](#general-parameters)
1. [Parámetros de canal de correo electrónico](#email-channel-parameters)
1. [Administración de correos electrónicos rechazados](#managing-bounced-emails)
1. [Configuración de seguimiento](#tracking-configuration)
1. [Parámetros de canal móvil](#mobile-channel-parameters)
1. [Configuración regional](#regional-settings)
1. [Acceso desde Internet](#access-from-the-internet)
1. [Administración de recursos públicos](#managing-public-resources)
1. [Depuración de datos](#purging-data)

## Parámetros generales {#general-parameters}

El primer paso del asistente de implementación permite introducir información general sobre la instancia.

![](assets/s_ncs_install_deployment_wiz_02.png)

### Información general {#general-information}

La sección inferior de la ventana permite seleccionar las opciones que se van a activar.

* **[!UICONTROL Customer identifier used in billing]** : puede ser el nombre de la instancia y el número de versión.
* **[!UICONTROL Common name of the customer]** : escriba una cadena de caracteres con el nombre de su compañía. Esta información se puede utilizar en los vínculos de baja.
* **[!UICONTROL Namespace]** : escriba un identificador corto en minúsculas. El objetivo es distinguir entre la configuración específica y la configuración de fábrica en caso de una actualización. El área de nombres predeterminada es **cus** - para cliente.

### Opciones técnicas {#technical-options}

La sección inferior de la ventana permite seleccionar las opciones que se van a activar.

Estas son las opciones disponibles:

* **[!UICONTROL Email channel]** : para activar el envío de correo electrónico. Consulte [Parámetros de canal de correo electrónico](#email-channel-parameters).
* **[!UICONTROL Tracking]** : para habilitar el seguimiento de la población de destino (aperturas y clics). Consulte [Configuración de seguimiento](#tracking-configuration).
* **[!UICONTROL Managing bounced emails]** : para definir la cuenta POP utilizada para recoger el correo electrónico entrante. Consulte [Administración de correos electrónicos rechazados](#managing-bounced-emails).
* **[!UICONTROL LDAP integration]** : para configurar la autenticación de usuarios mediante un directorio LDAP. Consulte [Conexión mediante LDAP](../../installation/using/connecting-through-ldap.md).

## Parámetros de canal de correo electrónico {#email-channel-parameters}

El siguiente paso permite definir la información que se muestra en los encabezados de los mensajes.

Estos parámetros se pueden sobrecargar en las plantillas de envío e individualmente para cada envío (si los usuarios tienen los derechos requeridos).

### Parámetros para correos electrónicos entregados {#parameters-for-delivered-emails}

![](assets/s_ncs_install_deployment_wiz_04.png)

Indique los siguientes parámetros:

* **[!UICONTROL Sender name]** : escriba el nombre del remitente.
* **[!UICONTROL Sender address]** : escriba la dirección de correo electrónico del remitente. Al enviar correos electrónicos desde Adobe Campaign, el buzón de **Dirección del remitente** no se supervisa y los usuarios de marketing no pueden acceder a este buzón. Adobe Campaign tampoco ofrece la capacidad de responder automáticamente o reenviar automáticamente los correos electrónicos recibidos en este buzón. Obtenga más información acerca de las prácticas recomendadas de entrega [en esta documentación](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/ac-starting-new-platform.html){_blank}.

* **[!UICONTROL Reply address text]**: escriba el nombre usado cuando el destinatario hace clic en el botón **[!UICONTROL Reply]**.
* **[!UICONTROL Reply address]** : escriba la dirección de correo electrónico que se usará cuando el destinatario haga clic en el botón **[!UICONTROL Reply]** en el software de cliente de correo electrónico. El propósito del campo **Dirección de respuesta** es cuando desea que el destinatario responda a una dirección diferente a la **Dirección del remitente**.  Esta dirección debe ser una dirección de correo electrónico válida, vinculada a un buzón supervisado y alojada por el cliente.  Podría ser un buzón de soporte técnico, por ejemplo, `customer-care@customer.com`, donde se lean y respondan los correos electrónicos.

* **[!UICONTROL Error address]** : escriba la dirección de correo electrónico de los mensajes con errores. Esta es la dirección técnica utilizada para gestionar el correo rechazado, incluidos los correos electrónicos recibidos por el servidor de Adobe Campaign debido a direcciones de destino inexistentes. Esta dirección debe ser una dirección de correo electrónico válida, vinculada a un buzón supervisado y alojada por el cliente. Podría ser un buzón de rechazos, por ejemplo, `errors@customer.com`. Esta dirección se puede cambiar para una entrega o en las plantillas de entrega, desde la pestaña **SMTP** de las propiedades de la entrega/plantilla de entrega. [Más información](../../delivery/using/email-parameters.md#managing-bounce-emails-managing-bounce-emails).


Además, puede especificar las **máscaras** autorizadas para la dirección del remitente y la dirección de error. Si es necesario, estas máscaras se pueden separar con comas. Esta configuración es opcional. Cuando se introducen campos, Adobe Campaign comprueba en el momento de la entrega (durante el análisis, si la dirección no incluye ninguna variable) que las direcciones son válidas. Este modo operativo garantiza que no se utilicen direcciones que puedan almacenar en déclencheur los problemas de envío. Las direcciones de envío deben configurarse en el servidor de envío.

>[!NOTE]
>
>* Esta configuración se guarda en las opciones de la plataforma de Campaign. [Más información](../../installation/using/configuring-campaign-options.md).
> 
>* Para las configuraciones de varias marcas, puede adaptar la Dirección de error y anular esta configuración desde la cuenta externa de enrutamiento de correo electrónico. [Más información](../../installation/using/external-accounts.md#email-routing-external-account).
>


### Caracteres autorizados en direcciones {#characters-authorized-in-addresses}

<!--This window enables you to define, for all email campaigns, the delivery and address-quality management options.-->

En la base de datos de Adobe Campaign, todas las direcciones de correo electrónico deben crearse de la siguiente manera: `x@y.z`. Los caracteres **x**, **y** y **z** no deben estar vacíos y no deben incluir caracteres no autorizados.

Puede definir aquí los caracteres autorizados (&quot;política de datos&quot;) en el campo de correo electrónico de la base de datos. Los caracteres no incluidos en la lista estarán prohibidos y, por lo tanto, se rechazarán al introducir información en la base de datos a través de la interfaz, un formulario web y también al importar datos.

Hay dos listas disponibles: **solo europeos** o **solo estadounidenses**. Se pueden agregar otros caracteres si es necesario.

### Parámetros de envío {#delivery-parameters}

El vínculo **Parámetros avanzados...** le permite acceder a las opciones de entrega, a los parámetros vinculados a reintentos y a las cuarentenas.

![](assets/s_ncs_install_deployment_wiz_05.png)

Esta ventana permite definir, para todas las campañas de correo electrónico, las opciones de envío y administración de la calidad de la dirección.

Estas son las opciones disponibles:

* **[!UICONTROL Delivery duration of messages]**: pasado este tiempo, la entrega se detiene (de forma predeterminada, 5 días).
* **[!UICONTROL Online resources validity duration]** : tiempo durante el cual se conserva la información del perfil de destinatario para generar páginas espejo.
* **[!UICONTROL Exclude recipients who no longer wish to be contacted]** : cuando se selecciona esta opción, no se contacta con los destinatarios de la lista de bloqueados en el momento de la.
* **[!UICONTROL Automatically ignore doubles]** : cuando se selecciona esta opción, no se realizará una entrega a direcciones duplicadas.

>[!NOTE]
>
>En el caso de instalaciones hospedadas o híbridas, si ha actualizado a [MTA mejorado](../../delivery/using/sending-with-enhanced-mta.md), **[!UICONTROL Delivery duration of the messages]** se utilizará únicamente si se establece en **3,5 días o menos**. Si define un valor superior a 3,5 días, no se tendrá en cuenta.

### Parámetros de reintento {#retry-parameters}

La información sobre las recuperaciones se proporciona en los campos **Periodos de recuperación** y **Número de recuperaciones**: cuando un destinatario no está disponible, por ejemplo, si su bandeja de entrada está llena, el programa intentará ponerse en contacto con él 5 veces de forma predeterminada, con un intervalo de una hora entre cada intento (durante el tiempo máximo de entrega). Estos valores se pueden cambiar para adaptarlos a sus necesidades.

>[!NOTE]
>
>En el caso de instalaciones hospedadas o híbridas, si ha actualizado a [MTA mejorado](../../delivery/using/sending-with-enhanced-mta.md), ya no se usan los parámetros de reintento de Campaign. Los reintentos de rechazo temporal y el periodo de tiempo entre ellos están determinados por el servidor de correo mejorado en función del tipo y la gravedad de las respuestas de rechazo procedentes del dominio de correo electrónico del mensaje.

### Parámetros de cuarentena {#quarantine-parameters}

Las opciones de configuración para cuarentenas son las siguientes:

* **[!UICONTROL Duration between two significant errors]** : introduzca un valor (&quot;1d&quot; de forma predeterminada: 1 día) para definir el tiempo que la aplicación espera antes de incrementar el contador de errores en caso de error.
* **[!UICONTROL Maximum number of errors before quarantine]** : una vez alcanzado este valor, la dirección de correo electrónico se pone en cuarentena (de forma predeterminada &quot;5&quot;: la dirección se pondrá en cuarentena en el sexto error). Esto significa que el contacto se excluirá automáticamente de las entregas posteriores.

## Administración de correos electrónicos rechazados {#managing-bounced-emails}

El correo rechazado es extremadamente importante para clasificar los errores de entrega. Estos errores se clasifican en NP@I una vez que las reglas han determinado su causa.

Este paso solo está disponible si las opciones de administración **Canal de correo electrónico** y **Correo rechazado** están seleccionadas en el primer paso del asistente de implementación. Consulte [Parámetros generales](#general-parameters).

Este paso permite definir la configuración para administrar los correos electrónicos rechazados.

![](assets/s_ncs_install_deployment_wiz_06.png)

### Cuenta POP utilizada para recuperar correos entrantes {#pop-account-used-to-retrieve-incoming-mails}

Indique los parámetros para conectarse a la cuenta y recuperar los correos electrónicos entrantes.

* **[!UICONTROL Label]** : nombre que incluye todos los parámetros indicados abajo,
* **[!UICONTROL Server]** : servidor utilizado para recuperar el correo rechazado (correo entrante),
* **[!UICONTROL Security]** : si es necesario, seleccione **[!UICONTROL SSL]** en la lista desplegable,
* **[!UICONTROL Port]** : puerto del servidor (generalmente 110),
* **[!UICONTROL Account]** : nombre de la cuenta utilizada para el correo rechazado,
* **[!UICONTROL Password]** : contraseña asociada a la cuenta.

Una vez especificada la configuración POP, haga clic en **Probar** para asegurarse de que es correcta.

### Correos rechazados sin procesar {#unprocessed-bounce-mails}

Adobe Campaign gestiona automáticamente las devoluciones aplicando las reglas enumeradas en el nodo **Administration > Campaign Management > Non deliverables Management > Delivery log qualification**. Para obtener más información, consulte [Administración de correos rechazados](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management).

Las devoluciones sin procesar no se muestran en la interfaz de Adobe Campaign. Se eliminan automáticamente a menos que se transfieran a un buzón de correo de terceros mediante los siguientes campos:

* **[!UICONTROL Forwarding address]** : complete este campo para transferir a una dirección de terceros todos los mensajes de error (procesados o no procesados ) recopilados por la plataforma de Adobe Campaign.
* **[!UICONTROL Address for errors]** : complete este campo para transferir a una dirección de terceros solo los mensajes de error que el proceso de inMail no pudo calificar.
* **[!UICONTROL SMTP server]** : servidor utilizado para enviar los correos electrónicos rechazados sin procesar.

>[!IMPORTANT]
>
>Para reenviar correos electrónicos rechazados sin procesar, Adobe solo recomienda rellenar el campo **[!UICONTROL Address for errors]**. Sin embargo, asegúrese de comprobar regularmente la dirección que utiliza, ya que esto podría suponer una carga pesada en el servidor de correo. Póngase en contacto con su administrador de cuentas para obtener más información.

## Configuración de seguimiento {#tracking-configuration}

El siguiente paso permite configurar el seguimiento de la instancia. La instancia debe declararse y registrarse con los servidores de seguimiento.

Este paso solo se ofrece cuando las opciones **Canal de correo electrónico** y **Seguimiento** están seleccionadas en la primera página del asistente de implementación. Consulte [Parámetros generales](#general-parameters).

Para obtener información más detallada sobre el seguimiento web (modo de seguimiento, creación e inserción de etiquetas...), consulte [este documento](../../configuration/using/about-web-tracking.md).

### Principio de funcionamiento {#operating-principle}

Al activar el seguimiento en una instancia, las direcciones URL de las entregas se cambian durante la entrega para habilitar el seguimiento.

* La información sobre direcciones URL externas (sean seguras o no) introducida en esta página del asistente de implementación se utiliza para crear la nueva dirección URL. Además de esta información, el vínculo modificado contiene los identificadores de la entrega, el destinatario y la dirección URL.

  Adobe Campaign recopila la información de seguimiento en los servidores de seguimiento para enriquecer los perfiles de los destinatarios y los datos vinculados a la entrega (pestañas **[!UICONTROL Tracking]**).

  El servidor de aplicaciones de Adobe Campaign solo utiliza la información sobre las direcciones URL internas para ponerse en contacto con los servidores de seguimiento.

  Para obtener más información, consulte [Servidor de seguimiento](#tracking-server).

* Una vez configuradas las direcciones URL, debe habilitar el seguimiento. Para ello, la instancia debe estar registrada en los servidores de seguimiento.

  Para obtener más información, consulte [Guardando seguimiento](#saving-tracking).

### Servidor de seguimiento {#tracking-server}

![](assets/s_ncs_install_deployment_wiz_08.png)

Para garantizar la eficacia del seguimiento en esta instancia, se debe mostrar la siguiente información:
<!--With Mid-sourcing architecture, you can externalize tracking management. To do this:-->

* **[!UICONTROL External URL]** y/o **[!UICONTROL Secure external URL]** : introduzca la URL de redirección que se utilizará en el correo electrónico que se enviará.
* **[!UICONTROL Internal URL(s)]** : direcciones URL utilizadas solamente por el servidor de Adobe Campaign para contactar con los servidores de seguimiento a fin de recopilar registros y cargar las direcciones URL. No es necesario asociarlo a la instancia.

  Si no especifica una dirección URL, esta se utilizará de forma predeterminada.

Con la arquitectura intermediaria, puede externalizar la administración de seguimiento. Para ello, haga lo siguiente:

1. Seleccione la opción **[!UICONTROL Externalize tracking management]** : esto le permite utilizar un servidor intermediario como servidor de seguimiento.
1. Rellene los campos **[!UICONTROL External account]** y **[!UICONTROL Instance name]** para poder conectar con el servidor intermediario.

   Para obtener más información, consulte [Servidor intermediario](../../installation/using/mid-sourcing-server.md).

1. Haga clic en el botón **[!UICONTROL Enable the tracking instance]** para aprobar la conexión con el servidor.

   ![](assets/s_ncs_install_deployment_wiz_18.png)

### Guardado del seguimiento {#saving-tracking}

Una vez completadas las direcciones URL, debe registrar el servidor de seguimiento.

Haga clic en el vínculo **Registro en los servidores de seguimiento** y, a continuación, seleccione una de las opciones disponibles.

![](assets/s_ncs_install_deployment_wiz_09.png)

Existen tres tipos posibles de arquitectura para implementar el seguimiento:

1. **Agregar compatibilidad con el seguimiento en una instancia existente**

   Esta opción se aplica si la instancia ya se ha creado para otras necesidades (servidor MTA, etc.) en servidores que se utilizarán como servidores de seguimiento.

   ![](assets/s_ncs_install_deployment_wiz_11.png)

   Escriba la contraseña de la cuenta **internal** en los servidores de redirección para configurar la instancia de seguimiento.

   >[!NOTE]
   >
   >Si se utilizan varios servidores de seguimiento, todos deben utilizar el mismo nombre y contraseña.

   Especifique el nombre de la instancia y la contraseña.

1. **Crear una nueva instancia dedicada al seguimiento**

   Esta opción es útil cuando las instancias de seguimiento están reservadas para el seguimiento y no tienen otros módulos de aplicación.

   ![](assets/s_ncs_install_deployment_wiz_10.png)

   Escriba la contraseña de la cuenta **internal** en los servidores de redirección para configurar la instancia de seguimiento.

   >[!NOTE]
   >
   >Si se configuran varios servidores de seguimiento, todos deben utilizar la misma contraseña.

   Especifique el nombre de la instancia, la contraseña y cualquier máscara DNS asociada, como **[!UICONTROL Campaign*]**.

1. **Validar una instancia de seguimiento ya preconfigurada**

   Esta opción se usa cuando no tiene la contraseña de la cuenta **internal**; en este caso, hay una cuenta de seguimiento preconfigurada para usted en los servidores de seguimiento. Introduzca la contraseña de la cuenta de seguimiento de los servidores de redirección para validar la instancia de seguimiento.

   ![](assets/s_ncs_install_deployment_wiz_17.png)

   Especifique el nombre de la instancia que desea validar.

Haga clic en **Aprobar** para iniciar el proceso de grabación con el servidor de seguimiento.

En la ventana anterior, un mensaje confirma el registro en el nivel de servidor de seguimiento:

![](assets/s_ncs_install_deployment_wiz_tracking_ok.png)

Los parámetros vinculados a las búsquedas de URL **no se deben modificar** para una instalación estándar. Para todos los demás parámetros, póngase en contacto con el Adobe.

## Parámetros de canal móvil {#mobile-channel-parameters}

El siguiente paso permite definir la configuración predeterminada para las entregas a móviles (SMS y push WAP).

>[!NOTE]
>
>El canal móvil es opcional: este paso solo aparece si se ha adquirido. Compruebe el acuerdo de licencia.

![](assets/s_ncs_install_deployment_wiz_12.png)

### Cuenta predeterminada para el envío de SMS {#default-account-for-sms-delivery}

Introduzca la siguiente información:

* **[!UICONTROL Label]** : escriba un nombre para esta cuenta push de SMS/Wap. Por ejemplo, es posible que desee utilizar el nombre de su enrutador.
* Para los campos **[!UICONTROL Server]**, **[!UICONTROL Port]**, **[!UICONTROL Account]**, **[!UICONTROL Password]**, **[!UICONTROL Connector]**, **[!UICONTROL Send Endpoint]**, **[!UICONTROL Reception Endpoint]**, **[!UICONTROL Notification Endpoint]**: póngase en contacto con su proveedor de servicios para obtener la configuración requerida.

### Parámetros de SMS enviados {#parameters-of-sms-sent}

En la lista desplegable **Prioridad**: seleccione &quot;Normal&quot;, &quot;Alta&quot; o &quot;Urgente&quot; para aplicarlo a los mensajes que se van a enviar.

### Parámetros avanzados {#advanced-parameters}

El vínculo **Parámetros avanzados...** le permite acceder a las opciones de reintento y cuarentena.

![](assets/s_ncs_install_deployment_wiz_13.png)

La información sobre los reintentos está disponible en los campos **Periodo de reintentos** y **Número de reintentos**: Cuando un dispositivo móvil no está disponible, de forma predeterminada, el programa lo intentará de nuevo 5 veces a intervalos de al menos 15 minutos (para el periodo máximo de envío). Estos valores se pueden adaptar para adaptarlos a sus necesidades.

Las opciones de configuración para cuarentenas son las siguientes:

* **[!UICONTROL Time between two significant errors]** : introduzca un valor predeterminado (de forma predeterminada &quot;1d&quot;: day) para definir el tiempo que la aplicación espera antes de incrementar el contador de errores para detectar un error.
* **[!UICONTROL Maximum number of errors before quarantine]**: una vez alcanzado este valor, el número móvil se pone en cuarentena (de forma predeterminada, &quot;5&quot;: el número se pondrá en cuarentena tras producirse el sexto error). Esto significa que el contacto se excluirá automáticamente de futuros envíos.

## Configuración regional {#regional-settings}

Esta fase permite incluir las preferencias de política de datos.

![](assets/s_ncs_install_deployment_wiz_14.png)

* **[!UICONTROL Consider all phone numbers as international ones]**: cuando se selecciona esta opción, la aplicación aplica el formato internacional a los números de teléfono (el prefijo de país es obligatorio porque el número de dígitos no se comprobará antes de aplicar el formato). Si esta opción no está seleccionada, debe codificar el número de teléfono internacional con &quot;+&quot; o &quot;00&quot;.
* **[!UICONTROL Store all phone numbers using the international format]**: esta opción solo se refiere a **números de teléfono nacionales** que se importan o editan. Defina si desea utilizar un formato nacional (como 425 555 0150) o internacional (por ejemplo, +1 425 555 0150)

## Acceso desde Internet {#access-from-the-internet}

>[!IMPORTANT]
>
>Por razones de privacidad, recomendamos utilizar HTTPS para todos los recursos externos.

Este paso le permite definir direcciones URL de acceso para páginas de Adobe Campaign expuestas en Internet.

También debe indicar aquí las opciones de publicación vinculadas a los formularios web.

![](assets/s_ncs_install_deployment_wiz_15.png)

### Servidores expuestos en la web {#servers-exposed-on-the-web}

Utilice esta página para rellenar las direcciones URL del servidor para:

1. Acceder al servidor de aplicaciones expuesto en Internet: formularios de suscripción/baja, extranet, etc.
1. Acceder al servidor de aplicaciones para recursos no expuestos en la web: formularios, intranet, páginas de confirmación.
1. Acceda a las páginas espejo de los envíos.

   Una página espejo es una página dinámica que muestra el contenido del correo electrónico. Se accede a él a través de un vínculo insertado en el mensaje enviado al destinatario y puede contener elementos personalizados. La página espejo ofrece al destinatario la posibilidad de leer el mensaje en un navegador de Internet en lugar del software de correo electrónico, independientemente del formato de entrega (texto o HTML). Sin embargo, las páginas espejo solo se generan para una entrega determinada si se ha definido el contenido HTML requerido.

Adobe Campaign permite diferenciar estas tres direcciones URL para distribuir la carga en varias plataformas.


>[!NOTE]
>
>* Esta configuración se guarda en las opciones de la plataforma de Campaign. [Más información](../../installation/using/configuring-campaign-options.md).
>* Para las configuraciones de varias marcas, puede adaptar la URL de la página espejo y anular esta configuración desde la cuenta externa de enrutamiento de correo electrónico. [Más información](../../installation/using/configuring-campaign-options.md).


## Administración de recursos públicos {#managing-public-resources}

>[!IMPORTANT]
>
>Por razones de privacidad, recomendamos utilizar HTTPS para todos los recursos externos.

Para que se puedan ver desde el exterior, las imágenes utilizadas en los correos electrónicos y recursos públicos vinculados a las campañas deben estar presentes en un servidor accesible de forma externa. Luego pueden estar disponibles para destinatarios u operadores externos.

![](assets/s_ncs_install_deployment_wiz_img_uploading.png)

Para este paso, debe introducir:

1. La nueva URL del recurso público. Para obtener más información, consulte la sección [URL de recursos públicos](#public-resources-url).
1. El modo de detección de imágenes en una entrega. Para obtener más información, consulte la sección [Detección de imágenes de entrega](#delivery-image-detection).
1. Opciones de publicación. Para obtener más información, consulte la sección [Modos de publicación](#publication-modes).

Se puede acceder a los recursos públicos a través del nodo **Administración > Recursos > En línea > Recursos públicos** del árbol de Adobe Campaign. Se recopilan en una biblioteca y se pueden incluir en correos electrónicos, pero también se utilizan en campañas o tareas y en la gestión de contenido.

![](assets/install_pub_resources_view.png)

### URL de recursos públicos {#public-resources-url}

El primer campo permite especificar el inicio de la dirección URL utilizada para los recursos una vez cargados. Cuando se cargan, los recursos son accesibles a través de esta nueva URL.

En una entrega, puede utilizar imágenes almacenadas en la biblioteca de recursos públicos o cualquier otra imagen local o imagen almacenada en un servidor.

* Para las imágenes de correo electrónico, la dirección URL **https://** server **/res/img**.

  Este valor se puede sobrescribir en cada envío.

* Para los recursos públicos, la dirección URL **https://** server **/res/** instance ****donde **instance**es el nombre de la instancia de seguimiento.

### Detección de imagen de entrega {#delivery-image-detection}

En una entrega, puede utilizar imágenes almacenadas en la biblioteca de recursos públicos o cualquier otra imagen local o imagen almacenada en un servidor.

El campo **Máscaras de URL** le permite especificar la lista de máscaras de URL que se omitirán al cargar imágenes automáticamente. Por ejemplo, si utiliza imágenes almacenadas en un sitio accesible desde el exterior, en particular en un sitio de Internet, puede introducir la dirección URL del sitio en este campo.

![](assets/s_ncs_install_deployment_wiz_img_mask.png)

Puede especificar varias máscaras de URL utilizando una coma para separar cada una de ellas.

* Para obtener información sobre cómo usar y administrar imágenes en correos electrónicos, consulte [esta sección](../../delivery/using/defining-the-email-content.md#adding-images).
* En el asistente de envíos, las imágenes a las que se llama desde estas direcciones URL tienen el estado &quot;Ignorado&quot;.

### Modos de publicación {#publication-modes}

La sección inferior del asistente le permite seleccionar las opciones de publicación de recursos públicos e imágenes.

Están disponibles los siguientes modos de publicación:

* Servidores de seguimiento

  Los recursos se copiarán automáticamente en los diferentes servidores de seguimiento. Se configuraron en el paso [Tracking configuration](#tracking-configuration).

* Otros servidores de Adobe Campaign

  Puede utilizar otros servidores de Adobe Campaign en los que se copiarán los recursos.

  Del lado del servidor, para utilizar un servidor de Adobe Campaign dedicado, debe crear una nueva instancia con el siguiente comando:

  ```
  nlserver config -addtrackinginstance:<trackingA>/<trackingA*>
  ```

  A continuación, introduzca la contraseña.

  Los parámetros de los servidores dedicados se indican en los campos **[!UICONTROL Media URL(s)]**, **[!UICONTROL Password]** y **[!UICONTROL Instance name]**.

  ![](assets/s_ncs_install_images_upload_b.png)

* Script de publicación manual (solo para recursos públicos)

  ![](assets/s_ncs_install_images_upload_c.png)

  Puede publicar las imágenes mediante una secuencia de comandos:

   * Debe crear esta secuencia de comandos: Su contenido depende de la configuración.
   * El siguiente comando llamará a la secuencia de comandos:

     ```
     [INSTALL]/copyToFrontal.vbs "$(XTK_INSTALL_DIR)\var\<instance>\upload\" "img1,img2,img3"
     ```

     donde `[INSTALL]` es la ruta de acceso a la carpeta de instalación de Adobe Campaign.

   * En Unix, asegúrese de que el script es ejecutable.

Para las imágenes, debe copiarlas de la carpeta &quot;images&quot; especificada mediante la opción **NmsDelivery_ImageSubDirectory** en uno o más servidores frontales. Estos servidores almacenarán las imágenes para que sean accesibles a través de la nueva dirección URL configurada.

En caso de publicación en un servidor de Adobe Campaign sin un script de publicación manual, las imágenes de una entrega se almacenan de forma predeterminada en `$(XTK_INSTALL_DIR)/var/res/img/ directory`. La dirección URL correspondiente es la siguiente: **`https://server/res/img`**.

`XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)`. La dirección URL correspondiente es la siguiente: **`https://server/res/instance`**, donde instance es el nombre de la instancia de seguimiento.

>[!NOTE]
>
>Es posible cambiar el directorio de almacenamiento de recursos públicos. Para obtener más información, consulte [Administración de recursos públicos](#managing-public-resources).

### Sincronización de recursos públicos {#synchronizing-public-resources}

Esta funcionalidad le permite **sincronizar recursos públicos** en varios servidores de repuesto.

Si un recurso público no está presente en el servidor de seguimiento o si el recurso devuelve un error 404, el servidor de seguimiento intentará encontrar el recurso en uno de los servidores de reserva.

La declaración y la configuración de los servidores de reserva deben realizarse en el archivo **serverConf.xml** del servidor de marketing. Todos los parámetros disponibles en **serverConf.xml** se enumeran en esta [sección](../../installation/using/the-server-configuration-file.md).

**Declaración**

```
<redirection>
<spareServer enabledIf="" id="" url=""/>
</redirection>
```

**Configuración**

Para cada recurso público que debe sincronizarse, debe agregar un atributo de estado al elemento `<url>` en la parte `<relay>`:

El atributo de estado puede tener uno de estos tres valores:

* de reserva: el recurso público está sincronizado

* normal: comportamiento existente (sin sincronización)

* lista negra: la dirección URL se agrega a la lista de bloqueados de la si devuelve un error 404. La duración (en segundos) de la dirección URL que se encuentra en la lista de bloqueados de la está definida por un atributo **timeout** cuyo valor predeterminado es 60 s.

La configuración predeterminada de la sincronización es:

```
(extracted from the serverConf.xml file)

<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="false" trackingPassword="">
<spareServer enabledIf="" id="1" url=""/>
</redirection>

....


<relay debugRelay="false" forbiddenCharsInAuthority="?#.@/:" forbiddenCharsInPath="?#/"
           modDir="index.html" startRelay="false" startRelayInModule="true" timeout="60">
   <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="normal" targetUrl="https://localhost:8080" timeout="" urlPath="/view/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="*.jsp"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="*.jssp"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="/webApp/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="/report/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="/jssp/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="normal" targetUrl="https://localhost:8080" timeout="" urlPath="/strings/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="normal" targetUrl="https://localhost:8080" timeout="" urlPath="/interaction/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="normal" targetUrl="https://localhost:8080" timeout="" urlPath="/barcode/*"/>

      <url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" status="spare" targetUrl="" timeout="" urlPath="/favicon.*"/>
      <url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" status="spare" targetUrl="" timeout="" urlPath="/*.html"/>
      <url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" status="spare" targetUrl="" timeout="" urlPath="/*.png"/>
      <url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" status="spare" targetUrl="" timeout="" urlPath="/*.jpg"/>

 </relay>
```

## Depuración de datos {#purging-data}

El último paso del asistente de implementación permite configurar la depuración automática de datos obsoletos. Los valores se expresan en días.

![](assets/s_ncs_install_deployment_wiz_16.png)

Los datos se eliminan automáticamente mediante el flujo de trabajo Database cleanup. Para obtener más información sobre cómo configurar y utilizar este flujo de trabajo, así como detalles sobre los elementos eliminados, consulte este [documento](../../production/using/database-cleanup-workflow.md).
