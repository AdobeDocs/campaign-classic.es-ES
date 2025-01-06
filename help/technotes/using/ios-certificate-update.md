---
product: campaign
title: 'Technote: actualización del certificado del servidor del servicio de notificaciones push de Apple'
description: Actualización del certificado del servidor del servicio de notificaciones push de Apple
feature: Technote, Push
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
source-git-commit: 0143e0d6ebcdbd96d183ddd0c7f07beb149a9670
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---

# Actualización del certificado del servidor del servicio de notificaciones push de Apple {#apns-certificate-update}



El 17 de octubre de 2024, una actualización de la infraestructura del servicio de notificaciones push de Apple (APN) afectó al canal de iOS de Adobe Campaign Classic. Un cambio en la configuración del sistema operativo es **obligatorio** para evitar la interrupción del canal push de iOS.

Obtenga más información acerca de los cambios de APN [en esta página](https://developer.apple.com/news/?id=09za8wzy).

Como cliente alojado, no es necesario realizar ninguna acción: Adobe ya ha incorporado el nuevo certificado raíz a su entorno.

Como cliente on-premise/híbrido, debe actualizar la configuración para garantizar una transición sin problemas **antes del 24 de febrero de 2025**.

Para incorporar el nuevo certificado, siga los pasos a continuación:

1. Descargue el **SHA-2 Root : USERTrust RSA Certification Authority certificate** certificado raíz [de esta página](https://www.sectigo.com/knowledge-base/detail/Sectigo-Intermediate-Certificates/kA01N000000rfBO).

1. Compruebe que el certificado AAA esté presente en los trustores de JAVA y del sistema operativo. Si no es así, agréguelo.

1. Reinicie el servicio web de Adobe Campaign:

   ```
   nlserver restart web
   ```
