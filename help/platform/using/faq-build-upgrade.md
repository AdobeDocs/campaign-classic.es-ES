---
solution: Campaign Classic
product: campaign
title: Preguntas frecuentes sobre la actualización de versiones
description: Preguntas comunes relacionadas con las actualizaciones de la compilación de Campañas
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: 5b35d2ffdd0f591e2fe31dc98a54be9ea0c0c18d
workflow-type: tm+mt
source-wordcount: '2017'
ht-degree: 6%

---


# Preguntas más frecuentes sobre la actualización de la compilación {#build-upgrade-faq}

Adobe Campaign se actualiza periódicamente. Si está familiarizado con nuestras [Notas de la versión](../../rn/using/rn-overview.md) publicadas, probablemente tenga en cuenta el hecho de que, en promedio, se publican 2/3 versiones menores repletas de nuevas funciones, mejoras y correcciones cada año. Además, lanzamos versiones periódicamente solamente con correcciones acumulativas. Esta cadencia habitual de actualizaciones tiene como objetivo conseguir lo último y bueno en tus manos, manteniendo tu entorno totalmente seguro y mejorando obviamente tu experiencia con nuestro producto.

Es fundamental que nuestros clientes ejecuten la versión más reciente de Adobe Campaign. También permite que el Adobe ayude de manera mucho más eficiente en caso de que se produzcan problemas: identificar, reproducir y corregir un problema en una antigua compilación suele llevar más tiempo, sin mencionar que algunos problemas que puede encontrar pueden haberse corregido ya en una compilación reciente.

Por lo tanto, iniciamos el programa [Gold Standard](https://helpx.adobe.com/es/campaign/kb/gold-standard.html) para trabajar en colaboración con nuestros clientes a fin de actualizar de manera proactiva y regular sus entornos.

## ¿Qué es una actualización de compilación?

Una actualización de compilación se produce cuando el software de Adobe Campaign Classic se actualiza al último número de compilación segura, pero permanece en el mismo nivel de compilación principal o menor. Por ejemplo: Campaign Classic 7, compilación 9026, a Campaign 7, compilación 9032.

Obtenga más información [en esta sección](../../rn/using/rn-overview.md).

## ¿Cuál es la versión más reciente de Adobe Campaign Classic?

La versión más reciente del Campaign Classic, que incluye nuevas funciones y documentación, se detalla en las [Notas de la versión](../../rn/using/latest-release.md) más recientes.

## ¿Cómo sé qué versión estoy ejecutando?

Compruebe su versión en el menú **[!UICONTROL Help > About...]** de la consola del cliente de Adobe Campaign. El cuadro **[!UICONTROL About]** contiene información detallada sobre la versión y la compilación que está ejecutando tanto para la consola como para el servidor.

Obtenga más información [en esta sección](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## ¿Qué significa el estado de la versión?

A partir de Campaign Classic 19.2, se asocia un estado a cada versión.

Obtenga más información [en esta sección](../../rn/using/rn-overview.md).

## ¿Es una actualización de compilación lo mismo que una actualización de versión?

No. Una actualización de compilación es una actualización incremental dentro de una versión principal determinada, mientras que una actualización de versión es un cambio de una versión principal a otra. Las actualizaciones de la compilación son sencillas, ya que no suelen implicar cambios importantes en los modelos arquitectónicos, técnicos o de datos.

Por otra parte, las actualizaciones de versiones suelen incluir importantes cambios técnicos y, en función de la profundidad de la configuración de un cliente determinado, pueden requerir cambios significativos en la configuración o una reimplementación parcial.

Por ejemplo, si se utiliza la información del servidor de la captura de pantalla de la sección anterior:

* Una actualización de la compilación implicaría pasar de la compilación 6880 a cualquier construcción buena que 6880. Por ejemplo: v6.1.1 compilación 8222 a v6.1.1 compilación 8666

* Una actualización de la versión implicaría pasar de la versión 6.0.2 a cualquier versión buena que no sea 6.0.2.  Por ejemplo: v6.0.1 compilación 222 a v6.1.1 compilación 8666

## ¿Debo hacer una copia de seguridad de mis datos antes de estas actualizaciones?

Adobe realizará una copia de seguridad del sistema antes de realizar cualquier cambio. Sin embargo, si hay un trabajo de personalización crítico en el sistema que no es de producción (servidores de ensayo o desarrollo), se RECOMIENDA MUCHO que exporte ese trabajo como paquete antes de cualquier actualización.

![](assets/do-not-localize/how-to-video.png) Para obtener más información,  [vea este vídeo](https://helpx.adobe.com/campaign/classic/how-to/generate-packages-in-acv6.html).

## ¿Cuándo se realizarán las actualizaciones?

A los clientes se les ofrecerá un intervalo de fechas para elegir. Los cambios en el sistema de producción no se realizan en días festivos.

Las actualizaciones de la compilación se pueden realizar de lunes a jueves y los viernes solo se utilizan para instancias que no sean de producción.

## ¿Cuánto tiempo tardará la actualización de la compilación?

El tiempo necesario para realizar una actualización de compilación depende de varios factores:

* El tamaño de la base de datos que se va a hacer backup o restore (las bases de datos más grandes requieren más tiempo para actualizarse)
* El tamaño de los entornos (muchos de nuestros clientes tienen varios servidores diferentes que cada uno gestiona funciones específicas, con entornos más grandes que requieren más tiempo para la actualización)
* La complejidad del sistema (algunos sistemas cuentan con servicios y conexiones más dependientes para verificar, lo que requiere la verificación de la estabilidad y el funcionamiento de esos sistemas)

La actualización de la compilación es un proceso de dos pasos:

1. Preparación del sistema para la actualización: Teniendo en cuenta las particularidades de su entorno, esta fase conduce esencialmente a una actualización completa en un entorno sin producción. Una vez que el entorno actualizado se haya iluminado desde un punto de vista técnico y funcional, puede producirse la fase 2. Esta primera fase, según los factores mencionados, puede durar de unos días a un par de semanas.

1. La actualización misma: se actualiza el entorno de producción. Esta fase se realiza generalmente en unas pocas horas. Para entornos muy complejos debe esperarse un tiempo de inactividad más largo. En el evento de que algo va mal, se define una estrategia de reversión que se puede ejecutar.

Para obtener más información, [consulte este documento](https://helpx.adobe.com/es/campaign/kb/acc-build-upgrade.html).

## ¿Qué recursos se necesitan para la actualización de la compilación?

El proceso de actualización de la compilación requiere los siguientes recursos:

* Arquitecto de Adobe: Para las arquitecturas híbridas o de mensajería en la nube o alojadas, el arquitecto debe coordinarse con el Servicio de atención al cliente.
* Administrador de proyectos - Alojado: el equipo de alojamiento se asociará con el equipo de atención al cliente y el cliente para coordinar la cronología de actualización de todas las instancias.
* Administrador de Adobe Campaign - Alojado: el equipo de alojamiento realiza la actualización.
* Operador de Adobe Campaign\usuario de marketing: el operador ejecuta pruebas en instancias de desarrollo, prueba y producción.

## ¿Cómo puedo prepararme para la actualización de la compilación?

En sus sistemas de desarrollo y ensayo, exporte cualquier trabajo que sea crítico y que deba preservarse. Para obtener más información, [vea este video](https://helpx.adobe.com/campaign/classic/how-to/generate-packages-in-acv6.html).

Actualice su conocimiento de los flujos de trabajo y envíos de ruta críticos desarrollados en los libros de ejecución (o por su equipo de consultoría o socio) mediante la revisión de la documentación proporcionada a su equipo al final de la implementación.

Identifique los tiempos de bajo volumen o bajo tráfico que sean ideales para las ventanas de mantenimiento, ya que producirán el menor impacto comercial.

Revise nuestra [lista de comprobación de actualización de la ](#check-list) compilación y sus planes de prueba y asegúrese de que los recursos que pueden realizar estas pruebas estén disponibles entre las 24 y las 48 horas. de la finalización de una actualización.

Para obtener más información, [consulte este documento](https://helpx.adobe.com/campaign/kb/acc-build-upgrade.html).

## ¿Se pueden realizar actualizaciones de la compilación por la noche o durante las horas fuera de servicio?

Las actualizaciones se pueden realizar fuera de horas. Siempre se recomienda actualizar el entorno durante las horas de inactividad del negocio cuando no haya usuarios comerciales conectados a la instancia.

## ¿Cuáles son los costos asociados con una actualización de la compilación?

No hay costo para instalar la actualización de compilación para clientes alojados. Si hay desarrollos personalizados en el sistema, el cliente deberá identificar los recursos necesarios para probar estos desarrollos después de la actualización y corregir cualquier problema que se encuentre con esos desarrollos personalizados.

## ¿Habrá acceso a la instancia durante el proceso de actualización?

No. El servidor se apaga durante una actualización para garantizar que se conserva la integridad de los datos mientras se actualiza el producto. Una vez finalizado, se reinicia y se reanudan todos los servicios.

## ¿Seguirán enviándose los mensajes de correo electrónico desde el Centro de mensajes durante el proceso de actualización?

Cuando la actualización se produce para el Centro de mensajes (RT), no envía correos electrónicos desde la instancia. Tenga en cuenta que cualquier proceso que se detenga cuando se apague un sistema de Campaña se reanudará automáticamente cuando se reinicie el sistema. Esto incluye envíos activos o programados, seguimiento y cálculos de métricas para envíos enviados anteriormente.

## ¿Seguirán los flujos de trabajo corriendo y enviarán los envíos?

No. Durante la actualización de la compilación, el flujo de trabajo y los servicios de correo se detienen. Esto significa que no se ejecutarán flujos de trabajo y no se enviarán envíos. Se reanudarán una vez que se reinicie el sistema. Sin embargo, Adobe recomienda encarecidamente que todos los flujos de trabajo de ruta críticos se comprueben después de una actualización para garantizar que se ejecuten y estén sanos.

## ¿Los vínculos de seguimiento seguirán funcionando durante la actualización?

Los vínculos de seguimiento funcionarán durante la actualización. No se pueden enviar nuevos correos electrónicos durante la actualización, pero los vínculos de seguimiento incluidos en los mensajes de correo electrónico ya enviados estarán operativos.

## ¿Debo estar disponible durante el proceso de actualización de la compilación?

Sí. Los clientes deben proporcionar al Adobe un punto de contacto disponible durante o inmediatamente después de la actualización de su instancia de producción.  Adobe se pondrá en contacto con esta persona por correo electrónico a menos que se tomen otras medidas. Esto garantizará una transición sin tropiezos y la validación inmediata de tareas críticas. Adobe se pondrá en contacto con el cliente una vez que se complete la actualización de la compilación para su confirmación.

## ¿Debo actualizar la consola de cliente?

Sí. La consola de cliente debe estar en la misma compilación que la instancia de servidor. Una vez completada la actualización, la consola de cliente debe solicitarle que actualice a la última compilación para asegurarse de que se mantiene alineada con la compilación del servidor.

## ¿Cuál es el plan de reversión? ¿Se guardan los backups de mis datos?

El plan de reversión es restaurar el sistema con la última copia de seguridad disponible. Las copias de seguridad se almacenan durante 7 días para los clientes del centro de datos y durante 14 días para los clientes del servicio Web de Amazon (AWS).

## ¿Cuánto tiempo tardará en revertirse?

Depende del tamaño de copia de seguridad de la base de datos. El tiempo promedio que se tarda es de 4 horas en completarse.

## ¿Qué tipos de pruebas se realizan en mi sistema después de la actualización?

Consulte la [lista de comprobación de la actualización de la &lt;a0/>compilación a continuación](#check-list).

## ¿Qué tipo de prueba debo realizar después de la actualización?

Los entornos de desarrollo y de fase se actualizan de forma secuencial o conjunta, pero se necesita una firma antes de actualizar la instancia de producción. Esto permite a cada cliente realizar pruebas exhaustivas antes de cerrar sesión en cualquier cambio en la producción.

Consulte la lista de comprobación de la actualización de la lista [compilación más abajo](#check-list). Los clientes deben ejecutar pruebas similares así como otras que puedan necesitar para el entorno.

## ¿Con qué frecuencia debo realizar una actualización de compilación?

Para garantizar un rendimiento, disponibilidad y seguridad óptimos del sistema, Adobe se asociará con los clientes para garantizar que los sistemas se actualicen al menos una vez al año.

## ¿Se cerrará con una actualización de compilación?

Sí. El servidor se apaga durante una actualización para garantizar que se conserva la integridad de los datos mientras se actualiza el producto. Una vez finalizado, se reinicia y se reanudan todos los servicios.

## ¿Con quién debo contactar para abrir una incidencia de actualización de compilación?

Si tiene problemas tras una actualización de la compilación, póngase en contacto con [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). El Servicio de atención al cliente programa las fechas de compilación y abre los tickets relacionados con la actualización de compilación.

Obtenga más información en [Opciones de ayuda y soporte para Campaign Classic](https://helpx.adobe.com/campaign/kb/ac-support.html#acc-support-req)

## Generar lista de comprobación de actualización {#check-list}

### Lista de comprobación posterior a la actualización del servidor de mensajería en la nube

1. Envío de un envío de prueba
   1. Validar los registros de envío y el flujo de trabajo relacionado
   1. Validar la actualización de los registros de seguimiento
   1. Validación de vínculos de seguimiento y página espejo
1. Confirmar que todos los flujos de trabajo técnicos están en estado de inicio
1. Verificar que todos los procesos también estén activos

### Lista de comprobación posterior a la actualización del servidor de marketing

* ¿Puede iniciar sesión en el servidor? Compruebe que la consola del cliente de Campaña funciona sin que aparezcan errores o advertencias.
* Asegúrese de utilizar la misma versión de la consola que la versión de compilación después de la actualización.
* ¿Tiene aplicaciones Web que inserten datos en la base de datos de Campaña? Si es así, ejecútelos y
compruebe que pueden insertar nuevos registros a través de la API.
* ¿Puede enviar una prueba de correo electrónico correctamente? Crear nuevo envío con una plantilla conocida, enviarla a
un destinatario de prueba, comprobar la personalización, dessubvincular, página espejo todos funcionan.
* ¿Se están ejecutando todos los flujos de trabajo de ruta críticos? Comprobar flujos de trabajo, abrir historial de flujo de trabajo, comprobar
que no hay errores.
* ¿Están todas las carpetas presentes, visibles y accesibles? Navegue por diferentes carpetas y verifique.
todo el contenido se muestra y está presente.
* ¿Llegan sus envíos con el huso horario correcto?

   * Verifique la fecha de creación y la fecha de modificación con la marca de tiempo y la zona horaria
   * Compruebe que la ejecución de Planificador funciona en un flujo de trabajo a la hora especificada
   * Buscar lista de flujos de trabajo en estado PAUSED y FAILED. Inicio y supervisión
   * Ejecutar prueba AB para un escenario
   * Probar las notificaciones push junto con su funcionalidad de seguimiento para los vínculos profundos
   * Probar el envío de SMS
   * Si tiene algún FDA externo conectado, pruebe si los datos se envían de ambas formas
   * Si utiliza integraciones como Adobe Campaign-Adobe Experience Manager, Adobe Campaign-Adobe Analytics, pruebe si siguen funcionando como antes

**Consulte también**

* [Realización de una actualización de versión](../../production/using/build-upgrade.md)
* [Notas de la versión de Campaign Classic ](../../rn/using/rn-overview.md)
* [Opciones de ayuda y asistencia técnica para Campaign Classic](https://helpx.adobe.com/campaign/kb/ac-support.html#acc-support-req)
* [Programa estándar Gold](https://helpx.adobe.com/campaign/kb/gold-standard.html)