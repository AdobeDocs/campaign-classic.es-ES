---
title: Resolución de problemas
seo-title: Resolución de problemas
description: Resolución de problemas
seo-description: null
page-status-flag: never-activated
uuid: 02bd48cf-3928-4817-97b0-1e64cc8ad8ef
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: b64c9729-cfe2-4d02-8c59-9e53efd34a96
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: fa2b6890d3c9eaf7b4b6521b2edfb494faa4798c

---


# Resolución de problemas{#troubleshooting}

Si su dispositivo móvil está conectado a una red Wi-Fi y no recibe notificaciones, compruebe que el cortafuegos no haya bloqueado los puertos FCM/APNS.

**Android**: El dispositivo móvil se conecta a los servidores FCM en los puertos 5228 a 5230. Por lo tanto, se debe configurar el cortafuegos para que autorice la conexión con FCM. Los puertos que se van a abrir son: 5228 (el más utilizado), 5229 y 5230.

**iOS**:

Conector binario: para enviar notificaciones, se debe autorizar el tráfico TCP entrante y saliente en el puerto 2195. Los dispositivos conectados al servicio push deben autorizar el tráfico TCP entrante y saliente en el puerto 5223.

Conector HTTP/2: se debe permitir la comunicación con los siguientes servidores:

* api.push.apple.com: puerto 443
* api.development.push.apple.com: puerto 443

>[!NOTE]
>
>Para obtener más información sobre los dos conectores, consulte [Configuración de la aplicación móvil en Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md).
