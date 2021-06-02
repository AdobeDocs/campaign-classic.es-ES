---
product: campaign
title: Renderización de la bandeja de entrada   en Campaign
description: Obtenga información sobre cómo capturar las renderizaciones de correo electrónico y ponerlas a disposición en un informe dedicado
audience: delivery
content-type: reference
topic-tags: deliverability-management
exl-id: a3294e70-ac96-4e51-865f-b969624528ce
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 100%

---

# Renderización de la bandeja de entrada{#inbox-rendering}

## Acerca de la renderización de la bandeja de entrada {#about-inbox-rendering}

Antes de pulsar el botón **Send**, asegúrese de que su mensaje se mostrará a los destinatarios de una forma óptima en una gran variedad de clientes, correos Web y dispositivos web.

Para permitir esto, Adobe Campaign aprovecha la solución de prueba de correo electrónico basada en Web [Litmus](https://litmus.com/email-testing) para detectar las irregularidades y señalarlas en un informe dedicado. Esto le permite obtener una previsualización del mensaje enviado en los diferentes contextos en los que se puede recibir y comprobar la compatibilidad en las aplicaciones y los escritorios principales.

Litmus es una aplicación de validación y previsualización de correo electrónico con numerosas funciones. Permite a los creadores de contenido de correo electrónico obtener una previsualización del contenido de sus mensajes en más de 70 procesadores de correo electrónico, como la bandeja de entrada de Gmail o el cliente de correo de Apple.

Los clientes móviles, de mensajería y de correo web disponibles para **Renderización de la bandeja de entrada** en Adobe Campaign se enumeran en el [sitio web de Litmus](https://litmus.com/email-testing) (haga clic en **Ver todos los clientes de correo electrónico**).

>[!NOTE]
>
>No es necesario renderizar la bandeja de entrada para probar la personalización en las entregas. La personalización puede comprobarse con las herramientas de Adobe Campaign como **[!UICONTROL Preview]** y [Proofs](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

## Activación de la renderización de la bandeja de entrada{#activating-inbox-rendering}

Para los clientes alojados e híbridos, el servicio de asistencia técnica y consultores de Adobe configuran la renderización de la Bandeja de entrada en la instancia. Para obtener más información, póngase en contacto con su administrador de cuentas de Adobe.

Para las instalaciones in situ, siga los pasos a continuación para configurar la renderización de la Bandeja de entrada.

1. Mediante el menú **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]**, instale el paquete **[!UICONTROL Inbox rendering (IR)]**. Para obtener más información, consulte [Instalación de paquetes estándar de Campaign Classic](../../installation/using/installing-campaign-standard-packages.md).
1. Configure una cuenta externa del tipo HTTP mediante el nodo **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]**. Para obtener más información, consulte [Creación de una cuenta externa](../../installation/using/external-accounts.md#creating-an-external-account).
1. Defina los parámetros de cuenta externa de la siguiente manera:
   * **[!UICONTROL Label]**: Información del servidor de envío
   * **[!UICONTROL Internal name]**: deliverabilityInstance
   * **[!UICONTROL Type]**: HTTP
   * **[!UICONTROL Server]**: https://deliverability-app.neolane.net/deliverability
   * **[!UICONTROL Encryption]**: Ninguno
   * Marque la opción **[!UICONTROL Enabled]**.

   ![](assets/s_tn_inbox_rendering_external-account.png)

1. Vaya al nodo **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**. Busque la opción **[!UICONTROL DmRendering_cuid]** y póngase en contacto con el servicio de soporte técnico para obtener el identificador de los informes de envío que debe copiarse en el campo **[!UICONTROL Value (text)]**.
1. Edite el archivo **serverConf.xml** para permitir una llamada al servidor Litmus. Añada la siguiente línea a la sección `<urlPermission>`:

   ```
   <url dnsSuffix="deliverability-app.neolane.net" urlRegEx="https://.*"/>
   ```

1. Vuelva a cargar la configuración con el siguiente comando:

   ```
   nlserver config -reload
   ```

>[!NOTE]
>
>Es posible que tenga que cerrar la sesión desde la consola y volver a iniciarla para poder utilizar la renderización de la Bandeja de entrada.

## Acerca de los tokens de Litmus {#about-litmus-tokens}

Ya que Litmus es un servicio de terceros, funciona con un modelo de crédito. Cada vez que un usuario usa las funciones de Litmus, se reduce su crédito.

En Adobe Campaign, el crédito corresponde al número de representaciones disponibles (conocidas como tokens).

>[!NOTE]
>
>El número de tokens de Litmus disponibles depende de la licencia adquirida en Campaign. Compruebe el acuerdo de licencia.

Cada vez que se utiliza la función **[!UICONTROL Inbox rendering]** en una entrega, cada renderización generada reduce en uno los tokens disponibles.

>[!IMPORTANT]
>
>Los tokens corresponden a cada renderización individual y no al informe completo de renderización de la Bandeja de entrada, lo que significa que:
>
>* Cada vez que se genera el informe de renderización de la Bandeja de entrada, se resta un token por cada cliente de mensajería: uno para la renderización de Outlook 2000, uno para la renderización de Outlook 2010, uno para la renderización de Apple Mail 9, etc.
>* Para el mismo envío, si vuelve a generar la renderización de la bandeja de entrada, el número de tokens disponibles se reduce de nuevo según la cantidad de renderizaciones generadas.
>



El número de tokens disponibles restantes se muestra en **[!UICONTROL General summary]** de [Inbox rendering report](#inbox-rendering-report).

![](assets/s_tn_inbox_rendering_tokens.png)

Normalmente, la función de renderización de la bandeja de entrada se utiliza para probar el marco HTML de un correo electrónico recién diseñado. Cada renderización requiere aproximadamente 70 tokens (dependiendo de la cantidad de entornos en los que se pruebe). Sin embargo, en algunos casos puede necesitar varios informes de renderización de la bandeja de entrada para probar al completo su envío. Por lo tanto, puede requerir más tokens para realizar varias comprobaciones.

## Acceso al informe de renderización de la bandeja de entrada {#accessing-the-inbox-rendering-report}

Una vez que haya creado su envío de correo electrónico y definido su contenido, así como la población de destino, siga los pasos a continuación.

Para obtener más información sobre la creación, el diseño y la segmentación de los servicios de información, consulte [esta sección](../../delivery/using/about-email-channel.md).

1. En la barra superior de la entrega, haga clic en el botón **[!UICONTROL Inbox rendering]**.
1. Seleccione **[!UICONTROL Analyze]** para iniciar el proceso de captura.

   ![](assets/s_tn_inbox_rendering_button.png)

   Se envía una prueba. Se puede acceder a las miniaturas de renderización de esa prueba unos minutos después de enviar los mensajes de correo electrónico. Para obtener más información la entrega de pruebas, consulte [esta sección](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

1. Una vez enviada, la prueba aparece en la lista de envío. Haga doble clic en ella.

   ![](assets/s_tn_inbox_rendering_delivery_list.png)

1. Vaya a la pestaña **Inbox Rendering** de la prueba.

   ![](assets/s_tn_inbox_rendering_tab.png)

   Se muestra el informe de renderización de la bandeja de entrada.

## Informe de renderización de la bandeja de entrada {#inbox-rendering-report}

Este informe muestra las renderizaciones de la bandeja de entrada tal y como aparecen al destinatario. Las renderizaciones pueden variar en función del modo en que el destinatario abra la entrega de correo electrónico: en un navegador, en un dispositivo móvil o a través de una aplicación de correo electrónico.

**[!UICONTROL General summary]** presenta el número de mensajes recibidos, no deseados (correo no deseado), no recibidos o cuya recepción está pendiente en formato lista y a través de una representación gráfica codificada por colores.

![](assets/s_tn_inbox_rendering_summary.png)

Pase el ratón por encima del gráfico para ver los detalles de cada color.

El cuerpo del informe se divide en tres partes: **[!UICONTROL Mobile]**, **[!UICONTROL Messaging clients]** y **[!UICONTROL Webmails]**. Desplácese hacia abajo por el informe para mostrar todas las representaciones agrupadas en estas tres categorías.

![](assets/s_tn_inbox_rendering_report.png)

Para obtener los detalles de cada informe, haga clic en la tarjeta correspondiente. Se muestra la renderización del método de recepción seleccionado.

![](assets/s_tn_inbox_rendering_example.png)
