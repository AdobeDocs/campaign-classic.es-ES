---
product: campaign
title: Arquitectura general
description: Descubra cómo instalar y configurar Campaign Classic.
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
exl-id: 04e6dc17-427b-4745-84cc-bf45c03dbf81
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1336'
ht-degree: 0%

---

# Arquitectura general{#general-architecture}

La implementación típica de la solución Adobe Campaign consta de los siguientes componentes:

* **Entorno de cliente personalizado**

   Interfaz gráfica intuitiva en la que los usuarios pueden comunicarse y rastrear ofertas de marketing, crear campañas, revisar y administrar todas las actividades, programas y planes de marketing, incluidos correos electrónicos, flujos de trabajo y páginas de aterrizaje, crear y administrar perfiles de cliente y definir tipos de audiencia de cliente.

* **Entorno de desarrollo**

   Software del lado del servidor que ejecuta las campañas de marketing a través de los canales de comunicación seleccionados, incluidos correos electrónicos, SMS, notificaciones push, correo postal, web o social, en función de las reglas y flujos de trabajo definidos en la interfaz de usuario.

* **Contenedores de base de datos**

   Basándose en la tecnología de bases de datos relacionales, la base de datos de Adobe Campaign almacena toda la información de los clientes, los componentes de campañas, las ofertas y los flujos de trabajo, así como los resultados de las campañas en contenedores de bases de datos de clientes.

Adobe Campaign se basa en una arquitectura orientada a servicios (SOA) y consta de varios módulos funcionales. Estos módulos se pueden implementar en uno o más equipos, en instancias únicas o múltiples, según las restricciones en términos de escalabilidad, disponibilidad y aislamiento de servicio. Por lo tanto, el ámbito de las configuraciones de implementación es muy amplio y abarca un solo equipo central a través de configuraciones que incluyen varios servidores dedicados en varios sitios.

>[!NOTE]
>
>Como proveedor de software, especificamos infraestructuras de hardware y software compatibles. Las recomendaciones de hardware que se ofrecen aquí tienen propósitos meramente informativos y se basan en nuestra experiencia. El Adobe no será responsable de las decisiones que se adopten sobre su base. También dependerá de las reglas y prácticas de su negocio y de la importancia y los niveles de rendimiento requeridos del proyecto.

![](assets/s_ncs_install_architecture.png)

>[!CAUTION]
>
>Si no se indica explícitamente lo contrario, la instalación, las actualizaciones y el mantenimiento de todos los componentes de una plataforma de Adobe Campaign son responsabilidad de los administradores del equipo que los alojen. Esto incluye implementar los requisitos previos para las aplicaciones de Adobe Campaign, así como cumplir con la [Matriz de compatibilidad](../../rn/using/compatibility-matrix.md) de Campaign entre componentes.

## Capa de presentación {#presentation-layer}

Se puede acceder a la aplicación de diferentes maneras, según las necesidades de los usuarios: Cliente enriquecido, cliente ligero o integración de API.

* **Cliente** enriquecido: La interfaz de usuario principal de la aplicación es un cliente enriquecido, es decir, una aplicación nativa (Windows) que se comunica con el servidor de aplicaciones de Adobe Campaign únicamente con protocolos de Internet estándar (SOAP, HTTP, etc.). Esta consola proporciona una buena facilidad de uso para la productividad, utiliza muy poco ancho de banda (mediante el uso de una caché local) y está diseñada para una implementación sencilla. Esta consola se puede implementar desde un explorador de Internet, se puede actualizar automáticamente y no requiere ninguna configuración de red específica porque solo genera tráfico HTTP(S).
* **Cliente** ligero: Se puede acceder a ciertas partes de la aplicación a través de un explorador web simple mediante una interfaz de usuario HTML, que incluye el módulo de informes, las etapas de aprobación de la entrega, las funcionalidades del módulo Distributed Marketing (central/local), la supervisión de instancias, etc. Este modo permite incluir funcionalidades de Adobe Campaign en una intranet o extranet.
* **Integración mediante las API**: En algunos casos, se puede llamar al sistema desde una aplicación externa mediante las API de servicios web expuestas mediante el protocolo SOAP.

## Capa de aplicación lógica {#logical-application-layer}

Adobe Campaign es una plataforma única con diferentes aplicaciones que se combinan para crear una arquitectura abierta y escalable. La plataforma Adobe Campaign está escrita en una capa de aplicación flexible y es fácilmente configurable para satisfacer las necesidades comerciales de una empresa. Esto satisface las crecientes necesidades de la empresa desde una perspectiva funcional, así como desde una perspectiva técnica. La arquitectura distribuida garantiza la escalabilidad lineal del sistema desde miles de mensajes hasta millones de mensajes.

Adobe Campaign se basa en un conjunto de procesos del lado del servidor que funcionan juntos.

Los procesos principales son:

**Servidor de aplicaciones**  (nlserver web)

Este proceso expone toda la gama de funcionalidades de Adobe Campaign a través de las API de servicios web (SOAP - HTTP + XML). Además, puede generar dinámicamente las páginas web utilizadas para el acceso basado en HTML (informes, formularios web, etc.). Para conseguirlo, este proceso incluye un servidor JSP Apache Tomcat. Este es el proceso al que se conecta la consola.

**Motor de flujo de trabajo**  (nlserver wfserver)

Ejecuta los procesos de flujo de trabajo definidos en la aplicación.

También gestiona los flujos de trabajo técnicos que se ejecutan periódicamente, incluidos:

* Seguimiento: Recuperación y consolidación de registros de seguimiento. Permite recuperar los registros del servidor de redirección y crear los indicadores agregados utilizados por el módulo de informes.
* Limpieza: Limpieza de bases de datos. Se utiliza para purgar registros antiguos y evitar que la base de datos crezca exponencialmente.
* Facturación: Envío automático de un informe de actividad para la plataforma (tamaño de la base de datos, número de acciones de marketing, etc.).

**Servidor de entrega**  (nlserver mta)

Adobe Campaign tiene una funcionalidad nativa de difusión por correo electrónico. Este proceso funciona como un agente de transferencia de correo SMTP (MTA). Realiza la personalización &quot;uno a uno&quot; de los mensajes y gestiona su envío físico. Funciona utilizando trabajos de envío y gestiona los reintentos automáticos. Además, cuando el seguimiento está habilitado, reemplaza automáticamente las direcciones URL para que apunten al servidor de redirección.

Este proceso puede gestionar la personalización y el envío automático a un enrutador de terceros para SMS, fax y correo postal.

**Servidor de redirección**  (nlserver webmdl)

Para el correo electrónico, Adobe Campaign administra automáticamente el rastreo de clics y aperturas (el seguimiento transaccional a nivel de sitio web es otra posibilidad). Para conseguirlo, las direcciones URL incorporadas en los mensajes de correo electrónico se reescriben para que apunten a este módulo, que registra el paso del usuario de Internet antes de redirigirlos a la dirección URL requerida.

Para garantizar la mayor disponibilidad, este proceso es totalmente independiente de la base de datos: los demás procesos del servidor se comunican con él utilizando llamadas SOAP (HTTP, HTTP(S) y XML) únicamente. Técnicamente, esta funcionalidad se implementa en un módulo de extensión de un servidor HTTP (extensión ISAPI en IIS, o un módulo DSO Apache, etc.) y solo está disponible en Windows.

También hay disponibles otros procesos técnicos:

**Administración de correos electrónicos rechazados**  (nlserver inMail)

Este proceso permite recoger automáticamente el correo electrónico de los buzones configurados para recibir mensajes devueltos en caso de error de envío. A continuación, estos mensajes se someten a un procesamiento basado en reglas para determinar los motivos de la no entrega (destinatario desconocido, cuota excedida, etc.) y para actualizar el estado de entrega en la base de datos.

Todas estas operaciones son totalmente automáticas y están preconfiguradas.

**Estado de envío de SMS**  (nlserver sms)

Este proceso sondea el enrutador SMS para recopilar el estado del progreso y actualizar la base de datos.

**Escribiendo mensajes de registro**  (nlserver syslogd)

Este proceso técnico captura los mensajes de registro y los rastros generados por los otros procesos y los escribe en el disco duro. Esto proporciona amplia información disponible para el diagnóstico en caso de problemas.

**Escritura de registros de seguimiento**  (nlserver trackinglogd)

Este proceso guarda en disco los registros de seguimiento generados por el proceso de redirección.

**Escritura de eventos entrantes**  (nlserver interactiond)

Este proceso garantiza la grabación en el disco de eventos entrantes, dentro del marco de la interacción.

**Supervisión de módulos**  (nlserver watchdog)

Este proceso técnico actúa como un proceso principal que engendra a los demás. También los supervisa y los reinicia automáticamente en caso de incidentes, manteniendo así el máximo tiempo de actividad del sistema.

**Servidor de estadísticas**  (nlserver stat)

Este proceso mantiene estadísticas sobre el número de conexiones, los mensajes enviados para cada servidor de correo al que se envían los mensajes, así como sus limitaciones (el mayor número de conexiones simultáneas, mensajes por hora/ y/o conexión). También le permite federar varias instancias o equipos si comparten las mismas direcciones IP públicas.

>[!NOTE]
>
>La lista completa de módulos de Adobe Campaign está disponible en [este documento](../../production/using/operating-principle.md).

## Capa de persistencia {#persistence-layer}

La base de datos se utiliza como capa de persistencia y contiene casi toda la información administrada por Adobe Campaign. Esto incluye datos funcionales (perfiles, suscripciones, contenido, etc.), datos técnicos (registros y trabajos de envío, registros de seguimiento, etc.) y datos de trabajo (compras, posibles clientes).

La fiabilidad de la base de datos es de suma importancia porque la mayoría de los componentes de Adobe Campaign necesitan acceder a la base de datos para realizar sus tareas (con la notable excepción del módulo de redirección).

La plataforma viene predefinida con un data mart centrado en marketing o puede sentarse fácilmente sobre un data mart y un esquema existentes utilizando cualquiera de los sistemas de administración de bases de datos relacionales (RDBMS) más importantes. La plataforma de Adobe Campaign accede a todos los datos del data mart a través de llamadas SQL desde Adobe Campaign a la base de datos. Adobe Campaign también proporciona un complemento completo de las herramientas de extracción, transformación y carga (ETL) para realizar la importación y exportación de datos dentro y fuera del sistema.
