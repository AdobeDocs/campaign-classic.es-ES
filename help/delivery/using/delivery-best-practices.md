---
title: Prácticas recomendadas del envío de Campaña
seo-title: Prácticas recomendadas relacionadas con las entregas
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
source-git-commit: f599bc5483779ae62dd4d5eb1936cbc2760639b5
workflow-type: tm+mt
source-wordcount: '4348'
ht-degree: 23%

---


# Prácticas recomendadas relacionadas con las entregas {#delivery-best-practices}

## Optimización del envío {#optimize-delivery}

Antes de empezar a crear envíos, puede realizar varias acciones para proteger y optimizar el proceso de envío de forma ascendente.

En la siguiente sección se describen las prácticas recomendadas y los procedimientos recomendados para una configuración óptima de Adobe Campaign. Si sigue estas prácticas, se minimizarán los problemas que podría tener que afrontar en la fase posterior.

### Rendimiento de la plataforma

Varios factores pueden afectar directamente al rendimiento del servidor y ralentizar la plataforma:

* Número y tipo de elementos de personalización: la personalización en correos electrónicos extrae datos de la base de datos para cada destinatario. Si hay muchos elementos de personalización, esto aumenta la cantidad de datos necesarios para preparar la entrega.  Más información sobre personalización en [esta sección](../../delivery/using/about-personalization.md)

* Carga del servidor: cuando el servidor de mercadotecnia gestiona muchas tareas diferentes al mismo tiempo, puede ralentizar el rendimiento. El servidor de mercadotecnia debe coordinar todos los datos entrantes y salientes de todos los envíos para garantizar que los datos sean correctos y estén a tiempo.

   **SUGERENCIA** : Para evitar esto, coordine la programación de envíos con los demás miembros de su equipo para garantizar el mejor rendimiento.

* Ejecución del flujo de trabajo: la supervisión de sus flujos de trabajo es esencial para evitar problemas de rendimiento de la plataforma. Siga las directrices enumeradas [en este documento](../../workflow/using/workflow-best-practices.md#execution-and-performance).

* Como cliente alojado, puede aprovechar las funciones [del panel de control de](https://docs.adobe.com/content/help/es-ES/control-panel/using/discover-control-panel/key-features.html) Campaña para supervisar su plataforma mediante funciones de supervisión [del](https://docs.adobe.com/content/help/en/control-panel/using/performance-monitoring/about-performance-monitoring.html) rendimiento.

### Comprobación de la configuración de red {#network-config}

Para optimizar el envío al administrar correos electrónicos en grandes volúmenes y evitar que se confunda con un spam, asegúrese de tener una configuración de red legítima que no intente ocultar la identidad del servidor.

**Sugerencia**:  Utilice una dirección de remitente transparente correspondiente al sitio web de la marca. Por ejemplo, la compañía TravelAgency gestiona la cadena hotelera Valentino. Dispone de su propio dominio valentino.com para su sitio web. Para promocionar el hotel Valentino en París, utiliza el subdominio paris.valentino.com. Por lo tanto, una dirección de remitente relevante puede ser hotel@paris.valentino.com.

### Administración de la capacidad de entrega {#deliverability-management}

Para llegar a la bandeja de entrada de sus destinatarios sin rebotar ni ser marcado como correo no deseado, debe mejorar la tasa de entrega de sus mensajes.

* ¿Qué es la capacidad de entrega?

   * Hace referencia a los factores de un mensaje de correo electrónico que determinan su capacidad para ser aceptado por el servidor de un destinatario. Los ISP (Proveedores de servicio de Internet) filtran los correos electrónicos que identifican como SPAM o bloquean la descarga de imágenes. Si determinan que un determinado dominio está enviando demasiados correos electrónicos, establecerán un límite en el número de correos electrónicos que aceptarán de ese remitente.

   * Al comprobar la tasa de envíos de sus correos electrónicos, debe centrarse en cuatro categorías principales: calidad de los datos, mensaje y contenido, infraestructuras de envío y reputación. Para profundizar en este tema, consulte [esta sección](../../delivery/using/about-deliverability.md).

* Aplicar las recomendaciones detalladas [en este documento](../../delivery/using/deliverability-key-points.md).

* Póngase en contacto con su representante de Adobe para obtener ayuda.

### Administración de Cuarentenas {#quarantine-management}

Le conviene mantener buenos procesos de gestión de cuarentenas.

Al comenzar a enviar correos electrónicos en una nueva plataforma, puede utilizar una lista de direcciones que no esté totalmente confirmada. Si realiza envíos a direcciones no válidas o a direcciones honeypot (bandejas de entrada creadas únicamente para engañar a remitentes de correo electrónico no deseado), la reputación de su plataforma comenzará a reducirse. Los buenos procesos de administración de cuarentenas ayudan a: mantenga la calidad de la dirección, evite la lista de bloqueados de los proveedores de acceso a Internet y reduzca la tasa de errores, acelerando los envíos y el rendimiento.

**Sugerencias**

* Si tiene una lista de direcciones no válidas, Adobe recomienda importarlas a la tabla de cuarentenas, a través de **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Non deliverables and addresses]**.

* Los destinatarios cuyas direcciones están en cuarentena se excluyen de forma predeterminada durante el análisis de envío: no están segmentados. Esto acelera las entregas, ya que la tasa de error afecta significativamente a la velocidad de entrega. Una dirección de correo electrónico se puede poner en cuarentena, por ejemplo, cuando el buzón está lleno o si la dirección no existe. [Más información](#identifying-quarantined-addresses-for-a-delivery)

* Adobe Campaign administra las direcciones erróneas según el tipo de error devuelto. Para obtener más información, consulte [esta sección](../../delivery/using/understanding-quarantine-management.md).


* Algunos proveedores de acceso a Internet consideran automáticamente los correos electrónicos como no deseados si la tasa de direcciones no válidas es demasiado alta. Por lo tanto, la Cuarentena le permite evitar ser agregado a una lista de bloqueados por estos proveedores.

* La administración de Cuarentenas también ayudará a reducir los costos de envío de SMS al excluir los números de teléfono erróneos de los envíos.

### Mecanismo de selección de Dobles {#double-opt-in}

Para evitar el envío de mensajes a direcciones no válidas, limitar las comunicaciones incorrectas y mejorar la reputación del remitente, Adobe recomienda implementar un mecanismo de selección de dobles para la confirmación posterior a la suscripción. Esto ayuda a garantizar la suscripción intencionada de un destinatario.

Los detalles para la implementación de este mecanismo se describen en [esta sección](../../web/using/use-cases--web-forms.md).

## Uso de plantillas {#use-templates}

Las Plantillas de envíos permiten una mayor eficiencia al proporcionar escenarios listos para usar para los tipos de actividades más comunes. Con las plantillas, los especialistas en marketing pueden implementar nuevas campañas con una personalización mínima en un período de tiempo más corto.

Obtenga más información sobre Plantillas de envíos en [esta sección](../../delivery/using/creating-a-delivery-template.md).

### Introducción a las Plantillas de envíos {#gs-templates}

Una [Plantilla de envíos](../../delivery/using/creating-a-delivery-template.md) le permite definir una vez un conjunto de propiedades técnicas y funcionales que se adapten a sus necesidades y que pueden reutilizarse para futuros envíos. A continuación, puede ahorrar tiempo y estandarizar envíos cuando sea necesario.

Cuando se gestionan varias marcas en Adobe Campaign, Adobe recomienda tener un subdominio por marca. Por ejemplo, un banco puede tener varios subdominios correspondientes a cada una de sus agencias regionales. Si un banco posee el dominio bluebank.com, sus subdominios pueden ser @ny.bluebank.com, @ma.bluebank.com, @ca.bluebank.com, etc. Tener una plantilla de envíos para cada subdominio le permite utilizar los parámetros preconfigurados adecuados para cada una de sus marcas, lo que evita errores y le ahorra tiempo.

**Sugerencia**:  Para evitar errores de configuración en Campaign Standard, se recomienda que duplicado una plantilla nativa y modifique sus propiedades en lugar de crear una nueva plantilla.

**Configuración de direcciones**

* La dirección del remitente es obligatoria para permitir el envío de un correo electrónico.

* Algunos ISP (Proveedores de servicio de Internet) comprueban la validez de la dirección del remitente antes de aceptar mensajes.

* Una dirección mal formada puede resultar en que el servidor receptor la rechace. Debe asegurarse de que se proporciona una dirección correcta.

* La dirección debe identificar explícitamente al remitente. El dominio debe ser propiedad del remitente y estar registrado en él.

* Adobe recomienda crear cuentas de correo electrónico que se correspondan con las direcciones especificadas para envíos y respuestas. Consulte con el administrador del sistema de mensajería.

Para configurar direcciones en la interfaz de Campaña, siga los pasos a continuación:

1. En la [Plantilla de envíos](../../delivery/using/creating-a-delivery-template.md), haga clic en el **[!UICONTROL From]** vínculo. En la **[!UICONTROL Email header parameters]** ventana, rellene los campos siguientes:

   ![](assets/d_best_practices_email_header.png)

1. En el **[!UICONTROL Sender address]** campo, asegúrese de que el dominio de dirección es el mismo que el subdominio que delegó en Adobe. Puede cambiar la parte que precede a &#39;@&#39; pero no la dirección de dominio.

1. En el **[!UICONTROL From]** campo, utilice un nombre fácilmente identificable por los destinatarios, como el nombre de su marca, para aumentar la velocidad de apertura de sus envíos. Para mejorar aún más la experiencia del destinatario, puede agregar el nombre de una persona, por ejemplo &quot;Emma de Megastore&quot;.

1. En los **[!UICONTROL Reply address text]** campos, la dirección del remitente se utiliza de forma predeterminada para las respuestas. Sin embargo, Adobe recomienda utilizar una dirección real existente, como el servicio de atención al cliente de su marca. En este caso, si un destinatario envía una respuesta, el servicio de atención al cliente podrá atenderla.

**Configuración de un grupo de control**

Una vez enviado el envío, puede comparar el comportamiento de los destinatarios excluidos con los destinatarios que sí recibieron el envío. Puede medir la eficacia de sus campañas. Obtenga más información sobre grupos de control en [esta sección](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

Para configurar un grupo de control, haga clic en el **[!UICONTROL To]** vínculo. En la **[!UICONTROL Select target]** ventana, seleccione la **[!UICONTROL Control group]** ficha. Puede extraer una parte del destinatario, por ejemplo, una muestra aleatoria del 5 %.

![](assets/d_best_practices_control_group.png)

**Usar tipologías para aplicar filtros o reglas de control**

Una tipología contiene reglas de comprobación que se aplican durante la fase de análisis antes de enviar un mensaje.

En la **[!UICONTROL Typology]** ficha de las propiedades de la plantilla, cambie la tipología predeterminada según sus necesidades.

Por ejemplo, para controlar mejor el tráfico saliente, puede definir qué direcciones IP se pueden utilizar definiendo una afinidad por subdominio y creando una tipología por afinidad. Las afinidades se definen en el archivo de configuración de la instancia. Póngase en contacto con el administrador de Adobe Campaign.

For more on typologies, refer to [this section](../../campaign/using/about-campaign-typologies.md).

## Diseño y personalización {#design-and-personalize}

Al diseñar el contenido del mensaje, trate de evitar problemas comunes que podrían impedir la ejecución del envío. La mayoría de las veces, los posibles errores están relacionados con la [personalización](../../delivery/using/about-personalization.md), el [formato](../../delivery/using/defining-the-email-content.md#message-content) y [las imágenes](../../delivery/using/defining-the-email-content.md#adding-images).

### Optimizar la personalización {#optimize-personalization}

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

### Creación de contenido optimizado {#optimize-content}

Cuando cree sus correos electrónicos, tenga en cuenta las optimizaciones generales que se describen a continuación.

* El correo electrónico debe tener un diseño sencillo

* Tenga en cuenta a los usuarios de dispositivos móviles

* Evite los correos electrónicos basados por completo en imágenes

* Utilice fuentes seguras para el correo electrónico

* Codifique caracteres especiales

**Línea** de asunto - Trabajar en la línea [de](../../delivery/using/defining-the-email-content.md#message-content) asunto para mejorar los precios abiertos:

* Evite los asuntos demasiado largos. Utilice un máximo de 50 caracteres

* Evite utilizar palabras de forma repetida, tales como “gratis” u “oferta”, que podrían considerarse como spam

* Evite mayúsculas y caracteres especiales como &quot;!&quot;, &quot;£&quot;, &quot;€&quot;, &quot;$&quot;

**Página espejo** : incluya siempre un vínculo de página espejo. La posición preferida es la parte superior del correo electrónico. [Más información](../../delivery/using/sending-messages.md#generating-the-mirror-page)

**Vínculo** Baja - El vínculo baja es esencial. Debe ser visible y válido, y el formulario debe ser funcional. By default, when the message is analyzed, a [typology rule](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies) checks whether an opt-out link has been included and generates a warning if it is missing.

**Sugerencia**: Debido a que siempre es posible cometer un error humano, compruebe que el vínculo de exclusión funciona correctamente antes de cada envío. Por ejemplo, al enviar la prueba, asegúrese de que el vínculo sea válido, que el formulario esté en línea y que el campo Ya no se ponga en contacto con este destinatario se cambie a Sí.

Obtenga información sobre cómo insertar un vínculo de exclusión [en esta sección](../../delivery/using/personalization-blocks.md#personalization-blocks-example).

**Tamaño** del correo electrónico: para evitar problemas de rendimiento o de entrega, el tamaño máximo recomendado de un correo electrónico es de unos **35 KB**. To check the message size, go the **[!UICONTROL Preview]** tab and choose a test profile. Una vez generado, el tamaño del mensaje se muestra en la esquina superior derecha.

Para mantener el correo electrónico por debajo del límite, haga lo siguiente:

* Eliminar estilos redundantes o no utilizados

* Mover parte del contenido del correo electrónico a una página de aterrizaje

* Minimizar el código

Asegúrese de probar los cambios antes del envío final

**Longitud de SMS**

De forma predeterminada, el número de caracteres de un SMS cumple con los estándares del GSM (Sistema Global de Comunicaciones Móviles). Los mensajes SMS con codificación GSM están limitados a 160 caracteres, o a 153 caracteres por SMS en el caso de los mensajes enviados en varias partes.

La transliteración consiste en reemplazar un carácter de un SMS por otro cuando el estándar GSM no tiene en cuenta dicho carácter. Tenga en cuenta que la inserción de campos de personalización en el contenido del mensaje SMS puede introducir caracteres que no se tienen en cuenta en la codificación GSM. Puede autorizar la transliteración de caracteres marcando la casilla correspondiente en la ficha Ajustes de canal de SMPP de la correspondiente **[!UICONTROL External account]**.
Learn more [in this section](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

**Sugerencias**:

* Para mantener todos los caracteres en tus mensajes SMS tal como están, para no alterar nombres adecuados por ejemplo, no habilites la transliteración.

* Sin embargo, si sus mensajes SMS contienen muchos caracteres que no se tienen en cuenta en el estándar GSM, habilite la transliteración para limitar los costos de envío de sus mensajes.

Learn more [in this section](../../delivery/using/sms-channel.md#about-character-transliteration).

### Mejore el formato {#formatting}

Para evitar errores comunes de formato, consulte los siguientes elementos:

* Formato de **fecha correcto**: Adobe Campaign proporciona funciones de formato de fecha para las plantillas JavaScript y las hojas de estilo XSL. [Más información](../../delivery/using/formatting.md#date-display)

* Uso de caracteres **** autorizados en correos electrónicos: la lista de caracteres válidos para las direcciones de correo electrónico se define en la opción &quot;XtkEmail_Characters&quot;. Obtenga información sobre cómo acceder a las opciones de Campaña [en esta sección](../../installation/using/configuring-campaign-options.md). Para gestionar correctamente caracteres especiales, Adobe Campaign debe estar instalado en Unicode.

* Configuración de la autenticación por **correo electrónico**: asegúrese de que los encabezados de correo electrónico contienen la firma DKIM. La autenticación DKIM (correo identificado con claves de dominio) permite al servidor de correo electrónico receptor verificar que el mensaje fue enviado por la persona o entidad por la que afirma que fue enviado y si el contenido del mensaje se alteró entre el momento en que se envió originalmente (y DKIM &quot;firmado&quot;) y la hora en que fue recibido. Este estándar suele utilizar el dominio en el encabezado De o Remitente. Para obtener más información, consulte [esta sección](../../delivery/using/technical-recommendations.md#dkim).

* **El diseño de correo electrónico adaptable garantiza que un correo electrónico se represente de forma óptima en el dispositivo en el que se abre.**

   * Utilice HTML de correo electrónico interactivo en lugar de HTML web.

   * Utilice el modo de vista previa y envíe pruebas para probar el diseño en tantos dispositivos como sea posible.

   * The Adobe Campaign Classic Digital Content Editor (DCE) module includes some responsive design formatted templates for mobile available via **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Content templates]**. Obtenga más información [en este artículo](https://theblog.adobe.com/responsive-email-design-101/).



### Administración de imágenes {#manage-images}

Siga las directrices que se indican a continuación cuando tenga que administrar imágenes.

* **Impedir el bloqueo** de imágenes: algunos clientes de correo electrónico bloquean imágenes de forma predeterminada y algunos usuarios cambian su configuración para bloquear imágenes y guardarlas al usar datos. Por lo tanto, si las imágenes no se descargan, se puede perder todo el mensaje. Para evitarlo:

   * Equilibre el contenido con la imagen y el texto. Evite los correos electrónicos basados por completo en imágenes.

   * Si se debe incluir texto en una imagen, use texto alternativo y de título para que el mensaje tenga el efecto deseado. Establezca el formato de texto alternativo o de título para mejorar el aspecto del diseño.

   * Evite el uso de imágenes de fondo, ya que algunos servicios de correo electrónico no las admiten.

* **Hacer que las imágenes sean interactivas** : intente que las imágenes sean interactivas y se puedan cambiar de tamaño. Tenga en cuenta que esto puede tener un impacto en los costes, ya que se tarda más en crear.

* **Usar referencias** de imagen absolutas: para ser accesible desde el exterior, las imágenes utilizadas en correos electrónicos y recursos públicos vinculados a campañas deben estar presentes en un servidor accesible desde el exterior.

   * Puede comprobar si la configuración de la instancia habilita la administración de recursos públicos. [Más información](../../installation/using/deploying-an-instance.md#managing-public-resources)

   * Desde el asistente de entregas, puede importar una página HTML que contenga imágenes o insertar imágenes directamente utilizando el editor HTML mediante el icono **[!UICONTROL Image]**. [Más información](../../delivery/using/defining-the-email-content.md#adding-images)

   * Si las imágenes no se muestran, compruebe que las imágenes están disponibles en el servidor. Para ello, haga clic en la ficha Origen del envío. Busque las imágenes y copie y pegue la dirección URL de cada imagen en un navegador web. Si no se muestran las imágenes, póngase en contacto con el administrador de TI o con el proveedor de terceros que proporcione el contenido de envío.

### Previsualice el mensaje {#preview-msg}

Adobe recomienda previsualizar el mensaje para comprobar su personalización y cómo verán su envío sus destinatarios.

* In the delivery wozard, the **[!UICONTROL Preview]** sub-tab lets you view the rendering of each content for a recipient. Los campos personalizados y los elementos condicionales del contenido se sustituyen por la información correspondiente del perfil seleccionado. [Más información](../../delivery/using/defining-the-email-content.md#message-content)

* Durante cada previsualización se realiza una comprobación automática del contenido no deseado. En la **[!UICONTROL Preview]** subficha, marque la puntuación de spam [SpamAssassin](../../delivery/using/spamassassin.md) .  Haga clic **[!UICONTROL More...]** para obtener más información sobre la advertencia.  Antes de hacerlo, asegúrese de que SpamAssassin está correctamente instalado y configurado en el servidor de aplicaciones de Adobe Campaign. [Más información](../../installation/using/configuring-spamassassin.md)

## Definir los destinatarios adecuados {#define-the-right-target}

La población objetivo es clave: cree sus listas con cuidado, pruebe sus correos electrónicos en clientes de correo electrónico y dispositivos móviles populares y asegúrese de que sus listas de correo electrónico estén actualizadas (sin direcciones desconocidas u obsoletas). También puede enviar pruebas que ayuden a configurar un ciclo de validación completo.

Más información sobre las poblaciones de destinatarios [en esta sección](../../delivery/using/steps-defining-the-target-population.md)

### Destinatario de la audiencia correcta {#target-the-right-audience}

Cuando tenga preparado el contenido, debe definir cuidadosamente quién recibirá el mensaje.

Para que su envío tenga éxito, desea enviar el contenido personalizado más relevante a los destinatarios adecuados. Adobe Campaign le permite crear el destinatario más preciso: puede seleccionar destinatarios según su edad, localización, lo que compraron, si hicieron clic en un vínculo en un envío anterior, etc. Con Adobe Campaign, también puede definir perfiles, grupos de control y direcciones semilla de prueba para asegurarse de que el destinatario es correcto.

### Asignaciones de destino {#target-mappings}

En Campaign Classic, de forma predeterminada, Plantilla de envíos **Destinatarios** de destinatario. Adobe Campaign oferta otras asignaciones de destino para sus envíos, que puede cambiar según sus necesidades.

Por ejemplo, puede entregar a visitantes cuyos perfiles se hayan recopilado a través de las redes sociales o a visitantes suscritos a un servicio informativo.

Estas asignaciones se presentan [en esta sección](../../delivery/using/selecting-a-target-mapping.md).

También puede crear y utilizar una asignación de destino personalizada. Para obtener más información, consulte [esta sección](../../configuration/using/target-mapping.md).

### destinatarios externos {#external-recipients}

Puede enviar a destinatarios que estén almacenados en un archivo externo en lugar de guardarlos en la base de datos. Learn more [in this section](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

### Enviar a sus suscriptores {#send-to-subscribers}

Para enviar mensajes a los suscriptores de una newsletter, puede enviar directamente el destinatario de los suscriptores al servicio informativo correspondiente. Learn more [in this section](../../delivery/using/managing-subscriptions.md#delivering-to-the-subscribers-of-a-service).


### destinatarios y direcciones semilla de prueba {#test-recipients-seed-addresses}

Para probar el envío, utilice pruebas antes de enviar al destinatario principal.

Asegúrese de seleccionar los destinatarios de prueba adecuados, ya que validan el formulario y el contenido del mensaje. Los pasos para definir los destinatarios de prueba se presentan [en esta sección](../../delivery/using/steps-defining-the-target-population.md#selecting-the-proof-target).

Las Direcciones semilla se utilizan para destinatario de destinatarios que no coinciden con los criterios de destinatario definidos para probar un envío antes de enviarlo al destinatario principal. They are presented [in this section](../../delivery/using/about-seed-addresses.md).

### Desduplicar direcciones {#deduplicate-addresses}

Es importante evitar tener direcciones de correo electrónico de duplicado, ya que esto puede tener un impacto en el destinatario:

* El mismo mensaje se puede enviar más de una vez cuando se divide un destinatario.

* Si un destinatario deja de suscribirse después de recibir un mensaje, su perfil de duplicado seguirá recibiendo mensajes futuros.

La desduplicación de direcciones protege su reputación de envío y garantiza una buena administración de cuarentenas.

Obtenga más información [en este caso](../../workflow/using/deduplication.md#example--identify-the-duplicates-before-a-delivery)de uso.


### Indizar direcciones de correo electrónico {#index-addresses}

Para optimizar el rendimiento de las consultas SQL utilizadas en la aplicación, se puede declarar un índice a partir del elemento principal del esquema de datos.

Los pasos para agregar un índice a la dirección de correo electrónico se presentan [en esta sección](../../configuration/using/database-mapping.md#indexed-fields).

## Realizar todas las comprobaciones antes de enviar {#perform-all-checks}

Cuando el mensaje esté listo, asegúrese de que su contenido se muestra correctamente en todos los dispositivos y no contiene ningún error, como por ejemplo de personalización incorrecta o enlaces rotos.

Antes de enviar el mensaje, compruebe que los parámetros y la configuración se adecuan al envío.

### La validación es clave {#validation-is-key}

Antes de enviar un envío, debe asegurarse de que sus destinatarios recibirán el mensaje que realmente desea enviarlos. Para ello, debe validar el contenido del mensaje y los parámetros de envío.

Este paso le permite detectar posibles errores y corregirlos antes de enviarlos a su destinatario principal.

Los pasos para validar un envío se presentan [en esta sección](../../delivery/using/steps-validating-the-delivery.md).

### Renderización de la bandeja de entrada {#inbox-and-email-rendering}

El procesamiento de la bandeja de entrada le permite realizar previsualizaciones de sus mensajes en los principales clientes de correo electrónico, analizar el contenido y la reputación, descubrir cómo los destinatarios leen los mensajes.

**Sugerencias**:

* Puede vista del mensaje enviado en los diferentes contextos en los que se puede recibir: webmail, servicio de mensajes, móvil, etc.

* Las funciones de procesamiento de la bandeja de entrada son cruciales para identificar si las campañas de correo electrónico superan con éxito los filtros de los principales ISP (Proveedores de servicio de Internet) y servicios de correo web. Estas herramientas envían una copia de un mensaje de correo electrónico a una red de bandejas de entrada de prueba, lo que le permite ver cómo se muestra el mensaje o cómo se renderiza en estos servicios. También pueden incluir informes y opciones de corrección de código que le ayudan a identificar y realizar correcciones con rapidez para mejorar la capacidad de envío.

Learn more [in this section](../../delivery/using/inbox-rendering.md).

### Mensajes de Prueba {#proof-messages}

El envío de pruebas le permite comprobar el vínculo de exclusión, la página espejo y cualquier otro vínculo, validar el mensaje, comprobar que se muestran las imágenes, detectar posibles errores, etc. También es posible que desee comprobar el diseño y el procesamiento en distintos dispositivos.

Learn more [in this section](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Configuración de envíos de prueba A/B {#a-b-testing-deliveries}

Si tiene varios contenidos para un envío de correo electrónico, puede utilizar la prueba A/B para averiguar qué versión tendrá el mayor impacto en la población objetivo.

**Sugerencias**:

* Envíe las diferentes versiones a algunos de sus destinatarios

* Seleccione el que tenga la tasa de éxito más alta y envíelo al resto del destinatario

Learn more [in this section](../../workflow/using/a-b-testing.md).

### Asegúrese de que el mensaje se haya enviado {#make-sure-your-message-is-delivered}

Finalmente, maximice sus posibilidades y aproveche la potencia de Adobe Campaign Classic para garantizar que su mensaje se envía a los destinatarios relevantes.

**Realizar un proceso** de validación: puede definir un proceso de validación completo, en el que participen los operadores y grupos de Adobe Campaign, para validar tanto el destinatario como el contenido del mensaje. Esto garantizará la supervisión y el control plenos de los diversos procesos de la campaña: segmentación, contenido, presupuesto, extracción y envío de una prueba. Según sus permisos, los usuarios pueden recibir notificaciones, recibir pruebas y validar o rechazar el mensaje. Learn more [in this section](../../campaign/using/marketing-campaign-approval.md#approval-process).

**Usar olas** : puede aumentar progresivamente el volumen enviado mediante olas. Esto evitará que sus mensajes se marquen como correo no deseado o cuando desee restringir el número de mensajes por día. Mediante las oleadas puede dividir los envíos en varios lotes en lugar de enviar volúmenes altos de mensajes al mismo tiempo. Learn more [in this section](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).

**Priorizar mensajes** : puede establecer el orden de envío de sus envíos indicando el nivel de prioridad. Para ello:

1. Edite las propiedades del envío y seleccione la **[!UICONTROL Delivery]** ficha.

1. Defina el nivel de prioridad del envío en una escala de **[!UICONTROL Very low]** a **[!UICONTROL Very high]**.

>[!NOTE]
>
>No es posible definir el orden de envío de mensajes desde un envío.

**Configurar Afinidades** IP: para controlar mejor el tráfico SMTP saliente, puede administrar afinidades definiendo las direcciones IP específicas que se pueden usar para cada afinidad. Esto permite limitar el número de correos electrónicos para envíos específicos hacia equipos o direcciones de salida. Por ejemplo, puede utilizar una afinidad por país o subdominio. A continuación, puede crear una tipología por país y vincular cada afinidad a la tipología correspondiente.

Se puede:

* Defina las afinidades IP en el archivo de configuración serverConf.xml. [Más información](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* Para cada elemento IPAffinity, declare las direcciones IP que se pueden usar. [Más información](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* En la [tipología](../../campaign/using/about-campaign-typologies.md) que elija, utilice el **[!UICONTROL Managing affinities with IP addresses]** campo para vincular envíos al servidor de envío (MTA) que administra dicha afinidad. [Más información](../../campaign/using/applying-rules.md#control-outgoing-smtp-traffic).

* Una vez enviado el correo electrónico, compruebe el encabezado para comprobar de qué dirección IP se envió el envío. El administrador de correo electrónico debe ayudarle a obtener la información del encabezado.

>[!NOTE]
>
>La mayoría de estos pasos sólo los puede realizar un usuario experto.

**Usar tipologías** : puede utilizar reglas de tipología para excluir parte del destinatario según criterios específicos. Esto garantiza que los mensajes enviados respondan de la mejor forma a las necesidades y expectativas de los clientes, de acuerdo con las políticas de comunicación de la compañía. Por ejemplo, puede filtrar los destinatarios menores de edad del objetivo de su boletín informativo. Obtenga más información [en este ejemplo](../../campaign/using/filtering-rules.md).

**Evitar los archivos adjuntos** : los archivos adjuntos siguen siendo uno de los vectores más comunes para la proliferación de malware, especialmente cuando se envían de forma masiva. Incluya un enlace seguro al documento en lugar de adjuntar el propio documento. Esto garantiza un nivel adicional de seguridad para evitar una redistribución no deseada y reduce considerablemente las posibilidades de que el mensaje se rechace en las puertas de enlace de correo electrónico entrantes por motivos de seguridad o tamaño del mensaje.

## Seguimiento y monitorización {#track-and-monitor}

¿Ha hecho clic en el botón Enviar? Veamos qué pasa. Una vez enviado el envío, Adobe Campaign le permite realizar un seguimiento de los mensajes enviados y descubrir cómo reaccionan sus destinatarios al envío. Esto le ayudará a mejorar el envío futuro y a optimizar sus próximas campañas.

### Seguimiento de entregas {#monitoring-deliveries}

Para controlar sus campañas, debe asegurarse de que el mensaje se ha enviado a sus destinatarios.

Desde el panel de envío de Campaña, puede comprobar los mensajes procesados y los registros de auditoría de envío.
También puede controlar el estado de los mensajes en los registros de envío. [Más información](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard).

¿Qué sucede si no se envían los envíos y su estado sigue siendo **Pendiente**?

* El proceso de ejecución está esperando la disponibilidad de algunos recursos. Es posible que el MTA no se haya iniciado.
Compruebe que los módulos mta@instance se inician en los servidores MTA y, si es necesario, inicio el módulo MTA. [Más información](../../production/using/administration.md).

* El envío puede estar utilizando una afinidad que no se ha configurado en la instancia de envío.
Sugerencia: Compruebe la configuración de la administración del tráfico (afinidad IP). Para obtener más información sobre esto, consulte Control del tráfico SMTP saliente.

>[!NOTE]
>
>Estos pasos sólo los puede realizar un usuario experto.

### Seguimiento {#tracking-deliveries}

Para conocer mejor el comportamiento de sus destinatarios, puede rastrear cómo reaccionan a un envío: recepción, apertura, clics en enlaces, suscripciones, etc. En Campaign Classic, esta información se muestra en la ficha Seguimiento de los destinatarios dirigidos por el envío y en la ficha Seguimiento del envío. En Campaign Standard, se muestra en la ficha Registros de seguimiento del envío.

**Sugerencia**: El seguimiento de mensajes está habilitado de forma predeterminada. Para configurar direcciones URL, seleccione la opción Mostrar direcciones URL en la sección inferior del asistente de envíos. Para cada dirección URL del mensaje, puede elegir si desea activar el seguimiento.

Para obtener más información sobre esto, consulte la sección [Configuración del seguimiento](../../delivery/using/how-to-configure-tracked-links.md) y la descripción de los indicadores [de](../../reporting/using/delivery-reports.md#tracking-indicators) seguimiento.

### Rendimiento de envíos {#delivery-performances}

Para medir la velocidad a la que se entregan los mensajes, puede controlar el rendimiento del envío. Los criterios son el número de mensajes enviados por hora y el tamaño de los mensajes (en bits por segundo). Para obtener más información sobre esto, consulte Rendimiento [de Envío](../../reporting/using/global-reports.md#delivery-throughput).

**Sugerencias**:

* Evite mantener las entregas en estado de error en la instancia, ya que esto mantiene tablas temporales e influye en el rendimiento.

* Elimine los envíos que ya no sean necesarios y los destinatarios inactivos de la base de datos para mantener la calidad de la dirección.

* Evite programar entregas grandes al mismo tiempo. Tenga en cuenta que la carga puede tardar entre 5 y 10 minutos en propagarse uniformemente sobre el sistema.

## Solución de problemas de Envío {#delivery-troubleshooting}

Se pueden realizar acciones específicas al encontrar problemas con envíos:

* [Problemas de capacidad de entrega](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [Problemas de visualización de imágenes](../../production/using/image-display-issues.md)

* [Problemas de rendimiento de Envío](../../delivery/using/monitoring-a-delivery.md#performance_issues)

* [Problemas](../../production/using/temporary-files.md) de archivos temporales: sólo clientes *in situ*
