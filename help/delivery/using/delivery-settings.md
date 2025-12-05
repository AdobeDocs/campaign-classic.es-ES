---
product: campaign
title: Acerca de la configuración de entregas
description: Descubra la configuración específica de entrega de la versión 7
feature: Channel Configuration
role: User
hide: true
hidefromtoc: true
exl-id: 66250817-f829-4b8b-92dd-2daa92a97fe0
source-git-commit: 2e3a14c97706a873f0791ef83708d704d2eed6c3
workflow-type: tm+mt
source-wordcount: '709'
ht-degree: 94%

---

# Configuración del envío {#about-delivery-settings}

Los siguientes ajustes son específicos de Campaign Classic. Para obtener más información, consulte la [documentación de la versión 8 de Campaign](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/gs-message.html?lang=es){target="_blank"}.

## Análisis de envíos {#delivery-analysis}

### Mejora del rendimiento del análisis de entrega {#improving-delivery-analysis}

Para acelerar la preparación del envío, puede marcar la opción **[!UICONTROL Prepare the delivery parts in the database]** antes de iniciar el análisis.

Cuando esta opción está habilitada, la preparación de envíos se realiza directamente en la base de datos, lo que puede acelerar considerablemente el análisis.

Actualmente, esta opción solo está disponible cuando se cumplen las siguientes condiciones:

* El envío debe ser un correo electrónico. Los otros canales no son compatibles por ahora.
* Evite utilizar enrutamiento intermediario o externo, solo el tipo de enrutamiento de envío masivo. Puede comprobar el enrutamiento que se utiliza en la pestaña **[!UICONTROL General]** de la **[!UICONTROL Delivery properties]**.
* No se puede direccionar hacia una población procedente de un archivo externo. Para un solo envío, haga clic en el enlace **[!UICONTROL To]** desde el **[!UICONTROL Email parameters]** y compruebe que la **[!UICONTROL Defined in the database]** opción está seleccionada. Para un envío utilizado en un flujo de trabajo, compruebe que los destinatarios están **[!UICONTROL Specified by the inbound event(s)]** en la pestaña **[!UICONTROL Delivery]**.
* Debe estar utilizando una base de datos PostgreSQL.

### Configuración de la prioridad de análisis {#analysis-priority-}

Cuando la entrega forma parte de una campaña, la pestaña **[!UICONTROL Advanced]** ofrece una opción adicional. Esto permite organizar el orden de procesamiento de los envíos en la misma campaña.

Cada entrega se analiza antes de realizarlo. La duración del análisis depende del archivo de extracción de envíos. Cuanto más significativo sea el tamaño del archivo, más dura el análisis, lo que hace que los siguientes envíos deban esperar.

Las opciones de **[!UICONTROL Message preparation by the scheduler]** permiten priorizar el análisis de envíos en un flujo de trabajo de Campaign.

![](assets/delivery_analysis_priority.png)

Si una entrega es demasiado grande, es mejor asignarle una prioridad baja para evitar ralentizar el análisis de otros envíos del flujo de trabajo.

>[!NOTE]
>
>Para garantizar que los análisis de entrega más grandes no ralenticen el progreso de los flujos de trabajo, se puede programar su ejecución marcando **[!UICONTROL Schedule execution for a time of low activity]**.

## Envío de envíos {#delivery-sending}

### Configuración de reintentos {#configuring-retries}

Para los mensajes que no se hayan enviado temporalmente debido a un error **leve** o **ignorado**, se realiza un reintento automático. Los tipos y motivos del error de entrega se presentan en esta [sección](delivery-failures-quarantine.md#delivery-failure-types-and-reasons).

>[!IMPORTANT]
>
>En el caso de instalaciones hospedadas o híbridas, si ha actualizado al [servidor de correo mejorado](sending-with-enhanced-mta.md), la configuración de reintentos de la entrega ya no se utiliza en Campaign. Los reintentos de rechazo temporal y el periodo de tiempo entre ellos están determinados por el servidor de correo mejorado en función del tipo y la gravedad de las respuestas de rechazo procedentes del dominio de correo electrónico del mensaje.

En el caso de instalaciones on-premise e instalaciones hospedadas/híbridas que utilizan el servidor de correo de Campaign heredado, la sección central de la pestaña **[!UICONTROL Delivery]** para parámetros de envío indica cuántos reintentos deben realizarse al día siguiente del envío y el margen mínimo entre reintentos.

![](assets/s_ncs_user_wizard_retry_param.png)

De manera predeterminada, se programan cinco reintentos para el primer día de la entrega con un intervalo mínimo de una hora distribuidos durante las 24 horas del día. Después de ello, se programa un reintento por día hasta la fecha límite de entrega, que se define en la pestaña **[!UICONTROL Validity]**. Consulte [Definición del período de validez](#defining-validity-period).

### Definición del período de validez {#defining-validity-period}

Una vez iniciada la entrega, se pueden enviar los mensajes (y los reintentos) hasta la fecha límite de entrega. Esto se indica en las propiedades de envío a través de la pestaña **[!UICONTROL Validity]**.

![](assets/s_ncs_user_email_del_valid_period.png)

* El campo **[!UICONTROL Delivery duration]** permite introducir el límite de los reintentos de envío global. Esto significa que Adobe Campaign envía los mensajes comenzando en la fecha de inicio y, a continuación, para los mensajes que devuelven solo un error se realizan reintentos normales y configurables hasta que se alcanza el límite de validez.

  Asimismo, puede especificar fechas. Para ello, seleccione **[!UICONTROL Explicitly set validity dates]**. En este caso, las fechas de envío y de límite de validez también permiten especificar el tiempo. El tiempo actual se utiliza de forma predeterminada, pero puede modificarse directamente en el campo de entrada.

  >[!IMPORTANT]
  >
  >En el caso de instalaciones hospedadas o híbridas, si se ha actualizado al [servidor de correo mejorado](sending-with-enhanced-mta.md), la configuración **[!UICONTROL Delivery duration]** en sus envíos de correo electrónico de Campaign se utilizará únicamente si se establece en **3,5 días o menos**. Si define un valor superior a 3,5 días, no se tendrá en cuenta.

* **Límite de validez de los recursos**: El campo **[!UICONTROL Validity limit]** se utiliza para los recursos cargados, principalmente para la página espejo y las imágenes. Los recursos de esta página son válidos durante un tiempo limitado (para ahorrar espacio en el disco).

  Los valores de este campo se pueden expresar en las siguientes unidades: **s** para segundos, **m** para minutos, **h** para horas, **d** para días (predeterminado), **y** para años.
