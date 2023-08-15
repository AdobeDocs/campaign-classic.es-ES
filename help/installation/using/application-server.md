---
product: campaign
title: Servidor de aplicaciones
description: Servidor de aplicaciones
feature: Installation
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
badge-v7-prem: label="on-premise e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 87103c31-1530-4f8d-ab3a-6ff73093b80c
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 6%

---

# Servidor de aplicaciones{#application-server}



Las capas de acceso a la base de datos requeridas deben estar instaladas en el servidor y ser accesibles desde la cuenta de Adobe Campaign.

## Kit de desarrollo de Java: JDK {#java-development-kit---jdk}

El generador de páginas web dinámicas utiliza la tecnología JSP 1.2. Para ello, se incluye un motor Tomcat (de Apache) en la aplicación. Requiere un kit de desarrollo de Java (JDK) instalado en todos los servidores en los que está instalada la aplicación de Adobe Campaign.

Primero debe instalar un JDK en los equipos en los que desea ejecutar el servidor de aplicaciones de Adobe Campaign (**nlserver web** ) porque incorpora un contenedor de servlet, Apache Tomcat, utilizado para generar páginas web dinámicas (informes, formularios web, etc.).

La aplicación ha sido aprobada para el Kit de Desarrollo de Java (JDK) desarrollado por el Oracle, así como para **OpenJDK**.

Las versiones compatibles se detallan en Campaign [Matriz de compatibilidad](../../rn/using/compatibility-matrix.md).

>[!NOTE]
>
>Se puede instalar con la versión JDK adecuada que ya usan otras aplicaciones del equipo.
>  
>Al instalar, no es necesario realizar la integración con los exploradores web.
>
>En un equipo que solo ejecuta agentes de envío (**mta de nlserver** ) o el servidor de flujo de trabajo (**nlserver wfserver** ), no es necesario instalar un JDK.

Para descargar el JDK de Java, conecte a: [https://www.oracle.com/technetwork/java/javase/downloads/index.html](https://www.oracle.com/technetwork/java/javase/downloads/index.html).

**Advertencia: debe descargar un JDK, no un JRE.**

>[!CAUTION]
>
>Para conservar el rendimiento de las operaciones de la plataforma y garantizar la compatibilidad con la versión instalada, debe desactivar las funciones de actualización automática del JDK en Windows y Linux.

Para instalar JDSL en un entorno Linux, es preferible utilizar un administrador de paquetes.

En Debian 8 y 9, utilice el siguiente comando:

```
aptitude install openjdk-8-jdk
```

Para RHEL 7, utilice el siguiente comando:

```
yum install java-1.8.0-openjdk
```

## OpenSSL {#openssl}

En Linux, OpenSSL debe estar instalado. Adobe Campaign admite la versión 1.0.2 o superior de OpenSSL.

## Exportación de informes {#exporting-reports}

Adobe Campaign permite exportar informes de plataforma en formato Microsoft Excel y Adobe PDF. Para el formato de Microsoft Excel, Adobe Campaign utiliza **LibreOffice**. Para el formato Adobe PDF, Adobe Campaign utiliza el **PhantomJS** convertidor. PhantomJs está incluido en el paquete de fábrica y LibreOffice debe instalarse en los equipos en los que se ejecuta el servidor de aplicaciones de Adobe Campaign (**nlserver web** proceso).

>[!NOTE]
>
>En Linux, tendrá que añadir fuentes. Para obtener más información, consulte [Fuentes para estadísticas de MTA](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics).

## SpamAssassin {#spamassassin}

SpamAssassin le permite asignar una puntuación a los correos electrónicos para determinar si un mensaje corre el riesgo de ser considerado como no deseado por las herramientas de filtrado de correo no deseado utilizadas durante la recepción. La instalación es opcional.

La calificación de correos electrónicos como no deseados por SpamAssassin se basa completamente en reglas de filtrado y puntuación. Por lo tanto, estas reglas deben actualizarse al menos una vez al día para que la instalación de SpamAssassin y su integración en Adobe Campaign sean completamente funcionales y garanticen la relevancia de las puntuaciones asignadas a los envíos antes de enviarlos. Esta actualización es responsabilidad del administrador del servidor que aloja SpamAssassin.

La versión mínima admitida es: **3,4**

SpamAssassin requiere un acceso a Internet HTTP (tcp/80).

Las fases de instalación y configuración de SpamAssassin se presentan en [Configuración de SpamAssassin](../../installation/using/configuring-spamassassin.md).
