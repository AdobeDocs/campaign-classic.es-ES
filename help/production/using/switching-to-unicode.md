---
title: Cambio a Unicode
seo-title: Cambio a Unicode
description: Cambio a Unicode
seo-description: null
page-status-flag: never-activated
uuid: 5f15b285-7377-453a-aa98-ca4cf14a4c80
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
discoiquuid: 0f5399a8-860d-4a1b-86a9-9011b973346b
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 9%

---


# Cambio a Unicode{#switching-to-unicode}

Para una instancia de **prod** existente en Linux/PostgreSQL, los pasos para cambiar a unicode son los siguientes:

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

1. Restaure la base de datos:

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

   Añada el **carácter u** delante del valor relativo al identificador de la base de datos (**databaseId**):

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

1. Confirme el conmutador. Para ello, conéctese a través de la consola de Adobe Campaign y:

   * compruebe que los datos se muestran correctamente, en particular los caracteres acentuados:
   * inicie un envío y compruebe que la recuperación del seguimiento funciona.

