---
product: campaign
title: Envío con el servidor de envío mejorado en Adobe Campaign Classic
description: Obtenga información acerca del ámbito y las características específicas del envío de correos electrónicos con el servidor de correo mejorado de Adobe Campaign.
audience: delivery
content-type: reference
topic-tags: sending-emails
exl-id: 58cc23f4-9ab0-45c7-9aa2-b08487ec7e91
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1921'
ht-degree: 100%

---

# Envío con el servidor de correo mejorado {#sending-with-enhanced-mta}

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

Ahora puede actualizar Adobe Campaign para que utilice un nuevo servidor de correo (MTA) que ejecuta un MTA de correo electrónico comercial de SparkPost denominado **Momentum**.

Momentum representa una tecnología de MTA innovadora y de alto rendimiento que incluye gestión de devoluciones más inteligente y capacidad de optimización de envíos automatizados, lo que ayuda a los remitentes a lograr y mantener tasas de envío de bandeja de entrada óptimas. <!--More than 37% of the world’s business email is sent using SparkPost’s MTA technology.-->

**¿Cuáles son los beneficios?**

* Los clientes de Adobe Campaign que utilizan el servidor de correo mejorado han experimentado un <!--300%-->aumento masivo en la velocidad de rendimiento general y una <!--90%+-->reducción significativa de las devoluciones suaves.
* El servidor de correo mejorado utiliza la tecnología MTA más reciente para proporcionarle las velocidades de rendimiento óptimas para sus envíos de correos electrónicos.
* Al adaptarse instantánea y automáticamente a los comentarios que recibe, también garantiza envíos de correos electrónicos más precisos e inteligentes con los datos de envío en tiempo real.

**¿Puedo usar el servidor de correo nativo de Adobe Campaign y el mejorado a la vez?**

No. Solo se puede usar el servidor de correo mejorado para los envíos de correo electrónico después de actualizar la instancia.

<!--
**Is there a fee associated with upgrading my instance to and subsequent use of the Enhanced MTA?**
No, there is no extra fee associated with the upgrade process to enable the use of the Enhanced MTA.

**When will the Enhanced MTA be available to me?**

* If you are new to Adobe Campaign Classic, you are already using the Enhanced MTA.

* For Adobe Campaign Classic existing customers, we’ve implemented a phased rollout that covers all hosted or partially hosted (hybrid) instances. If you’re not already using it, we’ll be contacting you in the near future with the dates and details for upgrading your Adobe Campaign Classic instances to the Enhanced MTA.
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

Cualquier envío que se haya preparado antes de actualizar la instancia para utilizar el servidor de correo mejorado deberá volver a prepararse para poder usar correctamente el nuevo servidor de correo.

Para los clientes que utilizan la funcionalidad de mensajería transaccional de Adobe Campaign, cualquier llamada de API para activar un mensaje de correo electrónico se pondrá en cola durante el corto tiempo de inactividad de la actualización y se intentará cuando se complete la actualización.

## Especificaciones de servidor de correo mejorado {#enhanced-mta-impacts}

### Encabezados de servidor de correo mejorado

Las últimas instancias de Campaign Classic incluyen código que agrega los encabezados de servidor de correo mejorado necesarios a cada mensaje. Si utiliza Adobe Campaign 19.1 (compilación 9032) o superior y este no es el caso, debe solicitar al [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) que añada el parámetro useMomentum=true a la configuración de la instancia de ejecución (en el archivo [serverConf.xml](../../installation/using/the-server-configuration-file.md#mta)), que puede ser su instancia de marketing, [instancia de intermediario](../../installation/using/mid-sourcing-server.md) o [instancia de ejecución de mensajería transaccional](../../message-center/using/configuring-instances.md#execution-instance), según la configuración.

Sin embargo, si está utilizando una instancia anterior que no incluye este código, se debe añadir una nueva regla de tipología denominada **[!UICONTROL Typology Rule for Enhanced MTAs]** a todas las tipologías existentes en la instancia de Campaign.
Esta regla se añade mediante un paquete **[!UICONTROL Typology]** instalado como parte de la actualización al servidor de correo mejorado.

>[!IMPORTANT]
>
>Si ve esta regla de tipología en sus tipologías, no la elimine ni la modifique de ninguna manera. De lo contrario, sus envíos de correo electrónico podrían verse afectados negativamente.

Este paquete **[!UICONTROL Typology]** debe instalarse en la instancia de marketing de Adobe Campaign.

Si usted es un cliente híbrido, el equipo de Adobe Campaign le proporcionará instrucciones sobre cómo instalar el paquete **[!UICONTROL Typology]** en su instancia de marketing como parte de la actualización al servidor de correo mejorado. Póngase en contacto con el ejecutivo de cuentas para obtener las instrucciones completas.

>[!IMPORTANT]
>
>Las instrucciones proporcionadas por el equipo de Adobe Campaign sobre cómo instalar el paquete **[!UICONTROL Typology]** deben seguirse con atención. De lo contrario, podría encontrar problemas importantes con las direcciones IP utilizadas para enviar correos electrónicos.

Para obtener más información sobre las tipologías, consulte [esta sección](../../campaign/using/about-campaign-typologies.md).

### Nuevas reglas MX

Ya no se utilizan las reglas de rendimiento del envío de administración MX. El servidor de correo mejorado utiliza sus propias reglas MX que le permiten personalizar el rendimiento por dominio en función de su propia reputación histórica de correo electrónico y de los comentarios en tiempo real procedentes de los dominios a los que envía correos electrónicos.

Para saber más sobre la configuración MX, consulte [esta sección](../../installation/using/email-deliverability.md#mx-configuration).

### Calificación de rechazo

Las calificaciones de rechazo de la tabla **[!UICONTROL Delivery log qualification]** de Campaign ya no se utilizan para los mensajes de error de envío **simultáneos**. El servidor de correo mejorado determina el tipo de rechazo y la calificación, y envía esa información a Campaign.

>[!NOTE]
>
>El servidor de correo mejorado califica el rebote SMTP y devuelve esa calificación a Campaign en forma de código de rechazo asignado a un motivo y una calificación de Campaign.

Para obtener más información sobre la calificación de correo rechazado, consulte [esta sección](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification).

### Rendimiento del envío

El gráfico de rendimiento del envío de Campaign ya no mostrará el rendimiento a los destinatarios del correo electrónico. Muestra la velocidad de rendimiento del reenvío de sus mensajes desde Campaign hasta el servidor de correo mejorado.

Para obtener más información sobre el rendimiento del envío, consulte [esta sección](../../reporting/using/global-reports.md#delivery-throughput).

### Período de validez

El servidor de correo mejorado solo utilizará la configuración del período de validez de los envíos de Campaign si se establece en **3,5 días o menos**. Si define un valor superior a 3,5 días en Campaign, no se tendrá en cuenta.

Por ejemplo, si el período de validez se establece en el valor predeterminado de 5 días en Campaign, los mensajes de rebote suave se incluirán en la cola de reintentos del servidor de correo mejorado y se volverá a intentar su envío durante un máximo de 3,5 días a partir de la fecha en que el mensaje llegue al servidor de correo mejorado. En ese caso, no se utilizará el valor establecido en Campaign.

Una vez que un mensaje ha estado en la cola del servidor de correo mejorado durante 3,5 días y no se ha podido entregar, se agotará el tiempo de espera y su estado se actualizará de **[!UICONTROL Sent]** a **[!UICONTROL Failed]** en los registros de envío.

Para obtener más información sobre el período de validez, consulte [esta sección](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period).

### Firma DKIM

La autenticación por correo electrónico DKIM (DomainKeys Identified Mail) la realiza el servidor de correo mejorado. La firma DKIM por parte del servidor de correo de Campaign nativo se desactiva en la tabla de administración del dominio como parte de la actualización del servidor de correo mejorado.
Para obtener más información sobre DKIM, consulte la [Guía de prácticas recomendadas de entrega de Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=es#authentication).

### Sistema de informes de éxito de envío

En la vista **[!UICONTROL Summary]** de un [panel](../../delivery/using/delivery-dashboard.md)de envío de correo electrónico, el porcentaje de **[!UICONTROL Success]** empieza en el 100 % y luego desciende progresivamente a lo largo del [período de validez](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period)del envío, a medida que se informan los rebotes suaves y duros desde el servidor de correo mejorado a Campaign.

De hecho, todos los mensajes se muestran como **[!UICONTROL Sent]** en los [registros de envío](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history) en cuanto se transmiten correctamente desde Campaign al servidor de correo mejorado. Permanecen en ese estado a menos que un [rebote](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons) de ese mensaje se comunique desde el servidor de correo mejorado a Campaign, o hasta que esto ocurra.

Cuando se generan informes de los mensajes de rebote duro desde el servidor de correo mejorado, su estado cambia de **[!UICONTROL Sent]** a **[!UICONTROL Failed]** y el porcentaje de **[!UICONTROL Success]** disminuye en consecuencia.

Cuando se generan informes de los mensajes de rebote suave desde el servidor de correo mejorado, siguen mostrándose como **[!UICONTROL Sent]** y el porcentaje de **[!UICONTROL Success]** todavía no se actualiza. A continuación, la entrega de los mensajes de rebote suave se [reintenta](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) durante todo el período de validez del envío:

* Si un reintento se realiza correctamente antes del final del período de validez, el estado del mensaje permanece como **[!UICONTROL Sent]** y el porcentaje de **[!UICONTROL Success]** permanece sin cambios.

* De lo contrario, el estado cambia a **[!UICONTROL Failed]** y el porcentaje de **[!UICONTROL Success]** disminuye en consecuencia.

Por lo tanto, debe esperar hasta el final del período de validez para ver el porcentaje de **[!UICONTROL Success]** final y el número final de mensajes realmente **[!UICONTROL Sent]** y **[!UICONTROL Failed]**.

<!--The fact that the Success percentage will go to 100% very quickly indicates that your instance has been upgraded to the Enhanced MTA.-->

### Servicio de comentarios de correo electrónico (beta) {#email-feedback-service}

Con el servicio de comentarios de correo electrónico (SCCE), se informa del estado de cada correo electrónico con precisión, ya que los comentarios se capturan directamente desde el servidor de correo mejorado.

>[!IMPORTANT]
>
>El servicio de comentarios de correo electrónico está disponible actualmente como una funcionalidad beta.
>
>Si está interesado en participar en este programa beta, rellene [este formulario](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u) y le responderemos.

Una vez que se ha iniciado el envío, no se produce ningún cambio en el porcentaje de **[!UICONTROL Success]** cuando el mensaje se transmite correctamente de Campaign al servidor de correo mejorado.

<!--![](assets/efs-sending.png)-->

Los registros de envío muestran el estado **[!UICONTROL Taken into account by the service provider]** de cada dirección de destino.

<!--![](assets/efs-pending.png)-->

Cuando el mensaje se envía realmente a los perfiles objetivo y una vez que se transmite esta información en tiempo real desde el servidor de correo mejorado, los registros de envío muestran el estado **[!UICONTROL Sent]** para cada dirección que recibió el mensaje correctamente. El porcentaje de **[!UICONTROL Success]** se incrementa en consecuencia con cada envío correcto.

Cuando el servidor de correo mejorado devuelve mensajes de rebote duro, su estado de registro cambia de **[!UICONTROL Taken into account by the service provider]** a **[!UICONTROL Failed]**<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->.

Cuando los mensajes de rebote suaves vuelven a informarse desde el servidor de correo mejorado, su estado de registro permanece sin cambios (**[!UICONTROL Taken into account by the service provider]**): solo se actualiza[la razón de error](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->. El porcentaje de **[!UICONTROL Success]** permanece sin cambios. A continuación, se vuelven a intentar los mensajes de devolución suave a lo largo del [período de validez del envío](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period):

* Si un reintento se realiza correctamente antes del final del período de validez, el estado del mensaje cambia a **[!UICONTROL Sent]** y el porcentaje de **[!UICONTROL Success]** sube en consecuencia.

* De lo contrario, el estado cambia a **[!UICONTROL Failed]**. El porcentaje de **[!UICONTROL Success]** <!--and **[!UICONTROL Bounces + errors]** -->permanece sin cambios.

>[!NOTE]
>
>Para obtener más información acerca de las devoluciones suaves y duras, consulte [esta sección](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons).
>
>Para obtener más información sobre reintentos después de un error temporal de envío, consulte [esta sección](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure).


Las siguientes tablas muestran los cambios en los KPI y los estados de envío de registros introducidos por la capacidad de EFS.

**Con servicio de comentarios de correo electrónico**

| Paso en el proceso de envío | Resumen de KPI | Estado de envío de registros |
|--- |--- |--- |
| El mensaje se retransmite correctamente desde Campaign al servidor de correo mejorado | **[!UICONTROL Success]** no se muestra el porcentaje (comienza en 0 %) | El proveedor de servicios lo tiene en cuenta |
| Los mensajes de devolución dura se informan desde el servidor de correo mejorado | No hay cambios en el porcentaje de **[!UICONTROL Success]** | Error |
| Los mensajes de devolución suave se informan desde el servidor de correo mejorado | No hay cambios en el porcentaje de **[!UICONTROL Success]** | El proveedor de servicios lo tiene en cuenta |
| Los reintentos de mensajes de devolución suave se realizan correctamente | El porcentaje de **[!UICONTROL Success]** sube en consecuencia | Enviado |
| Error en los reintentos de mensajes de devolución suave | No hay cambios en el porcentaje de **[!UICONTROL Success]** | Error |

**Sin servicio de comentarios de correo electrónico**

| Paso en el proceso de envío | Resumen de KPI | Estado de envío de registros |
|--- |--- |--- |
| El mensaje se retransmite correctamente desde Campaign al servidor de correo mejorado | El porcentaje de **[!UICONTROL Success]** comienza en 100 % | Enviado |
| Los mensajes de devolución dura se informan desde el servidor de correo mejorado | El porcentaje de **[!UICONTROL Success]** baja en consecuencia | Error |
| Los mensajes de devolución suave se informan desde el servidor de correo mejorado | No hay cambios en el porcentaje de **[!UICONTROL Success]** | Enviado |
| Los reintentos de mensajes de devolución suave se realizan correctamente | No hay cambios en el porcentaje de **[!UICONTROL Success]** | Enviado | El porcentaje de **[!UICONTROL Success]** sube en consecuencia | Enviado |
| Error en los reintentos de mensajes de devolución suave | El porcentaje de **[!UICONTROL Success]** baja en consecuencia | Error |
