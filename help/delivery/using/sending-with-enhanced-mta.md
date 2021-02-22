---
solution: Campaign Classic
product: campaign
title: Envío con el MTA mejorado en Adobe Campaign Classic
description: Obtenga información sobre el alcance y las características específicas del envío de correos electrónicos con Adobe Campaign Enhanced MTA.
audience: delivery
content-type: reference
topic-tags: sending-emails
translation-type: tm+mt
source-git-commit: c64b6eccd0ad45ebcf4ecc18150f4409f5c66bc2
workflow-type: tm+mt
source-wordcount: '1880'
ht-degree: 5%

---


# Envío con el MTA mejorado {#sending-with-enhanced-mta}

El **MTA mejorado de Adobe Campaign** (Agente de transferencia de correo) proporciona una infraestructura de envío mejorada que permite una mejor capacidad de entrega, reputación, rendimiento, sistema de informes, gestión de devoluciones, ampliación de IP y administración de la configuración de conexión.

Se implementa para mejorar la escalabilidad, aumentar el rendimiento del envío y ayudar a enviar más correos electrónicos más rápido. Esto se logra con las nuevas técnicas de envío adaptable que modifican la configuración del envío de correo electrónico en tiempo real en función de los comentarios de los Proveedores de servicio de Internet.

>[!IMPORTANT]
>
>El MTA mejorado de Adobe Campaign solo está disponible para clientes alojados por Campaign Classic o híbridos. Las instalaciones in situ del Campaign Classic no se pueden actualizar para utilizar el MTA mejorado.

Si se le proporcionó una instancia de Campaign Classic después de septiembre de 2018, está utilizando el MTA mejorado. Para todos los demás clientes Campaign Classic, consulte las [preguntas más frecuentes](#enhanced-mta-faq) a continuación.

La implementación de MTA mejorada puede afectar a algunas de las funcionalidades de Campaña existentes. Para obtener más información sobre esto, consulte las [especificidades de MTA mejoradas](#enhanced-mta-impacts).

>[!NOTE]
>
>Si es un usuario final de Adobe Campaign y desea saber si su instancia se ha actualizado a la MTA mejorada, póngase en contacto con el administrador de Campañas internas.

## Preguntas frecuentes {#enhanced-mta-faq}

### Uso y beneficios

**¿Qué es el MTA mejorado?**

Ahora se puede actualizar Adobe Campaign para que utilice un nuevo MTA (Agente de transferencia de correo) que ejecute MTA de correo electrónico comercial de SparkPost denominado **Momentum**.

El impulso representa una tecnología MTA innovadora y de alto rendimiento que incluye una gestión de devoluciones más inteligente y una capacidad de optimización de la entrega automatizada que ayuda a los remitentes a lograr y mantener tasas de envío de entrada óptimas. <!--More than 37% of the world’s business email is sent using SparkPost’s MTA technology.-->

**¿Cuáles son los beneficios?**

* Los clientes de Adobe Campaign que utilizan el MTA mejorado han experimentado un <!--300%-->aumento masivo en la velocidad de rendimiento general y una <!--90%+-->reducción significativa en devoluciones en blanco.
* El MTA mejorado utiliza la tecnología MTA más reciente para proporcionarle las velocidades de rendimiento óptimas para su envío de correo electrónico.
* Al adaptarse instantánea y automáticamente a los comentarios que recibe, también garantiza un envío de correo electrónico más preciso e inteligente con los datos de envío en tiempo real.

**¿Puedo usar el MTA nativo de Adobe Campaign y el MTA mejorado al mismo tiempo?**

No. Solo se puede usar el MTA mejorado para los envíos de correo electrónico después de actualizar la instancia.

<!--
**Is there a fee associated with upgrading my instance to and subsequent use of the Enhanced MTA?**
No, there is no extra fee associated with the upgrade process to enable the use of the Enhanced MTA.

**When will the Enhanced MTA be available to me?**

* If you are new to Adobe Campaign Classic, you are already using the Enhanced MTA.

* For Adobe Campaign Classic existing customers, we’ve implemented a phased rollout that covers all hosted or partially hosted (hybrid) instances. If you’re not already using it, we’ll be contacting you in the near future with the dates and details for upgrading your Adobe Campaign Classic instances to the Enhanced MTA.
-->

### Actualización al MTA mejorado

**¿Qué se necesita para actualizar al MTA mejorado?**

Si se le proporcionó una instancia de Campaign Classic después de septiembre de 2018, no se requiere ninguna acción, ya que ya está utilizando el MTA mejorado.

Para todos los demás clientes alojados o alojados parcialmente (híbridos), el equipo de Adobe Campaign se pondrá en contacto para coordinar una fecha para la migración y proporcionará detalles sobre los pasos necesarios para la migración.

>[!IMPORTANT]
>
>El MTA mejorado no está disponible para instalaciones in situ.

**¿Cuál es el proceso para actualizar mi instancia al MTA mejorado?**

Todo el proceso de las instancias hospedadas requiere unos minutos de tiempo de inactividad. Adobe supervisará el rendimiento y la capacidad de entrega del correo electrónico durante un máximo de 24 horas después de la actualización para evaluar cualquier impacto en sus envíos de correo electrónico.

Si se detecta algún problema, Adobe puede revertir su instancia de forma rápida y temporal a la MTA nativa de Adobe Campaign.

Actualmente, el MTA mejorado solo afecta al canal de correo electrónico. Las notificaciones push y los envíos SMS seguirán utilizando la MTA de Campaña nativa y no se verán afectados por la actualización.

**¿Debo volver a pasar por el calentamiento de la IP después de actualizar al MTA mejorado?**

No. La actualización no requiere cambiar a direcciones IP nuevas, por lo que puede seguir usando las direcciones IP de correo electrónico calentadas existentes.

**¿Afectará la actualización al MTA mejorado a cualquier campaña o envío que se encuentre en curso?**

Cualquier envío que se haya preparado antes de actualizar la instancia para utilizar el MTA mejorado deberá volver a prepararse para poder usar correctamente el nuevo MTA.

Para los clientes que utilizan la funcionalidad de mensajería transaccional de Adobe Campaign, cualquier llamada de API al déclencheur de un mensaje de correo electrónico se pondrá en cola durante el corto tiempo de inactividad de la actualización y se intentará cuando se complete la actualización.

## Especificaciones de MTA mejoradas {#enhanced-mta-impacts}

### Encabezados MTA mejorados

Las últimas instancias de Campaign Classic incluyen código que agrega los encabezados MTA mejorados necesarios a cada mensaje. Si utiliza Adobe Campaign 19.1 (compilación 9032) o superior y no es el caso, debe agregar el parámetro &quot;useMomentum=true&quot; a la configuración de la instancia de marketing (en el archivo [serverConf.xml](../../installation/using/the-server-configuration-file.md#mta)).

Sin embargo, si está utilizando una instancia anterior que no incluye este código, se debe agregar una nueva reglas de tipología denominada **[!UICONTROL Typology Rule for Enhanced MTAs]** a todas las tipologías existentes en la instancia de Campaña.
Esta regla se agrega mediante un paquete **[!UICONTROL Typology]** instalado como parte de la actualización al MTA mejorado.

>[!IMPORTANT]
>
>Si ve esta reglas de tipología en sus tipologías, no la elimine ni la modifique de ninguna manera. De lo contrario, sus envíos de correo electrónico podrían verse afectados negativamente.

Este paquete **[!UICONTROL Typology]** debe instalarse en la instancia de mercadotecnia de Adobe Campaign.

Si usted es un cliente híbrido, el equipo de Adobe Campaign le proporcionará instrucciones sobre cómo instalar el paquete **[!UICONTROL Typology]** en su instancia de mercadotecnia como parte de la actualización al MTA mejorado. Póngase en contacto con el ejecutivo de cuentas para obtener las instrucciones completas.

>[!IMPORTANT]
>
>Las instrucciones proporcionadas por el equipo de Adobe Campaign sobre cómo instalar el paquete **[!UICONTROL Typology]** deben seguirse cuidadosamente. De lo contrario, podría encontrar problemas importantes con las direcciones IP utilizadas para enviar correos electrónicos.

Para obtener más información sobre las tipologías, consulte [esta sección](../../campaign/using/about-campaign-typologies.md).

### Nuevas reglas MX

Ya no se utilizan las reglas de rendimiento del envío de administración MX. El MTA mejorado tiene sus propias reglas MX que le permiten personalizar el rendimiento por dominio en función de su propia reputación histórica de correo electrónico y de los comentarios en tiempo real procedentes de los dominios a los que envía correos electrónicos.

Para saber más sobre la configuración MX, consulte [esta sección](../../installation/using/email-deliverability.md#mx-configuration).

### Calificación de devolución

Las cualificaciones de devoluciones de la tabla de Campaña **[!UICONTROL Delivery log qualification]** ya no se utilizan para los mensajes de error de error de envío **sincrónico**. El MTA mejorado determina el tipo de rechazo y la calificación, y envía esa información a Campaign.

>[!NOTE]
>
>El MTA mejorado califica el rebote SMTP y devuelve esa cualificación a la Campaña en forma de código de rebote asignado a un motivo y calificación de rebote de Campaña.

Para obtener más información sobre la calificación de devoluciones, consulte [esta sección](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification).

### Rendimiento de entrega

El gráfico de rendimiento del Envío de Campaña ya no mostrará el rendimiento de los destinatarios de correo electrónico. Ese gráfico ahora mostrará la velocidad de transferencia para el reenvío de sus mensajes desde la Campaña hasta el MTA mejorado.

Para obtener más información sobre el rendimiento del envío, consulte [esta sección](../../reporting/using/global-reports.md#delivery-throughput).

### Período de validez

La configuración del período de validez de los envíos de Campaña será utilizada por el MTA mejorado sólo si se establece en **3,5 días o menos**. Si define un valor superior a 3,5 días de Campaña, no se tendrá en cuenta.

Por ejemplo, si el período de validez se establece en el valor predeterminado de 5 días de Campaña, los mensajes de devolución en pantalla se incluirán en la cola de reintentos de MTA mejorada y se volverán a intentar durante un máximo de 3,5 días a partir de la fecha en que el mensaje llegue al MTA mejorado. En ese caso, no se utilizará el valor establecido en la Campaña.

Una vez que un mensaje ha estado en la cola de MTA mejorada durante 3,5 días y no se ha podido entregar, se agotará el tiempo de espera y se actualizará su estado de **[!UICONTROL Sent]** a **[!UICONTROL Failed]** en los registros de entregas.

Para obtener más información sobre el período de validez, consulte [esta sección](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period).

### Firma de DKIM

La autenticación por correo electrónico de DKIM (DomainKeys Identified Mail) se realiza mediante el MTA mejorado. La firma de DKIM por parte del MTA de Campaign nativo se desactiva en la tabla de administración Domain management como parte de la actualización de MTA mejorada.
Para obtener más información sobre DKIM, consulte [esta sección](../../delivery/using/technical-recommendations.md#dkim).

### Sistema de informes de éxito de envío

En la vista **[!UICONTROL Summary]** de un envío de correo electrónico [panel](../../delivery/using/delivery-dashboard.md), el inicio **[!UICONTROL Success]** se eleva al 100% y luego se desciende progresivamente a lo largo del período de validez [envío](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period), a medida que los rebotes no deseados y duros se informan desde el MTA mejorado a la Campaña.

De hecho, todos los mensajes se muestran como **[!UICONTROL Sent]** en los [registros de envío](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history) en cuanto se retransmiten correctamente desde la Campaña al MTA mejorado. Permanecen en ese estado a menos o hasta que un [rebote](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons) para ese mensaje se comunique de vuelta del MTA mejorado a la Campaña.

Cuando se generan informes de los mensajes de rebote desde el MTA mejorado, su estado cambia de **[!UICONTROL Sent]** a **[!UICONTROL Failed]** y el porcentaje **[!UICONTROL Success]** disminuye en consecuencia.

Cuando los mensajes de devolución en pantalla vuelven a informarse desde el MTA mejorado, siguen mostrándose como **[!UICONTROL Sent]** y el porcentaje **[!UICONTROL Success]** aún no se ha actualizado. A continuación, los mensajes de rebote en pantalla se [reintentan](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) durante todo el período de validez del envío:

* Si un reintento se realiza correctamente antes del final del período de validez, el estado del mensaje permanece como **[!UICONTROL Sent]** y el porcentaje **[!UICONTROL Success]** permanece sin cambios.

* De lo contrario, el estado cambia a **[!UICONTROL Failed]** y el porcentaje **[!UICONTROL Success]** disminuye en consecuencia.

Por lo tanto, debe esperar hasta el final del período de validez para ver el porcentaje final **[!UICONTROL Success]** y el número final de mensajes **[!UICONTROL Sent]** y **[!UICONTROL Failed]**.

<!--The fact that the Success percentage will go to 100% very quickly indicates that your instance has been upgraded to the Enhanced MTA.-->

### Servicio de comentarios de correo electrónico (beta) {#email-feedback-service}

Con la capacidad del servicio de comentarios de correo electrónico (EFS), el estado de cada correo electrónico se informa con precisión, ya que los comentarios se capturan directamente desde el MTA mejorado (Agente de transferencia de mensajes).

>[!IMPORTANT]
>
>El servicio de comentarios de correo electrónico está disponible actualmente como una capacidad beta.
>
>Si está interesado en participar en este programa beta, rellene [este formulario](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u) y le responderemos.

Una vez que se ha iniciado el envío, no se produce ningún cambio en el porcentaje **[!UICONTROL Success]** cuando el mensaje se transmite correctamente de la Campaña al MTA mejorado.

<!--![](assets/efs-sending.png)-->

Los registros de envío muestran el estado **[!UICONTROL Taken into account by the service provider]** de cada dirección de destino.

<!--![](assets/efs-pending.png)-->

Cuando el mensaje se envía realmente a los perfiles objetivo y una vez que esta información se reporta en tiempo real desde el MTA mejorado, los registros de envío muestran el estado **[!UICONTROL Sent]** de cada dirección que recibió el mensaje correctamente. El porcentaje **[!UICONTROL Success]** se incrementa en consecuencia con cada envío exitoso.

Cuando los mensajes de devolución en firme se devuelven desde el MTA mejorado, su estado de registro cambia de **[!UICONTROL Taken into account by the service provider]** a **[!UICONTROL Failed]**<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->.

Cuando los mensajes de devolución en pantalla vuelven a informarse desde el MTA mejorado, su estado de registro permanece sin cambios (**[!UICONTROL Taken into account by the service provider]**): sólo se actualiza[razón de error](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->. El porcentaje **[!UICONTROL Success]** permanece sin cambios. A continuación, se vuelven a intentar los mensajes de devolución en pantalla a lo largo del envío [período de validez](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period):

* Si un reintento se realiza correctamente antes del final del período de validez, el estado del mensaje cambia a **[!UICONTROL Sent]** y el porcentaje **[!UICONTROL Success]** se incrementa en consecuencia.

* De lo contrario, el estado cambia a **[!UICONTROL Failed]**. El porcentaje **[!UICONTROL Success]** <!--and **[!UICONTROL Bounces + errors]** -->permanece sin cambios.

>[!NOTE]
>
>Para obtener más información acerca de las devoluciones en bruto y en blanco, consulte [esta sección](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons).
>
>Para obtener más información sobre reintentos después de un error temporal de envío, consulte [esta sección](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure).


Las siguientes tablas muestran los cambios en los KPI y los estados de envío de registros introducidos por la capacidad de EFS.

**Con servicio de comentarios de correo electrónico**

| Paso en el proceso de envío | Resumen de KPI | Estado de envío de registros |
|--- |--- |--- |
| El mensaje se retransmite correctamente desde la Campaña al MTA mejorado | **[!UICONTROL Success]** no se muestra el porcentaje (inicios en 0 %) | Tenido en cuenta por el proveedor de servicios |
| Los mensajes de devolución del hardware se informan desde el MTA mejorado | No hay cambios en el porcentaje **[!UICONTROL Success]** | Error |
| Los mensajes de devolución en pantalla se informan desde el MTA mejorado | No hay cambios en el porcentaje **[!UICONTROL Success]** | Tenido en cuenta por el proveedor de servicios |
| Los reintentos de mensajes de devolución en pantalla se realizan correctamente | **[!UICONTROL Success]** el porcentaje se incrementa en consecuencia | Enviado |
| Fallan los reintentos de mensajes de devolución en pantalla | No hay cambios en el porcentaje **[!UICONTROL Success]** | Error |

**Sin servicio de comentarios de correo electrónico**

| Paso en el proceso de envío | Resumen de KPI | Estado de envío de registros |
|--- |--- |--- |
| El mensaje se retransmite correctamente desde la Campaña al MTA mejorado | **[!UICONTROL Success]** inicios porcentuales en 100% | Enviado |
| Los mensajes de devolución del hardware se informan desde el MTA mejorado | **[!UICONTROL Success]** el porcentaje disminuye en consecuencia | Error |
| Los mensajes de devolución en pantalla se informan desde el MTA mejorado | No hay cambios en el porcentaje **[!UICONTROL Success]** | Enviado |
| Los reintentos de mensajes de devolución en pantalla se realizan correctamente | No hay cambios en el porcentaje **[!UICONTROL Success]** | Enviado | **[!UICONTROL Success]** el porcentaje se incrementa en consecuencia | Enviado |
| Fallan los reintentos de mensajes de devolución en pantalla | **[!UICONTROL Success]** el porcentaje disminuye en consecuencia | Error |
