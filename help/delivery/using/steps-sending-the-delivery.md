---
product: campaign
title: Configuración y envío de la entrega
description: Obtenga información sobre cómo configurar y realizar la entrega
badge-v7: label="v7" type="Informative" tooltip="Se aplica a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="También se aplica a Campaign v8"
feature: Channel Configuration
role: User
exl-id: 0411686e-4f13-401e-9333-e14b05ebe9cd
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '1514'
ht-degree: 100%

---

# Configuración y envío de la entrega {#configuring-and-sending-the-delivery}

## Permisos{#delivery-permissions}

Solo el propietario de la entrega puede comenzar una entrega. Para que otros operadores (o grupo de operadores) puedan iniciar una entrega, agréguelos como revisores en el campo **[!UICONTROL Delivery start:]**. [Más información](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers).

## Parámetros adicionales de entrega {#delivery-additiona-parameters}

Antes de realizar el envío, se pueden definir los parámetros de envío en las propiedades de envío a través de la pestaña **[!UICONTROL Delivery]**.

![](assets/s_ncs_user_wizard_delivery.png)

* **[!UICONTROL Delivery priority]**: utilice esta opción para cambiar el orden de envío de los pedidos indicando su nivel de prioridad, normal, alto o bajo.

* **[!UICONTROL Message batch quantity]**: utilice esta opción para definir el número de mensajes agrupados dentro del mismo paquete de entrega XML. Si el parámetro se establece en 0, los mensajes se agrupan automáticamente. El tamaño del paquete se define mediante el cálculo `<delivery size>/1024`, con un mínimo de 8 y un máximo de 256 mensajes por paquete.

  >[!IMPORTANT]
  >
  >Cuando se crea la entrega duplicando una existente, este parámetro se restablece.

* **[!UICONTROL Send using multiple waves]**: utilice esta opción para enviar los mensajes en lotes, en lugar de a toda la audiencia a la vez. [Más información](#sending-using-multiple-waves).

* **[!UICONTROL Test SMTP delivery]**: utilice esta opción para probar el envío a través de SMTP. La entrega se procesa hasta la conexión con el servidor SMTP, pero no se envía. Para cada destinatario de la entrega, Campaign se conecta al servidor del proveedor SMTP, ejecuta el comando RCPT TO del servidor de correo saliente (SMTP) y cierra la conexión antes del comando DATA del SMTP.

  >[!NOTE]
  >
  >* Esta opción no debe configurarse en intermediario.
  >
  >* Obtenga más información acerca de la configuración del servidor de SMTP en [esta sección](../../installation/using/configure-delivery-settings.md).

* **[!UICONTROL Email BCC]**: utilice esta opción para almacenar correos electrónicos en un sistema externo como CCO simplemente añadiendo una dirección de correo electrónico a copia oculta (CCO) al destinatario del mensaje. [Más información](sending-messages.md#archiving-emails).

## Confirmación de la entrega {#confirming-delivery}

Cuando la entrega esté configurada y lista para enviarse, ejecute el análisis de entrega.

Para ello, haga clic en **[!UICONTROL Send]**, seleccione la acción que desee y haga clic en **[!UICONTROL Analyze]**. [Más información](steps-validating-the-delivery.md#analyzing-the-delivery).

![](assets/s_ncs_user_email_del_send.png)

Una vez finalizado, haga clic en **[!UICONTROL Confirm delivery]** para iniciar el envío de mensajes.

A continuación, se puede cerrar el asistente de envíos y realizar un seguimiento de la ejecución del envío desde la pestaña **[!UICONTROL Delivery]**, a la que se puede acceder mediante el detalle del envío o a través de la lista de envíos.

Después de enviar mensajes, puede monitorizar y realizar un seguimiento de las entregas. Para obtener más información, consulte estas secciones:

* [Monitorización de una entrega](about-delivery-monitoring.md)
* [Comprensión de los errores de entrega](understanding-delivery-failures.md)
* [Acerca del seguimiento de mensajes](about-message-tracking.md)

## Programación de los envíos de entregas {#scheduling-the-delivery-sending}

Puede retrasar el envío del mensaje programando la entrega.

1. Haga clic en el botón **[!UICONTROL Send]** y seleccione la opción **[!UICONTROL Postpone delivery]**.

1. En el campo **[!UICONTROL Contact date]** especifique una fecha de inicio.

![](assets/dlv_email_del_plan.png)

1. A continuación, puede iniciar el análisis de entrega y confirmar la entrega de la entrega. Sin embargo, la entrega del envío no comenzará hasta la fecha indicada en el campo **[!UICONTROL Contact date]**.

>[!IMPORTANT]
>
>Una vez iniciado el análisis, la fecha de contacto definida queda fijada. Si se modifica esta fecha, es necesario reiniciar el análisis para que se tengan en cuenta las modificaciones.

![](assets/s_ncs_user_email_del_start_delayed.png)

En la lista de envío, el envío aparecerá con el estado **[!UICONTROL Pending]**.

![](assets/s_ncs_user_email_del_waiting.png)

La programación se puede configurar en orden ascendente mediante el botón **[!UICONTROL Scheduling]** del envío.

![](assets/s_ncs_user_email_del_save_in_calendar_ico.png)

Permite retrasar la entrega a una fecha posterior o guardar la entrega en el calendario provisional.

* La opción **[!UICONTROL Schedule delivery (no automatic execution)]** permite programar un análisis provisional del envío.

  Cuando se guarda esta configuración, el envío cambia al estado **[!UICONTROL Targeting pending]**. El análisis se inicia en la fecha especificada.

* La opción **[!UICONTROL Schedule delivery (automatic execution on planned date)]** permite especificar la fecha de envío.

  Haga clic en **[!UICONTROL Send]** y seleccione **[!UICONTROL Postpone delivery]** luego inicie el análisis y confirme la entrega. Cuando el análisis finalice, el destinatario de entrega está listo y los mensajes se envían automáticamente en la fecha especificada.

Las fechas y horas se expresan en el huso horario del operador actual. La lista desplegable **[!UICONTROL Time zone]** situada debajo del campo “fecha de contacto” permite convertir automáticamente la fecha y la hora introducidas al huso horario seleccionado.

Por ejemplo, si se programa una entrega para que se ejecute automáticamente a las 8 en punto, hora de Londres, la hora se convierte automáticamente al huso horario seleccionado:

![](assets/s_ncs_user_email_del_plan_calendar_timezone.png)

## Envío mediante múltiples olas {#sending-using-multiple-waves}

Para equilibrar la carga, se pueden dividir los envíos en varios lotes. Configure el número de lotes y su proporción con respecto a todo la entrega.

>[!NOTE]
>
>Solo se puede definir el tamaño y el retraso entre dos olas consecutivas. No se pueden configurar los criterios de selección de destinatarios para cada ola.

1. Abra la ventana de propiedades de entrega y haga clic en la pestaña **[!UICONTROL Delivery]**.
1. Seleccione la opción **[!UICONTROL Send using multiple waves]** y haga clic en el enlace **[!UICONTROL Define waves...]**.

   ![](assets/s_ncs_user_wizard_waves.png)

1. Para configurar las olas, se puede:

   * Definir el tamaño de cada ola. Por ejemplo, si se introduce **[!UICONTROL 30%]** en el campo correspondiente, cada ola representa el 30 % de los mensajes incluidos en el envío, excepto el último, que representa el 10 % de los mensajes.

     En el campo **[!UICONTROL Period]** especifique el retardo entre el inicio de dos olas consecutivas. Por ejemplo, si se introduce **[!UICONTROL 2d]**, la primera ola comienza inmediatamente, la segunda ola comienza en dos días, la tercera ola en cuatro días, etc.

     ![](assets/s_ncs_user_wizard_waves_create_size.png)

   * Defina un calendario para enviar cada ola.

     En la columna **[!UICONTROL Start]** especifique el retardo entre el inicio de dos olas consecutivas. En la columna **[!UICONTROL Size]**, introduzca un número fijo o un porcentaje.

     En el siguiente ejemplo, la primera ola representa el 25 % del número total de mensajes incluidos en la entrega y se inicia inmediatamente. Las dos olas siguientes completan la entrega y se establecen para comenzar a intervalos de seis horas.

     ![](assets/s_ncs_user_wizard_waves_create.png)

   Una regla de tipología específica, **[!UICONTROL Wave scheduling check]**, garantiza que la última ola se programe antes del límite de validez del envío. Las tipologías de campaña y sus reglas, configuradas en la pestaña **[!UICONTROL Typology]** de las propiedades de envío, se muestran en [Proceso de validación con tipologías](steps-validating-the-delivery.md#validation-process-with-typologies).

   >[!IMPORTANT]
   >
   >Asegúrese de que las últimas olas no superen la fecha límite de envío, que se define en la pestaña **[!UICONTROL Validity]**. En caso contrario, es posible que algunos mensajes no se envíen.
   >
   >Al configurar las últimas olas, se debe dejar un margen suficiente para realizar reintentos. Consulte [esta sección](steps-sending-the-delivery.md#configuring-retries).

1. Para supervisar sus envíos, vaya a los “logs” de entrega. Consulte [esta página](delivery-dashboard.md#delivery-logs-and-history).

   Se pueden ver los envíos que ya se han realizado en las olas procesadas (estado **[!UICONTROL Sent]**) y las que se envían en las olas restantes (estado **[!UICONTROL Pending]**).

Los siguientes dos ejemplos son los casos más comunes para usar varias olas.

* **Durante el proceso de aceleración**

  Cuando se envían correos electrónicos utilizando una plataforma nueva, los proveedores de servicios de Internet (ISP) sospechan de las direcciones IP desconocidas. Si se envían, de repente, grandes volúmenes de correos electrónicos, los ISP suelen marcarlos como correo no deseado.

  Para evitar que se lo considere correo no deseado, puede aumentar progresivamente el volumen enviado mediante el uso de olas. Esto debería garantizar un desarrollo uniforme de la fase de inicio y permitir reducir la velocidad total de direcciones no válidas.

  Para ello, marque la opción **[!UICONTROL Schedule waves according to a calendar]**. Por ejemplo, defina la primera ola en 10 %, la segunda en 15 % y así sucesivamente.

  ![](assets/s_ncs_user_wizard_waves_ramp-up.png)

* **Campañas que implican un centro de llamadas**

  Al administrar una campaña de lealtad por teléfono, su organización tiene una capacidad limitada para procesar la cantidad de llamadas a los suscriptores.

  Al usar olas, restringimos el número de mensajes a 20 por día, es decir, la capacidad de procesamiento diaria de un centro de llamadas.

  Para ello, seleccione la opción **[!UICONTROL Schedule multiple waves of the same size]**. Introduzca **[!UICONTROL 20]** como tamaño de la ola y **[!UICONTROL 1d]** en el campo **[!UICONTROL Period]**.

  ![](assets/s_ncs_user_wizard_waves_call_center.png)

## Configuración de reintentos {#configuring-retries}

Para los mensajes que no se hayan enviado temporalmente debido a un error **leve** o **ignorado**, se realiza un reintento automático. Los tipos y motivos del error de entrega se presentan en esta [sección](understanding-delivery-failures.md#delivery-failure-types-and-reasons).

>[!IMPORTANT]
>
>En el caso de instalaciones hospedadas o híbridas, si ha actualizado al [servidor de correo mejorado](sending-with-enhanced-mta.md), la configuración de reintentos de la entrega ya no se utiliza en Campaign. Los reintentos de rechazo temporal y el periodo de tiempo entre ellos están determinados por el servidor de correo mejorado en función del tipo y la gravedad de las respuestas de rechazo procedentes del dominio de correo electrónico del mensaje.

En el caso de instalaciones on-premise e instalaciones hospedadas/híbridas que utilizan el servidor de correo de Campaign heredado, la sección central de la pestaña **[!UICONTROL Delivery]** para parámetros de envío indica cuántos reintentos deben realizarse al día siguiente del envío y el margen mínimo entre reintentos.

![](assets/s_ncs_user_wizard_retry_param.png)

De manera predeterminada, se programan cinco reintentos para el primer día de la entrega con un intervalo mínimo de una hora distribuidos durante las 24 horas del día. Después de ello, se programa un reintento por día hasta la fecha límite de entrega, que se define en la pestaña **[!UICONTROL Validity]**. Consulte [Definición del período de validez](#defining-validity-period).

## Definición del período de validez {#defining-validity-period}

Una vez iniciada la entrega, se pueden enviar los mensajes (y los reintentos) hasta la fecha límite de entrega. Esto se indica en las propiedades de envío a través de la pestaña **[!UICONTROL Validity]**.

![](assets/s_ncs_user_email_del_valid_period.png)

* El campo **[!UICONTROL Delivery duration]** permite introducir el límite de los reintentos de envío global. Esto significa que Adobe Campaign envía los mensajes comenzando en la fecha de inicio y, a continuación, para los mensajes que devuelven solo un error se realizan reintentos normales y configurables hasta que se alcanza el límite de validez.

  Asimismo, puede especificar fechas. Para ello, seleccione **[!UICONTROL Explicitly set validity dates]**. En este caso, las fechas de envío y de límite de validez también permiten especificar el tiempo. El tiempo actual se utiliza de forma predeterminada, pero puede modificarse directamente en el campo de entrada.

  >[!IMPORTANT]
  >
  >En el caso de instalaciones hospedadas o híbridas, si se ha actualizado al [servidor de correo mejorado](sending-with-enhanced-mta.md), la configuración **[!UICONTROL Delivery duration]** en sus envíos de correo electrónico de Campaign se utilizará únicamente si se establece en **3,5 días o menos**. Si define un valor superior a 3,5 días, no se tendrá en cuenta.

* **Límite de validez de los recursos**: El campo **[!UICONTROL Validity limit]** se utiliza para los recursos cargados, principalmente para la página espejo y las imágenes. Los recursos de esta página son válidos durante un tiempo limitado (para ahorrar espacio en el disco).

  Los valores de este campo se pueden expresar en las unidades enumeradas en [esta sección](../../platform/using/adobe-campaign-workspace.md#default-units).
