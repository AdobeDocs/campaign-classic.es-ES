---
title: Creación de contenido personalizado
seo-title: Creación de contenido personalizado
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c804745ae58a9bded885ac5aef32f019f43e82be
workflow-type: tm+mt
source-wordcount: '1269'
ht-degree: 29%

---


# Creación de contenido personalizado {#build-personalized-content}

Al diseñar el contenido del mensaje, trate de evitar problemas comunes que podrían impedir la ejecución del envío. La mayoría de las veces, los posibles errores están relacionados con la [personalización](../../delivery/using/about-personalization.md), el [formato](../../delivery/using/defining-the-email-content.md#message-content) y [las imágenes](../../delivery/using/defining-the-email-content.md#adding-images).

## Optimizar la personalización {#optimize-personalization}

Para evitar problemas comunes que podrían impedirle ejecutar su envío y mejorar la experiencia de sus destinatarios, Adobe Campaign le permite personalizar sus mensajes.

Puede utilizar los datos de destinatarios almacenados en la base de datos de Adobe Campaign o recopilados mediante seguimiento, páginas de aterrizaje, suscripciones, etc.
Los conceptos básicos de la personalización se presentan en [esta sección](../../delivery/using/personalization-fields.md).

Asegúrese de que el contenido del mensaje está diseñado correctamente para evitar errores, que generalmente están relacionados con la personalización.

**Sugerencias**: En campos de personalización procedentes de archivos externos proporcionados por proveedores externos, el contenido HTML externo puede ser incorrecto. Para evitarlo, compruebe la sintaxis, el uso de etiquetas, caracteres, etc. Por ejemplo, una etiqueta de personalización de Adobe Campaign siempre tiene el siguiente formulario: &lt;%=table.field%>. Para obtener más información, consulte [esta sección](../../delivery/using/about-personalization.md).

El uso incorrecto de parámetros en bloques de personalización puede ser un problema. Por ejemplo: las variables en JavaScript deben usarse de la siguiente manera:

    &lt;%
    
    var brand = &quot;xxx&quot;
    
    %>

For more on personalization blocks, refer to the [this section](../../delivery/using/personalization-blocks.md).

Puede preparar datos de personalización en un flujo de trabajo para mejorar la análisis de preparación de envíos. Esto debe utilizarse especialmente si los datos de personalización proceden de una tabla externa a través del Acceso de datos federado (FDA). Esta opción se describe en esta [sección](../../delivery/using/personalization-fields.md#optimizing-personalization)

## Creación de contenido optimizado {#optimize-content}

Cuando cree sus correos electrónicos, tenga en cuenta las optimizaciones generales que se describen a continuación.

* El correo electrónico debe tener un diseño sencillo

* Tenga en cuenta a los usuarios de dispositivos móviles

* Evite los correos electrónicos basados por completo en imágenes

* Utilice fuentes seguras para el correo electrónico

* Codifique caracteres especiales

### Línea de asunto

Work on the [subject line](../../delivery/using/defining-the-email-content.md#message-content) to improve open rates:

* Evite los asuntos demasiado largos. Utilice un máximo de 50 caracteres

* Evite utilizar palabras de forma repetida, tales como “gratis” u “oferta”, que podrían considerarse como spam

* Evite mayúsculas y caracteres especiales como &quot;!&quot;, &quot;£&quot;, &quot;€&quot;, &quot;$&quot;

### Página espejo

Incluya siempre un vínculo de página espejo. La posición preferida es la parte superior del correo electrónico. [Más información](../../delivery/using/sending-messages.md#generating-the-mirror-page)

### Vínculo de cancelación de suscripción

El vínculo baja es esencial. Debe ser visible y válido, y el formulario debe ser funcional. By default, when the message is analyzed, a [typology rule](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies) checks whether an opt-out link has been included and generates a warning if it is missing.

**Sugerencia**: Debido a que siempre es posible cometer un error humano, compruebe que el vínculo de exclusión funciona correctamente antes de cada envío. Por ejemplo, al enviar la prueba, asegúrese de que el vínculo sea válido, que el formulario esté en línea y que el campo Ya no se ponga en contacto con este destinatario se cambie a Sí.

Obtenga información sobre cómo insertar un vínculo de exclusión [en esta sección](../../delivery/using/personalization-blocks.md#personalization-blocks-example).

### Tamaño del correo electrónico

Para evitar problemas de rendimiento o de entrega, el tamaño máximo recomendado de un correo electrónico es de unos **35 KB**. To check the message size, go the **[!UICONTROL Preview]** tab and choose a test profile. Una vez generado, el tamaño del mensaje se muestra en la esquina superior derecha.

Para mantener el correo electrónico por debajo del límite, haga lo siguiente:

* Eliminar estilos redundantes o no utilizados

* Mover parte del contenido del correo electrónico a una página de aterrizaje

* Minimizar el código

Asegúrese de probar los cambios antes del envío final

### Longitud de SMS

De forma predeterminada, el número de caracteres de un SMS cumple con los estándares del GSM (Sistema Global de Comunicaciones Móviles). Los mensajes SMS con codificación GSM están limitados a 160 caracteres, o a 153 caracteres por SMS en el caso de los mensajes enviados en varias partes.

La transliteración consiste en reemplazar un carácter de un SMS por otro cuando el estándar GSM no tiene en cuenta dicho carácter. Tenga en cuenta que la inserción de campos de personalización en el contenido del mensaje SMS puede introducir caracteres que no se tienen en cuenta en la codificación GSM. Puede autorizar la transliteración de caracteres marcando la casilla correspondiente en la ficha Ajustes de canal de SMPP de la correspondiente **[!UICONTROL External account]**.
Learn more [in this section](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

**Sugerencias**:

* Para mantener todos los caracteres en tus mensajes SMS tal como están, para no alterar nombres adecuados por ejemplo, no habilites la transliteración.

* Sin embargo, si sus mensajes SMS contienen muchos caracteres que no se tienen en cuenta en el estándar GSM, habilite la transliteración para limitar los costos de envío de sus mensajes.

Learn more [in this section](../../delivery/using/sms-channel.md#about-character-transliteration).

## Mejore el formato {#formatting}

Para evitar errores comunes de formato, consulte los siguientes elementos:

* Formato de **fecha correcto**: Adobe Campaign proporciona funciones de formato de fecha para las plantillas JavaScript y las hojas de estilo XSL. [Más información](../../delivery/using/formatting.md#date-display)

* Uso de caracteres **** autorizados en correos electrónicos: la lista de caracteres válidos para las direcciones de correo electrónico se define en la opción &quot;XtkEmail_Characters&quot;. Obtenga información sobre cómo acceder a las opciones de Campaña [en esta sección](../../installation/using/configuring-campaign-options.md). Para gestionar correctamente caracteres especiales, Adobe Campaign debe estar instalado en Unicode.

* Configuración de la autenticación por **correo electrónico**: asegúrese de que los encabezados de correo electrónico contienen la firma DKIM. La autenticación DKIM (correo identificado con claves de dominio) permite al servidor de correo electrónico receptor verificar que el mensaje fue enviado por la persona o entidad por la que afirma que fue enviado y si el contenido del mensaje se alteró entre el momento en que se envió originalmente (y DKIM &quot;firmado&quot;) y la hora en que fue recibido. Este estándar suele utilizar el dominio en el encabezado De o Remitente. Para obtener más información, consulte [esta sección](../../delivery/using/technical-recommendations.md#dkim).

### Diseño de correo electrónico adaptable

El diseño adaptable garantiza que el correo electrónico se procese de forma óptima para el dispositivo en el que se abre.

* Utilice HTML de correo electrónico interactivo en lugar de HTML web

* Utilice el modo de vista previa y envíe pruebas para probar el diseño en tantos dispositivos como sea posible

* The Adobe Campaign Classic Digital Content Editor (DCE) module includes some responsive design formatted templates for mobile available via **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Content templates]**. Más información [en este artículo](https://theblog.adobe.com/responsive-email-design-101/)

## Administración de imágenes {#manage-images}

Siga las directrices que se indican a continuación cuando tenga que administrar imágenes.

### Evitar el bloqueo de imágenes

Algunos clientes de correo electrónico bloquean las imágenes de forma predeterminada y algunos usuarios cambian su configuración para bloquearlas y optimizar el consumo de datos. Por lo tanto, si las imágenes no se descargan, se puede perder todo el mensaje. Para evitarlo:

* Equilibre el contenido con la imagen y el texto. Evite los correos electrónicos basados por completo en imágenes.

* Si se debe incluir texto en una imagen, use texto alternativo y de título para que el mensaje tenga el efecto deseado. Establezca el formato de texto alternativo o de título para mejorar el aspecto del diseño.

* Evite el uso de imágenes de fondo, ya que algunos servicios de correo electrónico no las admiten.

### Conversión de imágenes en interactivas

Intente que las imágenes sean interactivas y se puedan cambiar de tamaño. Tenga en cuenta que esto puede tener un impacto en los costes, ya que se tarda más en crear.

### Usar referencias de imagen absolutas

Para que sea accesible desde el exterior, las imágenes utilizadas en correos electrónicos y recursos públicos vinculados a campañas deben estar presentes en un servidor accesible desde el exterior.

* Puede comprobar si la configuración de la instancia habilita la administración de recursos públicos. [Más información](../../installation/using/deploying-an-instance.md#managing-public-resources)

* Desde el asistente de entregas, puede importar una página HTML que contenga imágenes o insertar imágenes directamente utilizando el editor HTML mediante el icono **[!UICONTROL Image]**. [Más información](../../delivery/using/defining-the-email-content.md#adding-images)

* Si las imágenes no se muestran, compruebe que las imágenes están disponibles en el servidor. Para ello, haga clic en la ficha Origen del envío. Busque las imágenes y copie y pegue la dirección URL de cada imagen en un navegador web. Si no se muestran las imágenes, póngase en contacto con el administrador de TI o con el proveedor de terceros que proporcione el contenido de envío.

## Previsualice el mensaje {#preview-msg}

Adobe recomienda previsualizar el mensaje para comprobar su personalización y cómo verán su envío sus destinatarios.

* In the delivery wozard, the **[!UICONTROL Preview]** sub-tab lets you view the rendering of each content for a recipient. Los campos personalizados y los elementos condicionales del contenido se sustituyen por la información correspondiente del perfil seleccionado. [Más información](../../delivery/using/defining-the-email-content.md#message-content)

* Durante cada previsualización se realiza una comprobación automática del contenido no deseado. En la **[!UICONTROL Preview]** subficha, marque la puntuación de spam [SpamAssassin](../../delivery/using/spamassassin.md) .  Haga clic **[!UICONTROL More...]** para obtener más información sobre la advertencia.  Antes de hacerlo, asegúrese de que SpamAssassin está correctamente instalado y configurado en el servidor de aplicaciones de Adobe Campaign. [Más información](../../installation/using/configuring-spamassassin.md)
