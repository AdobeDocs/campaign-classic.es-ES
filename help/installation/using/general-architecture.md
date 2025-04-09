---
product: campaign
title: Arquitectura general de Campaign Classic
description: Obtenga información sobre cómo instalar y configurar Campaign Classic
feature: Installation, Architecture
audience: installation
content-type: reference
level: Intermediate, Experienced
topic-tags: architecture-and-hosting-models
exl-id: 04e6dc17-427b-4745-84cc-bf45c03dbf81
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '1342'
ht-degree: 0%

---

# Arquitectura general{#general-architecture}



La implementación típica de la solución de Adobe Campaign consta de los siguientes componentes:

* **Entorno de cliente personalizado**

  Interfaz gráfica intuitiva en la que los usuarios pueden comunicarse y rastrear ofertas de marketing, crear campañas, revisar y administrar todas las actividades, programas y planes de marketing, incluidos correos electrónicos, flujos de trabajo y páginas de aterrizaje, crear y administrar perfiles de clientes y definir tipos de audiencia de clientes.

* **Entorno de desarrollo**

  Software del lado del servidor que ejecuta las campañas de marketing a través de canales de comunicación seleccionados, incluidos correos electrónicos, SMS, notificaciones push, correo directo, web o social, en función de las reglas y flujos de trabajo definidos en la interfaz de usuario.

* **Contenedores de base de datos**

  Basada en la tecnología de bases de datos relacionales, la base de datos de Adobe Campaign almacena toda la información de los clientes, los componentes de campaña, las ofertas y los flujos de trabajo, así como los resultados de campaña, en contenedores de bases de datos de clientes.

Adobe Campaign is based on a service-oriented architecture (SOA) and comprises several functional modules. These modules can be deployed on one or more computers, in single or multiple instances, depending on constraints in terms of scalability, availability and service isolation. The scope of deployment configurations is therefore very broad, and spans a single, central computer through to configurations including multiple dedicated servers over multiple sites.

>[!NOTE]
>
>Como proveedor de software, especificamos infraestructuras de hardware y software compatibles. The hardware recommendations given here are for informational purposes only and are based on our experience. Adobe no se responsabilizará de las decisiones que se tomen en base a ellos. También dependerá de las reglas y prácticas empresariales y de la importancia y los niveles de rendimiento requeridos del proyecto.

![](assets/s_ncs_install_architecture.png)

>[!CAUTION]
>
>Si no se indica explícitamente lo contrario, la instalación, las actualizaciones y el mantenimiento de todos los componentes de una plataforma de Adobe Campaign son responsabilidad del administrador del equipo que los aloja. Esto incluye la implementación de los requisitos previos para las aplicaciones de Adobe Campaign, así como el cumplimiento de la [matriz de compatibilidad](../../rn/using/compatibility-matrix.md) de Campaign entre los componentes.

## Capa de presentación {#presentation-layer}

Se puede acceder a la aplicación de diferentes formas, según las necesidades de los usuarios: cliente enriquecido, cliente ligero o integración de API.

* **Rich client**: The main user interface of the application is a rich client, in other words, a native application (Windows) that communicates with the Adobe Campaign application server solely with standard internet protocols (SOAP, HTTP, etc.). This console provides great user-friendliness for productivity, uses very little bandwidth (through the use of a local cache) and is designed for easy deployment. This console can be deployed from an internet browser, can be updated automatically and does not require any specific network configuration because it only generates HTTP(S) traffic.
* **Thin client**: Certain parts of the application can be accessed via a simple web browser using an HTML user interface, including the reporting module, delivery approval stages, functionalities of the Distributed Marketing module (central/local), instance monitoring, etc. This mode makes it possible to include Adobe Campaign functionalities in an intranet or an extranet.
* **Integración mediante las API**: En algunos casos, se puede llamar al sistema desde una aplicación externa mediante las API de servicios web expuestas mediante el protocolo de SOAP.

## Capa de aplicación lógica {#logical-application-layer}

Adobe Campaign es una plataforma única con diferentes aplicaciones que se combinan para crear una arquitectura abierta y escalable. La plataforma Adobe Campaign está escrita en un nivel de aplicación flexible y se puede configurar fácilmente para satisfacer las necesidades comerciales de una empresa. Esto se adapta a las crecientes necesidades de la empresa desde una perspectiva funcional, así como desde una perspectiva técnica. La arquitectura distribuida garantiza la escalabilidad lineal del sistema, que puede abarcar desde miles de mensajes hasta millones de mensajes.

Adobe Campaign se basa en un conjunto de procesos del lado del servidor que funcionan juntos.

Los procesos principales son:

**Servidor de aplicaciones** (web nlserver)

Este proceso expone la gama completa de funcionalidades de Adobe Campaign a través de las API de servicios web (SOAP - HTTP + XML). Además, puede generar dinámicamente las páginas web utilizadas para el acceso basado en HTML (informes, formularios web, etc.). Para conseguirlo, este proceso incluye un servidor JSP Apache Tomcat. Este es el proceso al que se conecta la consola.

**Motor de flujo de trabajo** (nlserver wfserver)

It executes the workflow processes defined in the application.

It also handles periodically executed technical workflows, including:

* Seguimiento: Recuperando y consolidando los registros de seguimiento. Permite recuperar los registros del servidor de redirección y crear los indicadores acumulados utilizados por el módulo de creación de informes.
* Cleanup: Limpieza de bases de datos. Se utiliza para purgar registros antiguos y evitar que la base de datos crezca exponencialmente.
* Facturación: envío automático de un informe de actividad para la plataforma (tamaño de la base de datos, número de acciones de marketing, número de perfiles activos, etc.).

**Servidor de entrega** (mta de nlserver)

Adobe Campaign has native email broadcast functionality. This process functions as an SMTP mail transfer agent (MTA). It performs &quot;one-to-one&quot; personalization of messages and handles their physical delivery. It functions using delivery jobs and handles automatic retries. In addition, when tracking is enabled, it automatically replaces the URLs so that they point to the redirection server.

This process can handle the customization and automatic sending to a third-party router for SMS, fax and direct mail.

**Servidor de redirección** (nlserver webmdl)

Para el correo electrónico, Adobe Campaign administra automáticamente el seguimiento de aperturas y clics (el seguimiento transaccional en el nivel de sitio web es una posibilidad adicional). Para conseguirlo, las URL incorporadas en los mensajes de correo electrónico se reescriben para que apunten a este módulo, que registra el paso del usuario de Internet antes de redirigirlo a la URL requerida.

Para garantizar la máxima disponibilidad, este proceso es totalmente independiente de la base de datos: los demás procesos del servidor se comunican con él utilizando llamadas SOAP (HTTP, HTTP(S) y XML) únicamente. Técnicamente, esta funcionalidad se implementa en un módulo de extensión de un servidor HTTP (extensión ISAPI en IIS o módulo DSO Apache, etc.) y solo está disponible en Windows.

Otros procesos más técnicos también están disponibles:

**Administración de correos electrónicos rechazados** (nlserver inMail)

This process enables you to automatically pick up email from mailboxes configured to receive bounced messages that are returned in case of delivery failure. These messages then undergo rule-based processing to determine the reasons for non-delivery (unknown recipient, quota exceeded, etc.) and to update the delivery status in the database.

All these operations are fully automatic and preconfigured.

**Estado de entrega de SMS** (nlserver sms)

Este proceso sondea el enrutador SMS para recopilar el estado de progreso y actualizar la base de datos.

**Escribiendo mensajes de registro** (nlserver syslogd)

Este proceso técnico captura los mensajes de registro y los seguimientos generados por los otros procesos y los escribe en el disco duro. Esto hace que haya amplia información disponible para el diagnóstico en caso de problemas.

**Writing tracking logs** (nlserver trackinglogd)

This process saves to disk the tracking logs generated by the redirecting process.

**Writing inbound events** (nlserver interactiond)

Este proceso garantiza la grabación en disco de eventos entrantes, dentro del marco de Interacción.

**Módulos de supervisión** (nlserver watchdog)

Este proceso técnico actúa como un proceso principal que genera los demás. También los monitoriza y los relanza automáticamente en caso de incidentes, manteniendo así el máximo tiempo de actividad del sistema.

**Servidor de estadísticas** (nlserver stat)

Este proceso mantiene estadísticas sobre el número de conexiones, los mensajes enviados para cada servidor de correo al que se envían los mensajes, así como sus limitaciones (número máximo de conexiones simultáneas, mensajes por hora/hora y/o conexión). También permite federar varias instancias o equipos si comparten las mismas direcciones IP públicas.

>[!NOTE]
>
>La lista completa de módulos de Adobe Campaign está disponible en [este documento](../../production/using/operating-principle.md).

## Capa de persistencia {#persistence-layer}

La base de datos se utiliza como capa de persistencia y contiene casi toda la información administrada por Adobe Campaign. Esto incluye datos funcionales (perfiles, suscripciones, contenido, etc.), datos técnicos (trabajos de entrega y registros, registros de seguimiento, etc.) y datos de trabajo (compras, posibles clientes).

La fiabilidad de la base de datos es de suma importancia porque la mayoría de los componentes de Adobe Campaign requieren acceso a la base de datos para realizar sus tareas (con la notable excepción del módulo de redirección).

La plataforma viene predefinida con un data mart centrado en marketing o puede sentarse fácilmente sobre un data mart y esquema existentes usando cualquiera de los principales Sistemas de Administración de Bases de Datos Relacionales (RDBMS). All data within the data mart is accessed by the Adobe Campaign platform via SQL calls from Adobe Campaign to the database. Adobe Campaign also provides a full complement of Extract Transform and Load (ETL) tools to perform data import and export of data into and out of the system.
