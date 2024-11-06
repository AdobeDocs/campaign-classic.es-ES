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
source-git-commit: 387bcf39c13cc1f9544433b9441769f4b16b52ca
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 2%

---

# Servidor de aplicaciones{#application-server}

Las capas de acceso a la base de datos requeridas deben estar instaladas en el servidor y ser accesibles desde la cuenta de Adobe Campaign.

## Kit de desarrollo de Java: JDK {#jdk}

Java Development Kit, o JDK, es un kit de desarrollo de software. Es el componente fundamental que permite el desarrollo de aplicaciones Java y subprogramas Java.

El generador de páginas web dinámicas utiliza la tecnología JSP. Para ello, se incluye un motor Tomcat (de Apache) en la aplicación. Requiere un kit de desarrollo de Java (JDK) instalado en todos los servidores en los que está instalada la aplicación de Adobe Campaign.

Primero debe instalar un JDK en los equipos en los que desea ejecutar el servidor de aplicaciones de Adobe Campaign (**nlserver web** process) porque incorpora un contenedor de servlet, Apache Tomcat, que se utiliza para generar páginas web dinámicas (informes, formularios web, etc.).

La aplicación ha sido aprobada para el Kit de Desarrollo de Java (JDK) desarrollado por Oracle y para **OpenJDK**.

Las versiones compatibles se detallan en Campaign [Compatibility matrix](../../rn/using/compatibility-matrix.md).


>[!AVAILABILITY]
>
>* A partir de la versión 7.4.1, Campaign requiere al menos **Java JDK 11**. Si el servidor de Campaign está instalado en un entorno de Windows, Java Runtime (JRE) ya no se detecta automáticamente. La variable de entorno JRE_HOME debe estar configurada en la carpeta donde Campaign pueda encontrar el archivo `bin/server/jvm.dll`. Por ejemplo, si el JDK 11 está instalado en la carpeta `C:\Program Files\Java\jdk-11`, el JRE_HOME debe ser `C:\Program Files\Java\jdk-11`.
>
>* A partir de la versión 7.4.1, Tomcat 10.1 es la versión predeterminada.
>

### Recomendaciones

Al instalar y actualizar el kit de desarrollo de Java, aplique las siguientes recomendaciones:

* El kit de desarrollo de Java se puede instalar con la versión de JDK adecuada que ya usan otras aplicaciones del equipo.

* Al instalar el JDK, no es necesaria la integración con los exploradores web.

* En un equipo que solo ejecute agentes de envío (proceso **nlserver mta**) o el servidor de flujo de trabajo (proceso **nlserver wfserver**), no es necesario instalar un JDK.

* Al actualizar la versión de Java, primero debe desinstalar la versión anterior. Ambas versiones de Java instaladas en el mismo equipo pueden causar conflictos.

  Como cliente On-Premise, puede comprobar que la `LD_LIBRARY_PATH` [variable de entorno](installing-packages-with-linux.md#environment-variables) está configurada con la última versión (por ejemplo, java11). Si se establece en una versión anterior (por ejemplo, Java8), por lo que debe actualizarse. Para JDK 11, la ruta para localizar bibliotecas JDK es `/usr/lib/jvm/java-11-openjdk-amd64/lib`.


### Pasos de instalación

El kit de desarrollo de Java es específico de la plataforma: se necesitan instaladores independientes para cada sistema operativo.

Para descargar el JDK, conéctese a [sitio web de Oracle](https://www.oracle.com/technetwork/java/javase/downloads/index.html){target="_blank"}.

>[!CAUTION]
>
> Asegúrese de descargar un kit de desarrollo de Java (JDK), no un entorno de tiempo de ejecución de Java (JRE).


Para instalar JDSL en un entorno Linux, Adobe recomienda utilizar un administrador de paquetes.

Para Debian, utilice el siguiente comando:

```sql
apt install openjdk-11-jdk-headless
```

Para RHEL, utilice el siguiente comando:

```sql
dnf install java-11-openjdk-headless
```



## Exportación de informes {#exporting-reports}

Puede utilizar Adobe Campaign para exportar informes a Microsoft Excel y Adobe PDF.

* Para el formato Microsoft Excel, Adobe Campaign se basa en **LibreOffice**.

* Para el formato Adobe PDF, Adobe Campaign usa el convertidor **PhantomJS**. PhantomJs se incluye en el paquete de fábrica y LibreOffice debe instalarse en los equipos en los que se ejecuta el servidor de aplicaciones de Adobe Campaign (proceso web **nlserver**).

>[!NOTE]
>
>En Linux, tendrá que añadir fuentes. Para obtener más información, consulte [Fuentes para estadísticas de MTA](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics).

## SpamAssassin {#spamassassin}

SpamAssassin le permite asignar una puntuación a los correos electrónicos para determinar si un mensaje corre el riesgo de ser considerado como no deseado por las herramientas de filtrado de correo no deseado utilizadas durante la recepción. La instalación es opcional.

La calificación de correos electrónicos como no deseados por SpamAssassin se basa completamente en reglas de filtrado y puntuación. Por lo tanto, estas reglas deben actualizarse al menos una vez al día para que la instalación de SpamAssassin y su integración en Adobe Campaign sean completamente funcionales y garanticen la relevancia de las puntuaciones asignadas a los envíos antes de enviarlos. Esta actualización es responsabilidad del administrador del servidor que aloja SpamAssassin.

La versión mínima admitida es: **3.4**

SpamAssassin requiere un acceso a Internet HTTP (tcp/80).

Las fases de instalación y configuración de SpamAssassin se presentan en [Configuración de SpamAssassin](../../installation/using/configuring-spamassassin.md).
