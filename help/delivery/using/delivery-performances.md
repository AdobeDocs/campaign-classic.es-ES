---
solution: Campaign Classic
product: campaign
title: Prácticas recomendadas sobre el rendimiento de las entregas
description: Obtenga más información sobre el rendimiento de las entregas y las prácticas recomendadas.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
translation-type: ht
source-git-commit: 5b43412286762977c416665d296908a9bfc9b20a
workflow-type: ht
source-wordcount: '452'
ht-degree: 100%

---


# Prácticas recomendadas sobre el rendimiento de las entregas {#delivery-performances}

Recomendamos seguir las directrices que se indican a continuación para garantizar que sus entregas, así como las comprobaciones que se realizan en caso de que surjan problemas con estas, se llevan a cabo correctamente.

**Temas relacionados:**

* [Panel de entregas](../../delivery/using/delivery-dashboard.md)
* [Solución de problemas de entregas](../../delivery/using/delivery-troubleshooting.md)
* [Acerca de la capacidad de la entrega](../../delivery/using/about-deliverability.md)

## Prácticas recomendadas para el rendimiento {#best-practices-performance}

* Evite mantener las entregas en estado de error en la instancia, ya que esto mantiene tablas temporales e influye en el rendimiento.

* Elimine las entregas que ya no sean necesarios.

* Destinatarios inactivos en los últimos 12 meses que se deben eliminar de la base de datos para mantener la calidad de la dirección.

* Evite programar entregas grandes al mismo tiempo. Hay un lapso de 5 a 10 minutos para distribuir la carga de manera uniforme en el sistema. Coordine la programación de las entregas con los demás miembros de su equipo para garantizar el mejor rendimiento. Cuando el servidor de marketing gestiona muchas tareas diferentes al mismo tiempo, puede ralentizar el rendimiento.

* Mantenga el tamaño de sus correos electrónicos lo más bajo posible. El tamaño máximo recomendado de un correo electrónico es de unos 35 KB. El tamaño de una entrega por correo electrónico genera una cierta cantidad de volumen en los servidores de entrega.

* Las entregas grandes, como las entregas a más de un millón de destinatarios, necesitan espacio en las colas de entrega. Esto por sí solo no es un problema para el servidor, pero cuando se combina con docenas de entregas grandes que se realizan al mismo tiempo, puede provocar un retraso en la entrega.

* La personalización en correos electrónicos extrae datos de la base de datos de cada destinatario. Si hay muchos elementos de personalización, esto aumenta la cantidad de datos necesarios para preparar la entrega.

* Direcciones de índice. Para optimizar el rendimiento de las consultas SQL utilizadas en la aplicación, se puede declarar un índice a partir del elemento principal del esquema de datos.

>[!NOTE]
>
>Los ISP desactivarían las direcciones después de un periodo de inactividad. Los mensajes rechazados se envían a los remitentes para informarles sobre este nuevo estado.

## Lista de comprobación de problemas de rendimiento {#performance-issues}

Si los resultados de la entrega son malos, puede comprobar:

* **El tamaño de la entrega**: Las entregas grandes pueden tardar más en completarse. Los elementos MTA secundarios se configuran para gestionar un tamaño predeterminado que funciona con la mayoría de las instancias, pero es necesario comprobar si las entregas son constantemente lentos.
* **El destinatario de la entrega**: El rendimiento de las entregas se puede ver afectado por errores de rechazos leves que se gestionan según la configuración de reintento. Cuanto mayor sea el número de errores, más necesarios son los reintentos de entrega.
* **La carga de la plataforma general**: Cuando se envían varias entregas de gran tamaño, la plataforma general se puede ver afectada. También puede comprobar los problemas de reputación de la IP y de capacidad de entrega. Para obtener más información, consulte la [Guía de prácticas recomendadas de entrega](../../delivery/using/deliverability-key-points.md) de Adobe Campaign y [esta página](../../delivery/using/about-deliverability.md).

El mantenimiento de la plataforma y de la base de datos también puede afectar el rendimiento de las entregas. Para obtener más información, consulte [esta página](../../production/using/database-performances.md).
