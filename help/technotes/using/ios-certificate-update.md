---
product: campaign
title: 'Technote: actualización del certificado del servidor del servicio de notificaciones push de Apple'
description: Actualización del certificado del servidor del servicio de notificaciones push de Apple
feature: Technote, Push
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---

# Actualización del certificado del servidor del servicio de notificaciones push de Apple {#apns-certificate-update}



El 29 de marzo de 2021, una actualización de la infraestructura del servicio de notificaciones push de Apple (APN) afectó al canal de iOS de Adobe Campaign Classic. Un cambio en la configuración del sistema operativo es **obligatorio** para evitar la interrupción del canal push de iOS.

Más información sobre los cambios de APNS [en esta página](https://developer.apple.com/news/?id=7gx0a2lp).

Como cliente alojado, no es necesario realizar ninguna acción: Adobe ya ha incorporado el nuevo certificado raíz a su entorno.

Como cliente on-premise/híbrido, debe actualizar la configuración para garantizar una transición sin problemas **antes del 29 de marzo de 2021**.

Para incorporar el nuevo certificado, siga los pasos a continuación:

1. Descargue la **AAACertificateServices 12/5/2020** certificado raíz [desde esta página](https://support.sectigo.com/Com_KnowledgeDetailPage?Id=kA03l00000117cL).

1. Compruebe que el certificado AAA esté presente en los trustores de JAVA y del sistema operativo. Si no es así, agréguelo.

1. Reinicie el servicio web de Adobe Campaign:

   ```
   nlserver restart web
   ```
