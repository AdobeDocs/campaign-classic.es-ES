---
solution: Campaign Classic
product: campaign
title: Localización de la versión de Tomcat en Adobe Campaign
description: Aprenda a averiguar la versión actual del servlet web integrado Tomcat utilizado en una instancia de Adobe Campaign.
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 76411b29-d300-4aaa-8d3b-d8ff74c3ce93
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 0%

---

# Localizar la versión de Tomcat{#locate-tomcat-version}

Adobe Campaign utiliza un **servlet web integrado llamado Apache Tomcat** para procesar solicitudes HTTP/HTTPS entre la aplicación y cualquier interfaz externa (incluida la consola del cliente, los vínculos de URL rastreados, las llamadas SOAP y otros). A menudo hay un servidor web externo (normalmente IIS o Apache) delante de esto para cualquier instancia de Adobe Campaign externa.

Siga el procedimiento a continuación para averiguar la versión exacta de Tomcat utilizada en una instancia local **Campaign Classic** para ayudar a solucionar problemas.

## Tomcat utilizado en Adobe Campaign

Tomcat se ejecuta en Java y requiere que se instale JDK. Para obtener más información, consulte Kit de desarrollo de Java (JDK) en la sección [Matriz de compatibilidad de Campaign](../../rn/using/compatibility-matrix.md).

El Tomcat utilizado en Adobe Campaign es una versión incrustada personalizada que no utiliza todas las funciones de la versión completa disponible de Tomcat y que puede no sufrir todas las vulnerabilidades de la versión completa. El Tomcat tampoco debe estar expuesto a la Internet externa, y cualquier instancia de Adobe Campaign que esté expuesta debe tener un servidor web externo (IIS, Apache, etc.) delante de Tomcat para protegerlo.

Las versiones nuevas o actualizadas de las versiones incrustadas de Tomcat solo se publican con nuevas compilaciones de Adobe Campaign y no como parches independientes fuera de las compilaciones de Adobe Campaign.

## Cómo localizar la versión de Tomcat incrustado

Para localizar la versión de Tomcat integrado en una instancia de Adobe Campaign, siga los pasos a continuación.

>[!NOTE]
>
>Debe tener acceso a los archivos del servidor de Adobe Campaign que debe comprobar. El procedimiento descrito a continuación solo se aplica a los **modelos de alojamiento local**.

1. Vaya a la subcarpeta *\tomcat-7\lib* dentro de la carpeta de instalación de Adobe Campaign (por ejemplo, *C:\Program Files\ [Installation_folder]* en Windows o */usr/local/neolane/nl6* en Linux).

   Si utiliza una versión anterior de Adobe Campaign con Tomcat v6, utilice *\tomcat-6\lib*.

1. Copie el archivo *catalina.jar* en una carpeta temporal externa (por ejemplo, su escritorio) y cambie el nombre de la extensión de .jar a .zip.

1. Descomprima el archivo copiado. Resultará en muchas subcarpetas y archivos.

1. En los archivos o carpetas descomprimidos, abra o lea el siguiente archivo contenido utilizando un editor de texto: *org/apache/catalina/util/ServerInfo.properties*. Es posible que tenga que agregar una extensión .txt para facilitar la apertura con un editor de texto.

1. Una vez finalizado, si se encuentra en un equipo servidor, elimine los archivos temporales que ha creado.

Por ejemplo, el archivo *ServerInfo.properties* para Adobe Campaign contendrá la siguiente información, indicando Tomcat v8.5.X:

*server.info=Apache Tomcat/8.5.X*

*server.number=8.5.X.Y*

*server.built=MM DD AAAA HH:MM:SS*

Una vez que pueda establecer la versión exacta de Tomcat utilizada en una instancia en particular, puede ayudarle a solucionar los problemas relacionados con Tomcat.

>[!NOTE]
>
>La versión principal de Tomcat incorporado solo se actualiza cuando cambia la versión principal de Adobe Campaign (aunque es posible que las versiones anteriores ya no sean compatibles oficialmente, la información puede resultar útil, ya que algunos clientes pueden seguir ejecutando estas versiones).
>
>Por ejemplo, Adobe Campaign v6.02 siempre usará Tomcat v6.x.
