---
title: Definición del contenido del correo electrónico en Adobe Campaign Classic
description: Obtenga información sobre cómo definir el contenido del correo electrónico al utilizar Adobe Campaign Classic.
page-status-flag: never-activated
uuid: ddcc2e3b-e251-4a7a-a22a-28701522839f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-emails
discoiquuid: 2ea2747f-957f-41a9-a03f-20c03fa99116
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 4ac96bf0e54268832b84b17c3cc577af038cc712

---


# Definición del contenido del correo electrónico{#defining-the-email-content}

## Remitente {#sender}

Para definir el nombre y la dirección del remitente que aparece en el encabezado de los mensajes enviados, haga clic en el vínculo **[!UICONTROL From]**.

![](assets/s_ncs_user_wizard_email02.png)

Esta ventana permite introducir toda la información necesaria para crear los encabezados de los mensajes de correo electrónico. Dicha información puede personalizarse. Para ello, utilice los botones a la derecha de los campos de entrada para insertar campos personalizados.

Para saber cómo insertar y utilizar campos personalizados, consulte la sección [Acerca de la personalización](../../delivery/using/about-personalization.md).

>[!NOTE]
>
>* La dirección del remitente se utiliza en las respuestas de forma predeterminada.
>* Los parámetros de encabezado no deben estar vacíos. De forma predeterminada, contienen los valores introducidos al configurar el asistente de implementación. Para obtener más información, consulte la [Guía de instalación](../../installation/using/deploying-an-instance.md).
>* La dirección del remitente es obligatoria para permitir que se envíe un mensaje de correo electrónico (estándar RFC).
>* Adobe Campaign comprueba la sintaxis de las direcciones de correo electrónico introducidas.


>[!CAUTION]
>
>En el contexto de las comprobaciones implementadas por los proveedores de acceso a Internet (ISP) para luchar contra los mensajes de correo electrónico no deseados (spam), Adobe recomienda crear cuentas de correo electrónico que correspondan a las direcciones especificadas para las entregas y las respuestas. Consulte con el administrador del sistema de mensajería.

## Asunto del mensaje {#message-subject}

El asunto del mensaje se configura en el campo correspondiente. Puede introducirlo directamente en el campo o hacer clic en el vínculo **[!UICONTROL Subject]** para introducir una secuencia de comandos. El vínculo personalizado permite insertar campos de base de datos en el asunto.

>[!CAUTION]
>
>El asunto del mensaje es obligatorio.

![](assets/s_ncs_user_wizard_email_object.png)

El contenido del campo se sustituye por el valor del perfil de destinatario cuando se envía el mensaje.

Por ejemplo, en el mensaje anterior, el asunto del mensaje está personalizado para cada destinatario con datos de su perfil.

>[!NOTE]
>
>El uso de plantillas personalizadas se presenta en [Acerca de la personalización](../../delivery/using/about-personalization.md).

## Contenido del mensaje {#message-content}

>[!CAUTION]
>
>Por razones de privacidad, recomendamos utilizar HTTPS para todos los recursos externos.

El contenido del mensaje se define en la sección inferior de la ventana de configuración de entrega.

Los mensajes se envían en formato HTML o texto de forma predeterminada, según las preferencias del destinatario. Se recomienda crear contenido en ambos formatos para garantizar que los mensajes se puedan visualizar correctamente en cualquier sistema de correo. Para obtener más información, consulte [Seleccionar formatos de mensajes](#selecting-message-formats).

* Para importar un contenido HTML, usar el botón **[!UICONTROL Open]**. También puede pegar el código de fuente directamente en la subpestaña **[!UICONTROL Source]**.

   Si está utilizando el [Editor de contenido digital](../../web/using/about-campaign-html-editor.md) (DCE), consulte [Selección de una plantilla de contenido](../../web/using/use-case--creating-an-email-delivery.md#step-3---selecting-a-content).

   >[!CAUTION]
   >
   >El contenido HTML debe crearse de antemano y luego importarse en Adobe Campaign. El editor HTML no está diseñado para creación de contenido.

   La subpestaña **[!UICONTROL Preview]** permite ver la renderización de cada contenido para un destinatario. Los campos personalizados y los elementos condicionales del contenido se sustituyen por la información correspondiente del perfil seleccionado.

   Los botones de la barra de herramientas proporcionan acceso a las acciones estándar y a los parámetros de formato de la página HTML.

   ![](assets/s_ncs_user_wizard_email01_138.png)

   Puede insertar imágenes en mensajes desde un archivo local o desde una biblioteca de imágenes en Adobe Campaign. Para ello, haga clic en el icono **[!UICONTROL Image]** y seleccione las opciones deseadas.

   ![](assets/s_ncs_user_wizard_email01_18.png)

   Se puede acceder a las imágenes de biblioteca a través de la carpeta **[!UICONTROL Resources>Online>Public resources]** en el árbol de carpetas. Consulte también [Añadir imágenes](#adding-images).

   El último botón de la barra de herramientas permite insertar campos personalizados.

   >[!NOTE]
   >
   >El uso de plantillas personalizadas se presenta en [Acerca de la personalización](../../delivery/using/about-personalization.md).

   Las pestañas situadas en la parte inferior de la página permiten mostrar el código HTML de la página que se está creando y ver la renderización del mensaje con su personalización. Para iniciar esta pantalla, haga clic en **[!UICONTROL Preview]** y seleccione un destinatario con el botón **[!UICONTROL Test personalization]** de la barra de herramientas. Puede seleccionar un destinatario de los objetivos definidos o elegir otro destinatario.

   ![](assets/s_ncs_user_wizard_email01_139.png)

   Puede validar el mensaje HTML. También puede ver el contenido del encabezado del correo electrónico.

   ![](assets/s_ncs_user_wizard_email01_140.png)

* Para importar un contenido de texto, utilice el botón **[!UICONTROL Open]** o la pestaña **[!UICONTROL Text Content]** para introducir el contenido del mensaje cuando se muestre en formato de texto. Utilice los botones de la barra de herramientas para acceder a las acciones de los contenidos. El último botón permite insertar los campos personalizados.

   ![](assets/s_ncs_user_wizard_email01_141.png)

   En cuanto al formato HTML, haga clic en la pestaña **[!UICONTROL Preview]** situada en la parte inferior de la página para ver la renderización del mensaje con su personalización.

   ![](assets/s_ncs_user_wizard_email01_142.png)

## Selección de los formatos de mensaje {#selecting-message-formats}

Puede cambiar el formato de los mensajes de correo electrónico enviados. Para ello, edite las propiedades de la entrega y haga clic en la pestaña **[!UICONTROL Delivery]**.

![](assets/s_ncs_user_wizard_email_param.png)

Seleccione el formato del correo electrónico en la sección inferior de la ventana:

* **[!UICONTROL Use recipient preferences]** (modo predeterminado)

   El formato de mensaje se define según los datos almacenados en el perfil de destinatario y se almacena de forma predeterminada en el campo **[!UICONTROL email format]** (@emailFormat). Si un destinatario desea recibir mensajes en un formato determinado, este es el formato enviado. Si el campo no está rellenado, se envía un mensaje multipart-alternative (consulte a continuación).

* **[!UICONTROL Let recipient mail client choose the most appropriate format]**

   El mensaje contiene ambos formatos: texto y HTML. El formato que se muestra al recibirlo depende de la configuración del software de correo del destinatario (multipart-alternative).

   >[!CAUTION]
   >
   >Esta opción incluye ambas versiones del documento. Por lo tanto, esto afecta a la tasa de entrega ya que el tamaño del mensaje es mayor.

* **[!UICONTROL Send all messages in text format]**

   El mensaje se envía en formato de texto. El formato HTML no se envía, pero se utiliza solo para la página espejo cuando el destinatario hace clic en el mensaje.

## Definición del contenido interactivo {#amp-for-email-format}

Adobe Campaign le permite probar el nuevo formato [AMP interactivo para correo electrónico](https://amp.dev/about/email/), que permite enviar correos electrónicos dinámicos en ciertas condiciones.

Para obtener más información, consulte [esta sección](../../delivery/using/defining-interactive-content.md).

## Uso de la gestión de contenido {#using-content-management}

Puede definir el contenido de la entrega mediante los formularios de gestión de contenido directamente en el asistente de envíos. Para ello, debe hacer referencia a la plantilla de publicación de la gestión de contenido que se va a utilizar, en la pestaña **[!UICONTROL Advanced]** de las propiedades de entrega.

![](assets/s_ncs_content_in_delivery.png)

Una pestaña adicional permite introducir contenido que se integra y formatea automáticamente según las reglas de gestión de contenido.

![](assets/s_ncs_content_in_delivery_edition_tab.png)

>[!NOTE]
>
>Para obtener más información sobre la administración de contenido en Adobe Campaign, consulte [esta sección](../../delivery/using/about-content-management.md).

## Adición de imágenes {#adding-images}

Las entregas de correo electrónico de formato HTML pueden contener imágenes. Desde el asistente de entregas, puede importar una página HTML que contenga imágenes o insertar imágenes directamente utilizando el editor HTML mediante el icono **[!UICONTROL Image]**.

Las imágenes pueden ser:

* Una imagen local o una imagen obtenida desde un servidor
* Una imagen almacenada en la biblioteca de recursos públicos de Adobe Campaign

   Los recursos públicos son accesibles a través del nodo **[!UICONTROL Resources > Online]** de la jerarquía de Adobe Campaign. Se agrupan en una biblioteca y se pueden incluir en mensajes de correo electrónico, pero también se pueden utilizar para campañas o tareas, o para la gestión de contenido.

* Un recurso compartido con Adobe Experience Cloud. Consulte [esta sección](../../integrations/using/sharing-assets-with-adobe-experience-cloud.md).

>[!CAUTION]
>
>Para incluir imágenes en los mensajes de correo electrónico con el asistente de entregas, la instancia de Adobe Campaign debe configurarse para habilitar la gestión de recursos públicos. Este procedimiento se puede realizar desde el asistente de implementación. Consulte [esta sección](../../installation/using/deploying-an-instance.md) para obtener más información sobre la configuración.

El asistente de entrega permite añadir imágenes locales o imágenes almacenadas en la biblioteca al contenido de los mensajes. Para ello, haga clic en el botón **[!UICONTROL Image]** en la barra de herramientas HTML.

![](assets/s_ncs_user_image_from_library.png)

Para que los destinatarios puedan ver las imágenes incluidas en los mensajes que reciben, estos mensajes deben estar disponibles en un servidor accesible desde el exterior.

Para administrar imágenes mediante el asistente de entregas, debe hacer clic en el icono **[!UICONTROL Tracking & Images]** de la barra de herramientas.

![](assets/s_ncs_user_email_del_img_param.png)

Seleccione **[!UICONTROL Upload images]** en la **[!UICONTROL Images]** pestaña. Puede elegir si desea incluir las imágenes en el mensaje de correo electrónico.

![](assets/s_ncs_user_email_del_img_upload.png)

* Puede cargar imágenes manualmente sin esperar a la fase de análisis de entregas. Para ello, haga clic en el vínculo **[!UICONTROL Upload images now]**.
* Puede especificar otra ruta para acceder a las imágenes en el servidor de seguimiento. Para ello, indíquela en el campo **[!UICONTROL Image URL]**. Este valor anula el valor definido en los parámetros del asistente de instalación.

Cuando se abre contenido HTML con imágenes incluidas en el asistente de entregas, un mensaje le da la opción de cargar las imágenes inmediatamente en función de los parámetros de entrega.

![](assets/s_ncs_user_email_del_img_local.png)

>[!CAUTION]
>
>Las rutas de acceso a la imagen se modifican durante la carga manual o al enviar mensajes.

**Ejemplo: entrega de un mensaje con imágenes{#example--sending-a-message-with-images}**

A continuación se muestra un ejemplo de entrega con cuatro imágenes:

![](assets/s_ncs_user_images_in_delivery_wiz_1.png)

Estas imágenes provienen de un directorio local o sitio web que puede verificar desde la pestaña **[!UICONTROL Source]**.

![](assets/s_ncs_user_images_in_delivery_wiz_2.png)

Haga clic en el icono **[!UICONTROL Tracking & Images]** y, a continuación, en la pestaña **[!UICONTROL Images]** para comenzar a detectar imágenes en el mensaje.

Puede ver el estado de cada imagen detectada:

* Si una imagen se almacena localmente o se ubica en otro servidor, aunque este servidor sea visible desde el exterior (en un sitio de Internet, por ejemplo), se detecta como **[!UICONTROL Not yet online]**.
* Las imágenes se detectan como **[!UICONTROL Already online]** si se cargaron anteriormente antes de crear otro envío.
* En el asistente de implementación puede definir las direcciones URL para las que no se ha habilitado la detección de imágenes: la carga de estas imágenes pasa a estar **[!UICONTROL Skipped]**.

>[!NOTE]
>
>Las imágenes se identifican por su contenido y no por sus rutas de acceso. Esto significa que la imagen cargada previamente con un nombre diferente o en un directorio diferente se detecta como **[!UICONTROL Already online]**.

Durante la fase de análisis, las imágenes se cargan automáticamente en el servidor para poder acceder a ellas desde el exterior, excepto en las imágenes locales que deben cargarse de antemano.

Puede trabajar con previsión y cargar las imágenes para que puedan verlas otros operadores de Adobe Campaign. Esto resulta útil si trabaja de forma colaborativa. Para ello, haga clic en **[!UICONTROL Upload the images straightaway...]** para cargar las imágenes en el servidor.

![](assets/s_ncs_user_images_in_delivery_wiz_3.png)

>[!NOTE]
>
>A continuación, se modifican las URL de las imágenes del mensaje de correo electrónico, además de sus nombres, concretamente.

Una vez que las imágenes están en línea, puede ver los cambios en los nombres y en las rutas a través de la pestaña **[!UICONTROL Source]** del mensaje.

![](assets/s_ncs_user_images_in_delivery_wiz_4.png)

Si selecciona **[!UICONTROL Include the images in the email]** puede elegir las imágenes que desea incluir en la columna correspondiente.

![](assets/s_ncs_user_images_in_delivery_wiz_5.png)

>[!NOTE]
>
>Si las imágenes locales se incluyen en el mensaje, debe confirmar los cambios en el código de fuente del mensaje.

## Inserción de un código de barras en un correo electrónico{#inserting-a-barcode-in-an-email}

El módulo de generación de códigos de barras permite crear varios tipos de códigos de barras que cumplan con muchos estándares habituales, incluidos códigos de barras 2D.

Es posible generar dinámicamente un código de barras como mapa de bits que utilice un valor definido con criterios de cliente. Se pueden incluir códigos de barras personalizados en las campañas de correo electrónico. El destinatario puede imprimir el mensaje y mostrarlo a la empresa emisora para escanearlo (por ejemplo, durante la comprobación).

Para insertar un código de barras en un correo electrónico, coloque el cursor en el contenido en el que desea mostrarlo y, a continuación, haga clic en el botón de personalización. Seleccione **[!UICONTROL Include > Barcode...]**.

![](assets/barcode_insert_14.png)

A continuación, configure los siguientes elementos para adaptarlos a sus necesidades:

1. Seleccione el tipo de código de barras.

   * Para el formato 1D, los siguientes tipos están disponibles en Adobe Campaign: Codabar, Code 128, GS1-128 (anteriormente EAN-128), UPC-A, UPC-E, ISBN, EAN-8, Code39, Interleaved 2 de 5, POSTNET y Royal Mail (RM4SCC).

      Ejemplo de código de barras 1D:

      ![](assets/barcode_insert_08.png)

   * Los tipos DataMatrix y PDF417 están relacionados con el formato 2D.

      Ejemplo de código de barras 2D:

      ![](assets/barcode_insert_09.png)

   * Para insertar un código QR, seleccione este tipo e introduzca la tasa de corrección de errores que desee aplicar. Esta velocidad define la cantidad de información repetida y la tolerancia ante el deterioro.

      ![](assets/barcode_insert_06.png)

      Ejemplo de código QR:

      ![](assets/barcode_insert_12.png)

1. Introduzca el tamaño del código de barras que desea insertar en el correo electrónico: la configuración de la escala permite aumentar o reducir el tamaño del código de barras, de x1 a x10.
1. El campo **[!UICONTROL Value]** permite definir el valor del código de barras. Un valor puede coincidir con una oferta especial y puede ser la función de un criterio, puede ser el valor de un campo de base de datos vinculado a los clientes.

   Este ejemplo muestra un código de barras de tipo EAN-8 al que se ha añadido el número de cuenta de un destinatario. Para ello, haga clic en el botón de personalización a la derecha del campo **[!UICONTROL Value]** y seleccione **[!UICONTROL Recipient > Account number]**:

   ![](assets/barcode_insert_15.png)

1. El campo **[!UICONTROL Height]** permite configurar la altura del código de barras sin cambiar su anchura, modificando la cantidad de espacio entre cada barra.

   No hay ningún control de entrada restrictivo en función del tipo de código de barras. Si un valor de código de barras es incorrecto, solo se puede ver en el modo de **Preview** donde el código de barras aparece tachado en rojo.

   >[!NOTE]
   >
   >El valor asignado a un código de barras depende de su tipo. Por ejemplo, un tipo EAN-8 debe tener exactamente 8 números.
   >
   >El botón de personalización situado a la derecha del campo **[!UICONTROL Value]** permite añadir datos además del propio valor. Esto enriquece el código de barras, siempre que el estándar de código de barras lo acepte.
   >
   >Por ejemplo, si está utilizando un código de barras de tipo GS1-128 y desea introducir el número de cuenta de un destinatario además del valor, haga clic en el botón de personalización y seleccione **[!UICONTROL Recipient > Account number]**. Si el número de cuenta del destinatario seleccionado se introduce correctamente, el código de barras lo tiene en cuenta.

Una vez configurados estos elementos, puede finalizar su el correo electrónico y enviarlo. Para evitar errores, asegúrese siempre de que el contenido se muestra correctamente antes de realizar una entrega haciendo clic en la pestaña **[!UICONTROL Preview]**.

![](assets/barcode_insert_10.png)

>[!NOTE]
>
>Si el valor de un código de barras es incorrecto, su mapa de bits se muestra tachado en rojo.

![](assets/barcode_insert_11.png)

## Envío de correos electrónicos en móviles japoneses {#sending-emails-on-japanese-mobiles}

### Formatos de correo electrónico para móviles japoneses {#email-formats-for-japanese-mobiles}

Adobe Campaign administra tres formatos japoneses específicos para el correo electrónico en móviles: **Deco-mail** (móviles DoCoMo), **Decore Mail** (móviles Softbank) y **Decoration Mail** (móviles KDDI AU). Estos formatos imponen restricciones particulares de codificación, estructura y tamaño. Obtenga más información sobre las limitaciones y recomendaciones en [esta sección](#limitations-and-recommendations).

Para que el destinatario reciba mensajes correctamente en uno de estos formatos, se recomienda seleccionar **[!UICONTROL Deco-mail (DoCoMo)]**, **[!UICONTROL Decore Mail (Softbank)]** o **[!UICONTROL Decoration Mail (KDDI AU)]** en el perfil correspondiente:

![](assets/deco-mail_03.png)

Sin embargo, si deja la opción **[!UICONTROL Email format]** como **[!UICONTROL Unknown]**, **[!UICONTROL HTML]** o **[!UICONTROL Text]**, Adobe Campaign detecta (cuando envíe el correo electrónico) el formato japonés que debe usar de modo que el mensaje se muestre correctamente.

Este sistema de detección automática se basa en la lista de dominios predefinidos definidos en el conjunto de reglas de correo **[!UICONTROL Management of Email Formats]**. Para obtener más información sobre la gestión de formatos de correo electrónico, consulte [esta página](../../installation/using/email-deliverability.md#managing-email-formats).

### Limitaciones y recomendaciones {#limitations-and-recommendations}

Se aplican una serie de restricciones en la entrega de correos electrónico que se pueden leer en un móvil gestionado por un proveedor japonés (Softbank, DoCoMo, KDDI AU).

Por lo tanto, debe:

* Usar imágenes en formato JPEG o GIF.
* Crear una entrega con secciones de texto y HTML que sean inferiores a los 10 000 bytes (para KDDI AU y DoCoMo).
* Utilizar imágenes con un tamaño total inferior a 100 KB (antes de la codificación).
* No utilizar más de 20 imágenes por mensaje.
* Utilizar un formato HTML de tamaño reducido (hay un número limitado de etiquetas disponibles para cada operador).

>[!NOTE]
>
>Al crear el mensaje, se deben tener en cuenta las restricciones específicas de cada operador. Consulte:
>
>* Para obtener más información sobre DoCoMo, consulte [esta página](https://www.nttdocomo.co.jp/service/developer/make/content/deco_mail/index.html).
>* Para obtener más información sobre KDDI AU, consulte [esta página](https://www.au.com/ezfactory/tec/spec/decorations/template.html)
>* Para obtener más información sobre Softbank, consulte [esta página](https://www.support.softbankmobile.co.jp/partner/home_tech3/index.cfm)


### Prueba del contenido de correo electrónico {#testing-the-email-content}

#### Previsualización del mensaje {#previewing-the-message}

Adobe Campaign le permite comprobar que su formato de mensaje está adaptado a un móvil japonés.

Una vez que haya definido el contenido y haya introducido el asunto del correo electrónico, puede comprobar la visualización y el formato cuando se cree el mensaje.

En la pestaña **[!UICONTROL Preview]** de la ventana de edición de contenido, hacer clic en **[!UICONTROL More... > Deco-mail diagnostic]** le permite:

* Comprobar que las etiquetas de contenido HTML cumplan las restricciones de formato japonés
* Comprobar que el número de imágenes del mensaje no supere el límite impuesto por el formato (20 imágenes)
* Comprobar el tamaño total del mensaje (menor que 100 kB)

   ![](assets/deco-mail_06.png)

#### Ejecución de las reglas de tipología {#running-typology-rule}

Además del diagnóstico de la previsualización, se realiza una segunda comprobación al enviar una prueba o una entrega: una regla de tipología específica, **[!UICONTROL Deco-mail check]**, se inicia durante el análisis.

>[!CAUTION]
>
>Esta regla de tipología solo se ejecuta si al menos uno de los destinatarios está configurado para recibir correos electrónicos en formato **[!UICONTROL Deco-mail (DoCoMo)]**, **[!UICONTROL Decore Mail (Softbank)]** o **[!UICONTROL Decoration Mail (KDDI AU)]**.

Esta regla de tipología le permite asegurarse de que la entrega respeta las [limitaciones de formato](#limitations-and-recommendations) definidas por los operadores japoneses, especialmente en relación con el tamaño total del correo electrónico, el tamaño de las secciones HTML y de texto, el número de imágenes de los mensajes y las etiquetas del contenido HTML.

#### Envío de pruebas {#sending-proofs}

Puede realizar pruebas para probar su entrega. Cuando envíe la prueba, si utiliza direcciones de sustitución, introduzca direcciones que correspondan al formato de correo electrónico del perfil utilizado.

Por ejemplo, puede reemplazar la dirección de un perfil por test@softbank.ne.jp si el formato de correo electrónico de este perfil se ha definido previamente en **[!UICONTROL Decore Mail (Softbank)]**.

![](assets/deco-mail_05.png)

### Envío de mensajes {#sending-messages}

Para enviar un correo electrónico a los destinatarios con formatos de correo electrónico japoneses con Campaign, existen dos opciones:

* Crear dos entregas: uno solo para los destinatarios japoneses y otro para otros destinatarios. Consulte [esta sección](#designing-a-specific-delivery-for-japanese-formats).
* Crear una única entrega, y Adobe Campaign detecta automáticamente el formato que debe utilizar. Consulte [esta sección](#designing-a-delivery-for-all-formats).

#### Diseño de una entrega específico para formatos japoneses {#designing-a-specific-delivery-for-japanese-formats}

Puede crear un flujo de trabajo que contenga dos entregas: uno para su lectura en un dispositivo móvil japonés y otro para los destinatarios con un formato de correo electrónico estándar.

Para ello, utilice la actividad **[!UICONTROL Split]** de su flujo de trabajo y defina los formatos de correo electrónico japoneses (Deco-mail, Decoration Mail y Decore Mail) como condiciones de filtrado.

![](assets/deco-mail_08.png)

![](assets/deco-mail_07.png)

#### Diseño de una entrega para todos los formatos {#designing-a-delivery-for-all-formats}

Cuando Adobe Campaign administra de forma dinámica los formatos según el dominio (perfiles con formatos de correo electrónico definidos como **[!UICONTROL Unknown]**, **[!UICONTROL HTML]** o **[!UICONTROL Text]** ), puede realizar el mismo envío a todos los destinatarios.

El mensaje de contacto se muestra correctamente para los usuarios de móviles japoneses del mismo modo que para los destinatarios estándar.

>[!CAUTION]
>
>Asegúrese de respetar las funciones especiales asociadas a cada formato de correo electrónico japonés (Deco-mail, Decoration Mail y Decore Mail). Para obtener más información sobre las limitaciones, consulte [esta sección](#limitations-and-recommendations).
