---
solution: Campaign Classic
product: campaign
title: Nota técnica
description: Nota técnica
hide: false
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 08c6e84e07da2811c91aa58ddf40c5781de2b163
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---


# Actualización del certificado del servidor del servicio de notificaciones push de Apple {#apns-certificate-update}

El 29 de marzo de 2021, la actualización de la infraestructura del servicio de notificaciones push de Apple (APNS) afectará al canal iOS de Adobe Campaign Classic. Un cambio en la configuración del sistema operativo es **obligatorio** para evitar la interrupción del canal push de iOS.

Obtenga más información sobre los cambios de APNS [en esta página](https://developer.apple.com/news/?id=7gx0a2lp).

Como cliente alojado, no es necesario realizar ninguna acción: Adobe ya ha incorporado el nuevo certificado raíz a su entorno.

Como cliente local/híbrido, debe actualizar la configuración para garantizar una transición sin problemas **antes del 29 de marzo de 2021**.

Para incorporar el nuevo certificado, siga los pasos a continuación:

1. Descargue el **AAACcertificateServices 5/12/2020** certificado raíz [desde esta página](https://support.sectigo.com/Com_KnowledgeDetailPage?Id=kA03l00000117cL).

1. Compruebe que el certificado AAA esté presente tanto en las confianzas del sistema operativo como de JAVA. Si no es así, agréguelo.

1. Reinicie el servicio web de Adobe Campaign:

   ```
   nlserver restart web
   ```

