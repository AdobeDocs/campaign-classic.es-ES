---
product: campaign
title: Red, base de datos y SSL/TLS
description: Obtenga más información acerca de las prácticas recomendadas de configuración de red, base de datos y SSL/TLS
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 2a66dfaa-7fff-48de-bdd4-62f3ebfbab19
TQID: https://experienceleague.adobe.com/PLGVcm4QYeU0A1uEhlDEfweZ275xpxtxo91r4aidr1I
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 138
ht-degree: 9%

---

# Red, base de datos y SSL/TLS {#network-database}

## Configuración de red

Algo muy importante que hay que comprobar al implementar un tipo de arquitectura local es la [configuración de red](../../installation/using/network-configuration.md). Asegúrese de que el servidor Tomcat NO sea directamente accesible fuera del servidor:

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

También puede usar un script python [sslyze](https://github.com/nabla-c0d3/sslyze/releases) que hace ambas cosas.

```
python sslyze.py --sslv2 --sslv3 --tlsv1 --reneg --resum --certinfo=basic --hide_rejected_ciphers --sni=SNI myserver.com
```
