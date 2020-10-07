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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '741'
ht-degree: 87%

---


# Envío de correos electrónicos{#sending-an-email}

Para aprobar el mensaje y enviarlo a los destinatarios de la entrega que está creando, haga clic en **[!UICONTROL Send]**.

El proceso detallado para validar y realizar una entrega se presenta en las siguientes secciones:

* [Validación de la entrega](../../delivery/using/steps-validating-the-delivery.md)
* [Realización de la entrega](../../delivery/using/steps-sending-the-delivery.md)

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
1. Seleccione la entrega que desee o duplique la plantilla de **envío de correo electrónico** preestablecida y, a continuación, seleccione la plantilla duplicada.
1. Haga clic en el botón **Propiedades**.
1. Seleccione la pestaña **[!UICONTROL Delivery]** .
1. Marque la casilla **Archivar correos electrónicos** para mantener una copia de todos los mensajes enviados para este envío o para cada envío basado en esta plantilla.

   ![](assets/s_ncs_user_wizard_archiving.png)

   >[!NOTE]
   >
   >Si se abren y se hace clic en los correos electrónicos enviados a la dirección de CCO, esto se tiene en cuenta en el cálculo de **[!UICONTROL Total opens]** y **[!UICONTROL Clicks]** en el análisis de envío, lo cual podría provocar algunos cálculos erróneos.

## Generación de la página espejo {#generating-the-mirror-page}

La página espejo es una página HTML accesible en línea mediante un navegador web. Su contenido es idéntico al del correo electrónico.

De forma predeterminada, la página espejo se genera si el vínculo se inserta en el contenido del correo. Para obtener más información sobre cómo personalizar la inserción de bloques, consulte [Bloques de personalización](../../delivery/using/personalization-blocks.md).

En las propiedades de la entrega, el campo **[!UICONTROL Mode]** de la pestaña **[!UICONTROL Validity]** permite modificar el modo de generación de esta página.

![](assets/s_ncs_user_wizard_miror_page_mode.png)

>[!CAUTION]
>
>Se debe definir un contenido HTML para la entrega de la página espejo que se va a crear.

Además del modo predeterminado, también están disponibles las siguientes opciones:

* **[!UICONTROL Force the generation of the mirror page]** :: aunque no se inserte ningún vínculo a la página espejo en el envío, se creará la página espejo.
* **[!UICONTROL Do not generate the mirror page]** :: no se genera ninguna página espejo, aunque el vínculo esté presente en el envío.
* **[!UICONTROL Generates a mirror page accessible using only the message identifier]** :: esta opción le permite acceder al contenido de la página espejo, con información de personalización, en la ventana del registro de envíos. Para ello, tras finalizar la entrega, haga clic en la pestaña **[!UICONTROL Delivery]** y seleccione la línea del destinatario cuya página duplicada desee ver. Haga clic en el vínculo **[!UICONTROL Display the mirror page for this message...]**.

   ![](assets/s_ncs_user_wizard_miror_page_link.png)

## Gestión de correos electrónicos rechazados {#managing-bounce-emails}

La pestaña **[!UICONTROL SMTP]** de los parámetros de envío permite configurar la gestión de los correos electrónicos rechazados.

![](assets/s_ncs_user_email_del_properties_smtp_tab.png)

De forma predeterminada, los correos electrónicos rechazados se reciben en el cuadro de error predeterminado de la plataforma, pero se puede definir una dirección de error específica para una entrega.

Desde esta pantalla, también puede definir una dirección específica para investigar los motivos de rechazo de los correos electrónicos cuando la aplicación no pueda calificarlos automáticamente. Para cada uno de estos campos, el icono “Añadir campos personalizados” permite añadir parámetros de personalización.

## Codificación de caracteres {#character-encoding}

In the **[!UICONTROL SMTP]** tab of the delivery parameters, the **[!UICONTROL Character encoding]** section allows you to set a specific encoding.

La codificación predeterminada es UTF-8. Si algunos de los proveedores de correo electrónico de los destinatarios no admiten la codificación estándar UTF-8, es posible que desee configurar una codificación específica para que muestre correctamente los caracteres especiales a los destinatarios de los mensajes de correo electrónico.

Por ejemplo, desea enviar un correo electrónico que contenga caracteres japoneses. Para asegurarse de que todos los caracteres se mostrarán correctamente a los destinatarios en Japón, es posible que desee utilizar una codificación que admita los caracteres japoneses en lugar de la codificación UTF-8 estándar.

To do this, select the **[!UICONTROL Force the encoding used for messages]** option in the **[!UICONTROL Character encoding]** section and choose an encoding from the drop-down list that is displayed.

![](assets/s_ncs_user_email_del_properties_smtp_tab_encoding.png)

## Añadir encabezados SMTP {#adding-smtp-headers}

Es posible añadir encabezados SMTP a las entregas. Para ello, utilice la sección correspondiente en la pestaña **[!UICONTROL SMTP]** de la entrega.

La secuencia de comandos introducida en esta ventana debe hacer referencia a un encabezado por línea en el siguiente formulario **name:value**.

Los valores se codifican automáticamente si es necesario.

>[!CAUTION]
>
>La adición de secuencias de comandos para insertar encabezados SMTP se reserva para usuarios avanzados.
>
>La sintaxis de esta secuencia de comandos debe cumplir con los requisitos de este tipo de contenido: no dejar espacios sin utilizar, ninguna línea vacía, etc.
