---
solution: Campaign Classic
product: campaign
title: Error de conexión
description: Error de conexión
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 2%

---


# Error de conexión{#failure-to-connect}

Las razones para ello pueden ser múltiples y depender de diversos contextos.

Compruebe la configuración general de las zonas de seguridad.

>[!NOTE]
>
>For more on configuring security zones, refer to [this section](../../installation/using/configuring-campaign-server.md#defining-security-zones).

Compruebe la siguiente información:

1. **Comprobaciones de red**

   * ¿Tiene acceso a Internet desde su equipo?

      Compruebe que puede conectarse a sitios web en Internet (por ejemplo). Si no puede conectarse, el problema está en su equipo. Póngase en contacto con el administrador del sistema.

   * ¿Puede conectarse al servidor que aloja Adobe Campaign a través de otro servicio?

      Conectarse al servidor a través de SSH o por cualquier otro medio. Si esto no es posible, la compañía del host tiene un problema. Póngase en contacto con el administrador del sistema.

1. **Comprobaciones en el servidor** Web (IIS/apache/etc.)

   * ¿Responde el servidor Web?

      Conéctese a la URL de acceso al servidor de Adobe Campaign mediante un explorador Web: **http(s)://`<urlserver>`**. Si no responde, el servidor web se detiene en el equipo. Póngase en contacto con el administrador del sistema de la compañía del host para reiniciar el servicio.

   * ¿Se ha integrado correctamente Adobe Campaign?

      Inicie sesión en el **http(s):/// `<urlserver>`/r/test** URL. El servidor debe devolver el siguiente tipo de mensaje

      ```
      <redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='<hostname>' localHost='<server>'/>
      ```

      Si no obtiene este resultado, compruebe en la configuración del servidor Web que se tiene en cuenta la integración.

1. **Cheques en el lado de Adobe Campaign**

   * ¿Se ha iniciado el módulo Web de Adobe Campaign?

      Conéctese a la siguiente URL: **http(s)://`<URLSERVER>`/nl/jsp/logon.jsp**

      * Si obtiene un error de Java de Tomcat:

         ¿Se realiza correctamente la integración de JAVA? Adobe Campaign requiere un JDK SUN.

         Está integrado en el archivo **`[path of application]`/nl6/customer.sh**

      * Si obtiene una página en blanco:

         ¿Se ha iniciado el módulo Web de Adobe Campaign? Debe obtener:

         ```
         nlserver pdump
         HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
         [...]
         web@default (27515) - 55.2 Mb
         [...]
         ```

      * Si no es así, reinícielo con el siguiente comando:

         ```
         nlserver start web
         ```
>[!NOTE]
>
>Si obtiene una respuesta del tipo siguiente al realizar la lista de los módulos de Adobe Campaign: **nlserver pdump**
>HH:MM:SS > Servidor de aplicaciones para Adobe Campaign Classic (compilación 7.X YY.R XXX@SHA1) de DD/MM/AAAA Sin tareas Debe reiniciar toda la aplicación Adobe Campaign. Para ello, utilice el siguiente comando: **nlserver watdog -svc -noconsole **
