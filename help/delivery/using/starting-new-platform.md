---
title: Inicio de una nueva plataforma con Adobe Campaign Classic
description: Obtenga más información sobre la administración de la capacidad de entrega al iniciar una nueva plataforma con Adobe Campaign Classic.
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
source-git-commit: 68756f920fbc8658cff552615adbf023b4c5e3aa

---


# Inicio de una nueva plataforma {#starting-new-platform}

Es esencial mantener la reputación de su dominio y dirección IP. A continuación encontrará algunos consejos para configurar una nueva plataforma.

Comenzar a enviar correos electrónicos en una nueva plataforma es un paso importante porque la plataforma no tiene historial de uso ni reputación (cuando las direcciones IP de envío nunca se han utilizado para este fin). Los ISP sospechan naturalmente de las direcciones IP que nunca se han utilizado para enviar correos electrónicos y que de repente comienzan a enviar grandes volúmenes de tráfico de correo electrónico. De hecho, los remitentes de spam generalmente utilizan direcciones IP &quot;desconocidas&quot; (es decir, direcciones que nunca se han bloqueado) para enviar el mayor número posible de mensajes antes de la detección.

No se puede esperar alcanzar la velocidad operativa en términos de salida al inicio de la fase de producción. Además, no debería intentar enviar mensajes a este ritmo, ya que podría llevar a los ISP a bloquear las direcciones de envío y comprometer seriamente el resto de la fase de inicio.

El inicio de una plataforma suele ocurrir cuando se utiliza una lista de direcciones por primera vez y puede que no esté completamente cualificada. Si envía a direcciones no válidas o a direcciones de Honeypot, esto contribuirá a disminuir la reputación de la plataforma. Si dispone de una lista de direcciones no válidas, conviene importarla en la tabla de cuarentena (**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**) antes de enviarla por primera vez. Si, al mismo tiempo, desea recalificar las direcciones no válidas, es preferible hacerlo una vez que se establezca la reputación de la plataforma y poco a poco para &quot;diluir&quot; el uso de direcciones incorrectas con el tiempo.

Resumir los principios que deben seguirse al iniciar:

* Importación de direcciones no válidas en la tabla de cuarentena (si tiene esta información)
* Limitación de la velocidad de rendimiento (configuración técnica: limitar el número de equipos)
* Aumento progresivo de los volúmenes enviados: No dirija toda la base de datos desde el principio, sino que agregue una fracción adicional de la lista cada vez que envíe; esto debería permitirle aumentar el volumen en cada paso y reducir al mismo tiempo la tasa global de direcciones no válidas
* Enviando con regularidad: En cierta medida, es mejor enviar pequeñas tomas con regularidad que las grandes campañas esporádicamente
* Prestando especial atención a los informes de envío: los indicadores de error altos pueden significar que una configuración técnica está mal configurada.