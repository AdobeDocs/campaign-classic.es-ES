---
solution: Campaign Classic
product: campaign
title: Localizar la versión de Tomcat en Adobe Campaign
description: Conozca cómo encontrar la versión actual del servlet web integrado de Tomcat utilizado en una instancia de Adobe Campaign.
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 49e49d5e35d14a31236cc4f78188cdf77353fbbf
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 0%

---


# Localización de la versión de Tomcat{#locate-tomcat-version}

Adobe Campaign utiliza un **servlet web integrado llamado Apache Tomcat** para procesar solicitudes HTTP/HTTPS entre la aplicación y cualquier interfaz externa (incluida la consola de cliente, los vínculos de URL rastreados, las llamadas SOAP y otros). A menudo hay un servidor web externo (generalmente IIS o Apache) delante de esto para cualquier instancia de Adobe Campaign externa.

Siga el procedimiento que se describe a continuación para averiguar la versión exacta de Tomcat utilizada en una instancia local **Campaign Classic** para solucionar problemas.

## Tomcat utilizado en Adobe Campaign

Tomcat se ejecuta en Java y requiere que se instale JDK. Para obtener más información, consulte Java Development Kit (JDK) en la sección [Matriz de compatibilidad de Campaña](../../rn/using/compatibility-matrix.md).

El Tomcat utilizado en Adobe Campaign es una versión integrada personalizada que no utiliza todas las características de la versión completa de Tomcat, disponible en general, y puede no sufrir todas las vulnerabilidades de la versión completa. El Tomcat tampoco debe estar expuesto a Internet externo, y cualquier instancia de Adobe Campaign que se exponga debe tener un servidor web externo (IIS, Apache, etc.) delante del Tomcat para protegerlo.

Las versiones nuevas o actualizadas de las versiones incrustadas de Tomcat solo se publican con nuevas compilaciones de Adobe Campaign y no como parches independientes fuera de las compilaciones de Adobe Campaign.

## Cómo localizar la versión de Tomcat incrustado

Para localizar la versión de Tomcat incrustado en una instancia de Adobe Campaign, siga los pasos a continuación.

>[!NOTE]
>
>Debe tener acceso a los archivos del servidor de Adobe Campaign que debe comprobar. El procedimiento que se describe a continuación sólo se aplica a **modelos de alojamiento in situ**.

1. Vaya a la subcarpeta *\tomcat-7\lib* dentro de la carpeta de instalación de Adobe Campaign (por ejemplo, *C:\Program Files\ [Installation_folder]* en Windows o */usr/local/neolane/nl6* en Linux).

   Si está ejecutando una versión anterior de Adobe Campaign con Tomcat v6, utilice *\tomcat-6\lib*.

1. Copie el archivo *catalina.jar* en una carpeta temporal externa (por ejemplo, su escritorio) y cambie el nombre de la extensión de .jar a .zip.

1. Descomprima el archivo copiado. Tendrá como resultado muchas subcarpetas y archivos.

1. En las carpetas o archivos sin comprimir, abra o lea el siguiente archivo contenido con un editor de texto: *org/apache/catalina/util/ServerInfo.properties*. Es posible que deba agregar una extensión .txt para facilitar la apertura con un editor de texto.

1. Una vez finalizado, si se encuentra en un equipo servidor, elimine los archivos temporales que ha creado.

Por ejemplo, el archivo *ServerInfo.properties* para Adobe Campaign contendrá la siguiente información, indicando Tomcat v8.5.X:

*server.info=Apache Tomcat/8.5.X*

*server.number=8.5.X.Y*

*server.build=MM DD AAAA HH:MM:SS*

Una vez que pueda establecer la versión exacta de Tomcat utilizada en una instancia en particular, puede ayudarle a solucionar problemas relacionados con Tomcat.

>[!NOTE]
>
>La versión principal de Tomcat incrustado solo se actualiza cuando cambia la versión principal de Adobe Campaign (aunque es posible que las versiones anteriores ya no se admitan oficialmente, la información puede resultar útil, ya que algunos clientes pueden seguir ejecutando estas versiones).
>
>Por ejemplo, Adobe Campaign v6.02 siempre usará Tomcat v6.x.