---
product: campaign
title: Localice la versión de Tomcat en Adobe Campaign.
description: Aprenda a averiguar la versión actual del servlet web integrado de Tomcat utilizado en una instancia de Adobe Campaign
feature: Monitoring
badge-v7-prem: label="On-premise/híbrido solo" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 76411b29-d300-4aaa-8d3b-d8ff74c3ce93
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 2%

---

# Localice la versión de Tomcat{#locate-tomcat-version}

Adobe Campaign SOAP usa un servlet web **incrustado llamado Apache Tomcat** para procesar solicitudes HTTP/HTTPS entre la aplicación y cualquier interfaz externa (incluida la consola de cliente, vínculos de URL rastreados, llamadas de la y otros). A menudo hay un servidor web externo (generalmente IIS o Apache) delante de esto para cualquier instancia de Adobe Campaign externa.

Siga el siguiente procedimiento para averiguar la versión exacta de Tomcat usada en una **instancia local de Campaign Classic** para solucionar problemas.

## Tomcat utilizado en Adobe Campaign

Tomcat se ejecuta en Java y requiere que se instale JDK. Para obtener más información, consulte Kit de desarrollo de Java (JDK) en la sección [Matriz de compatibilidad de Campaign](../../rn/using/compatibility-matrix.md).

El Tomcat utilizado en Adobe Campaign es una versión integrada personalizada que no utiliza todas las funciones de la versión completa disponible de Tomcat y es posible que no sufra todas las vulnerabilidades de la versión completa. Tomcat tampoco debe estar expuesto a Internet externo, y las instancias de Adobe Campaign que estén expuestas deben tener un servidor web externo (IIS, Apache, etc.) delante de Tomcat para protegerlo.

Las versiones nuevas o actualizadas de las versiones incrustadas de Tomcat solo se publican con nuevas compilaciones de Adobe Campaign en sí y no como parches independientes fuera de las compilaciones de Adobe Campaign.

>[!AVAILABILITY]
>
>
>* A partir de la versión 7.4.1 de Campaign, Tomcat 10.1 es la versión predeterminada.
>
>* Adobe Campaign Classic no utiliza los protocolos WebSocket y HTTP2.
>


## Cómo localizar la versión de Tomcat incrustada

Para localizar la versión de Tomcat incrustada en una instancia de Adobe Campaign, siga los pasos a continuación.

>[!NOTE]
>
>Debe tener acceso a los archivos del servidor de Adobe Campaign que necesita comprobar. El procedimiento que se describe a continuación solo se aplica a **modelos de alojamiento locales**.

1. Vaya a la subcarpeta *\tomcat-11\lib* dentro de la carpeta de instalación de Adobe Campaign (por ejemplo, *C:\Program Files\ [Installation_folder]* en Windows o */usr/local/neolane/nl6* en Linux).

1. Copie el archivo *catalina.jar* a una carpeta temporal externa (por ejemplo, su escritorio) y cambie el nombre de la extensión de .jar a .zip.

1. Descomprima el archivo copiado. Esto generará muchas subcarpetas y archivos.

1. En los archivos o carpetas descomprimidos, abra o lea el siguiente archivo contenido con un editor de texto: *org/apache/catalina/util/ServerInfo.properties*. Es posible que tenga que añadir una extensión .txt para facilitar la apertura con un editor de texto.

1. Una vez finalizado, si se encuentra en un equipo servidor, elimine los archivos temporales que ha creado.

Por ejemplo, el archivo *ServerInfo.properties* para Adobe Campaign contiene la siguiente información, que indica Tomcat v11.X:

*`server.info=Apache Tomcat/11.X`*

*`server.number=A.B.X.Y`*

*`server.built=MM DD YYY HH:MM:SS`*

Una vez que pueda establecer la versión exacta de Tomcat utilizada en una instancia determinada, puede ayudarle a solucionar problemas relacionados con Tomcat.

>[!NOTE]
>
>La versión principal del Tomcat integrado solo se actualiza cuando cambia la versión principal de Adobe Campaign (aunque las versiones anteriores ya no son compatibles oficialmente, la información puede ser útil, ya que algunos clientes pueden seguir ejecutando estas versiones).
>

