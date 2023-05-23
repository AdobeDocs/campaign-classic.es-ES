---
product: campaign
title: Comandos habituales
description: Comandos habituales
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 472ccc04-e68e-4ccb-90e9-7d626a4e794f
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 4%

---

# Comandos habituales{#usual-commands}



Esta sección enumera los comandos habituales en Adobe Campaign.

El comando **nlserver** es el comando de entrada para toda la aplicación de Adobe Campaign.

Este comando tiene la sintaxis siguiente: **nlserver **`<command>`****`<arguments>`****

El parámetro **`<command>`** corresponde al módulo.

>[!NOTE]
>
>* En cualquier caso, puede agregar la variable **-noconsole** argumento para eliminar los comentarios mostrados una vez iniciados los módulos.
>* Por el contrario, puede agregar el argumento **-verboso** para mostrar más información.
>


## Supervisión de comandos {#monitoring-commands-}

>[!NOTE]
>
>Para enumerar todos los módulos, debe utilizar la variable **nlserver pdump** comando.

Puede añadir el parámetro **-who** para enumerar las conexiones en curso (base de datos y aplicación).

```
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

Otro comando útil es **monitor nlserver**. Muestra el archivo XML de monitorización (obtenido en el cliente de Adobe Campaign o a través de la variable **monitor.jsp** página web).

Puede añadir el parámetro **-falta** para enumerar los módulos ausentes (error en módulos, módulos cerrados, etc.)

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
inMail@test
mta@test
wfserver@test
```

Esto corresponde a los módulos con inicio automático pero que no se han iniciado.

## Comandos de lanzamiento del módulo {#module-launch-commands}

La sintaxis para iniciar los módulos seguirá teniendo el siguiente formato:

```
nlserver start <module>@<INSTANCE>
```

```
nlserver stop <module>@<INSTANCE>
```

>[!NOTE]
>
>**`<instance>`** corresponde al nombre de la instancia tal como se ha introducido en los archivos de configuración, o **predeterminado** para módulos de instancia mono.

## Cerrar servicios {#shut-down-services}

Para detener los servicios de Adobe Campaign, utilice uno de los siguientes comandos:

* Si tiene acceso de administrador o raíz:

   * En Linux:

      ```
      /etc/init.d/nlserver6 stop
      ```

      >[!NOTE]
      >
      >A partir de la versión 20.1, se recomienda utilizar el siguiente comando (para Linux): **systemctl stop nlserver**

   * En Windows:

      ```
      net stop nlserver6
      ```

* Si no es así, en la cuenta de Adobe Campaign:

   ```
   nlserver shutdown 
   ```

## Reiniciar servicios {#restart-services}

Del mismo modo, para reiniciar Adobe Campaign puede utilizar uno de los siguientes comandos:

* Si tiene acceso de administrador o raíz:

   * En Linux: /etc/init.d/nlserver6 start

      >[!NOTE]
      >
      >A partir de la versión 20.1, se recomienda utilizar el siguiente comando (para Linux): **systemctl start nlserver**

   * En Windows: net start nlserver6

* De lo contrario, en la cuenta de Adobe Campaign: **nlserver watchdog -svc -noconsole**

## El comando config {#the-config-command}

El **config** El comando permite administrar la configuración del servidor, incluida la reconfiguración de la conexión de base de datos.

Utilice el **config** al mando del **nlserver** archivo ejecutable con **-setdblogin** parámetro.

```
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

Introduzca la contraseña.

Para cambiar el **interno** contraseña: **nlserver config -internalpassword**

>[!IMPORTANT]
>
>Para iniciar sesión con **Interno** identificador, debe haber definido una contraseña previamente. Para obtener más información, consulte [esta sección](../../installation/using/configuring-campaign-server.md#internal-identifier).

>[!NOTE]
>
>* En general, en lugar de modificar los archivos de configuración manualmente, puede utilizar el **config** mando
>* Para obtener la lista de parámetros, utilice el **-?** parámetro: **Configuración de nlserver -?**
>* En el caso de una base de datos de Oracle, no debe especificar la cuenta. La sintaxis es la siguiente:
>
>  nlserver config -setdblogin:Oracle:test6@dbserver
