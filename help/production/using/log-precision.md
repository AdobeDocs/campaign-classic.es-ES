---
product: campaign
title: Precisión de registro
description: Precisión de registro
feature: Monitoring
badge-v7-prem: label="On-premise/híbrido solo" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: c2470098-62f3-4fee-b1c5-800ed0e91f75
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 5%

---

# Precisión de registro{#log-precision}



Puede aplicar este proceso a todos los módulos de Adobe Campaign para aumentar la precisión del registro.

Implica reiniciar los procesos con un nivel más alto de registros.

>[!IMPORTANT]
>
>Este procedimiento cancela los servicios en curso en este módulo.

Adobe Campaign puede funcionar con dos niveles de registro:

1. El modo **Detallado** es el primer nivel después del nivel estándar. El siguiente comando lo activa:

   ```
   nlserver restart <MODULE_NAME> -verbose 
   ```

   Compruebe que se ha producido el error y, a continuación, reinicie el proceso de forma normal:

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

1. El modo **TraceFilter**, que permite guardar el mayor número de registros. Se activa mediante el siguiente comando:

   ```
   nlserver stop <MODULE_NAME>; nlserver <MODULE_NAME> -verbose -tracefilter:*
   ```

   >[!NOTE]
   >
   >Si usa **tracefilter:&#42;**, se activarán todos los tipos de registro: ncm, rdr, nms, jst, timing, wdbc, ldap, soap, xtk, xtkquery, session, xtkwriter, network, pop3, inmail\
   >SOAP Los tipos de registro más útiles son: **wdbc** (muestra todas las consultas SQL), **soap** (muestra todas las llamadas a la), **ldap** (muestra todas las consultas LDAP después de la autenticación), **xtkquery** (muestra la lista de todas las consultas def).\
   >Puede usarlos por separado (**tracefilter:soap,wdbc** por ejemplo). También puede activarlos todos y elegir excluir otros: **-tracefilter:&#42;,!soap**

   Compruebe que se ha producido el error y, a continuación, reinicie el proceso de forma normal:

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

>[!IMPORTANT]
>
>Los registros de estos comandos se almacenan en el archivo de registro del módulo.

Este es un ejemplo específico del módulo web. Los otros módulos funcionan como se ha indicado anteriormente.

Antes de enviar este comando, compruebe que ningún trabajo en curso se vea afectado:

```
nlserver pdump -who
```

A continuación, apague y reinicie el módulo en el modo **TraceFilter**:

```
nlserver stop web; LD_PRELOAD=libjsig.so nlserver web -tomcat -verbose -tracefilter:* -tracefile:web_debug@default
```

Otro ejemplo:

```
nlserver stop mta@<INSTANCE_NAME>; nlserver mta -instance:<INSTANCE_NAME> -tracefilter:* -tracefile:mta_debug@<INSTANCE_NAME>
```

>[!NOTE]
>
>El modo **Tracefile** le permite guardar los registros. En los ejemplos anteriores, los registros se guardan en los archivos **var/`<instance-name>`/mta_debug.log** y **var/default/web_debug.log**.

>[!IMPORTANT]
>
>En Windows, no agregue la opción LD_PRELOAD. El siguiente comando es suficiente:\
>nlserver web -tomcat -verbose -tracefilter:&#42;

Compruebe que el problema vuelva a ocurrir y reinicie el módulo:

```
nlserver restart web -tomcat -noconsole
```

Toda la información está disponible en el archivo **/usr/local/neolane/nl6/var/default/log/web.log**.
