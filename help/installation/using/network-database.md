---
product: campaign
title: Red, base de datos y SSL/TLS
description: Obtenga más información sobre las prácticas recomendadas de configuración de red, base de datos y SSL/TLS.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 2a66dfaa-7fff-48de-bdd4-62f3ebfbab19
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 9%

---

# Red, base de datos y SSL/TLS {#network-database}

![](../../assets/v7-only.svg)

## Configuración de red

Un aspecto muy importante que debe comprobar al implementar un tipo de arquitectura local es la [configuración de red](../../installation/using/network-configuration.md). Asegúrese de que NO se pueda acceder directamente al servidor Tomcat desde fuera del servidor:

* Cierre el puerto Tomcat (8080) en direcciones IP externas (debe funcionar en localhost)
* No asigne el puerto HTTP estándar (80) al puerto Tomcat (8080)

Cuando sea posible, utilice un canal seguro: POP3S en lugar de POP3 (o POP3 sobre TLS).

## Database

Debe aplicar las prácticas recomendadas de seguridad del motor de base de datos.

## Configuración SSL/TLS

Para comprobar el certificado, puede utilizar openssl. Para comprobar las cifras activas, puede utilizar nmap:

```
#!/bin/sh
#
# usage: testSSL.sh remote.host.name [port]
#
REMHOST=$1
REMPORT=${2:-443}
 
echo |\
openssl s_client -connect ${REMHOST}:${REMPORT} -servername ${REMHOST} 2>&1 |\
sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p' |\
openssl x509 -noout -subject -dates
   
nmap --script ssl-enum-ciphers -p ${REMPORT} ${REMHOST}
```

También puede usar un [sslyze](https://github.com/nabla-c0d3/sslyze/releases) script python que hace ambos.

```
python sslyze.py --sslv2 --sslv3 --tlsv1 --reneg --resum --certinfo=basic --hide_rejected_ciphers --sni=SNI myserver.com
```
