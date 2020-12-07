---
solution: Campaign Classic
product: campaign
title: Envío de un correo electrónico con Adobe Campaign Classic
description: Información sobre los parámetros de envíos por correo electrónico
audience: delivery
content-type: reference
topic-tags: sending-emails
translation-type: ht
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: ht
source-wordcount: '739'
ht-degree: 100%

---


# Envío de correos electrónicos{#sending-an-email}

Para aprobar el mensaje y enviarlo a los destinatarios de la entrega que está creando, haga clic en **[!UICONTROL Send]**.

El proceso detallado para validar y realizar una entrega se presenta en las siguientes secciones:

* [Validación de la entrega](../../delivery/using/steps-validating-the-delivery.md)
* [Realización de la entrega](../../delivery/using/steps-sending-the-delivery.md)

Las secciones siguientes detallan los parámetros específicos para enviar correos electrónicos.

## Correo electrónico CCO {#archiving-emails}

Adobe Campaign permite almacenar correos electrónicos en un sistema externo a través de CCO añadiendo simplemente una dirección de correo electrónico CCO al destino del mensaje. Una vez activada la opción, se conserva una copia exacta de todos los mensajes enviados en este envío.

Para obtener más información sobre la configuración y las prácticas recomendadas para las direcciones de correo electrónico CCO, consulte [esta sección](../../installation/using/email-archiving.md).

>[!NOTE]
>
>El correo electrónico CCO es una capacidad opcional. Compruebe el acuerdo de licencia y póngase en contacto con el administrador de cuentas para activarlo.

Al crear un nuevo envío o una plantilla de envíos, el correo electrónico CCO no está habilitado de forma predeterminada. Debe habilitarlo manualmente en el nivel de envío o de plantilla de envíos de correo electrónico.

Para habilitar el correo electrónico CCO para una plantilla de envíos de correo electrónico, siga los pasos a continuación:

1. Vaya a **[!UICONTROL Campaign Management]** > **[!UICONTROL Deliveries]** o **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]**.
1. Seleccione la entrega que desee o duplique la plantilla de **envío de correo electrónico** preestablecida y, a continuación, seleccione la plantilla duplicada.
1. Haga clic en el botón **Propiedades**.
1. Seleccione la pestaña **[!UICONTROL Delivery]** .
1. Marque la opción **correo electrónico CCO**. Se enviará una copia de todos los mensajes entregados para cada envío en función de esta plantilla a la dirección de CCO de correo electrónico que se haya configurado.

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

* **[!UICONTROL Force the generation of the mirror page]**: incluso si no se inserta ningún vínculo a la página espejo en la entrega, se creará la página espejo.
* **[!UICONTROL Do not generate the mirror page]**: no se genera ninguna página espejo, aunque el vínculo esté presente en la entrega.
* **[!UICONTROL Generates a mirror page accessible using only the message identifier]**: esta opción permite acceder al contenido de la página duplicada, con información de personalización, en la ventana del “log” de envío. Para ello, tras finalizar la entrega, haga clic en la pestaña **[!UICONTROL Delivery]** y seleccione la línea del destinatario cuya página duplicada desee ver. Haga clic en el vínculo **[!UICONTROL Display the mirror page for this message...]**.

   ![](assets/s_ncs_user_wizard_miror_page_link.png)

## Gestión de correos electrónicos rechazados {#managing-bounce-emails}

La pestaña **[!UICONTROL SMTP]** de los parámetros de envío permite configurar la gestión de los correos electrónicos rechazados.

![](assets/s_ncs_user_email_del_properties_smtp_tab.png)

De forma predeterminada, los correos electrónicos rechazados se reciben en el cuadro de error predeterminado de la plataforma, pero se puede definir una dirección de error específica para una entrega.

Desde esta pantalla, también puede definir una dirección específica para investigar los motivos de rechazo de los correos electrónicos cuando la aplicación no pueda calificarlos automáticamente. Para cada uno de estos campos, el icono “Añadir campos personalizados” permite añadir parámetros de personalización.

## Codificación de caracteres {#character-encoding}

En la pestaña **[!UICONTROL SMTP]** de los parámetros de entrega, la sección **[!UICONTROL Character encoding]** le permite establecer una codificación específica.

La codificación predeterminada es UTF-8. Si algunos de los proveedores de correo electrónico de los destinatarios no admiten la codificación estándar UTF-8, es posible que desee configurar una codificación específica para que muestre correctamente los caracteres especiales a los destinatarios de los mensajes de correo electrónico.

Por ejemplo, desea enviar un correo electrónico que contenga caracteres japoneses. Para asegurarse de que todos los caracteres se mostrarán correctamente a los destinatarios en Japón, es posible que desee utilizar una codificación que admita los caracteres japoneses en lugar de la codificación UTF-8 estándar.

Para ello, seleccione la opción **[!UICONTROL Force the encoding used for messages]** en la sección **[!UICONTROL Character encoding]** y elija una codificación en la lista desplegable que se muestra.

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
