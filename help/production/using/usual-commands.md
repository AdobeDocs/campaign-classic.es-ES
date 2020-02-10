---
title: Comandos habituales
seo-title: Comandos habituales
description: Comandos habituales
seo-description: null
page-status-flag: never-activated
uuid: f06df8c0-d4ec-4d6b-84d5-f46d852388a3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: 90718075-87a7-4e9a-935b-571010908e79
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5f3ceab5ee82587d9f1829792bdabf2209f793cd

---


# Comandos habituales{#usual-commands}

Esta sección enumera los comandos habituales de Adobe Campaign.

El comando **nlserver** es el comando de entrada para toda la aplicación Adobe Campaign.

Este comando tiene la siguiente sintaxis: **nlserver **`<command>`****`<arguments>`****

El parámetro **`<command>`** corresponde al módulo.

>[!NOTE]
>
>* En cualquier caso, puede agregar el argumento **-noconsole** para eliminar los comentarios que se muestran una vez que se inician los módulos.
>* Por el contrario, puede agregar el argumento **-verbose** para mostrar más información.
>



## Comandos de supervisión {#monitoring-commands-}

>[!NOTE]
>
>Para enumerar todos los módulos, debe utilizar el comando **nlserver pdump** .

Puede agregar el parámetro **-who** para enumerar las conexiones en curso (base de datos y aplicación).

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

Otro comando útil es **nlserver monitor**. Enumera el archivo XML de supervisión (obtenido en el cliente de Adobe Campaign o a través de la página web **monitor.jsp** ).

Puede agregar el parámetro **-missing** para enumerar los módulos ausentes (error en módulos, módulos apagados, etc.)

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
>**`<instance>`** corresponde al nombre de la instancia tal como se especifica en los archivos de configuración, o **predeterminado** para los módulos de instancia única.

## Cerrar servicios {#shut-down-services}

Para detener los servicios de Adobe Campaign, utilice uno de los siguientes comandos:

* Si tiene acceso a la raíz o al administrador:

   * En Linux:

      ```
      /etc/init.d/nlserver6 stop
      ```

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

   * En Linux:/etc/init.d/nlserver6 start
   * En Windows:net start nlserver6

* En caso contrario, en la cuenta de Adobe Campaign: **nlserver watchdog -svc -noconsole**

## El comando config {#the-config-command}

El comando **config** permite administrar la configuración del servidor, incluida la reconfiguración de la conexión de base de datos.

Utilice el comando **config** del archivo ejecutable **nlserver** con el parámetro **-setdblogin** .

```
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

Introduzca la contraseña.

Para cambiar la contraseña **interna** : **nlserver config -internalpassword**

>[!CAUTION]
>
>Para iniciar sesión con el identificador **interno** , debe haber definido una contraseña de antemano. Para obtener más información, consulte [esta sección](../../installation/using/campaign-server-configuration.md#internal-identifier).

>[!NOTE]
>
>* En general, en lugar de modificar los archivos de configuración a mano, puede utilizar el comando **config**
>* Para obtener la lista de parámetros, utilice **-?** parámetro: **nlserver config -?**
>* En el caso de una base de datos Oracle, no debe especificar la cuenta. La sintaxis será la siguiente:
>
>  
nlserver config -setdblogin:Oracle:test6@dbserver


