---
solution: Campaign Classic
product: campaign
title: Arquitectura general
description: Descubra cómo instalar y configurar Campaign Classic.
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
translation-type: tm+mt
source-git-commit: c625b4109e2cb47446331cd009ff9827c8267c93
workflow-type: tm+mt
source-wordcount: '1336'
ht-degree: 0%

---


# Arquitectura general{#general-architecture}

La implementación típica de la solución Adobe Campaign consiste en los siguientes componentes:

* **Entorno de cliente personalizado**

   Interfaz gráfica intuitiva en la que los usuarios pueden comunicarse y rastrear ofertas de mercadotecnia, crear campañas, revisar y administrar todas las actividades, programas y planes de mercadotecnia, incluidos correos electrónicos, flujos de trabajo y páginas de aterrizaje, crear y administrar perfiles de clientes y definir tipos de audiencia de clientes.

* **Entorno de desarrollo**

   Software del lado del servidor que ejecuta las campañas de marketing a través de canales de comunicación elegidos, incluidos correos electrónicos, SMS, notificaciones push, correo directo, web o social, en función de las reglas y flujos de trabajo definidos en la interfaz de usuario.

* **Contenedores de base de datos**

   Basada en la tecnología de base de datos relacional, la base de datos de Adobe Campaign almacena toda la información de los clientes, los componentes de campaña, las ofertas y los flujos de trabajo, así como los resultados de campaña en contenedores de bases de datos de clientes.

Adobe Campaign se basa en una arquitectura orientada a servicios (SOA) y comprende varios módulos funcionales. Estos módulos se pueden implementar en uno o más equipos, en una o varias instancias, según las limitaciones de escalabilidad, disponibilidad y aislamiento de servicio. Por lo tanto, el alcance de las configuraciones de implementación es muy amplio y abarca un único equipo central a través de configuraciones que incluyen múltiples servidores dedicados en múltiples sitios.

>[!NOTE]
>
>Como proveedor de software, especificamos infraestructuras de hardware y software compatibles. Las recomendaciones de hardware que se proporcionan aquí tienen fines meramente informativos y se basan en nuestra experiencia. El Adobe no será responsable de las decisiones que se adopten sobre la base de ellas. También dependerá de sus reglas y prácticas comerciales y de la importancia y los niveles de rendimiento requeridos del proyecto.

![](assets/s_ncs_install_architecture.png)

>[!CAUTION]
>
>Si no se indica explícitamente lo contrario, la instalación, las actualizaciones y el mantenimiento de todos los componentes de una plataforma de Adobe Campaign son responsabilidad del administrador o administradores del equipo que los aloja. Esto incluye implementar los requisitos previos para las aplicaciones de Adobe Campaign, así como cumplir con la Campaña [Tabla de compatibilidad](../../rn/using/compatibility-matrix.md) entre componentes.

## Capa de presentación {#presentation-layer}

Se puede acceder a la aplicación de diferentes maneras, según las necesidades de los usuarios: Cliente enriquecido, cliente ligero o integración de API.

* **Cliente** enriquecido: La interfaz de usuario principal de la aplicación es un cliente rico, es decir, una aplicación nativa (Windows) que se comunica con el servidor de aplicaciones de Adobe Campaign únicamente con protocolos de Internet estándar (SOAP, HTTP, etc.). Esta consola proporciona una buena facilidad de uso para la productividad, utiliza muy poco ancho de banda (mediante el uso de una caché local) y está diseñada para una implementación sencilla. Esta consola se puede implementar desde un navegador de Internet, se puede actualizar automáticamente y no requiere ninguna configuración de red específica porque sólo genera tráfico HTTP(S).
* **Cliente** delgado: Se puede acceder a ciertas partes de la aplicación a través de un navegador web sencillo utilizando una interfaz de usuario HTML, incluyendo el módulo sistema de informes, las etapas de aprobación de envíos, las funcionalidades del módulo Distributed Marketing (Marketing distribuido) (central/local), la supervisión de instancias, etc. Este modo permite incluir funcionalidades de Adobe Campaign en una intranet o extranet.
* **Integración mediante las API**: En algunos casos, se puede llamar al sistema desde una aplicación externa mediante las API de servicios Web expuestas mediante el protocolo SOAP.

## Capa de aplicación lógica {#logical-application-layer}

Adobe Campaign es una plataforma única con diferentes aplicaciones que se combinan para crear una arquitectura abierta y escalable. La plataforma Adobe Campaign está escrita en una capa de aplicación flexible y se puede configurar fácilmente para satisfacer las necesidades comerciales de una compañía. Esto satisface las crecientes necesidades de la empresa desde una perspectiva funcional y desde una perspectiva técnica. La arquitectura distribuida garantiza la escalabilidad lineal del sistema, pasando de miles de mensajes a millones de mensajes.

Adobe Campaign se basa en un conjunto de procesos del lado del servidor que funcionan juntos.

Los principales procesos son:

**Servidor**  de aplicaciones (nlserver web)

Este proceso expone toda la gama de funcionalidades de Adobe Campaign mediante las API de servicios Web (SOAP - HTTP + XML). Además, puede generar dinámicamente las páginas Web utilizadas para el acceso basado en HTML (informes, Formularios web, etc.). Para lograrlo, este proceso incluye un servidor JSP Apache Tomcat. Este es el proceso al que se conecta la consola.

**Motor de flujos de trabajo** (nlserver wfserver)

Ejecuta los procesos de flujo de trabajo definidos en la aplicación.

También se ocupa de los flujos de trabajo técnicos que se ejecutan periódicamente, incluidos:

* Seguimiento: Recuperación y consolidación de registros de seguimiento. Permite recuperar los registros del servidor de redirección y crear los indicadores acumulados utilizados por el módulo de sistema de informes.
* Limpieza: Limpieza de bases de datos. Se utiliza para purgar registros antiguos y evitar que la base de datos crezca exponencialmente.
* Facturación: Envío automático de un informe de actividad para la plataforma (tamaño de base de datos, número de acciones de marketing, etc.).

**Envío Server** (nlserver mta)

Adobe Campaign tiene funcionalidad nativa de retransmisión por correo electrónico. Este proceso funciona como un agente de transferencia de correo SMTP (MTA). Realiza la personalización &quot;uno a uno&quot; de los mensajes y gestiona su envío físico. Funciona utilizando trabajos de envío y gestiona reintentos automáticos. Además, cuando el seguimiento está habilitado, reemplaza automáticamente las direcciones URL para que apunten al servidor de redirección.

Este proceso puede manejar la personalización y el envío automático a un router de terceros para SMS, fax y correo directo.

**Servidor**  de redirección (nlserver webmdl)

En el caso del correo electrónico, Adobe Campaign administra automáticamente el seguimiento de clics y de aperturas (el seguimiento de transacciones a nivel del sitio Web es otra posibilidad). Para conseguirlo, las direcciones URL incorporadas en los mensajes de correo electrónico se reescriben para que apunten a este módulo, que registra el paso del usuario de Internet antes de redirigirlo a la dirección URL requerida.

Para garantizar la mayor disponibilidad, este proceso es totalmente independiente de la base de datos: los demás procesos del servidor se comunican con él mediante llamadas SOAP (HTTP, HTTP(S) y XML) únicamente. Técnicamente, esta funcionalidad se implementa en un módulo de extensión de un servidor HTTP (extensión ISAPI en IIS, módulo DSO Apache, etc.) y solo está disponible en Windows.

También hay otros procesos técnicos disponibles:

**Administración de correos electrónicos**  de devolución (nlserver inMail)

Este proceso le permite recoger automáticamente el correo electrónico de los buzones configurados para recibir mensajes devueltos en caso de envío fallido. A continuación, estos mensajes se someten a un procesamiento basado en reglas para determinar los motivos de no envío (destinatario desconocido, cuota excedida, etc.) y para actualizar el estado del envío en la base de datos.

Todas estas operaciones son totalmente automáticas y están preconfiguradas.

**Estado**  del envío SMS(nlserver sms)

Este proceso sondea el router SMS para recopilar el estado de progreso y actualizar la base de datos.

**Escribiendo mensajes**  de registro (nlserver syslogd)

Este proceso técnico captura los mensajes de registro y los seguimientos generados por los demás procesos y los escribe en el disco duro. Esto permite disponer de amplia información para el diagnóstico en caso de problemas.

**Escritura de registros de seguimiento** (nlserver trackinglogd)

Este proceso guarda en disco los registros de seguimiento generados por el proceso de redirección.

**Escritura de eventos**  entrantes (nlserver interactiond)

Este proceso garantiza la grabación en el disco de eventos entrantes, dentro del marco de la interacción.

**Supervisar módulos**  (nlserver watchdog)

Este proceso técnico actúa como un proceso primario que engendra a los demás. También los supervisa y los reinicia automáticamente en caso de incidentes, manteniendo así el máximo tiempo de actividad del sistema.

**Servidor**  de estadísticas (nlserver stat)

Este proceso mantiene estadísticas sobre el número de conexiones, los mensajes enviados para cada servidor de correo al que se envían los mensajes, así como sus limitaciones (el mayor número de conexiones simultáneas, mensajes por hora/ y/o conexión). También permite federar varias instancias o equipos si comparten las mismas direcciones IP públicas.

>[!NOTE]
>
>La lista completa de los módulos de Adobe Campaign está disponible en [este documento](../../production/using/operating-principle.md).

## Capa de persistencia {#persistence-layer}

La base de datos se utiliza como capa de persistencia y contiene casi toda la información administrada por Adobe Campaign. Esto incluye datos funcionales (perfiles, suscripciones, contenido, etc.), datos técnicos (trabajos y registros de envío, registros de seguimiento, etc.) y datos de trabajo (compras, posibles clientes).

La fiabilidad de la base de datos es de suma importancia porque la mayoría de los componentes de Adobe Campaign requieren acceso a la base de datos para realizar sus tareas (con la notable excepción del módulo de redirección).

La plataforma viene predefinida con un data mart centrado en marketing o puede sentarse en la parte superior de un data mart y un esquema existentes con cualquiera de los principales sistemas de administración de bases de datos relacionales (RDBMS). La plataforma de Adobe Campaign accede a todos los datos dentro del data mart a través de llamadas SQL desde Adobe Campaign a la base de datos. Adobe Campaign también proporciona un completo complemento de las herramientas de Transformación y Carga de Extract (ETL) para realizar la importación y exportación de datos dentro y fuera del sistema.
