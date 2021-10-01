---
product: campaign
title: Resolución de problemas
description: Resolución de problemas
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
exl-id: 313eae5f-40db-4b1a-b013-f4adf8781763
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: ht
source-wordcount: '98'
ht-degree: 100%

---

# Resolución de problemas{#troubleshooting}

![](../../assets/common.svg)

Si su dispositivo móvil está conectado a una red wifi y no recibe las notificaciones, compruebe que el firewall no haya bloqueado los puertos FCM/APN.

**Android**: El dispositivo móvil se conecta a los servidores FCM en los puertos 5228 a 5230. Por lo tanto, se debe configurar el cortafuegos para que autorice la conexión con FCM. Los puertos que se van a abrir son: 5228 (el más utilizado), 5229 y 5230.

**iOS**:

Conector HTTP/2: se debe permitir la comunicación con los siguientes servidores:

* api.push.apple.com: puerto 443
* api.development.push.apple.com: puerto 443

>[!NOTE]
>
>Para obtener más información sobre los dos conectores, consulte [Configuración de la aplicación móvil en Adobe Campaign](configuring-the-mobile-application.md).
