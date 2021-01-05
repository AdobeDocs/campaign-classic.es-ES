---
solution: Campaign Classic
product: campaign
title: Inicio de una nueva plataforma con Adobe Campaign Classic
description: Obtenga más información sobre la administración de la capacidad de envío al iniciar una nueva plataforma con Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: ht
source-git-commit: 6d5dbc16ed6c6e5a2e62ceb522e2ccd64b142825
workflow-type: ht
source-wordcount: '490'
ht-degree: 100%

---


# Inicio de una nueva plataforma {#starting-new-platform}

Mantener la reputación de su dominio y dirección IP es esencial al configurar una nueva plataforma.

* Comenzar a enviar correos electrónicos es un paso importante porque la plataforma no tiene historial de uso ni reputación cuando las direcciones IP de envío nunca se han utilizado para este fin.

* Los ISP sospechan naturalmente de las direcciones IP que nunca se han utilizado para enviar correos electrónicos y que de repente comienzan a enviar grandes volúmenes de tráfico de correo electrónico. De hecho, los remitentes de correo no deseado generalmente utilizan direcciones IP &quot;desconocidas&quot; (direcciones que nunca quedaron en la lista de bloqueados) para enviar la mayor cantidad posible de mensajes antes de la detección.

* No se puede esperar alcanzar la velocidad operativa en términos de salida al inicio de la fase de producción. Además, no debería intentar enviar mensajes a este ritmo, ya que podría llevar a los ISP a bloquear las direcciones de envío y comprometer seriamente el resto de la fase de inicio.

A continuación se enumeran los principios principales que deben seguirse al iniciar una nueva plataforma:

* Si tiene esta información, **importe direcciones no válidas en la tabla de cuarentenas**.
El inicio de una plataforma suele ocurrir cuando se utiliza una lista de direcciones por primera vez y puede que no esté completamente cualificada. Si envía a direcciones no válidas o a direcciones de honeypot, esto contribuye a disminuir la reputación de la plataforma.

   * Si tiene una lista de direcciones no válidas, lo mejor es importarla a la tabla de cuarentena (disponible mediante el menú **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**) antes de enviarla por primera vez.
   * Si, al mismo tiempo, desea recalificar las direcciones no válidas, es preferible hacerlo una vez que se establezca la reputación de la plataforma y poco a poco para &quot;diluir&quot; el uso de direcciones incorrectas con el tiempo.

   Para obtener más información sobre esto, consulte [Optimización del envío mediante cuarentenas](../../delivery/using/understanding-quarantine-management.md#optimizing-your-delivery-through-quarantines).
* **Limite la velocidad de rendimiento** limitando el número de equipos. Para obtener más información sobre cómo ajustar esta configuración técnica, póngase en contacto con el administrador de Adobe Campaign.
* **Aumente progresivamente los volúmenes enviados** para evitar ser marcados como correo no deseado. Evite asignar toda la base de datos desde el mismo inicio; sino, añada una fracción adicional de la lista cada vez que envíe. Esto debería permitirle aumentar el volumen en cada paso y reducir al mismo tiempo la tasa global de direcciones no válidas. Para garantizar un desarrollo fluido de la fase de inicio, puede utilizar olas. Para obtener más información, consulte [Envío mediante varias olas](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).
* **Envíe regularmente**. En cierta medida, es mejor enviar pequeñas tomas con regularidad que grandes campañas esporádicamente.
* **Preste mucha atención a los informes de envío**. Los indicadores de error altos pueden significar que una configuración técnica está mal configurada. Para obtener más información sobre esto, consulte [Monitorización de un envío](../../delivery/using/about-delivery-monitoring.md).

**Temas relacionados**:
* [Aumente su reputación de correo electrónico con el calentamiento de IP](https://helpx.adobe.com/es/campaign/kb/increase-email-rep-ip-warming.html)
* [Todo acerca de las trampas de correo no deseado](https://helpx.adobe.com/es/campaign/kb/spam-traps.html)