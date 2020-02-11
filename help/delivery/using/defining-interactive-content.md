---
title: Definición de contenido interactivo en Adobe Campaign Classic
description: Aprenda a definir contenido de correo electrónico dinámico e interactivo con AMP en Adobe Campaign Classic.
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
translation-type: tm+mt
source-git-commit: 1815f9fc6063ec86d6c12ef492396e5afb82b3e1

---


# Definición de contenido interactivo{#defining-interactive-content}

Adobe Campaign le permite probar el nuevo formato [AMP interactivo para correo electrónico](https://amp.dev/about/email/) , que permite enviar correos electrónicos dinámicos, bajo ciertas condiciones.

>[!IMPORTANT]
>
>* Esta función es una función beta de Adobe Campaign.
>* AMP para correo electrónico es un nuevo formato de código abierto que permite a los desarrolladores crear correos electrónicos dinámicos e interactivos. Actualmente, cuenta con el apoyo de algunos proveedores de correo electrónico: Gmail, Outlook y Mail.ru.


Actualmente solo puede:
* Pruebe a enviar correos electrónicos AMP a direcciones específicas correctamente configuradas.
* Envíe correos electrónicos AMP a las direcciones de Gmail, Outlook o Mail.ru después de registrarse con los proveedores correspondientes.

Para obtener más información sobre la prueba y el envío de correos electrónicos AMP, consulte [Establecimiento de objetivos para un correo electrónico](#targeting-amp-email)AMP.

Esta función está disponible a través de un paquete dedicado en Adobe Campaign. Para utilizarlo, este paquete debe estar instalado. Una vez finalizado, reinicie el servidor para que el paquete se tenga en cuenta.

Para las arquitecturas híbridas y alojadas, el paquete debe instalarse en todos los servidores, incluidos el servidor [de](../../installation/using/mid-sourcing-server.md) abastecimiento intermedio y la instancia [de](../../message-center/using/creating-a-shared-connection.md#execution-instance)ejecución. Póngase en contacto con el ejecutivo de cuentas.

Vea este [vídeo](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/sending-messages/email-channel/defining-interactive-email-content-with-amp.html) para ver cómo activar AMP en Adobe Campaign y obtener más información sobre el uso.

## Acerca de AMP para correo electrónico {#about-amp-for-email}

El nuevo formato de **AMP para correo electrónico** permite incluir componentes de AMP dentro de los mensajes para mejorar la experiencia de correo electrónico con contenido enriquecido y procesable. Con la funcionalidad moderna de la aplicación disponible directamente en los correos electrónicos, los destinatarios pueden interactuar dinámicamente con el contenido del mensaje.

Por ejemplo:
* Los correos electrónicos escritos con AMP pueden contener elementos interactivos como carruseles de imágenes.
* El contenido permanece actualizado en el mensaje.
* Los destinatarios pueden realizar acciones como responder a un formulario sin salir de su bandeja de entrada.

AMP para correo electrónico es compatible con los correos electrónicos existentes. La versión AMP del mensaje se incrusta en el correo electrónico como una nueva parte MIME, además del HTML y/o el texto sin formato, lo que garantiza la compatibilidad entre todos los clientes de correo electrónico.

Para obtener más información sobre la AMP para los requisitos, especificaciones y formato de correo electrónico, consulte la documentación [para desarrolladores de](https://amp.dev/documentation/guides-and-tutorials/learn/email-spec/amp-email-format/?format=email)AMP.

## Pasos clave para utilizar AMP para correo electrónico con Adobe Campaign {#key-steps-to-use-amp}

Para probar y enviar correctamente un correo electrónico de AMP con Adobe Campaign, siga los pasos a continuación:
1. Instale el **[!UICONTROL AMP support (Beta)]** paquete. Consulte [Instalación de paquetes](../../installation/using/installing-campaign-standard-packages.md)estándar de Campaign.
1. Cree un correo electrónico y cree su contenido de AMP en Adobe Campaign. Consulte [Creación de contenido de correo electrónico de AMP con Adobe Campaign](#build-amp-email-content).
1. Asegúrese de seguir todos los requisitos de entrega de los proveedores de correo electrónico que admiten el formato AMP. Consulte [AMP para conocer los requisitos](#amp-for-email-delivery-requirements)de envío por correo electrónico.

   >[!NOTE]
   >
   >AMP para correo electrónico está disponible como una capacidad beta para fines de prueba. Actualmente, sólo unos pocos proveedores de correo electrónico admiten la prueba de este formato.

1. Al definir el objetivo, asegúrese de seleccionar los destinatarios que podrán mostrar el formato AMP. Consulte [Targeting an AMP email](#targeting-amp-email).

   >[!NOTE]
   >
   >Actualmente solo puede probar la entrega de correos electrónicos AMP a direcciones de correo electrónico específicas correctamente configuradas o después del registro con los proveedores de correo electrónico que participan en el programa beta AMP.

1. Envíe su correo electrónico como lo haría normalmente. Consulte [Envío de un correo electrónico](#sending-amp-email)de AMP.

## Creación de contenido de correo electrónico AMP en Adobe Campaign {#build-amp-email-content}

Para generar un correo electrónico con el formato AMP, siga los pasos a continuación.

>[!IMPORTANT]
>
>Asegúrese de seguir las especificaciones y los requisitos de correo electrónico de AMP detallados en la documentación [para desarrolladores de](https://amp.dev/documentation/guides-and-tutorials/learn/email_fundamentals/?format=email)AMP. También puede consultar la [AMP para conocer las optimizaciones](https://amp.dev/documentation/guides-and-tutorials/develop/amp_email_best_practices/?format=email)de correo electrónico.

1. Al crear la entrega por correo electrónico, seleccione cualquier plantilla.

   >[!NOTE]
   >
   >Una plantilla de AMP específica contiene un ejemplo de las capacidades principales que puede utilizar: lista de productos, carrusel, doble inclusión, encuesta y solicitud de servidor avanzada.

1.  Haga clic en la **[!UICONTROL AMP content]** ficha.

   ![](assets/amp_tab.png)

1. Edite el contenido de AMP para adaptarlo a sus necesidades.

   >[!NOTE]
   >
   >Para obtener más información sobre la creación del primer correo electrónico de AMP, consulte la documentación [para desarrolladores de](https://amp.dev/documentation/guides-and-tutorials/start/create_email/?format=email)AMP.

   Por ejemplo, puede utilizar el componente de lista de productos de la plantilla de AMP y mantener una lista de productos de un sistema de terceros, o incluso dentro de Adobe Campaign. Siempre que se ajuste un precio u otro elemento, se reflejará automáticamente cuando el destinatario vuelva a abrir el correo electrónico desde su buzón.

1. Personalice el contenido de AMP según sea necesario, como lo haría normalmente con el formato HTML en Adobe Campaign, con campos de personalización y bloques de personalización.

   ![](assets/amp_tab_perso.png)

1. Una vez finalizado el proceso de edición, seleccione todo el contenido de AMP y cópielo en el validador [web de](https://validator.ampproject.org) AMP o en un sitio web similar.

   >[!NOTE]
   >
   >Asegúrese de seleccionar **AMP4 EMAIL** en la lista desplegable de la parte superior de la pantalla.

   ![](assets/amp_validator.png)

   Los errores se marcarán en línea.

   >[!NOTE]
   >
   >El editor AMP de Adobe Campaign no está diseñado para la validación de contenido. Utilice un sitio web externo como el validador [basado en web de](https://validator.ampproject.org) AMP para comprobar si el contenido es correcto.

1. Realice las modificaciones necesarias hasta que el contenido de la AMP pase la validación.

   ![](assets/amp_validator_pass.png)

1. Copie y pegue el contenido validado en [AMP Playground](https://playground.amp.dev) o un sitio web similar para obtener una vista previa del contenido.

   >[!NOTE]
   >
   >Asegúrese de seleccionar **AMP para correo electrónico** en la lista desplegable de la parte superior de la pantalla.

   ![](assets/amp_playground.png)

   >[!NOTE]
   >
   >No puede obtener una vista previa del contenido de AMP directamente en Adobe Campaign. Utilice un sitio web externo como, por ejemplo, [AMP Playground](https://playground.amp.dev).

1. Vuelva a Adobe Campaign y copie y pegue el contenido validado en la **[!UICONTROL AMP content]** ficha.

1. Cambie a la ficha **[!UICONTROL HTML content]** o **[!UICONTROL Text content]** y defina el contenido para al menos uno de estos dos formatos.

   >[!IMPORTANT]
   >
   >Si el correo electrónico no contiene una versión HTML o de texto sin formato además del contenido de AMP, no se puede enviar.

## AMP para los requisitos de envío por correo electrónico {#amp-for-email-delivery-requirements}

Al crear el contenido de AMP en Adobe Campaign, debe cumplir las condiciones para que se envíe un correo electrónico dinámico, que son específicas de los proveedores de correo electrónico de los destinatarios.

Actualmente, tres proveedores de correo electrónico admiten la prueba de este formato: Gmail, Outlook y Mail.ru.

Todos los pasos y especificaciones requeridos para probar la entrega con formato AMP en cuentas de Gmail se detallan en las correspondientes documentaciones de desarrollador de [Gmail](https://developers.google.com/gmail/ampemail?), [Outlook ](https://docs.microsoft.com/en-gb/outlook/amphtml/) y [Mail.ru](https://postmaster.mail.ru/amp) .

En particular, deben cumplirse los siguientes requisitos:
* Siga los requisitos de seguridad de AMP específicos de [Gmail](https://developers.google.com/gmail/ampemail/security-requirements), [Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/security-requirements) y [Mail.ru](https://postmaster.mail.ru/amp/?lang=en#howto).
* La parte MIME de AMP debe contener un documento [AMP](https://amp.dev/documentation/guides-and-tutorials/learn/validation-workflow/validate_emails/?format=email)válido.
* La parte MIME de AMP debe ser inferior a 100 KB.

También puede consultar las [Sugerencias y las limitaciones conocidas de Gmail](https://developers.google.com/gmail/ampemail/tips) y las prácticas recomendadas de [AMP para Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/best-practices).

## Dirección de correo electrónico de AMP {#targeting-amp-email}

AMP para correo electrónico, disponible como capacidad beta, actualmente puede experimentar enviando un correo electrónico AMP en dos pasos:

1. Adobe Campaign le permite probar la entrega de un correo electrónico dinámico con tecnología AMP a las direcciones de correo electrónico seleccionadas correctamente configuradas, a fin de verificar su contenido y comportamiento. Consulte [Prueba de envío de correo electrónico AMP para las direcciones](#testing-amp-delivery-for-selected-addresses)seleccionadas.
1. Una vez probada, puede enviar una entrega o una campaña como parte del programa de AMP para la versión beta por correo electrónico registrándose con los proveedores de correo electrónico relevantes para que se incluya en la lista de dominios de remitente. Consulte [Envío de correos electrónicos AMP mediante registro en un proveedor](#delivering-amp-emails-by-registering)de correo electrónico.

### Comprobación del envío de correo electrónico AMP para direcciones seleccionadas {#testing-amp-delivery-for-selected-addresses}

Puede probar el envío de mensajes dinámicos desde Adobe Campaign a las direcciones de correo electrónico seleccionadas.

>[!NOTE]
>
>Actualmente, solo Gmail, Outlook y Mail.ru admiten la prueba del formato AMP.

Para Gmail y Outlook, primero debe incluir en la lista de direcciones permitidas las direcciones de remitente que está utilizando para enviar desde Adobe Campaign las cuentas de Gmail y Outlook que tiene como objetivo.

Para ello:
1. Asegúrese de que la opción que habilita el correo electrónico dinámico está marcada para los proveedores de correo electrónico relevantes.
1. Copie la dirección del remitente que se muestra en el campo del envío **[!UICONTROL From]** y péguela en la sección correspondiente de la configuración de la cuenta del proveedor de correo electrónico.

Para obtener más información, consulte las documentación para desarrolladores de [Gmail](https://developers.google.com/gmail/ampemail/testing-dynamic-email) y [Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/register-outlook#individual-mailbox-registration) .

![](assets/amp_from_field.png)

Para probar el envío de un correo electrónico AMP a una dirección Mail.ru, siga los pasos de la documentación [del desarrollador de](https://postmaster.mail.ru/amp/?lang=en#howto) Mail.ru (**si es un usuario** ).

### Envío de correos electrónicos AMP mediante registro con un proveedor de correo electrónico {#delivering-amp-emails-by-registering}

Puede experimentar enviando correos electrónicos dinámicos registrándose con los proveedores de correo electrónico que participan en el programa beta de AMP para que su dominio remitente quede en la lista blanca.

>[!NOTE]
>
>Actualmente solo Gmail, Outlook y Mail.ru admiten el formato AMP.

Una vez probadas con algunas direcciones, puede enviar correos electrónicos AMP a cualquier dirección de Gmail o Outlook. Para hacerlo, debe registrarse respetuosamente con Google o Microsoft y esperar su respuesta. Siga los pasos que se describen en la documentación para desarrolladores de [Gmail](https://developers.google.com/gmail/ampemail/register) y [Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/register-outlook#global-registration) . Después de registrarse correctamente, se convierte en un remitente autorizado.

Para enviar correos electrónicos AMP a direcciones de Mail.ru, siga los requisitos y pasos que se enumeran en la documentación [del desarrollador de](https://postmaster.mail.ru/amp/?lang=en#howto) Mail.ru (**si es un remitente** de correo electrónico).

## Envío de un correo electrónico de AMP {#sending-amp-email}

Una vez que el contenido de AMP y la reserva están listos, y una vez definido un objetivo compatible, puede enviar el correo electrónico como lo haría normalmente.

Actualmente solo Gmail, Outlook y Mail.ru admiten el formato AMP, bajo ciertas condiciones. Puede dirigirse a direcciones de otros proveedores de correo electrónico, pero recibirán la versión HTML o de texto sin formato de su correo electrónico.

>[!IMPORTANT]
>
>Si el correo electrónico no contiene una versión HTML o de texto sin formato además del contenido de AMP, no se puede enviar.

Los destinatarios coincidentes tendrán la versión AMP del correo electrónico en su buzón.

Por ejemplo, si ha incluido una lista de productos en el correo electrónico, al editar los precios en un sistema de terceros, los precios se ajustarán automáticamente cada vez que los destinatarios vuelvan a abrir el correo electrónico en su buzón.

>[!NOTE]
>
>Puede crear una regla de procesamiento de correo para evitar que dominios específicos reciban correos electrónicos AMP. Consulte [Administración de formatos](../../installation/using/email-deliverability.md#managing-email-formats)de correo electrónico.
>
>De forma predeterminada, la **[!UICONTROL AMP inclusion]** opción está definida como **[!UICONTROL No]**.
