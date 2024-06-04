---
product: campaign
title: Servidor de aplicaciones
description: Servidor de aplicaciones
feature: Installation
badge-v7-prem: label="On-premise/híbrido solo" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 87103c31-1530-4f8d-ab3a-6ff73093b80c
source-git-commit: 30670fba2fb84b968ef2e8a8f24746c81cc05f57
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 3%

---

# Servidor de aplicaciones{#application-server}

Las capas de acceso a la base de datos requeridas deben estar instaladas en el servidor y ser accesibles desde la cuenta de Adobe Campaign.

## Kit de desarrollo de Java: JDK {#java-development-kit---jdk}

Java Development Kit, o JDK, es un kit de desarrollo de software. Es el componente fundamental que permite el desarrollo de aplicaciones Java y subprogramas Java.

El generador de páginas web dinámicas utiliza la tecnología JSP 1.2. Para ello, se incluye un motor Tomcat (de Apache) en la aplicación. Requiere un kit de desarrollo de Java (JDK) instalado en todos los servidores en los que está instalada la aplicación de Adobe Campaign.

Primero debe instalar un JDK en los equipos en los que desea ejecutar el servidor de aplicaciones de Adobe Campaign (**nlserver web** ) porque incorpora un contenedor de servlet, Apache Tomcat, utilizado para generar páginas web dinámicas (informes, formularios web, etc.).

La aplicación ha sido aprobada para el Kit de Desarrollo de Java (JDK) desarrollado por el Oracle, así como para **OpenJDK**.

Las versiones compatibles se detallan en Campaign [Matriz de compatibilidad](../../rn/using/compatibility-matrix.md).



### Recomendaciones

El kit de desarrollo de Java se puede instalar con la versión de JDK adecuada que ya usan otras aplicaciones del equipo.

Al instalar el JDK, no es necesaria la integración con los exploradores web.

En un equipo que solo ejecuta agentes de envío (**mta de nlserver** ) o el servidor de flujo de trabajo (**nlserver wfserver** ), no es necesario instalar un JDK.


>[!CAUTION]
>
> Para conservar el rendimiento de las operaciones de la plataforma y garantizar la compatibilidad con la versión instalada, debe desactivar las funciones de actualización automática del JDK en Windows y Linux.
>
> Al actualizar la versión de Java, primero debe desinstalar la versión anterior. Ambas versiones de Java instaladas en el mismo equipo pueden causar conflictos.


### Pasos de instalación

El kit de desarrollo de Java es específico de la plataforma: se necesitan instaladores independientes para cada sistema operativo.

Para descargar el JDK de Java, conéctese a [sitio web de oracle](https://www.oracle.com/technetwork/java/javase/downloads/index.html){target="_blank"}.

>[!CAUTION]
>
> Asegúrese de descargar un kit de desarrollo de Java (JDK), no un entorno de tiempo de ejecución de Java (JRE).


Para instalar JDSL en un entorno Linux, Adobe recomienda utilizar un administrador de paquetes.

Para Debian, utilice el siguiente comando:

```sql
aptitude install openjdk-8-jdk
```

Para RHEL, utilice el siguiente comando:

```sql
yum install java-1.8.0-openjdk
```

## OpenSSL {#openssl}

En Linux, OpenSSL debe estar instalado. Adobe Campaign admite la versión 1.0.2 o superior de OpenSSL.

## Exportación de informes {#exporting-reports}

Puede utilizar Adobe Campaign para exportar informes a Microsoft Excel y Adobe PDF.

* Para el formato de Microsoft Excel, Adobe Campaign se basa en **LibreOffice**.

* Para el formato Adobe PDF, Adobe Campaign utiliza el **PhantomJS** convertidor. PhantomJs está incluido en el paquete de fábrica y LibreOffice debe instalarse en los equipos en los que se ejecuta el servidor de aplicaciones de Adobe Campaign (**nlserver web** proceso).

>[!NOTE]
>
>En Linux, tendrá que añadir fuentes. Para obtener más información, consulte [Fuentes para estadísticas de MTA](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics).

## SpamAssassin {#spamassassin}

SpamAssassin le permite asignar una puntuación a los correos electrónicos para determinar si un mensaje corre el riesgo de ser considerado como no deseado por las herramientas de filtrado de correo no deseado utilizadas durante la recepción. La instalación es opcional.

La calificación de correos electrónicos como no deseados por SpamAssassin se basa completamente en reglas de filtrado y puntuación. Por lo tanto, estas reglas deben actualizarse al menos una vez al día para que la instalación de SpamAssassin y su integración en Adobe Campaign sean completamente funcionales y garanticen la relevancia de las puntuaciones asignadas a los envíos antes de enviarlos. Esta actualización es responsabilidad del administrador del servidor que aloja SpamAssassin.

La versión mínima admitida es: **3,4**

SpamAssassin requiere un acceso a Internet HTTP (tcp/80).

Las fases de instalación y configuración de SpamAssassin se presentan en [Configuración de SpamAssassin](../../installation/using/configuring-spamassassin.md).
