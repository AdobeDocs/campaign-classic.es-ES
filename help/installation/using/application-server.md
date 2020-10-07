---
title: Servidor de aplicaciones
seo-title: Servidor de aplicaciones
description: Servidor de aplicaciones
seo-description: null
page-status-flag: never-activated
uuid: 837c6a5c-53a4-4d1b-a084-9cf77e7a0eee
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
discoiquuid: 7a9e028c-255d-4aad-9827-d19f9a7897b2
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 3%

---


# Servidor de aplicaciones{#application-server}

Las capas de acceso a la base de datos necesarias deben estar instaladas en el servidor y ser accesibles desde la cuenta de Adobe Campaign.

## Java Development Kit - JDK {#java-development-kit---jdk}

El generador dinámico de páginas Web utiliza la tecnología JSP 1.2. Para esto, se incluye un motor Tomcat (de Apache) en la aplicación. Requiere un kit de desarrollo de Java (JDK), instalado en todos los servidores en los que está instalada la aplicación de Adobe Campaign.

En primer lugar, debe instalar un JDK en los equipos en los que desea ejecutar el servidor de aplicaciones de Adobe Campaign (proceso web **de** nlserver) porque incorpora un contenedor servlet, Apache Tomcat, que se utiliza para generar páginas Web dinámicas (informes, Formularios web, etc.).

The application has been approved for the Java Development Kit (JDK) developed by Oracle as well as for **OpenJDK**.

The supported versions are detailed in the [Compatibility matrix](https://helpx.adobe.com/es/campaign/kb/compatibility-matrix.html).

>[!NOTE]
>
>Puede instalarse con la versión JDK adecuada que ya utilizan otras aplicaciones del equipo.
>  
>Al realizar la instalación, no es necesario que realice la integración con los exploradores Web.
>
>En un equipo que solo ejecuta agentes de envío (**proceso mta** de nlserver) o el servidor de flujo de trabajo (proceso wfserver **de** nlserver), no es necesario instalar un JDK.

Para descargar Java JDK, conéctese a: [https://www.oracle.com/technetwork/java/javase/downloads/index.html](https://www.oracle.com/technetwork/java/javase/downloads/index.html).

**Advertencia: debe descargar un JDK, no un JRE.**

>[!CAUTION]
>
>Para conservar el rendimiento de funcionamiento de la plataforma y garantizar la compatibilidad con la versión instalada, debe desactivar las funciones de actualización JDK automática en Windows y Linux.

Para instalar el JDSL en un entorno Linux, es preferible utilizar un administrador de paquetes.

En Debian 8 y 9, utilice el siguiente comando:

```
aptitude install openjdk-8-jdk
```

Para RHEL 7, utilice el siguiente comando:

```
yum install java-1.8.0-openjdk
```

## OpenSSL {#openssl}

En Linux, se debe instalar OpenSSL. Las versiones compatibles con Adobe Campaign son **OpenSSL 1.0.1** y **OpenSSL 0.9.8**. Se aceptan las subversiones 0.9.8g a 0.9.8o.

## Exportación de informes {#exporting-reports}

Adobe Campaign permite exportar informes de plataforma en formato Microsoft Excel y Adobe PDF. Para el formato de Microsoft Excel, Adobe Campaign utiliza **LibreOffice**. Para el formato Adobe PDF, Adobe Campaign utiliza el convertidor **PhantomJS** . PhantomJs está incluido en el paquete de fábrica y LibreOffice debe estar instalado en las máquinas en las que se ejecuta el servidor de aplicaciones de Adobe Campaign (proceso web **** nlserver).

>[!NOTE]
>
>Para Linux, necesitará agregar fuentes. Para obtener más información sobre esto, consulte [Fuentes para estadísticas](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics)de MTA.

## SpamAssassin {#spamassassin}

SpamAssassin le permite asignar una puntuación a los correos electrónicos para determinar si un mensaje corre el riesgo de ser considerado como no deseado por las herramientas antispam utilizadas en la recepción. La instalación es opcional.

La calificación de los correos electrónicos como indeseables por SpamAssassin se basa completamente en reglas de filtrado y puntuación. Por lo tanto, estas reglas deben actualizarse al menos una vez al día para que la instalación de SpamAssassin y su integración en Adobe Campaign sean completamente funcionales y para garantizar la relevancia de las puntuaciones asignadas a sus envíos antes de enviarlas. Esta actualización es responsabilidad del administrador del servidor que aloja SpamAssassin.

La versión mínima admitida es: **3,4**

SpamAssassin requiere acceso HTTP a Internet (tcp/80).

Las etapas de instalación y configuración de SpamAssassin se presentan en [Configuración de SpamAssassin](../../installation/using/configuring-spamassassin.md).
