---
product: campaign
title: Cambio a Unicode
description: Cambio a Unicode
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4cfecf2f-cf98-42c1-b979-cdd26d5de48b
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 7%

---

# Cambio a Unicode{#switching-to-unicode}



Para una **prod** en Linux/PostgreSQL, los pasos para cambiar a Unicode son los siguientes:

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

   Agregue la variable **u** delante del valor relativo al identificador de la base de datos (**databaseId**):

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

1. Reinicie todas las máquinas:

   ```
   /etc/init.d/apache stop
   /etc/init.d/nlserver6 stop
   /etc/init.d/nlserver6 start
   /etc/init.d/apache start
   ```

1. Confirme el conmutador. Para ello, conéctese a través de la consola de Adobe Campaign y:

   * compruebe que los datos se muestren correctamente, en particular los caracteres acentuados:
   * inicie una entrega y compruebe que la recuperación de seguimiento funciona.
