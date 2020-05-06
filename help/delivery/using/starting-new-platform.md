---
title: Inicio de una nueva plataforma con Adobe Campaign Classic
description: Obtenga más información sobre la administración de la capacidad de envío al iniciar una nueva plataforma con Adobe Campaign Classic.
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
source-git-commit: a1192bc804e752d13af869da66ba0505c077ed19
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 34%

---


# Inicio de una nueva plataforma {#starting-new-platform}

Mantener la reputación de su dominio y dirección IP es esencial al configurar una nueva plataforma.

* Comenzar a enviar correos electrónicos es un paso importante porque la plataforma no tiene historial de uso y, cuando las IP que envían nunca se han utilizado para este propósito, no tiene reputación.

* Los ISP sospechan naturalmente de las direcciones IP que nunca se han utilizado para enviar correos electrónicos y que de repente comienzan a enviar grandes volúmenes de tráfico de correo electrónico. De hecho, los remitentes de spam suelen utilizar direcciones IP &quot;desconocidas&quot; (direcciones que nunca se han en la lista negra) para enviar el mayor número posible de mensajes antes de la detección.

* No se puede esperar alcanzar la velocidad operativa en términos de salida al inicio de la fase de producción. Además, no debería intentar enviar mensajes a este ritmo, ya que podría llevar a los ISP a bloquear las direcciones de envío y comprometer seriamente el resto de la fase de inicio.

A continuación se enumeran los principios principales que deben seguirse al iniciar una nueva plataforma:

* Si tiene esta información, **importe direcciones no válidas en la tabla**de cuarentenas.
El inicio de una plataforma suele ocurrir cuando se utiliza una lista de direcciones por primera vez y puede que no esté completamente cualificada. Si envía a direcciones no válidas o a direcciones de honeypot, esto contribuirá a disminuir la reputación de la plataforma.

   * If you have a list of invalid addresses, it is in your best interests to import it into the quarantine table (available through the **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** menu) before sending for the first times.
   * Si, al mismo tiempo, desea recalificar las direcciones no válidas, es preferible hacerlo una vez que se establezca la reputación de la plataforma y poco a poco para &quot;diluir&quot; el uso de direcciones incorrectas con el tiempo.
   Para obtener más información sobre esto, consulte [Optimización del envío mediante cuarentenas](../../delivery/using/understanding-quarantine-management.md#optimizing-your-delivery-through-quarantines).
* **Limite la velocidad** de rendimiento limitando el número de equipos. Para obtener más información sobre cómo ajustar esta configuración técnica, póngase en contacto con el administrador de Adobe Campaign.
* **Aumente progresivamente los volúmenes enviados** para evitar ser marcados como spam. No destinatario toda la base de datos desde el mismo inicio, sino que agrega una fracción adicional de la lista cada vez que envía. Esto debería permitirle aumentar el volumen en cada paso y reducir al mismo tiempo la tasa global de direcciones no válidas. Para garantizar un desarrollo fluido de la fase de inicio, puede utilizar olas. For more on this, see [Sending using multiple waves](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).
* **Enviar regularmente**. En cierta medida, es mejor enviar pequeñas tomas con regularidad en lugar de grandes campañas esporádicamente.
* **Preste mucha atención a los informes de envío**. Los indicadores de error altos pueden significar que una configuración técnica está mal configurada. Para obtener más información sobre esto, consulte [Monitoreo de un envío](../../delivery/using/monitoring-a-delivery.md).

**Temas relacionados**:
* [Aumente su reputación de correo electrónico con el calentamiento de IP](https://helpx.adobe.com/campaign/kb/increase-email-rep-ip-warming.html)
* [Todo acerca de las trampas de spam](https://helpx.adobe.com/campaign/kb/spam-traps.html)