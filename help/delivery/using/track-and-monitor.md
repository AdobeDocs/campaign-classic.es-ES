---
title: Mensajes de seguimiento y monitorización
seo-title: Mensajes de seguimiento y monitorización
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '448'
ht-degree: 100%

---


# Seguimiento y monitorización {#track-and-monitor}

¿Ha hecho clic en el botón Enviar? Veamos qué pasa. Una vez entregado el envío, Adobe Campaign le permite realizar un seguimiento de los mensajes enviados y descubrir cómo reaccionan sus destinatarios al envío. Esto le ayudará a mejorar los envíos futuros y a optimizar sus próximas campañas.

## Seguimiento de entregas {#monitoring-deliveries}

Para controlar sus campañas, debe asegurarse de que el mensaje se haya enviado a sus destinatarios.

Desde el panel de envíos de Campaign, puede comprobar los mensajes procesados y los registros de auditoría de envíos.
También puede controlar el estado de los mensajes en los registros de envío. [Más información](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard).

¿Qué sucede si no se entregan los envíos y su estado sigue siendo **Pendiente**?

* El proceso de ejecución está esperando a que estén disponibles algunos recursos. Es posible que el MTA no se haya iniciado.
Compruebe que los módulos mta@instance se inicien en los servidores MTA y, si es necesario, inicie el módulo MTA. [Más información](../../production/using/administration.md).

* El envío puede estar utilizando una afinidad que no se ha configurado en la instancia remitente.
Sugerencia: Compruebe la configuración de la administración del tráfico (afinidad IP). Para obtener más información sobre esto, consulte Control del tráfico SMTP saliente.

>[!NOTE]
>
>Estos pasos solo los puede realizar un usuario experto.

## Seguimiento {#tracking-deliveries}

Para conocer mejor el comportamiento de sus destinatarios, puede rastrear cómo reaccionan a un envío: recepción, apertura, clics en enlaces, suscripciones, etc. En Campaign Classic, esta información se muestra en la pestaña Seguimiento de los destinatarios del envío y en la pestaña Seguimiento del envío. En Campaign Standard, se muestra en la pestaña Registros de seguimiento del envío.

**Sugerencia**: El seguimiento de mensajes está activado de forma predeterminada. Para configurar direcciones URL, seleccione la opción Mostrar direcciones URL en la sección inferior del asistente de envíos. Por cada dirección URL del mensaje, puede elegir si desea activar el seguimiento.

Para obtener más información sobre esto, consulte la sección [Configuración del seguimiento](../../delivery/using/how-to-configure-tracked-links.md) y la descripción de los [Indicadores de seguimiento](../../reporting/using/delivery-reports.md#tracking-indicators).

## Rendimiento de envíos {#delivery-performances}

Para medir la velocidad a la que se entregan los mensajes, puede controlar el rendimiento del envío. Los criterios son el número de mensajes enviados por hora y el tamaño de los mensajes (en bits por segundo). Para obtener más información sobre esto, consulte [Rendimiento de los envíos](../../reporting/using/global-reports.md#delivery-throughput).

**Sugerencias**:

* Evite mantener las entregas en estado de error en la instancia, ya que esto mantiene tablas temporales e influye en el rendimiento.

* Elimine los envíos que ya no sean necesarios y los destinatarios inactivos de la base de datos para mantener la calidad de la dirección.

* Evite programar entregas grandes al mismo tiempo. Tenga en cuenta que la carga puede tardar entre 5 y 10 minutos en propagarse uniformemente en el sistema.

## Solución de problemas de envío {#delivery-troubleshooting}

Se pueden realizar acciones específicas al encontrar problemas con envíos:

* [Problemas con entregas](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [Problemas de visualización de imágenes](../../production/using/image-display-issues.md)

* [Problemas de rendimiento de envíos](../../delivery/using/monitoring-a-delivery.md#performance_issues)

* [Problemas con archivos temporales](../../production/using/temporary-files.md): *solo clientes in situ*
