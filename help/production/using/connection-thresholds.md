---
product: campaign
title: Umbrales de conexión
description: Umbrales de conexión
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 4ee05559-e719-4e6e-b42c-1e82df428871
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 3%

---

# Umbrales de conexión{#connection-thresholds}



En el caso de los servidores con gran carga, es posible que se supere el umbral de conexión. En cualquier caso, es útil averiguar por qué.

Existen tres umbrales diferentes:

* El **Umbral de conexión web**, configurado en el servidor web. Para modificarla, póngase en contacto con el administrador del sistema.

* El **umbral de conexión a base de datos**. Para modificarla, póngase en contacto con el administrador de la base de datos.

* El **Umbral de conexión de Adobe Campaign**, disponible en dos lugares:

   * **Tomcat** : todas las consultas que llegan realmente al cliente de Adobe Campaign Tomcat.

      Este umbral se configura en la variable **nl6/tomcat-8/conf/server.xml** archivo. El **maxThreads** El atributo permite aumentar el umbral del número de consultas procesadas a la vez. Se puede cambiar a 250, por ejemplo.

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

   * **Base de datos**: conjunto de todas las conexiones abiertas al mismo tiempo en la base de datos por un proceso.

      Este umbral se configura en el archivo **nl6/conf/serverConf.xml**. El **maxCnx** atributo ubicado en **grupo de fuentes de datos** permite aumentar el umbral de consultas procesadas simultáneamente.

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
