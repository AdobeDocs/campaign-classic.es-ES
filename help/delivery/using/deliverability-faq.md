---
title: Puntos clave a la hora de administrar la entrega en Adobe Campaign Classic
description: ¿Cuáles son los puntos clave que hay que comprobar al administrar la capacidad de entrega en Adobe Campaign Classic?
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2aad7e586b83bbb6c7b4233e9844e038802f50d7
workflow-type: tm+mt
source-wordcount: '1301'
ht-degree: 12%

---


# Solución de problemas de entrega{#deliverability-faq}

¿Está experimentando un problema de entrega? Puede encontrar la solución aquí.

## Error de regla MX {#mx-rule-error}

**¿Qué significa el mensaje de error &#39;cuotas satisfechas&#39;?**

Este mensaje indica que ha alcanzado el límite de cuotas para un MX específico y que tiene que esperar para poder enviar otro correo electrónico a este proveedor.

En Adobe Campaign, existe una configuración relacionada con el número de correos electrónicos por hora que pueden enviarse. Esta configuración debe utilizarse con cautela, ya que el número definido en la instancia hace referencia al número de conexiones realizadas con el ISP y no al número de correos electrónicos realmente enviados.

Esto significa que una conexión puede utilizar una regla MX sin enviar correctamente un correo electrónico. En este caso, una configuración con una dirección IP o un dominio con una baja reputación debe probar varias conexiones antes de enviar un correo electrónico. Por cada intento, se gasta un crédito de messages per hour (mensajes por hora). Como resultado, el rendimiento de la campaña de marketing se ve afectado de forma significativa.

Así que &#39;cuotas cumplidas&#39; no es solamente un problema de configuración, sino que también puede estar vinculado a la reputación. Es importante analizar los mensajes de error del “log” SMTP.

For more on MX configuration, see the [detailed documentation](../../installation/using/email-deliverability.md#mx-configuration).

## El mismo mensaje de error para un ISP {#same-error-for-an-isp}

**¿Por qué siempre recibo el mismo mensaje de error para un ISP en particular?**

Si siempre recibe el mismo mensaje de error para un ISP, es posible que el ISP haya detectado un error en su dirección de correo electrónico o IP. Lleve a cabo las siguientes recomendaciones:
* Compruebe si recibe un gran porcentaje de errores vinculados a direcciones de correo electrónico inexistentes (errores desconocidos **del** usuario).
* Actualice los formularios de suscripción para detectar cualquier error en los nombres de dominio introducidos (por ejemplo: gmaul.com o yaho.com).
* Si nota errores que indican que sus mensajes están declarados como correo no deseado o que sus mensajes están bloqueados constantemente, intente excluir los destinatarios que no han abierto o hecho clic en uno de sus mensajes en los últimos 12 meses desde el destinatario.

Si el problema persiste, póngase en contacto con los servicios comerciales o de entrega, con Adobe Campaign Client Care o con la asistencia de Adobe Campaign.

## Lista negra versus cuarentena {#blacklisting-versus-quarantine}

* **¿Cuál es la diferencia entre una dirección de correo electrónico en la lista negra y una dirección de correo electrónico en cuarentena?**

   * El estado **[!UICONTROL Blacklisted]** es el resultado de un bucle de retroalimentación (cuando una persona informa un mensaje como correo no deseado).

   * El estado **[!UICONTROL Quarantined]** es el resultado de un rebote suave o fuerte.
   For more on this, see this [section](../../delivery/using/understanding-quarantine-management.md#quarantine-vs-blacklisting).

* **¿Qué significan las diferentes razones de error de cuarentena?**

   Estas son 10 razones posibles: no definido, usuario desconocido, dominio inválido, dirección en la lista negra, rechazado, error omitido, inaccesible, cuenta deshabilitada, buzón lleno, no conectado.

   For more on this, see [Understanding quarantine management](../../delivery/using/understanding-quarantine-management.md).

## Anular la lista negra {#unblacklisting}

* **Uno de mis destinatarios fue en la lista negra por error. ¿Cómo puedo desbloquearlos para que pueda enviar mensajes de nuevo con inicio?**

   * Vaya a **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**.
   * En los detalles del registro correspondiente, establezca el valor del **[!UICONTROL Status]** campo en **[!UICONTROL Valid]**.
   * Guarde el registro.

* **¿Cómo puedo averiguar si una de mis IP es en la lista negra? ¿Cómo desbloqueo mis IP?**

   Para comprobar si su dirección IP está en la lista negra, puede utilizar varios sitios Web para verificarla:
   * https://mxtoolbox.com/
   * https://whatismyipaddress.com/blacklist-check
   * https://www.blacklistalert.org/
   Generalmente, el resultado de la comprobación de la dirección IP devolverá una lista que contiene detalles de la lista negra y también el nombre del sitio Web que en la lista negra la dirección IP.

   Al hacer clic en el vínculo correspondiente, puede acceder a los detalles del sitio Web. A continuación, puede solicitar que el sitio web se elimine del sitio web que haya en la lista negra la dirección IP.

   >[!NOTE]
   >
   >El proceso de supresión de nombres de la lista puede variar según el sitio web. Algunos sitios requieren que cree una cuenta, mientras que otros solo necesitan que proporcione la dirección IP.

## Prácticas recomendadas {#best-practices}

### Identificar un problema de entrega {#identify-deliverability-issue}

* Métricas de correo o campaña: las tasas de cancelación de suscripción/abuso de queja/devolución son más altas de lo habitual.
* actividad del suscriptor: las aperturas/clics/transacciones son inferiores a lo habitual.
* Las cuentas de inicialización muestran los correos filtrados o no entregados.

### Causas potenciales de hipotecas {#potential-causes}

* ¿Hubo un cambio reciente en la segmentación de listas?
* ¿He adquirido fuentes de datos nuevas?
* ¿He enviado accidentalmente un archivo de cuarentena?
* ¿Podría deberse el problema al contenido de mi mensaje?
* ¿Envio correos con la frecuencia suficiente para mantener IP calientes?
* ¿Estoy segmentando mis correos por actividad/participación o enviando archivos completos?
* ¿Cuál es el segmento &#39;seguro&#39; de mi archivo en términos de actualización?
* ¿Tengo estrategias de reactivación y reconfirmación para segmentos que no están definidos como seguros?

### Abordar el problema {#address-issue}

**Reclamaciones**

Las quejas son definidas por los suscriptores que pulsan el botón &quot;esto es spam&quot;. Si su problema de envío fue causado por quejas, debe intentar determinar por qué los destinatarios se quejan. Es posible que los clientes con altas tasas de quejas también deseen cambiar el vínculo de cancelación de suscripción a la parte superior de su correo electrónico para animar a los suscriptores que han decidido hacer clic en el botón de spam a darse de baja en lugar de quejarse.

Los remitentes pueden obtener una gran cantidad de información a partir de sus quejas sobre el bucle de retroalimentación. Es importante agrupar los datos y buscar patrones en elementos como la fuente de inclusión, cuánto tiempo se ha suscrito la dirección o incluso ciertas características demográficas del comportamiento. Las quejas pueden identificar a menudo una fuente de datos o un segmento riesgosos dentro del archivo. Se define el riesgo como el más propenso a quejarse, lo que puede dañar la reputación y, a su vez, las tasas de entrada.

Las quejas también provienen de suscriptores que ya no quieren recibir correo electrónico. Esto a menudo puede deberse a mensajes excesivos, a su percepción del mensaje, a que no esperaban el mensaje o no recordaban adhesión. También es importante ejecutar una auditoría para asegurarse de que todos los puntos de recopilación están claros y de que no hay casillas premarcadas en los puntos de adquisición. También debe enviar un correo electrónico de bienvenida cuando los suscriptores opten por establecer el tono y explicar la frecuencia con la que pueden esperar recibir mensajes de correo electrónico de su parte.

**Validez de los datos**

Las devoluciones se producen cuando se envía a una dirección no entregable en un ISP. Una dirección puede no entregarse por muchas razones, como una dirección mal escrita, una lista incorrecta o una fuente de datos, o bien, puede enviarse a una dirección que estuvo activa en un momento determinado, pero que se cerró o finalizó después de un período de inactividad. Si se encuentra con una rebotancia alta, es importante revisar la lista. Si procede de un nuevo origen, revise cómo se recopilaron las direcciones y asegúrese de que haya permisos. Los datos incorrectos también pueden provenir de direcciones mal escritas. Esto se puede solucionar con un servicio de validación de datos en tiempo real o requiriendo una opción de inclusión confirmada antes de enviar correos electrónicos de marketing a esa dirección.

**Participación**

Además de las quejas y la validez de los datos, los proveedores de servicios de Internet se concentran más que nunca en la participación positiva para tomar decisiones de envío. Están buscando ver si sus suscriptores están abriendo sus correos electrónicos o eliminándolos sin leerlos. Dado que no comparten estos datos con los remitentes, debemos utilizar la información que tenemos disponible y traducir aperturas/clics/transacciones como participación.

Como parte del mantenimiento continuo de la reputación, es importante comprender cómo los suscriptores comprometidos están en su lista y desarrollar una jerarquía de riesgo de actualización para los suscriptores de cada archivo. La actualización se define como la última fecha de apertura/clic/transacción o de registro. Este intervalo de tiempo puede variar en función de la vertical. Determinar segmentos activos (&quot;seguros&quot;) para cada vertical. Generalmente son suscriptores que han estado activos en los últimos 3-6 meses.

Reducir la frecuencia a inactives. Cree una serie de recontratación para los inactivos de riesgo moderado. Generalmente, esto es de 6 a 9 meses sin compromiso. Desarrollar una campaña de reconfirmación para los inactivos de mayor riesgo. Generalmente son suscriptores que no han interactuado con un correo electrónico en 9-12 meses. Por último, debe establecer una regla desplegable y eliminar los suscriptores que no se hayan abierto en &quot;x&quot; meses. Normalmente recomendamos más de 12 meses, pero esto puede variar en función del ciclo de ventas y compras.

For more on re-engagement, see [this section](../../delivery/using/re-engagement-best-practices.md).
