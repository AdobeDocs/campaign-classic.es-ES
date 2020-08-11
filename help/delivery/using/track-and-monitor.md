---
title: Seguimiento y supervisión de mensajes
seo-title: Seguimiento y supervisión de mensajes
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5e6ecd636ee0b2199808c03b2fd898a194f0c1ea
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 9%

---


# Seguimiento y monitorización {#track-and-monitor}

¿Ha hecho clic en el botón Enviar? Veamos qué pasa. Una vez enviado el envío, Adobe Campaign le permite realizar un seguimiento de los mensajes enviados y descubrir cómo reaccionan sus destinatarios al envío. Esto le ayudará a mejorar el envío futuro y a optimizar sus próximas campañas.

## Seguimiento de entregas {#monitoring-deliveries}

Para controlar sus campañas, debe asegurarse de que el mensaje se ha enviado a sus destinatarios.

Desde el panel de envío de Campaña, puede comprobar los mensajes procesados y los registros de auditoría de envío.
También puede controlar el estado de los mensajes en los registros de envío. [Más información](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard).

¿Qué sucede si no se envían los envíos y su estado sigue siendo **Pendiente**?

* El proceso de ejecución está esperando la disponibilidad de algunos recursos. Es posible que el MTA no se haya iniciado.
Compruebe que los módulos mta@instance se inician en los servidores MTA y, si es necesario, inicio el módulo MTA. [Más información](../../production/using/administration.md).

* El envío puede estar utilizando una afinidad que no se ha configurado en la instancia de envío.
Sugerencia: Compruebe la configuración de la administración del tráfico (afinidad IP). Para obtener más información sobre esto, consulte Control del tráfico SMTP saliente.

>[!NOTE]
>
>Estos pasos sólo los puede realizar un usuario experto.

## Seguimiento {#tracking-deliveries}

Para conocer mejor el comportamiento de sus destinatarios, puede rastrear cómo reaccionan a un envío: recepción, apertura, clics en enlaces, suscripciones, etc. En Campaign Classic, esta información se muestra en la ficha Seguimiento de los destinatarios dirigidos por el envío y en la ficha Seguimiento del envío. En Campaign Standard, se muestra en la ficha Registros de seguimiento del envío.

**Sugerencia**: El seguimiento de mensajes está habilitado de forma predeterminada. Para configurar direcciones URL, seleccione la opción Mostrar direcciones URL en la sección inferior del asistente de envíos. Para cada dirección URL del mensaje, puede elegir si desea activar el seguimiento.

Para obtener más información sobre esto, consulte la sección [Configuración del seguimiento](../../delivery/using/how-to-configure-tracked-links.md) y la descripción de los indicadores [de](../../reporting/using/delivery-reports.md#tracking-indicators) seguimiento.

## Rendimiento de envíos {#delivery-performances}

Para medir la velocidad a la que se entregan los mensajes, puede controlar el rendimiento del envío. Los criterios son el número de mensajes enviados por hora y el tamaño de los mensajes (en bits por segundo). Para obtener más información sobre esto, consulte Rendimiento [de Envío](../../reporting/using/global-reports.md#delivery-throughput).

**Sugerencias**:

* Evite mantener las entregas en estado de error en la instancia, ya que esto mantiene tablas temporales e influye en el rendimiento.

* Elimine los envíos que ya no sean necesarios y los destinatarios inactivos de la base de datos para mantener la calidad de la dirección.

* Evite programar entregas grandes al mismo tiempo. Tenga en cuenta que la carga puede tardar entre 5 y 10 minutos en propagarse uniformemente sobre el sistema.

## Solución de problemas de envío {#delivery-troubleshooting}

Se pueden realizar acciones específicas al encontrar problemas con envíos:

* [Problemas de capacidad de entrega](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [Problemas de visualización de imágenes](../../production/using/image-display-issues.md)

* [Problemas de rendimiento de envío](../../delivery/using/monitoring-a-delivery.md#performance_issues)

* [Problemas](../../production/using/temporary-files.md) de archivos temporales: sólo clientes *in situ*
