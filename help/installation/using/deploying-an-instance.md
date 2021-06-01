---
product: campaign
title: Implementación de una instancia
description: Más información sobre el asistente de implementación de Campaign
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 8b07447c-9a86-4b56-8d29-e0b01357a6ec
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '3058'
ht-degree: 3%

---

# Implementación de una instancia{#deploying-an-instance}

>[!NOTE]
>
>Las configuraciones del lado del servidor solo se pueden realizar mediante Adobe para implementaciones alojadas en Adobe. Para obtener más información sobre las diferentes implementaciones, consulte la sección [Modelos de alojamiento](../../installation/using/hosting-models.md) o [esta página](../../installation/using/capability-matrix.md).

## Asistente de implementación {#deployment-wizard}

Un asistente gráfico, disponible en la consola del cliente de Adobe Campaign, permite definir los parámetros de la instancia a la que se va a conectar.

Para iniciar el asistente de implementación, seleccione **Tools > Advanced > Deployment wizard**.

![](assets/s_ncs_install_deployment_wiz_01.png)

Los pasos de configuración son los siguientes:

1. [Parámetros generales](#general-parameters)
1. [Parámetros de canal de correo electrónico](#email-channel-parameters)
1. [Administración de correos electrónicos devueltos](#managing-bounced-emails)
1. [Configuración de seguimiento](#tracking-configuration)
1. [Parámetros de canal móvil](#mobile-channel-parameters)
1. [Configuración regional](#regional-settings)
1. [Acceso a Internet](#access-from-the-internet)
1. [Administración de recursos públicos](#managing-public-resources)
1. [Depuración de datos](#purging-data)

## Parámetros generales {#general-parameters}

El primer paso del asistente de implementación permite introducir información general sobre la instancia.

![](assets/s_ncs_install_deployment_wiz_02.png)

### Información general {#general-information}

La sección inferior de la ventana permite seleccionar las opciones que se van a activar.

* **[!UICONTROL Customer identifier used in billing]** : puede ser el nombre de la instancia y el número de versión.
* **[!UICONTROL Common name of the customer]** : Escriba una cadena de caracteres con el nombre de su empresa. Esta información se puede utilizar en los vínculos de baja.
* **[!UICONTROL Namespace]** : Introduzca un identificador corto en minúsculas. El objetivo es distinguir entre la configuración específica y la configuración de fábrica en caso de una actualización. El espacio de nombres predeterminado es **cus** - para el cliente.

### Opciones técnicas {#technical-options}

La sección inferior de la ventana permite seleccionar las opciones que se van a activar.

Estas son las opciones disponibles:

* **[!UICONTROL Email channel]** : para activar el envío por correo electrónico. Consulte [Parámetros de canal de correo electrónico](#email-channel-parameters).
* **[!UICONTROL Tracking]** : Para habilitar el seguimiento de la población objetivo (aperturas y clics). Consulte [Configuración de seguimiento](#tracking-configuration).
* **[!UICONTROL Managing bounced emails]** : Para definir la cuenta POP utilizada para recoger el correo electrónico entrante. Consulte [Administración de correos electrónicos devueltos](#managing-bounced-emails).
* **[!UICONTROL LDAP integration]** : Para configurar la autenticación de usuario mediante un directorio LDAP. Consulte [Conexión a través de LDAP](../../installation/using/connecting-through-ldap.md).

## Parámetros de canal de correo electrónico {#email-channel-parameters}

El siguiente paso permite definir la información que se debe mostrar en los encabezados de mensaje.

Estos parámetros se pueden sobrecargar en plantillas de envío e individualmente para cada envío (si los usuarios tienen los derechos requeridos).

### Parámetros para correos electrónicos enviados {#parameters-for-delivered-emails}

![](assets/s_ncs_install_deployment_wiz_04.png)

Indique los siguientes parámetros:

* **[!UICONTROL Sender name]** : Nombre del remitente,
* **[!UICONTROL Sender address]** : La dirección del remitente,
* **[!UICONTROL Reply address text]** : El nombre, que se puede personalizar, que se utilizará cuando el destinatario haga clic en el  **[!UICONTROL Reply]** botón del software cliente de correo electrónico,
* **[!UICONTROL Reply address]** : La dirección de correo electrónico que se utiliza cuando el destinatario hace clic en el  **[!UICONTROL Reply]** botón del software cliente de correo electrónico,
* **[!UICONTROL Error address]** : Dirección de correo electrónico de los mensajes con errores. Esta es la dirección técnica que se utiliza para gestionar el correo rechazado, incluidos los correos electrónicos recibidos por el servidor de Adobe Campaign debido a que no existen direcciones de destino.

Además, puede especificar las **máscaras** autorizadas para la dirección del remitente y la dirección de error. Si es necesario, estas máscaras se pueden separar mediante comas. Esta configuración es opcional. Cuando se introducen campos, Adobe Campaign comprueba en el momento de la entrega (durante el análisis, si la dirección no incluye ninguna variable) que las direcciones son válidas. Este modo operativo garantiza que no se utilicen direcciones que puedan dar déclencheur a problemas de entrega. Las direcciones de envío deben configurarse en el servidor de envío.

### Caracteres autorizados en las direcciones {#characters-authorized-in-addresses}

<!--This window enables you to define, for all email campaigns, the delivery and address-quality management options.-->

En la base de datos de Adobe Campaign, todas las direcciones de correo electrónico deben crearse de la siguiente manera: `x@y.z`. Los caracteres **x**, **y** y **z** no deben estar vacíos y no deben incluir caracteres no autorizados.

Aquí puede definir los caracteres autorizados (&quot;política de datos&quot;) en el campo de correo electrónico de la base de datos. Los caracteres no incluidos en la lista estarán prohibidos y, por lo tanto, se rechazarán al introducir información en la base de datos a través de la interfaz, a través de un formulario web y también al importar datos.

Hay dos listas disponibles: **Solo europeo** o **solo EE.UU.**. Se pueden agregar otros caracteres si es necesario.

### Parámetros de envío {#delivery-parameters}

Los **Parámetros avanzados...El enlace** le permite acceder a las opciones de envío, a los parámetros vinculados a los reintentos y a las cuarentenas.

![](assets/s_ncs_install_deployment_wiz_05.png)

Esta ventana permite definir, para todas las campañas de correo electrónico, las opciones de entrega y administración de la calidad de la dirección.

Estas son las opciones disponibles:

* **[!UICONTROL Delivery duration of messages]** : Más allá de este tiempo, la entrega se detiene (de forma predeterminada, 5 días),
* **[!UICONTROL Online resources validity duration]** : Tiempo durante el cual se conserva la información del perfil de destinatario para generar páginas espejo,
* **[!UICONTROL Exclude recipients who no longer wish to be contacted]** : Cuando se selecciona esta opción, no se contacta con los destinatarios de lista de bloqueados,
* **[!UICONTROL Automatically ignore doubles]** : Cuando se selecciona esta opción, el envío no se realiza para duplicar direcciones.

### Parámetros de reintento {#retry-parameters}

La información sobre las recuperaciones se proporciona en los campos **Recovery periods** y **Number of recuperies**: cuando no se puede acceder a un destinatario, por ejemplo, si la bandeja de entrada está llena, el programa intentará ponerse en contacto con ellos 5 veces, con un intervalo de una hora entre cada intento (durante el tiempo de entrega máximo). Estos valores se pueden cambiar para adaptarlos a sus necesidades.

### Parámetros de cuarentena {#quarantine-parameters}

Las opciones de configuración para cuarentenas son las siguientes:

* **[!UICONTROL Duration between two significant errors]** : introduzca un valor (&quot;1d&quot;) de forma predeterminada: 1 día) para definir el tiempo que la aplicación espera antes de incrementar el contador de errores en caso de error,
* **[!UICONTROL Maximum number of errors before quarantine]** : una vez alcanzado este valor, la dirección de correo electrónico se pone en cuarentena (de forma predeterminada, &quot;5&quot;: la dirección se pondrá en cuarentena en el sexto error). Esto significa que el contacto se excluirá automáticamente de las entregas posteriores.

## Administración de correos electrónicos devueltos {#managing-bounced-emails}

El correo rechazado es extremadamente importante para clasificar los errores de envío. Estos errores se clasifican en la carpeta NP@I una vez que las reglas han determinado su causa.

Este paso solo está disponible si las opciones de administración **Email channel** y **Bounce mail** están seleccionadas en el primer paso del asistente de implementación. Consulte [Parámetros generales](#general-parameters).

Este paso permite definir la configuración para administrar los correos electrónicos rechazados.

![](assets/s_ncs_install_deployment_wiz_06.png)

### Cuenta POP utilizada para recuperar los correos entrantes {#pop-account-used-to-retrieve-incoming-mails}

Indique los parámetros que se van a conectar a la cuenta para recuperar los correos electrónicos entrantes.

* **[!UICONTROL Label]** : Nombre que incluye todos los parámetros indicados a continuación,
* **[!UICONTROL Server]** : Servidor utilizado para recuperar el correo rechazado (correo entrante),
* **[!UICONTROL Security]** : Si es necesario, seleccione  **[!UICONTROL SSL]** en la lista desplegable ,
* **[!UICONTROL Port]** : puerto del servidor (generalmente 110),
* **[!UICONTROL Account]** : Nombre de la cuenta utilizada para el correo rechazado,
* **[!UICONTROL Password]** : Contraseña asociada a la cuenta.

Una vez especificada la configuración POP, haga clic en **Test** para asegurarse de que es correcta.

### Correos devueltos sin procesar {#unprocessed-bounce-mails}

Adobe Campaign gestiona automáticamente las devoluciones aplicando las reglas enumeradas en el nodo **Administration > Campaign Management > Non deliverables Management > Delivery log qualification**. Para obtener más información, consulte [Administración de correos rechazados](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management).

Las devoluciones sin procesar no se muestran en la interfaz de Adobe Campaign. Se eliminan automáticamente a menos que se transfieran a un buzón de terceros mediante los campos siguientes:

* **[!UICONTROL Forwarding address]** : Rellene este campo para transferir a una dirección de terceros todos los mensajes de error (procesados o no procesados) recopilados por la plataforma de Adobe Campaign.
* **[!UICONTROL Address for errors]** : Rellene este campo para transferir a una dirección de terceros solo los mensajes de error que el proceso inMail no pudo clasificar.
* **[!UICONTROL SMTP server]** : Servidor utilizado para enviar correos electrónicos rechazados sin procesar.

>[!IMPORTANT]
>
>Para reenviar correos electrónicos rechazados sin procesar, Adobe recomienda rellenar solo el campo **[!UICONTROL Address for errors]** . Sin embargo, asegúrese de que la dirección que se usa se compruebe con regularidad, ya que esto podría suponer una carga pesada en el servidor de correo. Póngase en contacto con el ejecutivo de cuentas para obtener más información.

## Configuración de seguimiento {#tracking-configuration}

El siguiente paso permite configurar el seguimiento de la instancia. La instancia debe declararse y registrarse con los servidores de seguimiento.

Este paso solo se ofrece cuando las opciones **Email channel** y **Tracking** están seleccionadas en la primera página del asistente de implementación. Consulte [Parámetros generales](#general-parameters).

Para obtener información más detallada sobre el seguimiento web (modo de seguimiento, creación e inserción de etiquetas...), consulte [este documento](../../configuration/using/about-web-tracking.md).

### Principio de funcionamiento {#operating-principle}

Al activar el seguimiento en una instancia, las direcciones URL de los envíos se cambian durante el envío para habilitar el seguimiento.

* La información sobre las direcciones URL externas (seguras o no) introducida en esta página del asistente de implementación se utiliza para crear la nueva dirección URL. Además de esta información, el vínculo modificado contiene: los identificadores de la entrega, el destinatario y la URL.

   Adobe Campaign recopila información de seguimiento en los servidores de seguimiento para enriquecer los perfiles de destinatario y los datos vinculados al envío (pestañas **[!UICONTROL Tracking]** ).

   El servidor de aplicaciones de Adobe Campaign solo utiliza la información de las direcciones URL internas para comunicarse con los servidores de seguimiento.

   Para obtener más información, consulte [Servidor de seguimiento](#tracking-server).

* Una vez configuradas las direcciones URL, debe habilitar el seguimiento. Para ello, la instancia debe estar registrada en los servidores de seguimiento.

   Para obtener más información, consulte [Guardar seguimiento](#saving-tracking).

### Servidor de seguimiento {#tracking-server}

![](assets/s_ncs_install_deployment_wiz_08.png)

Para garantizar la eficacia del seguimiento en esta instancia, se debe mostrar la siguiente información:
<!--With Mid-sourcing architecture, you can externalize tracking management. To do this:-->

* **[!UICONTROL External URL]** y/o  **[!UICONTROL Secure external URL]** : Introduzca la URL de redirección que se utilizará en el correo electrónico que se enviará.
* **[!UICONTROL Internal URL(s)]** : Las direcciones URL que solo usa el servidor de Adobe Campaign para comunicarse con los servidores de seguimiento y recopilar registros y cargar las direcciones URL. No es necesario asociarlo a la instancia.

   Si no especifica una dirección URL, la dirección URL de seguimiento se utilizará de forma predeterminada.

Con la arquitectura intermediaria, puede externalizar la administración del seguimiento. Para ello:

1. Seleccione la opción **[!UICONTROL Externalize tracking management]** : esto le permite utilizar un servidor de mid-sourcing como servidor de seguimiento.
1. Rellene los campos **[!UICONTROL External account]** y **[!UICONTROL Instance name]** para poder conectarse al servidor de mid-sourcing.

   Para obtener más información, consulte [Mid-sourcing server](../../installation/using/mid-sourcing-server.md).

1. Haga clic en el botón **[!UICONTROL Enable the tracking instance]** para aprobar la conexión con el servidor.

   ![](assets/s_ncs_install_deployment_wiz_18.png)

### Guardado del seguimiento {#saving-tracking}

Una vez que se hayan rellenado las direcciones URL, debe registrar el servidor de seguimiento.

Haga clic en el enlace **Registration on the tracking server(s)** y, a continuación, seleccione una de las opciones disponibles.

![](assets/s_ncs_install_deployment_wiz_09.png)

Existen tres tipos de arquitectura posibles para implementar el seguimiento:

1. **Agregar compatibilidad para el seguimiento en una instancia existente**

   Esta opción se aplica si la instancia ya se creó para otras necesidades (servidor MTA, etc.) en servidores que se utilizarán como servidores de seguimiento.

   ![](assets/s_ncs_install_deployment_wiz_11.png)

   Introduzca la contraseña de la cuenta **internal** en los servidores de redirección para configurar la instancia de seguimiento.

   >[!NOTE]
   >
   >Si se utilizan varios servidores de seguimiento, todos deben utilizar el mismo nombre y contraseña.

   Especifique el nombre de la instancia y la contraseña.

1. **Crear una nueva instancia dedicada al seguimiento**

   Esta opción es útil cuando las instancias de seguimiento están reservadas para el seguimiento y no tienen ningún otro módulo de aplicación.

   ![](assets/s_ncs_install_deployment_wiz_10.png)

   Introduzca la contraseña de la cuenta **internal** en los servidores de redirección para configurar la instancia de seguimiento.

   >[!NOTE]
   >
   >Si hay varios servidores de seguimiento configurados, todos deben utilizar la misma contraseña.

   Especifique el nombre de la instancia, la contraseña y las máscaras DNS asociadas, como **[!UICONTROL Campaign*]**.

1. **Valide una instancia de seguimiento ya preconfigurada para usted**

   Esta opción se utiliza cuando no tiene la contraseña de la cuenta **internal**; En este caso, una cuenta de seguimiento está preconfigurada para usted en los servidores de seguimiento. Introduzca la contraseña de la cuenta de seguimiento de los servidores de redirección para validar la instancia de seguimiento.

   ![](assets/s_ncs_install_deployment_wiz_17.png)

   Especifique el nombre de la instancia que se va a validar.

Haga clic en **Aprobar** para iniciar el proceso de grabación con el servidor de seguimiento.

En la ventana anterior, un mensaje confirma el registro a nivel de servidor de seguimiento:

![](assets/s_ncs_install_deployment_wiz_tracking_ok.png)

Los parámetros vinculados a búsquedas de URL **no deben modificarse** para una instalación estándar. Para todos los demás parámetros, póngase en contacto con el Adobe.

## Parámetros de canal móvil {#mobile-channel-parameters}

El siguiente paso permite definir la configuración predeterminada para los envíos a móviles (SMS y WAP Push).

>[!NOTE]
>
>El canal móvil es opcional: este paso solo aparece si se ha comprado. Compruebe el acuerdo de licencia.

![](assets/s_ncs_install_deployment_wiz_12.png)

### Cuenta predeterminada para envío de SMS {#default-account-for-sms-delivery}

Introduzca la siguiente información:

* **[!UICONTROL Label]** : Escriba un nombre para esta cuenta push de SMS/Wap. Por ejemplo, puede que desee utilizar el nombre del enrutador.
* Para los campos **[!UICONTROL Server]**, **[!UICONTROL Port]**, **[!UICONTROL Account]**, **[!UICONTROL Password]**, **[!UICONTROL Connector]**, **[!UICONTROL Send Endpoint]**, **[!UICONTROL Reception Endpoint]**, **[!UICONTROL Notification Endpoint]**: Póngase en contacto con su proveedor de servicios para obtener la configuración necesaria.

### Parámetros de SMS enviados {#parameters-of-sms-sent}

En la lista desplegable **Priority**: Seleccione &quot;Normal&quot;, &quot;Alto&quot; o &quot;Urgente&quot; para aplicarlo a los mensajes que se van a enviar.

### Parámetros avanzados {#advanced-parameters}

Los **Parámetros avanzados...El enlace** le permite acceder a las opciones de reintento y cuarentena.

![](assets/s_ncs_install_deployment_wiz_13.png)

La información sobre los reintentos está disponible en los campos **Period of retry** y **Number of retry**: Cuando no se puede acceder a un móvil, de forma predeterminada, el programa lo volverá a intentar 5 veces a intervalos de al menos 15 minutos (para el período de entrega máximo). Estos valores se pueden adaptar a sus necesidades.

Las opciones de configuración para cuarentenas son las siguientes:

* **[!UICONTROL Time between two significant errors]** : Introduzca un valor predeterminado (de forma predeterminada &quot;1d&quot;: día) para definir el tiempo que la aplicación espera antes de incrementar el contador de errores en caso de error.
* **[!UICONTROL Maximum number of errors before quarantine]** : Una vez alcanzado este valor, el número de móvil se pone en cuarentena (de forma predeterminada, &quot;5&quot;: el número se pondrá en cuarentena tras el sexto error). Esto significa que el contacto se excluirá automáticamente de futuros envíos.

## Configuración regional {#regional-settings}

Esta etapa permite incluir las preferencias de la política de datos.

![](assets/s_ncs_install_deployment_wiz_14.png)

* **[!UICONTROL Consider all phone numbers as international ones]** : Cuando se selecciona esta opción, la aplicación aplica el formato internacional a los números de teléfono (el prefijo country es obligatorio porque el número de dígitos no se comprobará antes de aplicar el formato). Si esta opción no está seleccionada, debe anteponer el número de teléfono internacional con &quot;+&quot; o &quot;00&quot; usted mismo.
* **[!UICONTROL Store all phone numbers using the international format]** : Esta opción solo afecta a los números de teléfono  **** nacionales importados o editados. Defina si desea utilizar un formato doméstico (como 425 555 0150) o el formato internacional (p. ej. +1 425 55 0150)

## Acceso desde Internet {#access-from-the-internet}

>[!IMPORTANT]
>
>Por razones de privacidad, recomendamos utilizar HTTPS para todos los recursos externos.

Este paso permite definir las direcciones URL de acceso para las páginas de Adobe Campaign expuestas en Internet.

También debe indicar aquí las opciones de publicación vinculadas a los formularios web.

![](assets/s_ncs_install_deployment_wiz_15.png)

### Servidores expuestos en la Web {#servers-exposed-on-the-web}

Utilice esta página para rellenar las URL del servidor para:

1. Acceda al servidor de aplicaciones expuesto en Internet: formularios de suscripción/baja, extranet, etc.
1. Acceda al servidor de aplicaciones para los recursos que no están expuestos en la web: formularios, intranet, páginas de confirmación.
1. Acceda a las páginas espejo de los envíos.

   Una página espejo es una página dinámica que muestra el contenido del correo electrónico. Se accede a través de un vínculo insertado en el mensaje enviado al destinatario y puede contener elementos personalizados. La página espejo ofrece al destinatario la posibilidad de leer el mensaje en un navegador de Internet en lugar del software de correo electrónico, independientemente del formato de envío (texto o HTML). Sin embargo, las páginas espejo solo se generan para un envío determinado si se ha definido el contenido HTML requerido.

Adobe Campaign permite diferenciar estas tres direcciones URL para distribuir la carga en varias plataformas.

## Administración de recursos públicos {#managing-public-resources}

>[!IMPORTANT]
>
>Por razones de privacidad, recomendamos utilizar HTTPS para todos los recursos externos.

Para que se puedan ver desde el exterior, las imágenes utilizadas en los mensajes de correo electrónico y recursos públicos vinculados a las campañas deben estar presentes en un servidor accesible de forma externa. A continuación, pueden estar disponibles para destinatarios u operadores externos.

![](assets/s_ncs_install_deployment_wiz_img_uploading.png)

Para este paso, debe introducir:

1. La nueva URL del recurso público. Para obtener más información, consulte la sección [URL de recursos públicos](#public-resources-url) .
1. El modo de detección de imágenes en una entrega. Para obtener más información, consulte la sección [Detección de imágenes de entrega](#delivery-image-detection) .
1. Opciones de publicación. Para obtener más información, consulte la sección [Modos de publicación](#publication-modes) .

Se puede acceder a los recursos públicos a través del nodo **Administration > Resources > Online > Public resources** del árbol de Adobe Campaign. Se recopilan en una biblioteca y se pueden incluir en correos electrónicos, pero también se utilizan en campañas o tareas, y en la administración de contenido.

![](assets/install_pub_resources_view.png)

### URL de recursos públicos {#public-resources-url}

El primer campo permite especificar el inicio de la URL utilizada para los recursos una vez cargados. Cuando se cargan, se puede acceder a los recursos a través de esta nueva dirección URL.

En una entrega, puede utilizar imágenes almacenadas en la biblioteca de recursos públicos o en cualquier otra imagen o imagen local almacenada en un servidor.

* Para imágenes de correo electrónico, la dirección URL **https://** server **/res/img**.

   Este valor se puede sobrescribir para cada envío.

* Para los recursos públicos, la URL **https://** server **/res/** instance ****donde **instance**es el nombre de la instancia de seguimiento.

### Detección de imágenes de entrega {#delivery-image-detection}

En una entrega, puede utilizar imágenes almacenadas en la biblioteca de recursos públicos o en cualquier otra imagen o imagen local almacenada en un servidor.

El campo **URL masks** permite especificar la lista de máscaras de URL que se deben omitir al cargar imágenes automáticamente. Por ejemplo, si utiliza imágenes almacenadas en un sitio accesible desde el exterior, en particular en un sitio de Internet, puede introducir la dirección URL del sitio en este campo.

![](assets/s_ncs_install_deployment_wiz_img_mask.png)

Puede especificar varias máscaras de URL usando una coma para separar cada una de ellas.

* Para obtener información sobre el uso y la administración de imágenes en correos electrónicos, consulte [esta sección](../../delivery/using/defining-the-email-content.md#adding-images).
* En el asistente de entregas, las imágenes llamadas desde estas direcciones URL tendrán el estado &quot;Ignorado&quot;.

### Modos de publicación {#publication-modes}

La sección inferior del asistente le permite seleccionar las opciones de publicación de recursos públicos e imágenes. Estas opciones también están disponibles para los formularios web y las encuestas.

Están disponibles los siguientes modos de publicación:

* Servidores de seguimiento

   Los recursos se copiarán automáticamente en los distintos servidores de seguimiento. Se configuran en el paso [Configuración de seguimiento](#tracking-configuration).

* Otros servidores de Adobe Campaign

   Puede utilizar otros servidores de Adobe Campaign donde se copiarán los recursos.

   En el servidor, para utilizar un servidor Adobe Campaign dedicado, debe crear una nueva instancia con el siguiente comando:

   ```
   nlserver config -addtrackinginstance:<trackingA>/<trackingA*>
   ```

   A continuación, introduzca la contraseña.

   Los parámetros de los servidores dedicados se indican en los campos **[!UICONTROL Media URL(s)]**, **[!UICONTROL Password]** y **[!UICONTROL Instance name]**.

   ![](assets/s_ncs_install_images_upload_b.png)

* Secuencia de comandos de publicación manual (solo para recursos públicos)

   ![](assets/s_ncs_install_images_upload_c.png)

   Puede publicar las imágenes mediante una secuencia de comandos:

   * Debe crear esta secuencia de comandos: Su contenido depende de la configuración.
   * El siguiente comando llama a la secuencia de comandos:

      ```
      [INSTALL]/copyToFrontal.vbs "$(XTK_INSTALL_DIR)\var\<instance>\upload\" "img1,img2,img3"
      ```

      donde `[INSTALL]` es la ruta de acceso a la carpeta de instalación de Adobe Campaign.

   * En Unix, asegúrese de que la secuencia de comandos sea ejecutable.

Para las imágenes, debe copiarlas de la carpeta &quot;imágenes&quot; especificada a través de la opción **NmsDelivery_ImageSubDirectory** en uno o más servidores frontales. Estos servidores almacenan las imágenes para que sean accesibles a través de la nueva URL configurada.

En caso de publicación en un servidor de Adobe Campaign sin una secuencia de comandos de publicación manual, de forma predeterminada, las imágenes de una entrega se almacenan en el `$(XTK_INSTALL_DIR)/var/res/img/ directory`. La URL correspondiente es la siguiente: **`https://server/res/img`**.

`XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)`. La URL correspondiente es la siguiente: **`https://server/res/instance`** donde instancia es el nombre de la instancia de seguimiento.

>[!NOTE]
>
>Es posible cambiar el directorio de almacenamiento de recursos públicos. Para obtener más información, consulte [Administración de recursos públicos](#managing-public-resources).

### Sincronización de recursos públicos {#synchronizing-public-resources}

Esta funcionalidad le permite **sincronizar recursos públicos** en varios servidores de reserva.

Si un recurso público no está presente en el servidor de seguimiento o si el recurso devuelve un error 404, el servidor de seguimiento intentará encontrar el recurso en uno de los servidores de reserva.

La declaración y la configuración de los servidores de repuesto deben realizarse en el archivo **serverConf.xml** del servidor de marketing. Todos los parámetros disponibles en **serverConf.xml** se enumeran en esta [sección](../../installation/using/the-server-configuration-file.md).

**Declaración**

```
<redirection>
<spareServer enabledIf="" id="" url=""/>
</redirection>
```

**Configuración**

Para cada recurso público que debe sincronizarse, debe añadir un atributo de estado al elemento `<url>` en la parte `<relay>`:

El atributo de estado puede tener uno de estos tres valores:

* repuesto: El recurso público está sincronizado

* normal: Comportamiento existente (sin sincronización)

* lista negra: La dirección URL se agrega a la  de lista de bloqueados si devuelve un error 404. La duración (en segundos) de la URL que se encuentra en la  de lista de bloqueados se define mediante un atributo **timeout** cuyo valor predeterminado es 60s.

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

El último paso del asistente de implementación permite configurar la depuración automática de los datos obsoletos. Los valores se expresan en días.

![](assets/s_ncs_install_deployment_wiz_16.png)

Los datos se eliminan automáticamente mediante el flujo de trabajo Database cleanup . Para obtener más información sobre cómo configurar y operar este flujo de trabajo y detalles sobre los elementos eliminados, consulte este [documento](../../production/using/database-cleanup-workflow.md).
