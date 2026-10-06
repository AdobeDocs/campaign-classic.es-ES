---
product: campaign
title: 'Technote: actualización del certificado del servidor del servicio de notificaciones push de Apple'
description: Actualización del certificado del servidor del servicio de notificaciones push de Apple
feature: Technote, Push
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
TQID: 'https://experienceleague.adobe.com/3tQ4npyE0-ZfCgVPYy3kiRv1q0HPcq-DI4rpAXTCXb0'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: ab81f6c3-9317-564f-af92-6670a8784294
    internal-label: Technote
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
    internal-label: Analytics integration
  - id: a4657621-810c-498b-8a27-7ced9c176dda
    internal-label: Push notifications
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '160'
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
