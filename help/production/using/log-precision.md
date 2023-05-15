---
product: campaign
title: Precisión de registro
description: Precisión de registro
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: c2470098-62f3-4fee-b1c5-800ed0e91f75
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 1%

---

# Precisión de registro{#log-precision}



Puede aplicar este proceso a todos los módulos de Adobe Campaign para aumentar la precisión de registro.

Requiere relanzar los procesos con un mayor nivel de registros.

>[!IMPORTANT]
>
>Este procedimiento cancela los servicios en curso en este módulo.

Adobe Campaign puede operar con dos niveles de registro:

1. La variable **Verbose** es el primer nivel después del nivel estándar. El siguiente comando lo activa:

   ```
   nlserver restart <MODULE_NAME> -verbose 
   ```

   Compruebe que el error se haya producido realmente y, a continuación, reinicie el proceso de la forma normal:

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

1. La variable **TraceFilter** , que permite guardar el número bueno de registros. Se activa mediante el siguiente comando:

   ```
   nlserver stop <MODULE_NAME>; nlserver <MODULE_NAME> -verbose -tracefilter:*
   ```

   >[!NOTE]
   >
   >Si usa **tracefilter:&#42;**, todos los tipos de registro están activados: ncm, rdr, nms, jst, temporización, wdbc, ldap, soap, xtk, xtkquery, sesión, xtkwriter, red, pop3, inmail\
   >Los tipos de registro más útiles son: **wdbc** (muestra todas las consultas SQL), **soap** (muestra todas las llamadas SOAP), **ldap** (muestra todas las consultas LDAP después de la autenticación), **xtkquery** (muestra la lista de todos los querydef).\
   >Puede utilizarlos de forma individual (**tracefilter:soap,wdbc** por ejemplo). También puede activarlos todos y elegir excluir algunos otros: **-tracefilter:&#42;,!soap**

   Compruebe que el error se haya producido realmente y, a continuación, reinicie el proceso de la forma normal:

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

>[!IMPORTANT]
>
>Los registros de estos comandos se almacenan en el archivo de registro del módulo.

Este es un ejemplo específico del módulo web. Los demás módulos funcionan como se ha indicado anteriormente.

Antes de enviar este comando, compruebe que no se vea afectado ningún trabajo en curso:

```
nlserver pdump -who
```

A continuación, cierre y reinicie el módulo en **TraceFilter** modo:

```
nlserver stop web; LD_PRELOAD=libjsig.so nlserver web -tomcat -verbose -tracefilter:* -tracefile:web_debug@default
```

Otro ejemplo:

```
nlserver stop mta@<INSTANCE_NAME>; nlserver mta -instance:<INSTANCE_NAME> -tracefilter:* -tracefile:mta_debug@<INSTANCE_NAME>
```

>[!NOTE]
>
>La variable **Archivo de seguimiento** permite guardar los registros. En los ejemplos anteriores, los registros se guardan en la variable **var/`<instance-name>`/mta_debug.log** y **var/default/web_debug.log** archivos.

>[!IMPORTANT]
>
>En Windows, no agregue la opción LD_PRELOAD . El siguiente comando es suficiente:\
>nlserver web -tomcat -verbose -tracefilter:&#42;

Compruebe que el problema vuelva a ocurrir y, a continuación, reinicie el módulo:

```
nlserver restart web -tomcat -noconsole
```

Toda la información está disponible en el archivo **/usr/local/neolane/nl6/var/default/log/web.log**.
