---
product: campaign
title: Recomendaciones de tamaño de hardware para Campaign Classic v7
description: Recomendaciones de tamaño de hardware para Campaign Classic v7
feature: Technote
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
exl-id: c47e73a0-dbd8-43f5-a363-7e6783dc7685
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '2519'
ht-degree: 1%

---

# Recomendaciones de tamaño de hardware{#hardware-sizing-reco}



## Información general

>[!CAUTION]
>
>Este artículo se proporciona solo como guía de ejemplo general. Debe ponerse en contacto con el administrador de satisfacción del cliente de Adobe Campaign para medir el tamaño exacto de la implementación antes de iniciar el proyecto de Campaign. **No hacer** adquiera o implemente cualquier infraestructura o hardware hasta que esto se haga.

Este documento proporciona recomendaciones generales para la implementación de Adobe Campaign Classic v7 en su centro de datos local o entorno de nube virtualizado. Este tipo de implementación, denominado **híbrido** o **intermediario**, coloca la instancia de marketing de Campaign y la base de datos de marketing bajo su control operativo, mientras utiliza los servicios de mensajería de Adobe Cloud para enviar correos electrónicos, SMS o mensajes SMPP, y recopilar datos de aperturas, devoluciones y rastreos de clics por correo electrónico.

La instancia de marketing es la parte de la arquitectura de Adobe Campaign que administra toda la actividad de marketing y almacena todos los datos de destinatario y los datos de análisis devueltos por las campañas. La instancia de marketing es un conjunto de servidores locales que ejecutan Adobe Campaign Services y una base de datos relacional.

>[!CAUTION]
>
>La información contenida en este documento no se aplica si utiliza una instancia de Adobe Campaign totalmente alojada (implementada en Cloud Service de Adobe).

La compatibilidad del software se detalla en la [Matriz de compatibilidad](../../rn/using/compatibility-matrix.md).


### Escenarios

Se proporcionan diagramas de implementación y recomendaciones de tamaño de hardware para tres escenarios representativos:

1. [De Tamaño Moderado](#scenario-1) - 5 millones de destinatarios activos en el sistema
1. [De Gran Tamaño](#scenario-2) - 20 millones de destinatarios activos en el sistema
1. [Empresa](#scenario-3) - 50 millones de destinatarios activos, con mensajería transaccional

### Suposiciones

Este documento supone también los siguientes tipos de uso para los tres casos:

* Las campañas de correo electrónico grandes se envían dos veces a la semana a aproximadamente el 50 % de los destinatarios activos
* Los envíos de correo postal se generan una vez al mes para cada destinatario del sistema
* Los mensajes SMS se envían aproximadamente al 10 % de los destinatarios activos cada mes
* El esquema de base de datos que define cada destinatario se ha ampliado con una tabla adicional, que contiene unos 200 bytes de datos para cada destinatario
* El módulo de interacción de Adobe Campaign se utiliza para añadir ofertas al correo electrónico saliente
* Los datos de seguimiento de correo electrónico se conservan en el sistema de Campaign durante 90 días

## Directrices generales

Campaign es una aplicación centrada en la base de datos, y el rendimiento del servidor de la base de datos es fundamental. La ejecución de flujos de trabajo, segmentación, seguimiento de cargas de datos, interacciones entrantes, análisis y otras actividades genera actividad de base de datos. En general, el tamaño y la frecuencia de estas operaciones determinan el tamaño de los servidores de base de datos.

Los servidores de aplicaciones de la instancia de marketing requieren suficiente CPU y memoria para ejecutar flujos de trabajo y responder a llamadas a la API de SOAP, incluidas las solicitudes de los usuarios de la consola de Campaign. Los requisitos de CPU pueden ser significativos para flujos de trabajo que utilizan interacciones salientes con reglas de oferta complejas, flujos de trabajo que ejecutan JavaScript personalizado y aplicaciones web con niveles de tráfico elevados.

Las aplicaciones web de Campaign también se pueden implementar en los servidores de aplicaciones de la instancia de marketing o en sistemas de servidores web independientes. Dado que las cargas de trabajo de las aplicaciones web entran en conflicto con los flujos de trabajo críticos y los usuarios de la consola de Campaign, las aplicaciones web y las interacciones entrantes se pueden implementar en servidores independientes para garantizar que la funcionalidad principal de Campaign se ejecute de forma fiable con un buen rendimiento.

Por motivos de seguridad y disponibilidad, Adobe recomienda separar el tráfico de Internet del tráfico generado por los usuarios empresariales. Por este motivo, los diagramas contienen dos grupos de servidores: el servidor web (Internet orientado a Web1 y Web2) y los servidores de aplicaciones (los procesos empresariales App1 y App2).

Es un requisito legal que los remitentes de correo electrónico comerciales tengan una página web de exclusión funcional. Adobe recomienda tener una máquina redundante en cada servidor de grupo para escenarios de conmutación por error. Esto es especialmente cierto si Adobe Campaign aloja las páginas de exclusión.

### Proxy inverso

La arquitectura de Campaign impone una alta seguridad utilizando SSL a través de HTTP (HTTPS) para comunicarse entre su instancia de marketing y la mensajería de Adobe Cloud. La seguridad, fiabilidad y disponibilidad se aplican mediante el uso de proxies inversos en una subred de &quot;zona desmilitarizada&quot; (DMZ) para aislar y proteger los servidores y la base de datos de instancias de marketing.

### Equilibrador de carga

El equilibrador de carga de los servidores de aplicaciones se configura en una configuración activa/pasiva, con HTTPS finalizado en el proxy. El equilibrador de carga de los servidores web se configura en una configuración activa/activa, con HTTPS finalizado en el proxy.

El Adobe le proporciona la lista exclusiva de rutas URL que se pueden retransmitir al servidor de Adobe Campaign en el entorno de implementación.

### Arquitectura

La arquitectura general es casi idéntica independientemente de los volúmenes. Los requisitos de seguridad y alta disponibilidad dictan un mínimo de cuatro servidores; dos servidores si no se utiliza ninguna aplicación web. La diferencia en la configuración varía principalmente en la configuración del hardware, como el núcleo de la CPU y la memoria.

## Escenario 1: implementación moderada{#scenario-1}

![](assets/scenario-1.png)

Volumen estimado:

| Canal | Volumen |
| ----------------------- | ----------------- |
| Destinatarios activos | 5 millones |
| Correo electrónico | 4,2 millones/mes |
| Correo directo | 1 millón/mes |
| SMS móvil | 100.000 al mes |
| Volumen diario máximo de correo electrónico | 500 |

Para estos volúmenes, un par de sistemas de servidor de aplicaciones de Adobe Campaign proporciona toda la funcionalidad para los usuarios del cliente de Adobe Campaign y la ejecución del flujo de trabajo. Para 5 millones de destinatarios activos y este volumen de correo electrónico, las cargas de trabajo del servidor de aplicaciones no son intensivas en CPU ni en E/S; la mayor parte del estrés está en la base de datos.

Los servidores web de Adobe Campaign se muestran en la zona segura.

### Servidores web y de aplicaciones

Este escenario recomienda instalar Adobe Campaign en cuatro equipos, con la siguiente especificación:

**CPU de núcleo cuádruple a 3 GHz+, 8 GB de RAM, RAID 1 o 10, 2 SSD de 80 GB**

Estos sistemas crean la instancia de marketing Application Server, que da soporte directamente a los usuarios de la consola de Campaign y ejecuta los flujos de trabajo de la campaña.

Invertir proxies en una DMZ equilibra el tráfico de carga a los servidores web de Adobe Campaign. No es necesario instalar la pila de software de Adobe Campaign en máquinas proxy; se puede utilizar cualquier software de proxy inverso o equipo de red.

Las funciones de inclusión/exclusión de suscripción y del centro de preferencias las puede proporcionar Campaign o su propio sitio web. Si decide implementar esta funcionalidad en el sitio web, debe asegurarse de que la información de preferencias y suscripciones se propague a la base de datos de marketing de Campaign. Normalmente se realiza creando archivos de extracción que los flujos de trabajo de Campaign cargan automáticamente.

El consumo de espacio en disco en los servidores de aplicaciones depende del período de retención de archivos intercambiados con proveedores de servicios de terceros (por ejemplo, proveedores de impresión para correo postal) y del tamaño y la retención de archivos planos importados, como actualizaciones de suscripciones o preferencias de su sitio web, o extractos de sus propios sistemas de CRM o marketing.

### Database

Las recomendaciones de hardware para el servidor de bases de datos son las siguientes:

**CPU de 4 núcleos a 3 Ghz+, 16 GB de RAM, RAID 1 o 10, SSD de 128 GB como mínimo**

La estimación de memoria supone un almacenamiento en caché completo de aproximadamente 500 000 destinatarios para un inicio de campaña de gran tamaño, además de espacio en búfer RDBMS para ejecutar flujos de trabajo, importar datos de seguimiento y otras actividades simultáneas.

Se estima que el espacio en disco necesario en la base de datos para almacenar todos los datos técnicos de Adobe Campaign (campañas, seguimiento, tablas de trabajo, etc.) es de aproximadamente 35 GB en función de un periodo de retención de tres meses. Si decide conservar los datos de seguimiento durante 6 meses, el tamaño de la base de datos aumenta hasta aproximadamente 40 GB y la retención de 12 meses aumenta el tamaño de la base de datos hasta aproximadamente 45 GB. Los datos del destinatario consumen unos 5 GB para este entorno.

>[!CAUTION]
>
>Esta estimación no incluye datos de clientes adicionales. Si planea replicar columnas o tablas adicionales de datos de clientes en la base de datos de Adobe Campaign, debe estimar el espacio en disco adicional necesario para ello. Los segmentos o listas cargados también requieren más almacenamiento, según su tamaño, frecuencia y período de retención.

Tenga en cuenta también que debido al volumen de información procesada diariamente, las IOPS del servidor de la base de datos son críticas. Por ejemplo, en un día récord, puede implementar campañas dirigidas a un total de 500 000 destinatarios. Para ejecutar cada campaña, Adobe Campaign inserta 500 000 registros en una tabla que contiene aproximadamente 12 millones de registros (la tabla de registro de envíos). Para proporcionar un rendimiento aceptable durante la implementación de la campaña, Adobe recomienda un mínimo de 60 000 IOPS aleatorias de lectura y escritura de 4 KB para este escenario.


## Escenario 2: implementación de gran tamaño{#scenario-2}

![](assets/scenario-2.png)

Volumen estimado:

| Canal | Volumen |
| ----------------------- | ----------------- |
| Destinatarios activos | 20 millones |
| Correo electrónico | 42 millones/mes |
| Correo directo | 10 millones/mes |
| SMS móvil | 1.000.000/mes |
| Volumen diario máximo de correo electrónico | 5,000,000 |

### Servidores web y de aplicaciones

En esta situación, Adobe recomienda instalar Adobe Campaign en cuatro equipos, dos servidores de aplicaciones y dos servidores web, con la siguiente especificación:

**CPU de núcleo cuádruple a 3 GHz+, 8 GB de RAM, RAID 1 o 10, SSD de 80 GB**

Los servidores de aplicaciones admiten directamente a los usuarios de la consola de Campaign y la ejecución de flujos de trabajo de campaña. Esta funcionalidad se implementa en dos servidores idénticos para alta disponibilidad, compartiendo un sistema de archivos de almacenamiento con conexión a red (NAS) para habilitar la conmutación por error.

Los servidores web alojan aplicaciones web de Campaign que admiten los 10 millones de destinatarios activos del sistema.

Consulte [Escenario 1: implementación moderada](#scenario-1) para obtener más comentarios sobre los proxies, los centros de preferencias/gestión de suscripciones y el uso del espacio en disco.

### Database

Las recomendaciones de hardware para el servidor de bases de datos son las siguientes:

**CPU de 8 núcleos a 3 Ghz+, 64 GB de RAM, RAID 1 o 10, 2 SSD de 320 GB o RAID 10, SSD de 640 GB como mínimo**

La estimación de memoria supone un almacenamiento en caché completo de aproximadamente 5 000 000 de destinatarios para un inicio de campaña de gran tamaño, además de espacio en búfer RDBMS para ejecutar flujos de trabajo, importar datos de seguimiento y otras actividades simultáneas.

Se estima que el espacio en disco necesario en la base de datos para almacenar todos los datos técnicos de Adobe Campaign (campañas, seguimiento, tablas de trabajo, etc.) es de aproximadamente 280 GB en función de un periodo de retención de 3 meses. Si decide conservar los datos de seguimiento durante 6 meses, el tamaño de la base de datos aumenta hasta aproximadamente 450 GB y la retención de 12 meses aumenta el tamaño de la base de datos hasta aproximadamente 900 GB. Los datos del destinatario consumen unos 15 GB para este entorno.

## Escenario 3: implementación empresarial con centro de mensajes{#scenario-3}

![](assets/scenario-3.png)

Volumen estimado:

| Canal | Volumen |
| ----------------------- | ----------------- |
| Destinatarios activos | 50 millones |
| Correo electrónico | 108 millones/mes |
| Correo directo | 25 millones/mes |
| SMS móvil | 2,5 millones/mes |
| Mensajes transaccionales | 2,5 millones/mes |
| Volumen diario máximo de correo electrónico | 2,5 millones |


La implementación que admite 50 millones de destinatarios es esencialmente la misma que se muestra en [Escenario 2](#scenario-2): el tráfico de la aplicación web de Campaign se enruta a los servidores web de Campaign, por lo que las ráfagas de tráfico web después de grandes lanzamientos de campañas no afectan a los flujos de trabajo de Campaign ni a los usuarios de la consola del cliente.

Esta implementación también incluye llamadas del Centro de mensajería, impulsadas desde sus propios sitios web y aplicaciones.


### Servidores web y de aplicaciones

En esta situación, Adobe recomienda instalar Adobe Campaign en cuatro equipos, como se indica a continuación:

* Servidores de aplicaciones
  **Dos sistemas, CPU de núcleo cuádruple a más de 3 Ghz, 8 GB de RAM, RAID 1 o 10, SSD de 80 GB**

* Servidores web
  **Dos sistemas, CPU de núcleo cuádruple a más de 3 GHz, 16 GB de RAM, RAID 1 o 10, SSD de 80 GB**


Los servidores de aplicaciones admiten directamente a los usuarios de la consola de Campaign y la ejecución de flujos de trabajo de campaña. Esta funcionalidad se implementa en dos servidores idénticos para alta disponibilidad, compartiendo un sistema de archivos de almacenamiento con conexión a red (NAS) para habilitar la conmutación por error.

Los servidores web alojan aplicaciones web de Campaign que admiten los 10 millones de destinatarios activos del sistema.

Consulte [Escenario 1: implementación moderada](#scenario-1) para obtener más comentarios sobre los proxies, los centros de preferencias/gestión de suscripciones y el uso del espacio en disco.

### Database

Las recomendaciones de hardware para el servidor de bases de datos son las siguientes:

**CPU de 8 núcleos a 3 GHz+, RAM de 96 GB, RAID 1 o 10, SSD de 1,5 TB como mínimo**

La estimación de memoria supone un almacenamiento en caché completo de aproximadamente 12 500 000 destinatarios para un inicio de campaña de gran tamaño, además de espacio en búfer RDBMS para ejecutar flujos de trabajo, importar datos de seguimiento y otras actividades simultáneas.

Se estima que el espacio en disco necesario en la base de datos para almacenar todos los datos técnicos de Adobe Campaign (campañas, seguimiento, tablas de trabajo, etc.) es de aproximadamente 700 GB en función de un periodo de retención de 3 meses. Si decide conservar los datos de seguimiento durante 6 meses, el tamaño de la base de datos aumenta hasta aproximadamente 1,2 TB y la retención de 12 meses aumenta el tamaño de la base de datos hasta aproximadamente 2 TB. Los datos del destinatario consumen unos 50 GB para este entorno.

## Directrices para cambiar suposiciones

Las suposiciones realizadas para estos escenarios tienen un impacto significativo en las recomendaciones de hardware y en la arquitectura de implementación. En esta sección se describen las directrices que rigen las distintas suposiciones. Póngase en contacto con el equipo de consultoría de Adobe Campaign para obtener recomendaciones específicas que satisfagan sus necesidades.

* **Número de destinatarios**
Los destinatarios activos requieren tanto espacio de almacenamiento como espacio de búfer de base de datos, por lo que un mayor número de destinatarios suele requerir más memoria y capacidad de CPU en el servidor de base de datos. Los incrementos de almacenamiento son relativamente pequeños para los propios destinatarios, pero pueden ser significativos para los datos de seguimiento de eventos que se conservan para las campañas de correo electrónico.

* **Tamaño de campaña de correo electrónico**
La frecuencia de los lanzamientos de campañas afecta a los requisitos de CPU del servidor de bases de datos. Combinadas con el correo directo, las interacciones entrantes y otros flujos de trabajo, las operaciones de segmentación para campañas de correo electrónico suponen una carga significativa en el servidor de la base de datos.

* **Frecuencia de correo directo**
La frecuencia de los correos directos puede afectar a los requisitos de CPU del servidor de base de datos. Combinadas con lanzamientos de campañas y otros flujos de trabajo, las operaciones de segmentación para correos directos suponen una carga significativa en el servidor de la base de datos.

* **Volumen del mensaje SMS**
Al igual que el tamaño de la campaña de correo electrónico, el volumen de mensajes SMS no coloca grandes cargas en servidores de Campaign ubicados en las instalaciones; la carga se realiza principalmente en servidores de mensajería de Adobe Cloud en la nube. La segmentación para campañas SMS, como correo electrónico y correo directo, puede suponer una carga significativa en la base de datos de marketing. Por lo tanto, la frecuencia de los lanzamientos de campañas SMS y la complejidad de la segmentación son más relevantes que el volumen de mensajes SMS.

* **Complejidad del esquema de base de datos**
La cantidad de datos para cada destinatario activo requiere tanto espacio de almacenamiento como espacio de búfer de base de datos, por lo que más destinatarios generalmente requieren más memoria y CPU en el servidor de base de datos. Los esquemas complejos también requieren que se unan más tablas para la segmentación, por lo que las operaciones de segmentación pueden ejecutarse mucho más lentamente y requieren más CPU y memoria de base de datos cuando los datos se distribuyen en varias tablas.

  La memoria del servidor de base de datos se calcula asegurando que el grupo de búferes de base de datos puede ser lo suficientemente grande como para contener todos los datos de destinatario, además de tablas temporales para ejecutar flujos de trabajo, más un margen para otras operaciones de base de datos.

* **Uso de interacción saliente**
Las reglas para interacción en modo por lotes se evalúan en flujos de trabajo que transfieren toda la complejidad del cálculo a la base de datos. El principal factor de esfuerzo de la base de datos es la cantidad total de ofertas aptas calculadas durante una visualización del motor (tamaño del objetivo X cantidad promedio de ofertas por destinatario antes de mantener las N mejores ofertas). La velocidad de CPU del servidor de base de datos es el primer factor de rendimiento.

* **Interacciones entrantes o uso de API de SOAP**
Las reglas y ofertas de interacción entrantes se evalúan en la base de datos de marketing, lo que requiere recursos significativos del servidor de la base de datos, especialmente CPU. El uso intensivo de interacciones entrantes o API de SOAP requiere servidores web independientes para separar la carga de trabajo de la ejecución de flujos de trabajo de Campaign.

* **Período de retención de datos de seguimiento**
El aumento de la retención de datos de seguimiento más allá de 90 días requiere más almacenamiento de la base de datos y puede ralentizar el sistema, ya que la inserción de nuevos datos de seguimiento se dirige a tablas grandes. El seguimiento de datos no es útil para la segmentación de campañas después de 90 días, por lo que se recomienda un período de retención más corto.

  Los datos de seguimiento deben moverse a Adobe Analytics u otro sistema de análisis si necesita un análisis a largo plazo de la experiencia de marketing del destinatario.

## Virtualización

Todos los servidores de Campaign son buenos candidatos para la virtualización. Se deben abordar varios problemas para garantizar una disponibilidad y un rendimiento adecuados.

* **Configuración de conmutación por error**
Los servidores agrupados, por ejemplo, los servidores de aplicaciones redundantes bajo un proxy de equilibrio de carga, deben implementarse en hardware independiente para garantizar que ambas VM no se desactiven si se produce un error de hardware.

* **Configuración de E/S**
Cualquier configuración RAID recomendada debe mantenerse para la seguridad de la base de datos, a fin de garantizar que la pérdida de un dispositivo de almacenamiento no cause la pérdida de datos.

* **Rendimiento de E/S**
Se debe respetar la clasificación de IOPS recomendada para el almacenamiento de la base de datos. Es posible que los servicios en la nube como Amazon EC2 no proporcionen el rendimiento requerido y deben evaluarse cuidadosamente. Por ejemplo, los volúmenes SSD aprovisionados por Amazon EC2 se clasifican actualmente en 20 000 IOPS cada uno. Obtenga más información en [Documentación de Amazon](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volume-types.html)), por lo que una configuración RAID de 4 volúmenes se clasificaría en 80 000 IOPS, lo que puede no ser suficiente.

Adobe recomienda realizar pruebas de rendimiento para cualquier implementación virtualizada de Adobe Campaign antes de poner el sistema en producción.

## Temas relacionados

* [Procesos de monitorización de Campaign](../../production/using/monitoring-processes.md)
* [Arquitectura general de Campaign](../../installation/using/general-architecture.md)
* [Problemas de rendimiento y producción](../../production/using/performance-and-throughput-issues.md)
* [Lista de comprobación de seguridad y privacidad](../../installation/using/get-started-security-privacy.md)
