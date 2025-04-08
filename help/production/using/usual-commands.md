---
product: campaign
title: Comandos habituales
description: Comandos habituales
feature: Monitoring
badge-v7-prem: label="On-premise/híbrido solo" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 472ccc04-e68e-4ccb-90e9-7d626a4e794f
source-git-commit: b8a6a0db27826309456c285c08d4f1d85de70283
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 6%

---

# Comandos habituales{#usual-commands}



Esta sección enumera los comandos habituales en Adobe Campaign.

El comando **nlserver** es el comando de entrada para toda la aplicación de Adobe Campaign.

Este comando tiene la siguiente sintaxis: **nlserver **`<command>`****`<arguments>`****

El parámetro **`<command>`** corresponde al módulo.

>[!NOTE]
>
>* En cualquier caso, puede agregar el argumento **-noconsole** para eliminar los comentarios mostrados una vez iniciados los módulos.
>* Por el contrario, puede agregar el argumento **-verbose** para mostrar más información.
>

## Supervisión de comandos {#monitoring-commands-}

>[!NOTE]
>
>Para enumerar todos los módulos, debe usar el comando **nlserver pdump**.

Puede agregar el parámetro **-who** para enumerar las conexiones en curso (base de datos y aplicación).

```sql
nlserver pdump -who
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
web@default (9984) - 50.1 Mo
watchdog (2273) - 6.6 Mo
syslogd@default (9931) - 7.0 Mo
trackinglogd@default (9985) - 45.6 Mo
mta@test (9986) - 9.6 Mo
wfserver@test (9987) - 8.8 Mo

Connections ------------------------------------------------------
Last Access IP Instance Login 
DD/MM/YYYY HH:MM:SS 127.0.0.1 default formation_fr|tracking
DD/MM/YYYY HH:MM:SS 127.0.0.1 default internal|monitoring

Connection pool --------------------------------------------------
Datasource Server Provider Login 
default xxxxx myserver myprovider test400
```

Otro comando útil es **nlserver monitor**. Muestra el archivo XML de supervisión (obtenido en el cliente de Adobe Campaign o a través de la página web **monitor.jsp**).

Puede agregar el parámetro **-missing** para enumerar los módulos ausentes (error en módulos, módulos apagados, etc.)

```sql
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
inMail@test
mta@test
wfserver@test
```

Esto corresponde a los módulos con inicio automático pero que no se han iniciado.

## Comandos de lanzamiento del módulo {#module-launch-commands}

La sintaxis para iniciar los módulos seguirá teniendo el siguiente formato:

```sql
nlserver start <module>@<INSTANCE>
```

```sql
nlserver stop <module>@<INSTANCE>
```

>[!NOTE]
>
>**`<instance>`** corresponde al nombre de la instancia tal como se introdujo en los archivos de configuración, o **default** para módulos de instancia mono.

## Cerrar servicios {#shut-down-services}

Para detener los servicios de Adobe Campaign, utilice uno de los siguientes comandos:

* Si tiene acceso de administrador o raíz:

   * En Linux:

     ```sql
     /etc/init.d/nlserver6 stop
     ```

     >[!NOTE]
     >
     >A partir de la versión 20.1, se recomienda utilizar el siguiente comando en su lugar (para Linux): **systemctl stop nlserver**

   * En Windows:

     ```sql
     net stop nlserver6
     ```

* Si no es así, en la cuenta de Adobe Campaign:

  ```sql
  nlserver shutdown 
  ```

## Reiniciar servicios {#restart-services}

Del mismo modo, para reiniciar Adobe Campaign puede utilizar uno de los siguientes comandos:

* Si tiene acceso de administrador o raíz:

   * En Linux: `/etc/init.d/nlserver6 start`

     >[!NOTE]
     >
     >A partir de la versión 20.1, se recomienda utilizar el siguiente comando (en Linux): **systemctl start nlserver**

   * En Windows: `net start nlserver6`

* De lo contrario, en la cuenta de Adobe Campaign: **nlserver watchdog -svc -noconsole**

## El comando config {#the-config-command}

El comando **config** le permite administrar la configuración del servidor, incluida la reconfiguración de la conexión a la base de datos.

Use el comando **config** del archivo ejecutable **nlserver** con el parámetro **-setdblogin**.

```sql
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```sql
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

Introduzca la contraseña.

Para cambiar la contraseña de **internal**: **nlserver config -internalpassword**

>[!IMPORTANT]
>
>Para iniciar sesión con el identificador **Internal**, debe haber definido previamente una contraseña. Para obtener más información, consulte [esta sección](../../installation/using/configuring-campaign-server.md#internal-identifier).

>[!NOTE]
>
>* En general, en lugar de modificar manualmente los archivos de configuración, puede usar el comando **config**
>* Para obtener la lista de parámetros, use el **-?** parámetro: **nlserver config -?**
>* En el caso de una base de datos de Oracle, no debe especificar la cuenta. La sintaxis es la siguiente:
>
>  `nlserver config -setdblogin:Oracle:test6@dbserver`
>

Este es un ejemplo para MSSQL:

```sql
nlserver config -setdblogin:mssql:<login>/"<password>"@<server> -instance:<instance_name> 
```

* login (p. ej. account:user) y server se pueden encontrar en el nodo dataSource del archivo config-&lt;instance_name>.xml.
* La contraseña debe ir entre comillas &quot;&quot;.

