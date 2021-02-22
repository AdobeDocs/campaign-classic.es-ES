---
solution: Campaign Classic
product: campaign
title: Comandos habituales
description: Comandos habituales
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 3%

---


# Comandos habituales{#usual-commands}

Esta sección lista los comandos habituales en Adobe Campaign.

El comando **nlserver** es el comando de entrada para toda la aplicación de Adobe Campaign.

Este comando tiene la siguiente sintaxis: **nlserver **`<command>`****`<arguments>`****

El parámetro **`<command>`** corresponde al módulo.

>[!NOTE]
>
>* En cualquier caso, puede agregar el argumento **-noconsole** para eliminar los comentarios que se muestran una vez que se inician los módulos.
>* Por el contrario, puede agregar el argumento **-verbose** para mostrar más información.
>



## Comandos de monitoreo {#monitoring-commands-}

>[!NOTE]
>
>Para lista de todos los módulos, debe utilizar el comando **nlserver pdump**.

Puede agregar el parámetro **-who** para la lista de las conexiones en curso (base de datos y aplicación).

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

Otro comando útil es **nlserver monitor**. Lista el archivo XML de supervisión (obtenido en el cliente de Adobe Campaign o a través de la **página web monitor.jsp**).

Puede agregar el parámetro **-missing** para la lista de los módulos ausentes (error en módulos, módulos apagados, etc.)

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
inMail@test
mta@test
wfserver@test
```

Esto corresponde a los módulos con inicio automático pero que no se han iniciado.

## Comandos de inicio del módulo {#module-launch-commands}

La sintaxis para iniciar los módulos seguirá teniendo el siguiente formato:

```
nlserver start <module>@<INSTANCE>
```

```
nlserver stop <module>@<INSTANCE>
```

>[!NOTE]
>
>**`<instance>`** corresponde al nombre de la instancia tal como se especifica en los archivos de configuración o  **** de forma predeterminada para los módulos de instancia única.

## Cerrar servicios {#shut-down-services}

Para detener los servicios de Adobe Campaign, utilice uno de los siguientes comandos:

* Si tiene acceso a la raíz o al administrador:

   * En Linux:

      ```
      /etc/init.d/nlserver6 stop
      ```

      >[!NOTE]
      >
      >A partir de 20.1, se recomienda utilizar el siguiente comando en su lugar (para Linux): **systemctl stop nlserver**

   * En Windows:

      ```
      net stop nlserver6
      ```

* En caso contrario, en la cuenta de Adobe Campaign:

   ```
   nlserver shutdown 
   ```

## Reiniciar servicios {#restart-services}

Del mismo modo, para reiniciar Adobe Campaign puede utilizar uno de los siguientes comandos:

* Si tiene acceso a la raíz o al administrador:

   * En Linux: /etc/init.d/nlserver6 inicio

      >[!NOTE]
      >
      >A partir de 20.1, se recomienda utilizar el siguiente comando en su lugar (para Linux): **inicio de sistema nlserver**

   * En Windows: net inicio nlserver6

* En caso contrario, en la cuenta de Adobe Campaign: **nlserver watchdog -svc -noconsole**

## El comando config {#the-config-command}

El comando **config** permite administrar la configuración del servidor, incluida la reconfiguración de la conexión de base de datos.

Utilice el comando **config** del archivo ejecutable **nlserver** con el parámetro **-setdblogin**.

```
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

Introduzca la contraseña.

Para cambiar la contraseña **interna**: **nlserver config -internalpassword**

>[!IMPORTANT]
>
>Para iniciar sesión con el identificador **Interno**, debe haber definido una contraseña de antemano. Para obtener más información, consulte [esta sección](../../installation/using/campaign-server-configuration.md#internal-identifier).

>[!NOTE]
>
>* En general, en lugar de modificar los archivos de configuración a mano, puede utilizar el comando **config**
>* Para obtener la lista de los parámetros, utilice el **-?** parámetro:  **nlserver config -?**
>* En el caso de una base de datos de Oracle, no debe especificar la cuenta. La sintaxis será la siguiente:
>
>  nlserver config -setdblogin:Oracle:test6@dbserver

