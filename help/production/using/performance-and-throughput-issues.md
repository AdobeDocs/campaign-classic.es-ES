---
product: campaign
title: Problemas de rendimiento y producción
description: Problemas de rendimiento y producción
feature: Monitoring
badge-v7-prem: label="On-premise/híbrido solo" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: fe69efda-a052-4f67-9c13-665f011d0a2b
source-git-commit: 6803b6628313db9108a191fd143dac68ee799149
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 13%

---

# Problemas de rendimiento y producción{#performance-and-throughput-issues}

En primer lugar, debe comprobar que tiene instalada la última compilación. Esto garantiza que dispone de las últimas funciones y correcciones de errores.

Consulte las [Notas de la versión](../../rn/using/latest-release.md) para obtener más información sobre el contenido de cada versión.

## Hardware e infraestructura {#hardware-and-infrastructure}

Las directrices generales para los requisitos de hardware para el Campaign Classic local se detallan en esta [página](https://helpx.adobe.com/es/campaign/kb/hardware-sizing-guide.html).

El equipo de consultoría puede proporcionar a los clientes alojados una herramienta que le permite ver fácilmente cuánto espacio utilizan varios tipos de tablas en la base de datos, así como el espacio utilizado en el sitio SFTP. Además, proporciona herramientas que le permiten limpiar datos innecesarios. Póngase en contacto con el Servicio de atención al cliente de [Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) si necesita implementar esta herramienta. A continuación se indican algunos aspectos importantes que se deben comprobar con esta herramienta:

* Si el tamaño del índice es mayor que el tamaño de la tabla, se requiere un vacío.
* Compruebe las tablas que tienen la hinchazón máxima. Si estas tablas se utilizan con frecuencia, es necesario aspirarlas.
* El bloqueo de bases de datos puede hacer que los correos electrónicos dejen de enviarse.

Adobe Campaign también proporciona una [herramienta](../../production/using/monitoring-processes.md#manual-monitoring) para comprobar el uso de la CPU y la RAM. Utilice esta herramienta y observe indicadores específicos como: **Memoria**, **Memoria de intercambio**, **Disco**, **Procesos activos**. Si los valores son demasiado altos, puede intentar reducir el número de flujos de trabajo o programar flujos de trabajo para que se inicien en momentos diferentes.

## Comprobación de base de datos {#database-performances}

La mayoría de las veces, los problemas de rendimiento están vinculados al mantenimiento de la base de datos. Estos son los elementos principales que se deben comprobar:

* Configuración: se recomienda comprobar la configuración inicial de la plataforma Adobe Campaign y ejecutar una comprobación completa del hardware.
* Instalación y configuración de la plataforma Adobe Campaign: compruebe la configuración de red y las opciones de envío de la plataforma.
* Database maintenance: asegúrese de que la tarea de limpieza de la base de datos esté operativa y de que el mantenimiento de la base de datos esté correctamente programado y ejecutado. Compruebe el número y el tamaño de las tablas de trabajo.
* Diagnóstico en tiempo real: compruebe los archivos de registro de procesos y plataformas y, a continuación, monitorice la actividad de la base de datos al volver a crear el problema.

>[!NOTE]
>
>Para obtener más información, consulte esta sección: [Rendimiento de la base de datos](../../production/using/database-performances.md).

## Configuración de aplicación {#application-configuration}

A continuación se muestra una lista de artículos relacionados con las prácticas recomendadas de configuración de la aplicación:

* Procesos y memoria MTA y MTAChild: el módulo **mta** distribuye mensajes a sus módulos secundarios **mtachild**. Cada **mtachild** prepara los mensajes antes de solicitar una autorización al servidor de estadísticas y enviarlos. Consulte esta [página](../../installation/using/email-deliverability.md) para obtener más información.
* Configuración de TLS: no se recomienda habilitar TLS globalmente porque puede reducir el rendimiento. En su lugar, la configuración de TLS por dominio, administrada por el equipo de entrega, debe ajustarse según las necesidades. Consulte esta [página](../../installation/using/email-deliverability.md#mx-configuration) para obtener más información.

  >[!NOTE]
  >
  >La participación del equipo de entregabilidad se basa en el contrato y los clientes deben ponerse en contacto con su representante de Adobe para obtener información relacionada con la participación en la entregabilidad.

* DKIM: para asegurar el nivel de seguridad del DKIM, 1024b es el tamaño de codificación recomendado por la práctica recomendada. La mayoría de los proveedores de acceso no consideran válidas las claves DKIM menores. Consulte [esta página](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=es#authentication).

## Problemas de entregas {#deliverability-issues}

A continuación se muestra una lista de prácticas recomendadas y artículos relacionados con la capacidad de entrega:

* Reputación de la IP: si la reputación de la IP no es lo suficientemente buena, el rendimiento se verá afectado. El módulo **Supervisión de la capacidad de envío** ofrece varias herramientas para rastrear el rendimiento de la capacidad de envío de su plataforma. Consulte [esta página](../../delivery/using/monitoring-deliverability.md).
* Preparación de la IP: la preparación de la IP la realiza el equipo de entrega. Esto implica aumentar gradualmente el número de correos electrónicos a través de nuevas direcciones IP durante un periodo de unas semanas.

  >[!NOTE]
  >
  >La participación del equipo de entregabilidad se basa en el contrato y los clientes deben ponerse en contacto con su representante de Adobe para obtener información relacionada con la participación en la entregabilidad.

* Configuración de afinidad IP: una configuración de afinidad IP incorrecta puede detener por completo los correos electrónicos (nombre de operador/afinidad incorrecto en la configuración) o reducir el rendimiento (pequeño número de IP en la afinidad). Consulte [esta página](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).
* Tamaño del correo electrónico: el tamaño del correo electrónico desempeña un papel importante en el rendimiento. El tamaño de correo electrónico máximo recomendado es de 60 KB. Consulte esta [página](https://helpx.adobe.com/es/legal/product-descriptions/campaign.html). En el informe [Rendimiento de entrega](../../reporting/using/global-reports.md#delivery-throughput), compruebe el número de bytes transferidos por hora.
* Gran número de destinatarios no válidos: cuando hay un gran número de destinatarios no válidos, puede afectar al rendimiento. El MTA sigue reintentando enviar correos electrónicos a destinatarios no válidos. Asegúrese de que la base de datos esté bien mantenida.
* Cantidad de personalización: si una entrega permanece en &quot;Personalization en curso&quot;, compruebe el JavaScript utilizado en los bloques de personalización.

>[!NOTE]
>
>Consulte también la sección [Capacidad de entrega](../../delivery/using/about-deliverability.md). Para profundizar en la capacidad de entrega, consulte la [Guía de prácticas recomendadas de entrega de Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=es).
