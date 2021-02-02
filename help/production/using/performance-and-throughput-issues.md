---
solution: Campaign Classic
product: campaign
title: Problemas de rendimiento y producción
description: Problemas de rendimiento y producción
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 3139a9bf5036086831e23acef21af937fcfda740
workflow-type: tm+mt
source-wordcount: '692'
ht-degree: 8%

---


# Problemas de rendimiento y producción{#performance-and-throughput-issues}

En primer lugar, debe comprobar que tiene instalada la última compilación. Esto garantiza que dispone de las últimas funciones y correcciones de errores.

Consulte las [Notas de la versión](../../rn/using/latest-release.md) para obtener más información sobre el contenido de cada versión.

## Hardware e infraestructura {#hardware-and-infrastructure}

En esta [página](https://helpx.adobe.com/es/campaign/kb/hardware-sizing-guide.html) se detallan las directrices generales para los requisitos de hardware para el Campaign Classic local.

El equipo de consultoría puede proporcionar a los clientes alojados una herramienta que le permite realizar vistas sencillas sobre el espacio que utilizan los distintos tipos de tablas de la base de datos, así como sobre el espacio utilizado en el sitio SFTP. Además, proporciona herramientas que le permiten limpiar datos innecesarios. Póngase en contacto con [Adobe Customer Care](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) si necesita implementar esta herramienta. A continuación se indican algunos aspectos importantes que hay que comprobar con esta herramienta:

* Si el tamaño de índice es mayor que el tamaño de tabla, se requiere un vacío.
* Compruebe las tablas que tienen el máximo brillo. Si estas tablas se utilizan con frecuencia, deben aspirarse.
* El bloqueo de la base de datos puede hacer que los mensajes de correo electrónico dejen de enviarse.

Adobe Campaign también proporciona una [herramienta](../../production/using/monitoring-processes.md#manual-monitoring) para comprobar el uso de CPU y RAM. Utilice esta herramienta y observe indicadores específicos como: **Memoria**, **Intercambiar memoria**, **Disco**, **Procesos activos**. Si los valores son demasiado altos, puede intentar reducir el número de flujos de trabajo o programar flujos de trabajo a inicios en diferentes momentos.

## Comprobación de base de datos {#database-performances}

La mayoría de las veces, los problemas de rendimiento están vinculados al mantenimiento de la base de datos. Estos son los elementos principales para comprobar:

* Configuración: recomendamos comprobar la configuración inicial de la plataforma Adobe Campaign y ejecutar una comprobación completa de hardware.
* Instalación y configuración de la plataforma Adobe Campaign: compruebe las opciones de configuración de red y de entrega de plataforma.
* Mantenimiento de la base de datos: asegúrese de que la tarea de limpieza de la base de datos está en funcionamiento y de que el mantenimiento de la base de datos está correctamente programado y ejecutado. Compruebe el número y el tamaño de las tablas de trabajo.
* Diagnóstico en tiempo real: compruebe el proceso y los archivos de registro de la plataforma y, a continuación, supervise la actividad de la base de datos mientras vuelve a crear el problema.

>[!NOTE]
>
>Para obtener más información, consulte esta sección: [Rendimiento de la base de datos](../../production/using/database-performances.md).

## Configuración de la aplicación {#application-configuration}

A continuación se muestra una lista de los artículos relacionados con las optimizaciones de configuración de la aplicación:

* Procesos y memoria MTA y MTAChild: el módulo **mta** distribuye mensajes a sus **módulos secundarios**. Cada **mtachild** prepara mensajes antes de solicitar una autorización del servidor de estadísticas y enviarlos. Consulte esta [página](../../installation/using/email-deliverability.md) para obtener más información.
* Configuración TLS: no se recomienda habilitar TLS de forma global porque puede reducir el rendimiento. En su lugar, la configuración de TLS por dominio, administrada por el equipo de entregabilidad, debe ajustarse según las necesidades. Consulte esta [página](../../installation/using/email-deliverability.md#mx-configuration) para obtener más información.
* DKIM: para asegurar el nivel de seguridad del DKIM, 1024b es el tamaño de codificación recomendado de optimizaciones. La mayoría de los proveedores de acceso no consideran válidas las claves DKIM menores. Consulte esta [página](../../delivery/using/technical-recommendations.md#dkim) y esta [nota técnica](https://helpx.adobe.com/es/campaign/kb/domain-name-delegation.html).

## Problemas con entregas {#deliverability-issues}

A continuación se muestra una lista de las prácticas recomendadas y los artículos relacionados con la posibilidad de entrega:

* Conocimiento de IP: si la reputación de IP no es lo suficientemente buena, habrá un impacto en el rendimiento. El módulo **de supervisión de la entrega** oferta varias herramientas para rastrear el rendimiento de la entrega de la plataforma. Consulte [esta página](../../delivery/using/monitoring-deliverability.md).
* calentamiento de IP: el equipo de entrega realiza el calentamiento de IP. Esto implica un aumento gradual del número de correos electrónicos a través de nuevas direcciones IP durante un período de pocas semanas.
* Configuración de afinidad IP: una configuración de afinidad IP incorrecta puede detener los mensajes de correo electrónico por completo (nombre de operador/afinidad incorrecto en la configuración) o reducir el rendimiento (número reducido de IP en la afinidad). Consulte [esta página](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).
* Tamaño del correo electrónico: el tamaño del correo electrónico juega un papel importante en el rendimiento. El tamaño máximo recomendado de correo electrónico es de 60 KB. Consulte [esta página](https://helpx.adobe.com/legal/product-descriptions/campaign.html). En el informe [rendimiento del Envío](../../reporting/using/global-reports.md#delivery-throughput), compruebe el número de bytes transferidos por hora.
* Gran número de destinatarios no válidos: cuando hay un gran número de destinatarios no válidos, puede afectar al rendimiento. El MTA sigue reintentando enviar correos electrónicos a destinatarios no válidos. Asegúrese de que la base de datos esté bien mantenida.
* Cantidad de personalización: si un envío permanece en &quot;Personalización en curso&quot;, compruebe el JavaScript utilizado en bloques de personalización.

>[!NOTE]
>
>Consulte también la sección [Puntos clave de entrega](../../delivery/using/deliverability-key-points.md).
