---
solution: Campaign Classic
product: campaign
title: Resolución de problemas
description: Resolución de problemas
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 100%

---


# Resolución de problemas{#troubleshooting}

Si su dispositivo móvil está conectado a una red wifi y no recibe las notificaciones, compruebe que el firewall no haya bloqueado los puertos FCM/APN.

**Android**: El dispositivo móvil se conecta a los servidores FCM en los puertos 5228 a 5230. Por lo tanto, se debe configurar el cortafuegos para que autorice la conexión con FCM. Los puertos que se van a abrir son: 5228 (el más utilizado), 5229 y 5230.

**iOS**:

Conector binario: para enviar notificaciones, se debe autorizar el tráfico TCP entrante y saliente en el puerto 2195. Los dispositivos conectados al servicio push deben autorizar el tráfico TCP entrante y saliente en el puerto 5223.

Conector HTTP/2: se debe permitir la comunicación con los siguientes servidores:

* api.push.apple.com: puerto 443
* api.development.push.apple.com: puerto 443

>[!NOTE]
>
>Para obtener más información sobre los dos conectores, consulte [Configuración de la aplicación móvil en Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md).
