---
title: Umbrales de conexión
seo-title: Umbrales de conexión
description: Umbrales de conexión
seo-description: null
page-status-flag: never-activated
uuid: a4b6959a-0f5b-41a2-b4c3-d7d6613d1a18
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: f3db77db-94cc-4d75-a59b-2dddce776759
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Umbrales de conexión{#connection-thresholds}

Para los servidores con gran carga, puede que se supere el umbral de conexión. En cualquier caso, es útil saber por qué.

Existen tres umbrales diferentes:

1. El umbral de conexión Web, configurado en el servidor Web. Para modificarlo, póngase en contacto con el administrador del sistema.
1. Umbral de conexión de base de datos. Para modificarla, póngase en contacto con el administrador de la base de datos.
1. El umbral de conexión de Adobe Campaign, disponible en dos lugares:

   * Lado de Tomcat: todas las consultas que llegan realmente al cliente Tomcat de Adobe Campaign.

      Este umbral se configura en el archivo **nl6/tomcat-7/conf/server.xml** . El atributo **maxThread** permite aumentar el umbral del número de consultas procesadas a la vez. Se puede cambiar a 250, por ejemplo.

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

   * Base de datos: conjunto de todas las conexiones abiertas al mismo tiempo en la base de datos mediante un proceso.

      Este umbral se configura en el archivo **nl6/conf/serverConf.xml**. El atributo **maxCnx** ubicado en el grupo **de** orígenes de datos permite aumentar el umbral de consultas procesadas simultáneamente.

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

