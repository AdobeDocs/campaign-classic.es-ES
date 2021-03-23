---
solution: Campaign Classic
product: campaign
title: Preguntas frecuentes sobre la actualización de versiones
description: Preguntas frecuentes relacionadas con las actualizaciones de las compilaciones de Campaign
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: b77a56a97e499f60c092fae45c7809f7bfd9f2ea
workflow-type: tm+mt
source-wordcount: '2034'
ht-degree: 98%

---


# Preguntas frecuentes sobre la actualización de versiones {#build-upgrade-faq}

Adobe Campaign se actualiza periódicamente. Si conoce nuestras [Notas de la versión](../../rn/using/rn-overview.md) publicadas, probablemente sea consciente de que se lanza un promedio anual de dos o tres versiones menores repletas de nuevas funciones, mejoras y correcciones. Además, lanzamos versiones periódicamente solamente con correcciones acumulativas. Esta cadencia regular de actualizaciones tiene como objetivo ofrecerle lo más novedoso y lo mejor, mantener el entorno seguro y, por supuesto, mejorar su experiencia con nuestro producto.

Es fundamental que nuestros clientes usen la versión más reciente de Adobe Campaign. Esto permite a Adobe ayudarle de manera mucho más eficiente en caso de que se produzcan problemas: identificar, reproducir y corregir un problema en una compilación antigua suele llevar más tiempo, sin mencionar que algunos problemas pueden haberse corregido ya en una versión reciente.

[!DNL Gold Standard] es la versión de soporte a largo plazo de Campaign Classic. Como usuario [!DNL Gold Standard] alojado, se beneficia automáticamente de la actualización [!DNL Gold Standard] con la última versión estable sin ninguna acción. Los clientes locales e híbridos también pueden beneficiarse de las versiones [!DNL Gold Standard]. Si migra desde una versión antigua, le recomendamos que la actualice primero a esta versión. [Más información](../../rn/using/gs-overview.md).

## ¿Qué es una actualización de compilación?

Una actualización de versión se produce cuando el software Adobe Campaign Classic se actualiza al último número de compilación segura, pero permanece en el mismo nivel de compilación principal/menor. Por ejemplo: Campaign Classic 7, compilación 9026, a Campaign 7, compilación 9032.

Obtenga más información [en esta sección](../../rn/using/rn-overview.md).

## ¿Cuál es la versión más reciente de Adobe Campaign Classic?

La versión más reciente de Campaign Classic, que incluye nuevas funciones y documentación, se detalla en las [Notas de la versión](../../rn/using/latest-release.md) más recientes.

## ¿Cómo sé qué versión estoy ejecutando?

Compruebe su versión en el menú **[!UICONTROL Help > About...]** de la consola del cliente de Adobe Campaign. El cuadro **[!UICONTROL About]** contiene información detallada sobre la versión y la compilación que está ejecutando tanto para la consola como para el servidor.

Obtenga más información [en esta sección](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## ¿Qué significa el estado de la versión?

A partir de Campaign Classic 19.2, se asocia un estado a cada versión.

Obtenga más información [en esta sección](../../rn/using/rn-overview.md).

## ¿Es una actualización de compilación lo mismo que una actualización de versión?

No. Una actualización de compilación es una actualización incremental dentro de una versión principal determinada, mientras que una actualización de versión es un cambio de una versión principal a otra. Las actualizaciones de la compilación son sencillas, ya que no suelen implicar cambios importantes en los modelos arquitectónicos, técnicos o de datos.

Por otra parte, las actualizaciones de versiones suelen incluir importantes cambios técnicos y, en función de la profundidad de la configuración de un cliente determinado, pueden requerir cambios significativos en la configuración o una reimplementación parcial.

Por ejemplo, con la información del servidor de la captura de pantalla de la sección anterior:

* Una actualización de la compilación implicaría pasar de la compilación 6880 a cualquier compilación superior a 6880. Por ejemplo, de la versión 6.1.1 compilación 8222 a la versión 6.1.1 compilación 8666

* Una actualización de la versión implicaría pasar de la versión 6.0.2 a cualquier versión superior a 6.0.2. Por ejemplo: versión 6.0.1 compilación 2222 a versión 6.1.1 compilación 8666

## ¿Debo hacer una copia de seguridad de mis datos antes de estas actualizaciones?

Adobe realizará una copia de seguridad del sistema antes de realizar cualquier cambio. Sin embargo, si hay un trabajo de personalización crítico en el sistema que no es de producción (servidores de ensayo o desarrollo), se RECOMIENDA que exporte ese trabajo como paquete antes de cualquier actualización.

![](assets/do-not-localize/how-to-video.png) Para obtener más información, [vea este vídeo](https://helpx.adobe.com/es/campaign/classic/how-to/generate-packages-in-acv6.html).

## ¿Cuándo se realizarán las actualizaciones?

A los clientes se les ofrecerá un intervalo de fechas para elegir. Los cambios en el sistema de producción no se realizan en días festivos.

Las actualizaciones de la compilación se pueden realizar de lunes a jueves y los viernes solo se utilizan para instancias que no sean de producción.

## ¿Cuánto tiempo tardará la actualización de la compilación?

El tiempo necesario para realizar una actualización de compilación depende de varios factores:

* El tamaño de la base de datos que restaurar o de la que hacer copias de seguridad (las bases de datos más grandes requieren más tiempo para actualizarse)
* El tamaño de los entornos (muchos de nuestros clientes tienen varios servidores diferentes y cada uno gestiona funciones específicas, donde los entornos más grandes requieren más tiempo para la actualización)
* La complejidad del sistema (algunos sistemas cuentan con servicios y conexiones más dependientes que verificar, lo que requiere la verificación de la estabilidad y el funcionamiento de esos sistemas)

La actualización de la compilación es un proceso de dos pasos:

1. Preparación del sistema para la actualización: teniendo en cuenta las particularidades de su entorno, esta fase conduce esencialmente a una actualización completa en un entorno sin producción. Una vez que el entorno actualizado esté bien desde un punto de vista técnico y funcional, puede producirse la fase 2. Esta primera fase, según los factores mencionados, puede durar de unos días a un par de semanas.

1. Es la actualización misma, donde se actualiza el entorno de producción. Esta fase se realiza generalmente en unas pocas horas. En el caso de entornos muy complejos, debe esperarse un tiempo de inactividad más largo. Si algo va mal, se define una estrategia de reversión que se puede ejecutar.

Para obtener más información, [consulte este documento](https://helpx.adobe.com/es/campaign/kb/acc-build-upgrade.html).

## ¿Qué recursos se necesitan para la actualización de la compilación?

El proceso de actualización de la compilación requiere los siguientes recursos:

* Arquitecto de Adobe: para las arquitecturas híbridas o de mensajería en la nube o alojadas, el arquitecto debe coordinarse con el Servicio de atención al cliente.
* Administrador de proyectos (alojado): el equipo de alojamiento se asociará con el equipo de atención al cliente y el cliente para coordinar la cronología de actualización de todas las instancias.
* Administrador de Adobe Campaign (alojado): el equipo de alojamiento realiza la actualización.
* Operador/usuario de marketing de Adobe Campaign: el operador ejecuta pruebas en instancias de desarrollo, prueba y producción.

## ¿Cómo puedo prepararme para la actualización de la compilación?

En sus sistemas de desarrollo y ensayo, exporte cualquier trabajo que sea crítico y que deba preservarse. Para obtener más información, [vea este vídeo](https://helpx.adobe.com/campaign/classic/how-to/generate-packages-in-acv6.html).

Actualice su conocimiento en cuanto a los flujos de trabajo y las entregas de ruta críticos desarrollados en los libros de ejecución (o por su equipo de consultoría o socio) mediante la revisión de la documentación proporcionada a su equipo al final de la implementación.

Identifique los tiempos de bajo volumen o bajo tráfico que sean ideales para las ventanas de mantenimiento, ya que producirán el menor impacto comercial.

Revise nuestra [lista de comprobación de actualización de compilaciones ](#check-list) a continuación, así como sus planes de prueba, y asegúrese de que los recursos que pueden realizar estas pruebas estén disponibles entre 24 y 48 horas tras la finalización de una actualización.

Para obtener más información, [consulte este documento](https://helpx.adobe.com/campaign/kb/acc-build-upgrade.html).

## ¿Se pueden realizar actualizaciones de la compilación por la noche o durante las horas fuera de servicio?

Las actualizaciones se pueden realizar fuera de horas. Siempre se recomienda actualizar el entorno durante las horas de inactividad cuando no haya usuarios comerciales conectados a la instancia.

## ¿Cuáles son los costes asociados con una actualización de compilación?

La instalación de una actualización de compilación para clientes alojados no supone ningún coste. Si hay desarrollos personalizados en el sistema, el cliente deberá identificar los recursos necesarios para probar estos desarrollos después de la actualización y corregir cualquier problema que se encuentre con esos desarrollos personalizados.

## ¿Habrá acceso a la instancia durante el proceso de actualización?

No. El servidor se apaga durante la actualización para garantizar que se conserva la integridad de los datos mientras se actualiza el producto. Una vez finalizado, se reinicia y se reanudan todos los servicios.

## ¿Seguirán enviándose los mensajes de correo electrónico desde el Centro de mensajes durante el proceso de actualización?

Cuando la actualización se produce en el Centro de mensajes, no se envían correos electrónicos desde la instancia. Tenga en cuenta que cualquier proceso que se detenga cuando se apague un sistema de Campaign se reanudará automáticamente cuando se reinicie el sistema. Esto incluye envíos activos o programados, seguimiento y cálculos de métricas para envíos enviados anteriormente.

## ¿Seguirán funcionando los flujos de trabajo y realizarán envíos?

No. Durante la actualización de la compilación, el flujo de trabajo y los servicios de correo se detienen. Esto significa que no se ejecutarán flujos de trabajo y no se enviarán envíos. Se reanudarán una vez que se reinicie el sistema. No obstante, Adobe recomienda encarecidamente que todos los flujos de trabajo de ruta críticos se comprueben después de la actualización para garantizar que se ejecuten y no se hayan dañado.

## ¿Seguirán funcionando los vínculos de seguimiento durante la actualización?

Los vínculos de seguimiento funcionarán durante la actualización. No se pueden enviar nuevos correos electrónicos durante la actualización, pero los vínculos de seguimiento incluidos en los mensajes de correo electrónico ya enviados estarán operativos.

## ¿Debo estar disponible durante el proceso de actualización de la compilación?

Sí. Los clientes deben proporcionar a Adobe un punto de contacto disponible durante o inmediatamente después de la actualización de su instancia de producción.  Adobe se pondrá en contacto con esta persona por correo electrónico a menos que se tomen otras medidas. Esto garantizará una transición sin problemas y la validación inmediata de tareas críticas. Adobe se pondrá en contacto con el cliente una vez que se complete la actualización de la compilación para su confirmación.

## ¿Debo actualizar la consola de cliente?

Sí. La consola de cliente debe estar en la misma compilación que la instancia de servidor. Una vez completada la actualización, la consola de cliente le pide actualizar a la última compilación para asegurarse de estar alineada con la compilación del servidor.

## ¿Cuál es el plan de reversión? ¿Se guardan las copias de seguridad de mis datos?

El plan de reversión es restaurar el sistema con la última copia de seguridad disponible. Las copias de seguridad se almacenan durante 7 días para los clientes del centro de datos y durante 14 días para los clientes del servicio web de Amazon (AWS).

## ¿Cuánto tiempo tarda en revertirse?

Depende del tamaño de copia de seguridad de la base de datos. El tiempo promedio que tarda en completarse es de 4 horas.

## ¿Qué tipos de pruebas se realizan en mi sistema después de la actualización?

Consulte la [lista de comprobación de actualización de compilaciones](#check-list) a continuación.

## ¿Qué tipo de prueba debo realizar después de la actualización?

Los entornos de desarrollo y de fase se actualizan de forma secuencial o conjunta, pero se necesita una firma antes de actualizar la instancia de producción. Esto permite a cada cliente realizar pruebas exhaustivas antes de cerrar sesión en cualquier cambio en la producción.

Consulte la [lista de comprobación de actualización de compilaciones ](#check-list)más abajo. Los clientes deben ejecutar pruebas similares y todas las que puedan necesitar para el entorno.

## ¿Con qué frecuencia debo realizar una actualización de compilación?

Para garantizar un rendimiento, disponibilidad y seguridad óptimos del sistema, Adobe se asociará con los clientes para garantizar que los sistemas se actualicen al menos una vez al año.

## ¿Se cerrará con una actualización de compilación?

Sí. El servidor se apaga durante la actualización para garantizar que se conserva la integridad de los datos mientras se actualiza el producto. Una vez finalizado, se reinicia y se reanudan todos los servicios.

## ¿Con quién debo contactar para abrir una incidencia de actualización de compilación?

Si tiene problemas tras una actualización de compilación, póngase en contacto con el [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). El Servicio de atención al cliente programa las fechas de compilación y abre los tickets relacionados con la actualización de compilación.

Obtenga más información en [Opciones de ayuda y asistencia para Campaign Classic](https://helpx.adobe.com/es/campaign/kb/ac-support.html)

## Generar lista de comprobación de actualizaciones {#check-list}

### Lista de comprobación posterior a la actualización del servidor de mensajería en la nube

1. Enviar una entrega de prueba
   1. Validar los registros de entregas y el flujo de trabajo relacionado
   1. Validación de la actualización de los registros de seguimiento
   1. Validar vínculos de seguimiento y páginas espejo
1. Confirmar que todos los flujos de trabajo técnicos están en estado de inicio
1. Verificar que todos los procesos también estén activos

### Lista de comprobación posterior a la actualización del servidor de marketing

* ¿Puede iniciar sesión en el servidor? Compruebe que la consola del cliente de Campaign funciona sin que aparezcan errores o advertencias.
* Asegúrese de utilizar la misma versión de la consola que la versión de compilación después de la actualización.
* ¿Tiene aplicaciones web que insertan datos en la base de datos de Campaign? Si es así, ejecútelos y
compruebe que pueden insertar nuevos registros a través de la API.
* ¿Puede enviar una prueba de correo electrónico correctamente? Cree una nueva entrega con una plantilla conocida, envíela a
un destinatario de prueba, compruebe la personalización y el vínculo de cancelación de suscripción, y asegúrese de que las páginas espejo funcionen.
* ¿Se están ejecutando todos los flujos de trabajo de ruta críticos? Compruebe los flujos de trabajo, abra el historial de flujo de trabajo y compruebe
que no hay errores.
* ¿Están todas las carpetas presentes, visibles y accesibles? Navegue por diferentes carpetas y verifique
que todo el contenido se muestra y está presente.
* ¿Llegan sus envíos con el huso horario correcto?

   * Verifique la fecha de creación y la fecha de modificación con la marca de tiempo y la zona horaria.
   * Compruebe que la ejecución del cronograma funciona en un flujo de trabajo a la hora especificada.
   * Busque la lista de flujos de trabajo en estado PAUSED y FAILED. Inicio y supervisión
   * Ejecutar prueba AB para un escenario
   * Probar las notificaciones push junto con su funcionalidad de seguimiento para los vínculos profundos
   * Probar el envío de SMS
   * Si tiene algún FDA externo conectado, pruebe si los datos se envían de ambas formas
   * Si utiliza integraciones como Adobe Campaign-Adobe Experience Manager o Adobe Campaign-Adobe Analytics, pruebe si siguen funcionando como antes

**Consulte también**

* [Realización de una actualización de versión](../../production/using/build-upgrade.md)
* [Notas de la versión de Campaign Classic ](../../rn/using/rn-overview.md)
* [Opciones de ayuda y asistencia para Campaign Classic](https://helpx.adobe.com/campaign/kb/ac-support.html)
* [[!DNL Gold Standard] programa](../../rn/using/gs-overview.md)
