---
product: campaign
title: 'Nota técnica: Actualización de certificados del servidor del servicio de notificaciones push de Apple'
description: Actualización de certificados del servidor del servicio de notificaciones push de Apple
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# Actualización de certificados del servidor del servicio de notificaciones push de Apple {#apns-certificate-update}



El 29 de marzo de 2021, una actualización de la infraestructura del servicio de notificaciones push de Apple (APNS) afectó al canal iOS de Adobe Campaign Classic. Un cambio en la configuración de SO es **mandatory** para evitar la interrupción del canal push de iOS.

Más información sobre los cambios de APNS [en esta página](https://developer.apple.com/news/?id=7gx0a2lp).

Como cliente alojado, no es necesario realizar ninguna acción: Adobe ya ha incorporado el nuevo certificado raíz a su entorno.

Como cliente local/híbrido, debe actualizar la configuración para garantizar una transición sin problemas **antes del 29 de marzo de 2021**.

Para incorporar el nuevo certificado, siga los pasos a continuación:

1. Descargue el **AAACcertificateServices 5/12/2020** certificado raíz [desde esta página](https://support.sectigo.com/Com_KnowledgeDetailPage?Id=kA03l00000117cL).

1. Compruebe que el certificado AAA esté presente tanto en las confianzas del sistema operativo como de JAVA. Si no es así, agréguelo.

1. Reinicie el servicio web de Adobe Campaign:

   ```
   nlserver restart web
   ```
