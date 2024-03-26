---
product: campaign
title: Cambio a Unicode
description: Cambio a Unicode
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
badge-v7-prem: label="On-Premise e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4cfecf2f-cf98-42c1-b979-cdd26d5de48b
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 12%

---

# Cambio a Unicode{#switching-to-unicode}



Para un existente **picar** En Linux/PostgreSQL, los pasos para cambiar a Unicode son los siguientes:

1. Detenga los procesos que escriben en la base de datos:

   ```
   su - neolane
   nlserver shutdown
   ```

1. Volcar la base de datos:

   ```
   su - postgres
   pg_dump mydatabase > mydatabase.sql
   ```

1. Crear una base de datos Unicode:

   ```
   createdb -E UNICODE mydatabase_unicode
   ```

1. Restaurar la base de datos:

   ```
   psql mydatabase_unicode < mydatabase.sql
   ```

1. Actualice la opción que indica que la base de datos es Unicode:

   ```
   psql mydatabase_unicode
   update XtkOption set sStringValue = 'u'||sStringValue where sName='XtkDatabaseId' and sStringValue not like 'u%';
   ```

1. En los servidores de seguimiento:

   ```
   su - neolane
   cd nl6/conf
   vi config-prod.xml
   ```

   Añada el **u** delante del valor relacionado con el identificador de la base de datos (**databaseId**):

   ```
   <web>
    <redirection databaseId="u7F0000010554364C" trackingPassword="myPassword="/>
   </web>
   ```

1. En servidores que llaman a la base de datos:

   ```
   su - neolane
   cd nl6/conf
   vi config-prod.xml
   ```

   Modifique la referencia de la base de datos:

   ```
   <dataSource name="default">
    <dbcnx encrypted="1" 
    login="<dbuser>:<base_unicode>" password="xxxx="
    provider="postgresql" server="yyyy"/>
   </dataSource>
   ```

1. Reinicie todos los equipos:

   ```
   /etc/init.d/apache stop
   /etc/init.d/nlserver6 stop
   /etc/init.d/nlserver6 start
   /etc/init.d/apache start
   ```

1. Confirme el interruptor. Para ello, conéctese a través de la consola de Adobe Campaign y:

   * compruebe que los datos se muestran correctamente, en particular los caracteres acentuados:
   * inicie una entrega y compruebe que la recuperación del seguimiento funcione.
