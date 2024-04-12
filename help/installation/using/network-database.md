---
product: campaign
title: Red, base de datos y SSL/TLS
description: Obtenga más información acerca de las prácticas recomendadas de configuración de red, base de datos y SSL/TLS
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 2a66dfaa-7fff-48de-bdd4-62f3ebfbab19
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 9%

---

# Red, base de datos y SSL/TLS {#network-database}



## Configuración de red

Una cosa muy importante que hay que comprobar al implementar un tipo de arquitectura local es la [configuración de red](../../installation/using/network-configuration.md). Asegúrese de que el servidor Tomcat NO sea directamente accesible fuera del servidor:

* Cierre el puerto Tomcat (8080) en direcciones IP externas (debe funcionar en localhost)
* No asigne el puerto HTTP estándar (80) al Tomcat one (8080)

Cuando sea posible, utilice un canal seguro: POP3S en lugar de POP3 (o POP3 a través de TLS).

## Base de datos

Debe aplicar las prácticas recomendadas de seguridad del motor de la base de datos.

## Configuración de SSL/TLS

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

También puede utilizar un [pudrirse](https://github.com/nabla-c0d3/sslyze/releases) python script que hace ambas cosas.

```
python sslyze.py --sslv2 --sslv3 --tlsv1 --reneg --resum --certinfo=basic --hide_rejected_ciphers --sni=SNI myserver.com
```
