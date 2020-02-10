---
title: Envío de un correo electrónico con Adobe Campaign Classic
description: Obtenga información sobre los parámetros específicos para enviar correos electrónicos en Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 791f7a54-3225-46ca-ad6f-6c32e9c62d75
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-emails
discoiquuid: e2dd8161-fe38-48bf-a288-8ec328b2660e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7c800c20fff89b97f6fa38b3c659ca765765e157

---


# Envío de un correo electrónico{#sending-an-email}

To approve your email and send it to the recipients of the delivery being created, click **[!UICONTROL Send]**.

El proceso detallado para validar y realizar un envío se presenta en las siguientes secciones:

* [Validación del envío](../../delivery/using/steps-validating-the-delivery.md)
* [Realización del envío](../../delivery/using/steps-sending-the-delivery.md)

Las secciones siguientes detallan los parámetros específicos para enviar correos electrónicos.

## Archivado de correos electrónicos {#archiving-emails}

Adobe Campaign permite almacenar correos electrónicos en un sistema externo a través de CCO añadiendo simplemente una dirección de correo electrónico CCO al destino del mensaje. Una vez activada la opción, se conserva una copia exacta de todos los mensajes enviados en este envío.

Para obtener más información sobre la configuración de la CCO, consulte [esta sección](../../installation/using/email-archiving.md).

>[!NOTE]
>
>Esta función es opcional. Compruebe el acuerdo de licencia y póngase en contacto con el administrador de cuentas para activarlo.

Al crear un nuevo envío o plantilla de envío, el correo electrónico CCO no está activado de forma predeterminada, incluso si se ha adquirido la opción. Debe activarlo manualmente en cada envío o plantilla donde desee usarlo.

Para realizar esto, siga los pasos a continuación:

1. Vaya a **[!UICONTROL Campaign Management]** > **[!UICONTROL Deliveries]** o **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]**.
1. Seleccione el envío que desee o duplique la plantilla de **envío de correo electrónico** preestablecida y, a continuación, seleccione la plantilla duplicada.
1. Haga clic en el botón **Propiedades**.
1. Select the **[!UICONTROL Delivery]** tab.
1. Marque la casilla **Archivar correos electrónicos** para mantener una copia de todos los mensajes enviados para este envío o para cada envío basado en esta plantilla.

   ![](assets/s_ncs_user_wizard_archiving.png)

   >[!NOTE]
   >
   >If the emails sent to the BCC address are opened and clicked through, this will be taken into account in the **[!UICONTROL Total opens]** and **[!UICONTROL Clicks]** from the send analysis, which could cause some miscalculations.

## Generación de la página espejo {#generating-the-mirror-page}

La página espejo es una página HTML accesible en línea mediante un navegador web. Su contenido es idéntico al del correo electrónico.

De forma predeterminada, la página espejo se genera si el enlace se inserta en el contenido del correo. For more on personalization blocks insertion, refer to [Personalization blocks](../../delivery/using/personalization-blocks.md).

In the delivery properties, the **[!UICONTROL Mode]** field of the **[!UICONTROL Validity]** tab lets you modify the generation mode for this page.

![](assets/s_ncs_user_wizard_miror_page_mode.png)

>[!CAUTION]
>
>Se debe definir un contenido HTML para el envío de la página espejo que se va a crear.

Además del modo predeterminado, también están disponibles las siguientes opciones:

* **[!UICONTROL Force the generation of the mirror page]** :: aunque no se inserte ningún vínculo a la página de reflejo en el envío, se creará la página de reflejo.
* **[!UICONTROL Do not generate the mirror page]** :: no se genera ninguna página reflejada, incluso si el vínculo está presente en la entrega.
* **[!UICONTROL Generates a mirror page accessible using only the message identifier]** :: esta opción le permite acceder al contenido de la página reflejada, con información de personalización, en la ventana del registro de entrega. To do this, after the end of the delivery, click the **[!UICONTROL Delivery]** tab and select the line of the recipient whose mirror page you wish to view. Haga clic en el **[!UICONTROL Display the mirror page for this message...]** vínculo.

   ![](assets/s_ncs_user_wizard_miror_page_link.png)

## Gestión de correos electrónicos rechazados {#managing-bounce-emails}

The **[!UICONTROL SMTP]** tab of the delivery parameters lets you configure the management of bounce mails.

![](assets/s_ncs_user_email_del_properties_smtp_tab.png)

De forma predeterminada, los correos electrónicos rechazados se reciben en el cuadro de error predeterminado de la plataforma, pero se puede definir una dirección de error específica para un envío.

Desde esta pantalla, también puede definir una dirección específica para investigar los motivos de rechazo de los correos electrónicos cuando la aplicación no pueda calificarlos automáticamente. Para cada uno de estos campos, el icono “Añadir campos personalizados” permite añadir parámetros de personalización.

## Codificación de caracteres {#character-encoding}

En la **[!UICONTROL SMTP]** ficha de los parámetros de envío, la **[!UICONTROL Character encoding]** sección le permite establecer una codificación específica.

La codificación predeterminada es UTF-8. Si algunos de los proveedores de correo electrónico de los destinatarios no admiten la codificación estándar UTF-8, es posible que desee configurar una codificación específica para que muestre correctamente los caracteres especiales a los destinatarios de los mensajes de correo electrónico.

Por ejemplo, desea enviar un correo electrónico que contenga caracteres japoneses. Para asegurarse de que todos los caracteres se mostrarán correctamente a los destinatarios en Japón, es posible que desee utilizar una codificación que admita los caracteres japoneses en lugar de la codificación UTF-8 estándar.

Para ello, seleccione la **[!UICONTROL Force the encoding used for messages]** opción en la **[!UICONTROL Character encoding]** sección y elija una codificación en la lista desplegable que se muestra.

![](assets/s_ncs_user_email_del_properties_smtp_tab_encoding.png)

## Añadir encabezados SMTP {#adding-smtp-headers}

Es posible añadir encabezados SMTP a los envíos. To do this, use the relevant section of the **[!UICONTROL SMTP]** tab in the delivery.

The script entered in this window must reference one header per line in the following form: **name:value**.

Los valores se codifican automáticamente si es necesario.

>[!CAUTION]
>
>La adición de secuencias de comandos para insertar encabezados SMTP se reserva para usuarios avanzados.
>
>La sintaxis de esta secuencia de comandos debe cumplir con los requisitos de este tipo de contenido: no dejar espacios sin utilizar, ninguna línea vacía, etc.
