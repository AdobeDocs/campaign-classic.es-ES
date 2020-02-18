---
title: Problemas de rendimiento y rendimiento
seo-title: Problemas de rendimiento y rendimiento
description: Problemas de rendimiento y rendimiento
seo-description: null
page-status-flag: never-activated
uuid: 28c35453-9a15-44a3-9961-f4c604c209c2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: ec66e3e3-b09a-44a4-914d-e3b38c7643f8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 8fd9949ec03b7c2cdf88a9d5fcf5c8d8fd85f7d0

---


# Problemas de rendimiento y rendimiento{#performance-and-throughput-issues}

>[!NOTE]
>
>En primer lugar, debe comprobar que tiene instalada la última compilación. Esto garantiza que dispone de las últimas funciones y correcciones de errores. Consulte las [Notas](https://docs.campaign.adobe.com/doc/AC/en/RN.html) de la versión para obtener más información sobre el contenido de cada versión.

## Hardware e infraestructura {#hardware-and-infrastructure}

En este [artículo](https://helpx.adobe.com/campaign/kb/hardware-sizing-guide.html)se detallan las directrices generales para los requisitos de hardware de On-premise Campaign Classic.

El equipo de consultoría puede proporcionar a los clientes alojados una herramienta que le permite ver fácilmente cuánto espacio utilizan los distintos tipos de tablas de la base de datos, así como el espacio utilizado en el sitio SFTP. Además, proporciona herramientas que le permiten limpiar datos innecesarios. Póngase en contacto con los equipos de asesoría o asistencia si necesita implementar esta herramienta. A continuación se indican algunos aspectos importantes que hay que comprobar con esta herramienta:

* Si el tamaño de índice es mayor que el tamaño de tabla, se requiere un vacío.
* Compruebe las tablas que tienen el máximo brillo. Si estas tablas se utilizan con frecuencia, deben aspirarse.
* El bloqueo de la base de datos puede hacer que los mensajes de correo electrónico dejen de enviarse.

Adobe Campaign también ofrece una [herramienta](../../production/using/monitoring-processes.md#manual-monitoring) para comprobar el uso de CPU y RAM. Utilice esta herramienta y observe indicadores específicos como: **Memoria**, **Intercambiar Memoria**, **Disco**, Procesos **Activos**. Si los valores son demasiado altos, puede intentar reducir el número de flujos de trabajo o programar flujos de trabajo para que se inicien en momentos diferentes.

## Rendimiento de la base de datos {#database-performances}

La mayoría de las veces, los problemas de rendimiento están vinculados al mantenimiento de la base de datos. Estos son los elementos principales para comprobar:

* Configuración: recomendamos comprobar la configuración inicial de la plataforma de Adobe Campaign y ejecutar una comprobación completa de hardware.
* Instalación y configuración de la plataforma de Adobe Campaign: compruebe las opciones de configuración de red y de entrega de plataforma.
* Mantenimiento de la base de datos: asegúrese de que la tarea de limpieza de la base de datos está operativa y de que el mantenimiento de la base de datos está correctamente programado y ejecutado. Compruebe el número y el tamaño de las tablas de trabajo.
* Diagnóstico en tiempo real: compruebe el proceso y los archivos de registro de la plataforma y, a continuación, supervise la actividad de la base de datos mientras vuelve a crear el problema.

>[!NOTE]
>
>For more information, refer to this section: [Database performances](../../production/using/database-performances.md).

## Configuración de la aplicación {#application-configuration}

A continuación se muestra una lista de artículos relacionados con las prácticas recomendadas de configuración de aplicaciones:

* Procesos y memoria MTA y MTAChild: el **módulo mta** distribuye mensajes a sus módulos secundarios **integrados** . Cada **equipo** prepara mensajes antes de solicitar una autorización al servidor de estadísticas y enviarlos. Refer to this [page](../../installation/using/email-deliverability.md) for more information.
* Configuración TLS: no se recomienda habilitar TLS de forma global porque puede reducir el rendimiento. En su lugar, la configuración de TLS por dominio, administrada por el equipo de entregabilidad, debe ajustarse según las necesidades. Refer to this [page](../../installation/using/email-deliverability.md#mx-configuration) for more information.
* DKIM: para asegurar el nivel de seguridad del DKIM, 1024b es el tamaño de codificación recomendado de optimizaciones. La mayoría de los proveedores de acceso no consideran válidas las claves DKIM menores. Consulte esta [página](../../delivery/using/technical-recommendations.md#dkim) y esta [nota técnica](https://helpx.adobe.com/campaign/kb/domain-name-delegation.html).

## Problemas de capacidad de entrega {#deliverability-issues}

A continuación se muestra una lista de prácticas recomendadas y artículos relacionados con la posibilidad de entrega:

* Conocimiento de IP: si la reputación de IP no es lo suficientemente buena, habrá un impacto en el rendimiento. El módulo **de supervisión** de la entrega ofrece varias herramientas para rastrear el rendimiento de la entrega de su plataforma. Consulte [esta página](../../delivery/using/technical-monitoring.md).
* calentamiento de IP: el equipo de entrega realiza el calentamiento de IP. Esto implica un aumento gradual del número de correos electrónicos a través de nuevas direcciones IP durante un período de pocas semanas.
* Configuración de afinidad IP: una configuración de afinidad IP incorrecta puede detener los mensajes de correo electrónico por completo (nombre de operador/afinidad incorrecto en la configuración) o reducir el rendimiento (número reducido de IP en la afinidad). Consulte [esta página](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).
* Tamaño del correo electrónico: el tamaño del correo electrónico juega un papel importante en el rendimiento. El tamaño máximo recomendado de correo electrónico es de 60 KB. Consulte [esta página](https://helpx.adobe.com/legal/product-descriptions/campaign.html). En el informe Rendimiento [de](../../reporting/using/delivery-reports.md#delivery-throughput) envío, compruebe el número de bytes transferidos por hora.
* Gran número de destinatarios no válidos: cuando hay un gran número de destinatarios no válidos, puede afectar al rendimiento. El MTA sigue reintentando enviar correos electrónicos a destinatarios no válidos. Asegúrese de que la base de datos esté bien mantenida.
* Cantidad de personalización: si una entrega permanece en &quot;Personalización en curso&quot;, compruebe el JavaScript utilizado en los bloques de personalización.

>[!NOTE]
>
>No olvide consultar la guía de introducción a [la entrega](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) .

