---
solution: Campaign Classic
product: campaign
title: Problemas de rendimiento y producción
description: Problemas de rendimiento y producción
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: d1b38acc5209a5c96ab7a35fe9640159141b110f
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 8%

---


# Problemas de rendimiento y producción{#performance-and-throughput-issues}

En primer lugar, debe comprobar que tiene instalada la última compilación. Esto garantiza que dispone de las últimas funciones y correcciones de errores.

Consulte las [Notas de la versión](../../rn/using/latest-release.md) para obtener más información sobre el contenido de cada versión.

## Hardware e infraestructura {#hardware-and-infrastructure}

Las directrices generales para los requisitos de hardware para el Campaign Classic local se detallan en esta [página](https://helpx.adobe.com/es/campaign/kb/hardware-sizing-guide.html).

El equipo de consultoría puede proporcionar a los clientes alojados una herramienta que le permite ver fácilmente cuánto espacio utilizan los distintos tipos de tablas de la base de datos, así como el espacio utilizado en el sitio SFTP. Además, proporciona herramientas que le permiten limpiar datos innecesarios. Póngase en contacto con [Adobe Customer Care](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) si necesita implementar esta herramienta. Estas son algunas cosas importantes que debe comprobar mediante esta herramienta:

* Si el tamaño del índice es mayor que el tamaño de la tabla, se requiere un vacío.
* Compruebe las tablas que tienen el máximo peso. Si estas tablas se utilizan con frecuencia, necesitan ser aspiradas.
* El bloqueo de bases de datos puede hacer que los correos electrónicos dejen de enviarse.

Adobe Campaign también proporciona una [herramienta](../../production/using/monitoring-processes.md#manual-monitoring) para comprobar el uso de la CPU y la RAM. Utilice esta herramienta y observe indicadores específicos como: **Memoria**, **Intercambiar memoria**, **Disco**, **Procesos activos**. Si los valores son demasiado altos, puede intentar reducir el número de flujos de trabajo o programar flujos de trabajo para que se inicien en momentos diferentes.

## Comprobación de la base de datos {#database-performances}

La mayoría de las veces, los problemas de rendimiento están vinculados al mantenimiento de la base de datos. Estos son los elementos principales para comprobar:

* Configuración: recomendamos comprobar la configuración inicial de la plataforma Adobe Campaign y ejecutar una comprobación de hardware completa.
* Instalación y configuración de la plataforma Adobe Campaign: compruebe las opciones de configuración de red y envío de plataforma.
* Mantenimiento de la base de datos: asegúrese de que la tarea de limpieza de la base de datos esté operativa y de que el mantenimiento de la base de datos esté correctamente programado y se ejecute. Compruebe el número y el tamaño de las tablas de trabajo.
* Diagnóstico en tiempo real: compruebe los archivos de registro de proceso y plataforma y, a continuación, supervise la actividad de la base de datos mientras vuelve a crear el problema.

>[!NOTE]
>
>Para obtener más información, consulte esta sección: [Rendimiento de la base de datos](../../production/using/database-performances.md).

## Configuración de la aplicación {#application-configuration}

A continuación se muestra una lista de artículos relacionados con las prácticas recomendadas de configuración de aplicaciones:

* Procesos y memoria MTA y MTAChild: el módulo **mta** distribuye mensajes a sus módulos secundarios **mtachild**. Cada **mtachild** prepara los mensajes antes de solicitar una autorización al servidor de estadísticas y enviarlos. Consulte esta [página](../../installation/using/email-deliverability.md) para obtener más información.
* Configuración de TLS: no se recomienda habilitar TLS globalmente porque puede reducir el rendimiento. En su lugar, la configuración de TLS por dominio, administrada por el equipo de entrega, debe ajustarse según las necesidades. Consulte esta [página](../../installation/using/email-deliverability.md#mx-configuration) para obtener más información.
* DKIM: para asegurar el nivel de seguridad del DKIM, el tamaño de cifrado recomendado es 1024b. La mayoría de los proveedores de acceso no consideran válidas las claves DKIM menores. Consulte [esta página](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).

## Problemas con entregas {#deliverability-issues}

Esta es una lista de prácticas recomendadas y artículos relacionados con la capacidad de envío:

* Conocimiento de IP: si la reputación de la IP no es lo suficientemente buena, habrá un impacto en el rendimiento. El módulo **Deliverability Monitoring** ofrece varias herramientas para rastrear el rendimiento de envío de su plataforma. Consulte [esta página](../../delivery/using/monitoring-deliverability.md).
* Calificación de IP: el equipo de entrega realiza la preparación de la IP. Esto implica aumentar gradualmente el número de correos electrónicos a través de nuevas direcciones IP durante un periodo de pocas semanas.
* Configuración de afinidad IP: una configuración de afinidad de IP incorrecta puede detener los correos electrónicos por completo (nombre de operador/afinidad incorrecto en la configuración) o reducir el rendimiento (número pequeño de IP en la afinidad). Consulte [esta página](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).
* Tamaño del correo electrónico: el tamaño del correo electrónico juega un papel importante en el rendimiento. El tamaño máximo recomendado del correo electrónico es de 60 KB. Consulte [esta página](https://helpx.adobe.com/legal/product-descriptions/campaign.html). En el informe [Delivery throughput](../../reporting/using/global-reports.md#delivery-throughput), compruebe el número de bytes transferidos por hora.
* Gran número de destinatarios no válidos: cuando hay un gran número de destinatarios no válidos, puede afectar al rendimiento. El MTA sigue reintentando enviar correos electrónicos a destinatarios no válidos. Asegúrese de que la base de datos esté bien mantenida.
* Cantidad de personalización: si una entrega permanece en &quot;Personalization in progress&quot;, compruebe el JavaScript utilizado en los bloques de personalización.

>[!NOTE]
>
>Consulte también la sección [Deliverability](../../delivery/using/about-deliverability.md). Para profundizar en la capacidad de envío, consulte la [Guía de prácticas recomendadas de entrega de Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html).
