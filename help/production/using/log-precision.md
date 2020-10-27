---
title: Precisión de registro
seo-title: Precisión de registro
description: Precisión de registro
seo-description: null
page-status-flag: never-activated
uuid: 8396bc4f-2954-40bb-b511-61802e60e123
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: c6c39b7d-7bbd-4789-b1ea-b938153e9679
translation-type: tm+mt
source-git-commit: 849e1ebf14f707d9e86c5a152de978acb6f1cb35
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 2%

---


# Precisión de registro{#log-precision}

Puede aplicar este proceso a todos los módulos de Adobe Campaign para aumentar la precisión del registro.

Implica reiniciar los procesos con un nivel de registros más alto.

>[!IMPORTANT]
>
>Este procedimiento cancela los servicios en curso en este módulo.

Adobe Campaign puede funcionar con dos niveles de registro:

1. El modo **Verbose** es el primer nivel después del nivel estándar. El siguiente comando lo activa:

   ```
   nlserver restart <MODULE_NAME> -verbose 
   ```

   Compruebe que el error se ha producido realmente y, a continuación, reinicie el proceso de la forma normal:

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

1. El modo **TraceFilter** , que permite guardar el número bueno de registros. Se activa mediante el siguiente comando:

   ```
   nlserver stop <MODULE_NAME>; nlserver <MODULE_NAME> -verbose -tracefilter:*
   ```

   >[!NOTE]
   >
   >Si utiliza **tracefilter:***, se activan todos los tipos de registro: ncm, rdr, nms, jst, temporización, wdbc, ldap, soap, xtk, xtkquery, sesión, xtkwriter, red, pop3, inmail\
   Los tipos de registro más útiles son: **wdbc** (muestra todas las consultas SQL), **soap** (muestra todas las llamadas SOAP), **ldap** (muestra todas las consultas LDAP después de la autenticación), **xtkquery** (muestra la lista de toda la querydef).\
   Puede utilizarlos individualmente (**tracefilter:soap,wdbc** , por ejemplo). También puede activarlas todas y elegir excluir otras: **-tracefilter:*,!soap**

   Compruebe que el error se ha producido realmente y, a continuación, reinicie el proceso de la forma normal:

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

>[!IMPORTANT]
Los registros de estos comandos se almacenan en el archivo de registro del módulo.

Este es un ejemplo específico del módulo Web. Los demás módulos funcionan como se ha indicado anteriormente.

Antes de enviar este comando, compruebe que no se verá afectado ningún trabajo en curso.

```
nlserver pdump -who
```

A continuación, apague y reinicie el módulo en modo **TraceFilter** .

```
nlserver stop web; LD_PRELOAD=libjsig.so nlserver web -tomcat -verbose -tracefilter:* -tracefile:web_debug@default
```

Otro ejemplo:

```
nlserver stop mta@<INSTANCE_NAME>; nlserver mta -instance:<INSTANCE_NAME> -tracefilter:* -tracefile:mta_debug@<INSTANCE_NAME>
```

>[!NOTE]
El modo **Archivo** de seguimiento permite guardar los registros. En los ejemplos anteriores, los registros se guardan en los archivos **var/`<instance-name>`/mta_debug.log** y **var/default/web_debug.log** .

>[!IMPORTANT]
En Windows, no agregue la opción LD_PRELOAD. Basta con el siguiente comando:\
nlserver web -tomcat -verbose -tracefilter:*

Compruebe que el problema vuelve a producirse y, a continuación, reinicie el módulo:

```
nlserver restart web -tomcat -noconsole
```

Toda la información está disponible en el archivo **/usr/local/neolane/nl6/var/default/log/web.log**.
