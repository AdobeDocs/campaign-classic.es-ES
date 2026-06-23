---
product: campaign
title: Enviar con el MTA mejorado en Adobe Campaign Classic
description: Obtenga información acerca del ámbito y las características específicas del envío de correos electrónicos con el servidor de correo mejorado de Adobe Campaign
feature: Email
role: User, Admin, Developer
exl-id: 58cc23f4-9ab0-45c7-9aa2-b08487ec7e91
TQID: https://experienceleague.adobe.com/d6tF02X7K9j9mDk90wyH-3iXm8iBZzMo1da2PPkYHGs
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: b631758a-142d-425f-b9aa-f756d85cb979id: c858a28b-ea19-49b0-8d48-828717fad89c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
subfeature_v2: id: e95a583b-fcfa-4524-8666-46a29c828119id: c8da4fdd-eb94-4751-a43c-f82733fb2d6eid: d5bbe3da-ba85-4242-817e-54f7c4b943e0id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: c8d13469884744554fd504fed8842dd0c9ab5feb
workflow-type: tm+mt
source-wordcount: 1393
ht-degree: 96%

---

# Envío con el MTA mejorado {#sending-with-enhanced-mta}

El **servidor de correo mejorado de Adobe Campaign** (MTA) proporciona una infraestructura de envío mejorada que ofrece mayor capacidad de entrega, reputación, rendimiento, sistema de informes, gestión de devoluciones, ampliación de IP y administración de la configuración de conexión.

Se implementa para mejorar la escalabilidad, aumentar el rendimiento del envío y permitir enviar más correos electrónicos más rápido. Esto se logra con las nuevas técnicas de envío adaptable que modifican la configuración del envío de correo electrónico en tiempo real en función de los comentarios de los proveedores de servicio de Internet.

>[!IMPORTANT]
>
>El servidor de correo mejorado de Adobe Campaign solo está disponible para clientes híbridos o alojados por Campaign Classic. Las instalaciones on-premise del Campaign Classic no se pueden actualizar para utilizar el servidor de correo mejorado.

Si se le ha proporcionado una instancia de Campaign Classic después de septiembre de 2018, está utilizando el servidor de correo mejorado. Para todos los demás clientes de Campaign Classic, consulte las [preguntas frecuentes](#enhanced-mta-faq) a continuación.

La implementación del servidor de correo mejorado puede afectar a algunas de las funcionalidades de Campaign existentes. Para obtener más información sobre esto, consulte las [especificidades del servidor de correo mejorado](#enhanced-mta-impacts).

>[!NOTE]
>
>Si es un usuario final de Adobe Campaign y desea saber si su instancia se ha actualizado al servidor de correo mejorado, póngase en contacto con el administrador de Campaign interno.

## Preguntas frecuentes {#enhanced-mta-faq}

### Uso y beneficios

**¿Qué es el servidor de correo mejorado (MTA)?**

Ahora puede actualizar Adobe Campaign para que utilice el **servidor de correo mejorado** (Agente de transferencia de correo), un motor de entrega de correo electrónico de alto rendimiento.

El servidor de correo mejorado incluye una gestión de devoluciones más inteligente y una capacidad de optimización de la capacidad de envío automatizada que ayuda a los remitentes a lograr y mantener tasas de envío de bandeja de entrada óptimas.

**¿Cuáles son los beneficios?**

* Los clientes de Adobe Campaign que utilizan MTA mejorado han experimentado un <!--300%-->aumento masivo en la velocidad de rendimiento general y una reducción significativa de los rechazos temporales.
  <!--90%+-->
* El servidor de correo mejorado utiliza la tecnología MTA más reciente para proporcionarle las velocidades de rendimiento óptimas para sus envíos de correos electrónicos.
* Al adaptarse instantánea y automáticamente a los comentarios que recibe, también garantiza envíos de correos electrónicos más precisos e inteligentes con los datos de envío en tiempo real.

**¿Puedo usar el servidor de correo nativo de Adobe Campaign y el mejorado a la vez?**

No. Solo se puede usar el servidor de correo mejorado para los envíos de correo electrónico después de actualizar la instancia.

<!--
**Is there a fee associated with upgrading my instance to and subsequent use of the Enhanced MTA?**
No, there is no extra fee associated with the upgrade process to enable the use of the Enhanced MTA.

**When will the Enhanced MTA be available to me?**

* If you are new to Adobe Campaign Classic, you are already using the Enhanced MTA.

* For Adobe Campaign Classic existing customers, we've implemented a phased rollout that covers all hosted or partially hosted (hybrid) instances. If you're not already using it, we'll be contacting you in the near future with the dates and details for upgrading your Adobe Campaign Classic instances to the Enhanced MTA.
-->

### Actualización al servidor de correo mejorado

**¿Qué se necesita para actualizar al servidor de correo mejorado?**

Si se le proporcionó una instancia de Campaign Classic después de septiembre de 2018, no se requiere ninguna acción, ya que ya está utilizando el servidor de correo mejorado.

Para todos los demás clientes alojados o alojados parcialmente (híbridos), el equipo de Adobe Campaign se pondrá en contacto para concertar una fecha para la migración y proporcionará detalles sobre los pasos necesarios para la migración.

>[!IMPORTANT]
>
>El servidor de correo mejorado no está disponible para instalaciones on-premise.

**¿Cuál es el proceso para actualizar mi instancia al servidor de correo mejorado?**

Todo el proceso de las instancias hospedadas requiere unos minutos de tiempo de inactividad. Adobe supervisará el rendimiento y la capacidad de entrega del correo electrónico durante un máximo de 24 horas después de la actualización para evaluar cualquier impacto en sus envíos de correo electrónico.

Si se detecta algún problema, Adobe puede revertir su instancia de forma rápida y temporal al servidor de correo nativo de Adobe Campaign.

Actualmente, el servidor de correo mejorado solo afecta al canal de correo electrónico. Las notificaciones push y los envíos SMS seguirán utilizando el servidor de correo de Campaign nativo y no se verán afectados por la actualización.

**¿Debo volver a calentar la IP después de actualizar al servidor de correo mejorado?**

No. La actualización no requiere cambiar a direcciones IP nuevas, por lo que puede seguir usando las direcciones IP de correo electrónico calentadas existentes.

**¿Afectará la actualización al servidor de correo mejorado a cualquier campaña o envío que se encuentre en curso?**

Para los clientes que utilizan la funcionalidad de mensajería transaccional de Adobe Campaign, cualquier llamada de API para activar un mensaje de correo electrónico se pondrá en cola durante el corto tiempo de inactividad de la actualización y se intentará cuando se complete la actualización.

## Especificaciones del MTA mejorado {#enhanced-mta-impacts}

### Nuevas reglas MX

Ya no se utilizan las reglas de rendimiento del envío de administración MX. El servidor de correo mejorado utiliza sus propias reglas MX que le permiten personalizar el rendimiento por dominio en función de su propia reputación histórica de correo electrónico y de los comentarios en tiempo real procedentes de los dominios a los que envía correos electrónicos.

Para saber más sobre la configuración MX, consulte [esta sección](../../installation/using/email-deliverability.md#mx-configuration).

### Calificación de rechazo

Las calificaciones de rechazo de la tabla **[!UICONTROL Delivery log qualification]** de Campaign ya no se utilizan para los mensajes de error de envío **simultáneos**. El servidor de correo mejorado determina el tipo de rechazo y la calificación, y envía esa información a Campaign.

>[!NOTE]
>
>El servidor de correo mejorado califica el rebote SMTP y devuelve esa calificación a Campaign en forma de código de rechazo asignado a un motivo y una calificación de Campaign.

Para obtener más información sobre la calificación de correo rechazado, consulte [esta sección](delivery-failures-quarantine.md#bounce-mail-qualification).

### Envío

Un envío no se puede detener una vez transferido al MTA mejorado, aunque se muestre con el estado **[!UICONTROL Stopped]** en Campaign.

### Rendimiento del envío

El gráfico de rendimiento del envío de Campaign ya no mostrará el rendimiento a los destinatarios del correo electrónico. Muestra la velocidad de rendimiento del reenvío de sus mensajes desde Campaign hasta el servidor de correo mejorado.

Para obtener más información sobre el rendimiento del envío, consulte [esta sección](../../reporting/using/global-reports.md#delivery-throughput).

### Reintentos

Campaign ya no utiliza la configuración de reintentos en la entrega. Los reintentos de rebote suave y el periodo entre ellos están determinados por el servidor de correo mejorado en función del tipo y la gravedad de las respuestas de devoluciones procedentes del dominio de correo electrónico del mensaje.

Para obtener más información sobre los reintentos, consulte esta [página](communication-channels.md) en **Envío de entregas** > **Configurar reintentos**.

### Período de validez

El servidor de correo mejorado solo utilizará la configuración del período de validez de los envíos de Campaign si se establece en **3,5 días o menos**. Si define un valor superior a 3,5 días en Campaign, no se tendrá en cuenta.

Por ejemplo, si el período de validez se establece en el valor predeterminado de 5 días en Campaign, los mensajes de rebote suave se incluirán en la cola de reintentos del servidor de correo mejorado y se volverá a intentar su envío durante un máximo de 3,5 días a partir de la fecha en que el mensaje llegue al servidor de correo mejorado. En ese caso, no se utilizará el valor establecido en Campaign.

Una vez que un mensaje ha estado en la cola del servidor de correo mejorado durante 3,5 días y no se ha podido entregar, se agotará el tiempo de espera y su estado se actualizará de **[!UICONTROL Sent]** a **[!UICONTROL Failed]** en los registros de envío.

Para obtener más información sobre el período de validez, consulte esta [página](communication-channels.md) en **Envío de entregas** > **Definir el período de validez**.

### Firma DKIM

La firma de autenticación de correo electrónico DKIM (DomainKeys Identified Mail) la realiza el MTA mejorado. La firma DKIM por parte del MTA de Campaign nativo se desactiva en la tabla de administración del dominio como parte de la actualización del MTA mejorado. Para obtener más información sobre DKIM, consulte la [Guía de prácticas recomendadas sobre entregabilidad de Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=es#authentication).

### Sistema de informes de éxito de envío

En la vista **[!UICONTROL Summary]** de un [panel](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}de envío de correo electrónico, el porcentaje de **[!UICONTROL Success]** empieza en 100 % y luego desciende progresivamente a lo largo del [período de validez](communication-channels.md) de la entrega, a medida que se informan los rebotes suaves y duros desde el MTA mejorado a Campaign.

De hecho, todos los mensajes se muestran como **[!UICONTROL Sent]** en los [registros de envío](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/send/monitor/delivery-dashboard#delivery-logs-and-history){target="_blank"} en cuanto se transmiten correctamente desde Campaign al MTA mejorado. Permanecen en ese estado a menos que un [rebote](delivery-failures-quarantine.md#delivery-failure-types-and-reasons) de ese mensaje se comunique desde el MTA mejorado a Campaign, o hasta que esto ocurra.

Cuando se generan informes de los mensajes de rebote duro desde el servidor de correo mejorado, su estado cambia de **[!UICONTROL Sent]** a **[!UICONTROL Failed]** y el porcentaje de **[!UICONTROL Success]** disminuye en consecuencia.

Cuando se generan informes de los mensajes de rebote suave desde el servidor de correo mejorado, siguen mostrándose como **[!UICONTROL Sent]** y el porcentaje de **[!UICONTROL Success]** todavía no se actualiza. A continuación, la entrega de los mensajes de rebote suave se [reintenta](delivery-failures-quarantine.md#retries-after-a-delivery-temporary-failure) durante todo el período de validez del envío:

* Si un reintento se realiza correctamente antes del final del período de validez, el estado del mensaje permanece como **[!UICONTROL Sent]** y el porcentaje de **[!UICONTROL Success]** permanece sin cambios.

* De lo contrario, el estado cambia a **[!UICONTROL Failed]** y el porcentaje de **[!UICONTROL Success]** disminuye en consecuencia.

Por lo tanto, debe esperar hasta el final del período de validez para ver el porcentaje de **[!UICONTROL Success]** final y el número final de mensajes realmente **[!UICONTROL Sent]** y **[!UICONTROL Failed]**.

En la tabla siguiente se muestran los diferentes pasos del proceso de envío con los indicadores clave de rendimiento (KPI) y los estados de registros de envío correspondientes.

| Paso en el proceso de envío | Resumen de KPI | Estado de envío de registros |
|--- |--- |--- |
| El mensaje se retransmite correctamente desde Campaign al servidor de correo mejorado | El porcentaje de **[!UICONTROL Success]** comienza en 100 % | Enviado |
| Los mensajes de devolución dura se informan desde el servidor de correo mejorado | El porcentaje de **[!UICONTROL Success]** baja en consecuencia | Error |
| Los mensajes de devolución suave se informan desde el servidor de correo mejorado | No hay cambios en el porcentaje de **[!UICONTROL Success]** | Enviado |
| Los reintentos de mensajes de devolución suave se realizan correctamente | Sin cambios en el porcentaje de **[!UICONTROL Success]** \|  el porcentaje de **[!UICONTROL Success]** se aumenta en consecuencia | Enviado |
| Error en los reintentos de mensajes de devolución suave | El porcentaje de **[!UICONTROL Success]** baja en consecuencia | Error |
