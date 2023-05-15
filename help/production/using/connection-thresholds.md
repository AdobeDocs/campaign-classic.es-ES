---
product: campaign
title: Umbrales de conexión
description: Umbrales de conexión
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 4ee05559-e719-4e6e-b42c-1e82df428871
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 3%

---

# Umbrales de conexión{#connection-thresholds}



En los servidores cargados de forma intensiva, es posible que se supere el umbral de conexión. En cualquier caso, es útil averiguar por qué.

Hay tres umbrales diferentes:

* La variable **Umbral de conexión web**, configurado en el servidor web. Para modificarlo, póngase en contacto con el administrador del sistema.

* La variable **umbral de conexión de base de datos**. Para modificarlo, póngase en contacto con el administrador de la base de datos.

* La variable **Umbral de conexión de Adobe Campaign**, disponible en dos lugares:

   * **Tomcat** lado: todas las consultas que llegan realmente al cliente Tomcat de Adobe Campaign.

      Este umbral se configura en la variable **nl6/tomcat-8/conf/server.xml** archivo. La variable **maxThreads** permite aumentar el umbral del número de consultas procesadas a la vez. Se puede cambiar a 250, por ejemplo.

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

      Este umbral se configura en el archivo **nl6/conf/serverConf.xml**. La variable **maxCnx** atributo ubicado en **grupo de orígenes de datos** permite aumentar el umbral de consultas procesadas simultáneamente.

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
