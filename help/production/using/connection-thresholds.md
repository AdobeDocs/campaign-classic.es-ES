---
product: campaign
title: Umbrales de conexión
description: Umbrales de conexión
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 4ee05559-e719-4e6e-b42c-1e82df428871
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 3%

---

# Umbrales de conexión{#connection-thresholds}

En los servidores cargados de forma intensiva, es posible que se supere el umbral de conexión. En cualquier caso, es útil averiguar por qué.

Hay tres umbrales diferentes:

* El **umbral de conexión web**, configurado en el servidor web. Para modificarlo, póngase en contacto con el administrador del sistema.

* El **umbral de conexión a la base de datos**. Para modificarlo, póngase en contacto con el administrador de la base de datos.

* El **umbral de conexión de Adobe Campaign**, disponible en dos lugares:

   * **** Tomcatside: todas las consultas que llegan realmente al cliente Tomcat de Adobe Campaign.

      Este umbral se configura en el archivo **nl6/tomcat-8/conf/server.xml**. El atributo **maxThreads** permite aumentar el umbral del número de consultas procesadas a la vez. Se puede cambiar a 250, por ejemplo.

      ```
      <Connector protocol="HTTP/1.1" port="8080"
                     maxThreads="75"
                     minSpareThreads="5"
                     enableLookups="true" redirectPort="8443"
                     acceptCount="100" connectionTimeout="20000"
                     disableUploadTimeout="true" />
          <Engine name="Tomcat-Standalone" defaultHost="localhost">
            <Host name="localhost" appBase="./"
                  unpackWARs="true" autoDeploy="true">
      ```

   * **Base de datos**: conjunto de todas las conexiones abiertas al mismo tiempo en la base de datos mediante un proceso.

      Este umbral se configura en el archivo **nl6/conf/serverConf.xml**. El atributo **maxCnx** ubicado en **datasource pool** permite aumentar el umbral de consultas procesadas simultáneamente.

      ```
          <!-- Data source
               -->
            <dataSource name="default">
              <dbcnx NChar="" bulkCopyUtility="" dbSchema="" encrypted="" login="" password="" provider="" server="" timezone="" unicodeData="" useTimestampTZ=""/>
              <sqlParams funcPrefix="">
                <postConnectSQL/>
              </sqlParams>
              <pool aliveTestDelaySec="600" freeCnx="0" maxCnx="90" maxIdleDelaySec="1200"/>
            </dataSource>
      ```
