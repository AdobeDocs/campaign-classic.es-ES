---
product: campaign
title: Recomendaciones de tamaño de hardware para Campaign Classic v7
description: Recomendaciones de tamaño de hardware para Campaign Classic v7
source-git-commit: 3912874210ab16a132e51d9bb71508c8d244fe22
workflow-type: tm+mt
source-wordcount: '2513'
ht-degree: 1%

---

# Recomendaciones de tamaño de hardware para Campaign Classic v7 {#hardware-sizing-reco}

![](../../assets/v7-only.svg)

## Información general

>[!CAUTION]
>
>Esta guía se proporciona únicamente como guía de ejemplo general. Debe ponerse en contacto con el administrador de éxito de los clientes de Adobe Campaign para medir el tamaño exacto de la implementación antes de iniciar el proyecto de Campaign. **No** adquiera ni implemente ninguna infraestructura o hardware hasta que esto se haga.

Este documento proporciona directrices generales para la implementación de Adobe Campaign Classic v7 en su centro de datos local o entorno de nube virtualizado. Este tipo de implementación, denominada **hybrid** o **mid-sourcing**, coloca la instancia de marketing de Campaign y la base de datos de marketing bajo su control operativo, mientras utiliza los servicios de mensajería de Adobe Cloud para enviar correos electrónicos, SMS o mensajes SMPP, y recopilar datos de seguimiento de aperturas, devoluciones y clics de correos electrónicos.

La instancia de marketing es la parte de la arquitectura de Adobe Campaign que impulsa toda la actividad de marketing y almacena todos los datos de destinatario y los datos de análisis devueltos por las campañas. La instancia de marketing es un conjunto de servidores locales que ejecutan servicios de Adobe Campaign y una base de datos relacional.

>[!CAUTION]
>
>La información de este documento no se aplica si utiliza una instancia de Adobe Campaign totalmente alojada (implementada en Cloud Services de Adobe).

La compatibilidad del software se detalla en la [Matriz de compatibilidad](../../rn/using/compatibility-matrix.md).


### Situaciones

Se proporcionan diagramas de implementación y recomendaciones de tamaño de hardware para tres escenarios representativos:

1. [Tamaño moderado](#scenario-1) : 5 millones de destinatarios activos en el sistema
1. [Tamaño grande](#scenario-2) : 20 millones de destinatarios activos en el sistema
1. [Enterprise](#scenario-3) : 50 millones de destinatarios activos, con mensajería transaccional

### Suposiciones

Este documento también asume los siguientes tipos de uso para los tres escenarios:

* Dos veces a la semana se envían grandes campañas de correo electrónico a aproximadamente el 50 % de los destinatarios activos
* Los correos directos se generan una vez al mes para cada destinatario en el sistema
* Los mensajes SMS se envían a aproximadamente el 10 % de sus destinatarios activos cada mes
* El esquema de la base de datos que define cada destinatario se ha ampliado con una tabla adicional que contiene unos 200 bytes de datos para cada destinatario
* El módulo Interacción de Adobe Campaign se utiliza para añadir ofertas al correo electrónico saliente
* Los datos de seguimiento de correo electrónico se conservan en el sistema de Campaign durante 90 días

## Directrices generales

Campaign es una aplicación centrada en las bases de datos y el rendimiento del servidor de las bases de datos es fundamental. La ejecución de flujos de trabajo, segmentación, seguimiento de cargas de datos, interacciones entrantes, análisis y otras actividades genera actividad en la base de datos. En general, el tamaño y la frecuencia de estas operaciones determinan el tamaño de los servidores de base de datos.

Los servidores de aplicaciones de la instancia de marketing requieren suficiente CPU y memoria para ejecutar flujos de trabajo y responder a llamadas de API SOAP, incluidas las solicitudes de los usuarios de la consola de Campaign. Los requisitos de CPU pueden ser importantes para los flujos de trabajo que utilizan interacciones salientes con reglas de oferta complejas, flujos de trabajo que ejecutan JavaScript personalizado y aplicaciones web con altos niveles de tráfico.

Las aplicaciones web de Campaign también se pueden implementar en la instancia de marketing de los servidores de aplicaciones o en sistemas de servidores web independientes. Dado que las cargas de trabajo de las aplicaciones web entran en conflicto con los flujos de trabajo críticos y los usuarios de la consola de Campaign, las aplicaciones web y las interacciones entrantes se pueden implementar en servidores separados para garantizar que la funcionalidad principal de Campaign se ejecute de forma fiable con un buen rendimiento.

Para garantizar la seguridad y la disponibilidad, Adobe recomienda separar el tráfico de Internet del tráfico generado por los usuarios empresariales. Por este motivo, los diagramas contienen dos grupos de servidores: el servidor web (para Web1 y Web2) y los servidores de aplicaciones (para los procesos empresariales App1 y App2).

Es un requisito legal que los remitentes de correo electrónico comerciales tengan una página web de exclusión funcional. Adobe recomienda tener una máquina redundante en cada servidor de grupo para situaciones de conmutación por error. Es especialmente cierto si Adobe Campaign aloja las páginas de exclusión.

### Sustitutos inversa

La arquitectura de Campaign impone una alta seguridad al utilizar SSL sobre HTTP (HTTPS) para comunicarse entre la instancia de marketing y la mensajería de Adobe Cloud. La seguridad, la fiabilidad y la disponibilidad se refuerzan utilizando proxies inversos en una subred de &quot;zona desmilitarizada&quot; (DMZ) para aislar y proteger los servidores y la base de datos de instancias de marketing.

### Equilibrio de carga

El equilibrador de carga para los servidores de aplicaciones se configura en una configuración activa/pasiva, con HTTPS finalizado en el proxy. El equilibrador de carga para los servidores web se configura en una configuración activa/activa, con HTTPS finalizado en el proxy.

Adobe le proporciona la lista exclusiva de rutas de URL que se pueden retransmitir al servidor de Adobe Campaign en su entorno de implementación.

### Arquitectura

La arquitectura general es casi idéntica independientemente de los volúmenes. Los requisitos de seguridad y alta disponibilidad dictan un mínimo de cuatro servidores; dos servidores si no se utilizan WebApps. La diferencia en la configuración varía principalmente en la configuración del hardware, como el núcleo de la CPU y la memoria.

## Escenario 1: Implementación de tamaño moderado{#scenario-1}

![](assets/scenario-1.png)

Volumen estimado:

| Canal | Volumen |
| ----------------------- | ----------------- |
| Destinatarios activos | 5 millones |
| Correo electrónico | 4,2 millones/mes |
| Correo directo | 1 millón/mes |
| SMS móvil | 100.000/mes |
| Volumen máximo diario de correo electrónico | 500 |

Para estos volúmenes, un par de sistemas de servidor de aplicaciones de Adobe Campaign proporciona toda la funcionalidad para los usuarios de Adobe Campaign Client y la ejecución del flujo de trabajo. Para 5 millones de destinatarios activos y este volumen de correo electrónico, las cargas de trabajo de los servidores de aplicaciones no son intensivas en CPU o E/S; la mayor parte del estrés está en la base de datos.

Los servidores web de Adobe Campaign se muestran en la zona segura.

### Servidores Web y de aplicaciones

En esta situación se recomienda instalar Adobe Campaign en cuatro equipos, con la siguiente especificación:

**CPU de núcleo cuádruple de 3 Ghz+, 8 GB de RAM, RAID 1 o 10, 2 x SSD de 80 GB**

Estos sistemas crean la instancia de marketing Application Server, que es compatible directamente con los usuarios de la consola de Campaign y ejecuta los flujos de trabajo de la campaña.

Revierta los proxies en un tráfico de equilibrio de carga DMZ a los servidores web de Adobe Campaign. No es necesario instalar la pila de software de Adobe Campaign en máquinas proxy; se puede utilizar cualquier software de proxy inverso o equipo de red.

Campaign o su propio sitio web pueden proporcionar las funciones de inclusión/exclusión de suscripción y del centro de preferencias. Si decide implementar esta funcionalidad en su sitio web, debe asegurarse de que la información de preferencias y suscripciones se propague a la base de datos de marketing de Campaign. Normalmente se realiza creando archivos de extracción que los flujos de trabajo de Campaign cargan automáticamente.

El consumo de espacio en disco en los servidores de aplicaciones depende del período de retención de archivos intercambiados con proveedores de servicios de terceros (por ejemplo, proveedores de impresión para correo directo), del tamaño y la retención de archivos planos importados, como las actualizaciones de suscripción o preferencias de su sitio web, o de los extractos de su propio CRM o sistema de marketing.

### Database

Las recomendaciones de hardware para el servidor de la base de datos son las siguientes:

**CPU de 4 núcleos de 3 Ghz+, RAM de 16 GB, RAID 1 o 10, SSD de 128 GB mínimo**

La estimación de la memoria supone el almacenamiento en caché completo de aproximadamente 500 000 destinatarios para un lanzamiento de campaña grande, además del espacio de búfer RDBMS para ejecutar flujos de trabajo, importar datos de seguimiento y otras actividades simultáneas.

Se estima que el espacio en disco necesario en la base de datos para almacenar todos los datos técnicos de Adobe Campaign (campañas, seguimiento, tablas de trabajo, etc.) es de aproximadamente 35 GB en función de un período de retención de tres meses. Si decide conservar los datos de seguimiento durante 6 meses, el tamaño de la base de datos aumenta a aproximadamente 40 GB y la retención de 12 meses aumenta el tamaño de la base de datos a aproximadamente 45 GB. Los datos de destinatario consumen aproximadamente 5 GB para este entorno.

>[!CAUTION]
>
>Esta estimación no incluye datos de cliente adicionales. Si planea replicar columnas o tablas adicionales de datos de clientes en la base de datos de Adobe Campaign, debe estimar el espacio en disco adicional necesario para ella. Los segmentos o listas cargados también requieren más almacenamiento, según su tamaño, frecuencia y período de retención.

Tenga en cuenta también que, debido al volumen de información procesada diariamente, el IOPS del servidor de base de datos es crítico. Por ejemplo, en un día pico, puede implementar campañas dirigidas a un total de 500.000 destinatarios. Para ejecutar cada campaña, Adobe Campaign inserta 500 000 registros en una tabla que contiene aproximadamente 12 millones de registros (la tabla de registro de entregas). Para proporcionar un rendimiento aceptable durante la implementación de la campaña, Adobe recomienda un mínimo de 60 000 IOPS aleatorias de lectura y escritura de 4 KB para este escenario.


## Escenario 2: Implementación de gran tamaño{#scenario-2}

![](assets/scenario-2.png)

Volumen estimado:

| Canal | Volumen |
| ----------------------- | ----------------- |
| Destinatarios activos | 20 millones |
| Correo electrónico | 42 millones/mes |
| Correo directo | 10 millones al mes |
| SMS móvil | 1 000 000 al mes |
| Volumen máximo diario de correo electrónico | 5 000 000 |

### Servidores Web y de aplicaciones

En esta situación, Adobe recomienda instalar Adobe Campaign en cuatro equipos, dos servidores de aplicaciones y dos servidores web, con la siguiente especificación:

**CPU de núcleo cuádruple de 3 Ghz+, 8 GB de RAM, RAID 1 o 10, SSD de 80 GB**

Los servidores de aplicaciones admiten directamente a los usuarios de Campaign Console y la ejecución de flujos de trabajo de campaña. Esta funcionalidad se implementa en dos servidores idénticos para alta disponibilidad, compartiendo un sistema de archivos de almacenamiento conectado a la red (NAS) para permitir failover.

Los servidores web alojan aplicaciones web de Campaign que admiten los 10 millones de destinatarios activos del sistema.

Consulte [Escenario 1: Implementación de tamaño moderado](#scenario-1) para obtener más comentarios sobre proxies, centros de preferencias/administración de suscripciones y uso del espacio en disco.

### Base de datos

Las recomendaciones de hardware para el servidor de la base de datos son las siguientes:

**CPU de 8 núcleos de 3 Ghz+, 64 GB de RAM, RAID 1 o 10, 2 SSD de 320 GB o SSD RAID de 10, 640 GB mínimo**

El cálculo de la memoria supone el almacenamiento en caché completo de aproximadamente 5 000 000 destinatarios para un lanzamiento de campaña grande, además del espacio de búfer RDBMS para ejecutar flujos de trabajo, importar datos de seguimiento y otras actividades simultáneas.

Se estima que el espacio en disco necesario en la base de datos para almacenar todos los datos técnicos de Adobe Campaign (campañas, seguimiento, tablas de trabajo, etc.) es de aproximadamente 280 GB en función de un período de retención de 3 meses. Si decide conservar los datos de seguimiento durante 6 meses, el tamaño de la base de datos aumenta a aproximadamente 450 GB y la retención de 12 meses aumenta el tamaño de la base de datos a aproximadamente 900 GB. Los datos de destinatario consumen unos 15 GB para este entorno.

## Escenario 3: Implementación empresarial con centro de mensajes{#scenario-3}

![](assets/scenario-3.png)

Volumen estimado:

| Canal | Volumen |
| ----------------------- | ----------------- |
| Destinatarios activos | 50 millones |
| Correo electrónico | 108 millones/mes |
| Correo directo | 25 millones/mes |
| SMS móvil | 2,5 millones/mes |
| Mensajes transaccionales | 2,5 millones/mes |
| Volumen máximo diario de correo electrónico | 2,5 millones |


La implementación que admite 50 millones de destinatarios es esencialmente la misma que se muestra en [Escenario 2](#scenario-2): El tráfico de la aplicación web de Campaign se redirige a los servidores web de Campaign, por lo que los estallidos de tráfico web después de que se inicien campañas grandes no afectan a los flujos de trabajo de Campaign ni a los usuarios de la consola de cliente.

Esta implementación también incluye llamadas al Centro de mensajes, dirigidas desde sus propios sitios web y aplicaciones.


### Servidores Web y de aplicaciones

En esta situación, Adobe recomienda instalar Adobe Campaign en cuatro equipos de la siguiente manera:

* Servidores de aplicaciones
   **Dos sistemas, CPU de núcleo cuádruple de 3 Ghz+, 8 GB de RAM, RAID 1 o 10, SSD de 80 GB**

* Servidores web
   **Dos sistemas, CPU de núcleo cuádruple de 3 Ghz+, RAM de 16 GB, RAID 1 o 10, SSD de 80 GB**


Los servidores de aplicaciones admiten directamente a los usuarios de Campaign Console y la ejecución de flujos de trabajo de campaña. Esta funcionalidad se implementa en dos servidores idénticos para alta disponibilidad, compartiendo un sistema de archivos de almacenamiento conectado a la red (NAS) para permitir failover.

Los servidores web alojan aplicaciones web de Campaign que admiten los 10 millones de destinatarios activos del sistema.

Consulte [Escenario 1: Implementación de tamaño moderado](#scenario-1) para obtener más comentarios sobre proxies, centros de preferencias/administración de suscripciones y uso del espacio en disco.

### Base de datos

Las recomendaciones de hardware para el servidor de la base de datos son las siguientes:

**CPU de 8 núcleos de 3 Ghz+, RAM de 96 GB, RAID 1 o 10, SSD de 1,5 TB mínimo**

El cálculo de la memoria supone el almacenamiento en caché completo de aproximadamente 12.500.000 destinatarios para un lanzamiento de campaña grande, además del espacio de búfer RDBMS para ejecutar flujos de trabajo, importar datos de seguimiento y otras actividades simultáneas.

Se estima que el espacio en disco necesario en la base de datos para almacenar todos los datos técnicos de Adobe Campaign (campañas, seguimiento, tablas de trabajo, etc.) es aproximadamente de 700 GB en función de un período de retención de 3 meses. Si decide conservar los datos de seguimiento durante 6 meses, el tamaño de la base de datos aumenta a aproximadamente 1,2 TB y la retención de 12 meses aumenta el tamaño de la base de datos a aproximadamente 2 TB. Los datos de destinatario consumen unos 50 GB para este entorno.

## Directrices para cambiar las hipótesis

Las hipótesis formuladas para estos escenarios tienen un impacto significativo en las recomendaciones de hardware y en la arquitectura de implementación. En esta sección se tratan las directrices sobre diferentes supuestos. Póngase en contacto con el equipo de consultoría de Adobe Campaign para obtener recomendaciones específicas que satisfagan sus necesidades.

* **Número de**
DestinatariosLos destinatarios activos requieren tanto espacio de almacenamiento como espacio de búfer de base de datos, por lo que más destinatarios generalmente requieren más memoria y capacidad de CPU en el servidor de base de datos. Los aumentos de almacenamiento son relativamente pequeños para los propios destinatarios, pero pueden ser significativos para los datos de seguimiento de eventos guardados para las campañas de correo electrónico.

* **Tamaño de campaña de correo electrónicoLa frecuencia de los inicios de campaña tiene un impacto en los requisitos de CPU del servidor de la base de datos.**
Combinadas con el correo directo, las interacciones entrantes y otros flujos de trabajo, las operaciones de segmentación para las campañas de correo electrónico suponen una carga significativa en el servidor de la base de datos.

* **Frecuencia de correo**
directoLa frecuencia de los correos directos puede afectar a los requisitos de CPU del servidor de la base de datos. Combinadas con los lanzamientos de campañas y otros flujos de trabajo, las operaciones de segmentación para los correos directos suponen una carga significativa en el servidor de la base de datos.

* **Mensaje SMS**
VolumeAl igual que el tamaño de la campaña de correo electrónico, el volumen de los mensajes SMS no coloca cargas grandes en los servidores de Campaign ubicados in situ; la carga se realiza principalmente en servidores de mensajería de Adobe Cloud en la nube. La segmentación de campañas SMS, como correo electrónico y correo postal, puede colocar una carga significativa en la base de datos de marketing. Por lo tanto, la frecuencia de los lanzamientos de campañas SMS y la complejidad de la segmentación son más relevantes que el volumen de mensajes SMS.

* **Complejidad del esquema de la base de datosLa cantidad de datos para cada destinatario activo requiere tanto espacio de almacenamiento como espacio de búfer de la base de datos, por lo que más destinatarios generalmente requieren más memoria y CPU en el servidor de la base de datos.**
Los esquemas complejos también requieren que se unan más tablas para la segmentación, por lo que las operaciones de segmentación pueden ejecutarse mucho más lentamente y requieren más CPU y memoria de base de datos cuando los datos se distribuyen en varias tablas.

   La memoria del servidor de la base de datos se calcula asegurándose de que el grupo de búfer de la base de datos sea lo suficientemente grande como para contener todos los datos del destinatario, además de tablas temporales para ejecutar flujos de trabajo, además de un margen para otras operaciones de la base de datos.

* **Las reglas de**
uso de interacción saliente para la interacción en modo por lotes se evalúan en flujos de trabajo que pasan toda la complejidad del cálculo a la base de datos. El principal factor de esfuerzo en la base de datos es el número total de ofertas aptas calculadas durante una llamada al motor (tamaño del objetivo X número promedio de ofertas por destinatario antes de mantener las N mejores ofertas). La velocidad de CPU del servidor de la base de datos es el primer factor de rendimiento.

* **Las interacciones entrantes o el**
uso de la API SOAPLas reglas y ofertas de interacción entrante se evalúan en la base de datos de marketing, lo que requiere recursos importantes del servidor de la base de datos, especialmente la CPU. El uso intensivo de las interacciones entrantes o las API SOAP requiere servidores web independientes para separar la carga de trabajo de la ejecución de flujos de trabajo de Campaign.

* **Seguimiento del**
período de retención de datosPara aumentar la retención de datos de seguimiento más allá de 90 días se requiere más almacenamiento de la base de datos y se puede ralentizar el sistema, ya que la inserción de nuevos datos de seguimiento se introduce en tablas grandes. Los datos de seguimiento no son útiles para la segmentación de campañas después de 90 días, por lo que se recomienda un periodo de retención más corto.

   Los datos de seguimiento se deben mover a Adobe Analytics u otro sistema de análisis si necesita realizar un análisis a largo plazo de la experiencia de marketing de destinatario.

## Virtualización

Todos los servidores de Campaign son buenos candidatos para la virtualización. Hay que abordar varias cuestiones para garantizar una disponibilidad y un rendimiento adecuados.

* **Los servidores**
en clúster de configuración de conmutación por error, por ejemplo, los servidores de aplicaciones redundantes bajo un proxy de carga equilibrada, deben implementarse en hardware independiente para garantizar que ambas VM no se apaguen si se produce una falla en el hardware.

* **Configuración**
de E/SCualquier configuración RAID recomendada debe mantenerse para la seguridad de la base de datos, para garantizar que la pérdida de un dispositivo de almacenamiento no cause pérdida de datos.

* **Rendimiento de E/S**
Se debe respetar la clasificación IOPS recomendada para el almacenamiento de la base de datos. Es posible que los servicios de nube como Amazon EC2 no proporcionen el rendimiento requerido y que deban evaluarse cuidadosamente. Por ejemplo, los volúmenes SSD aprovisionados por Amazon EC2 están actualmente clasificados en 20.000 IOPS cada uno. Obtenga más información en la [documentación de Amazon](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSVolumeTypes.html), por lo que una configuración RAID de 4 volúmenes se clasificaría en 80.000 IOPS, lo que puede no ser suficiente.

Adobe recomienda pruebas de rendimiento para cualquier implementación virtualizada de Adobe Campaign antes de poner el sistema en producción.

## Temas relacionados

* [Procesos de monitorización de campañas](../../production/using/monitoring-processes.md)
* [Problemas de rendimiento y producción](../../production/using/performance-and-throughput-issues.md)
* [Lista de comprobación de seguridad y privacidad](../../installation/using/get-started-security-privacy.md)
