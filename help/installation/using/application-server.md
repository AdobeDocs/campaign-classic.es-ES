---
product: campaign
title: Servidor de aplicaciones
description: Servidor de aplicaciones
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 87103c31-1530-4f8d-ab3a-6ff73093b80c
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 1%

---

# Servidor de aplicaciones{#application-server}

Las capas de acceso a la base de datos necesarias deben estar instaladas en el servidor y ser accesibles desde la cuenta de Adobe Campaign.

## Kit de desarrollo de Java - JDK {#java-development-kit---jdk}

El generador de páginas web dinámicas utiliza la tecnología JSP 1.2. Para esto, se incluye un motor Tomcat (de Apache) en la aplicación. Requiere un Kit de desarrollo de Java (JDK), instalado en todos los servidores en los que está instalada la aplicación de Adobe Campaign.

Primero debe instalar un JDK en los equipos en los que desea ejecutar el servidor de aplicaciones de Adobe Campaign (**nlserver web** proceso) porque incorpora un contenedor de servlets, Apache Tomcat, que se utiliza para generar páginas web dinámicas (informes, formularios web, etc.).

La aplicación ha sido aprobada para el Kit de desarrollo de Java (JDK) desarrollado por Oracle, así como para **OpenJDK**.

Las versiones compatibles se detallan en la matriz de compatibilidad [de Campaign](../../rn/using/compatibility-matrix.md).

>[!NOTE]
>
>Se puede instalar utilizando la versión JDK adecuada que ya utilizan otras aplicaciones del equipo.
>  
>Al instalar, no es necesario que realice la integración con los exploradores web.
>
>En un equipo que solo ejecuta agentes de envío (proceso **nlserver mta**) o el servidor de flujo de trabajo (proceso **nlserver wfserver**), no es necesario instalar un JDK.

Para descargar Java JDK, conéctese a: [https://www.oracle.com/technetwork/java/javase/downloads/index.html](https://www.oracle.com/technetwork/java/javase/downloads/index.html).

**Advertencia: debe descargar un JDK, no un JRE.**

>[!CAUTION]
>
>Para conservar el rendimiento de las operaciones de la plataforma y garantizar la compatibilidad con la versión instalada, debe deshabilitar las funciones de actualización automática de JDK en Windows y Linux.

Para instalar JDSL en un entorno Linux, es preferible utilizar un gestor de paquetes.

En Debian 8 y 9, utilice el siguiente comando:

```
aptitude install openjdk-8-jdk
```

Para RHEL 7, utilice el siguiente comando:

```
yum install java-1.8.0-openjdk
```

## OpenSSL {#openssl}

En Linux, OpenSSL debe estar instalado. Las versiones compatibles con Adobe Campaign son **OpenSSL 1.0.1** y **OpenSSL 0.9.8**. Se aceptan las subversiones 0.9.8g a 0.9.8o.

## Exportación de informes {#exporting-reports}

Adobe Campaign permite exportar informes de plataforma en formato de Microsoft Excel y Adobe PDF. Para el formato de Microsoft Excel, Adobe Campaign utiliza **LibreOffice**. Para el formato Adobe PDF, Adobe Campaign utiliza el convertidor **PhantomJS**. PhantomJs está incluido en el paquete de fábrica y LibreOffice debe estar instalado en los equipos en los que se ejecuta el servidor de aplicaciones de Adobe Campaign (**nlserver web** proceso).

>[!NOTE]
>
>Para Linux, necesitará añadir fuentes. Para obtener más información, consulte [Fuentes para estadísticas de MTA](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics).

## SpamAssassin {#spamassassin}

SpamAssassin permite asignar una puntuación a los correos electrónicos para determinar si un mensaje corre el riesgo de ser considerado como no deseado por las herramientas antispam utilizadas en la recepción. La instalación es opcional.

La calificación de correos electrónicos como no deseados por SpamAssassin se basa completamente en reglas de filtrado y puntuación. Por lo tanto, estas reglas deben actualizarse al menos una vez al día para que la instalación de SpamAssassin y su integración en Adobe Campaign sean completamente funcionales y para garantizar la relevancia de las puntuaciones asignadas a los envíos antes de enviarlos. Esta actualización es responsabilidad del administrador del servidor que aloja SpamAssassin.

La versión mínima admitida es: **3.4**

SpamAssassin requiere un acceso HTTP a Internet (tcp/80).

Las etapas de instalación y configuración de SpamAssassin se presentan en [Configuración de SpamAssassin](../../installation/using/configuring-spamassassin.md).
