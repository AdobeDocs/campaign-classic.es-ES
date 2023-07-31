---
product: campaign
title: Resolución de problemas push
description: Resolución de problemas push
badge-v7-only: label="v7" type="Informative" tooltip="Solo se aplica a Campaign Classic v7"
feature: Push, Troubleshooting
exl-id: 313eae5f-40db-4b1a-b013-f4adf8781763
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 94%

---

# Resolución de problemas{#troubleshooting}



Si su dispositivo móvil está conectado a una red wifi y no recibe las notificaciones, compruebe que el firewall no haya bloqueado los puertos FCM/APN.

**Android**: El dispositivo móvil se conecta a los servidores FCM en los puertos 5228 a 5230. Por lo tanto, se debe configurar el cortafuegos para que autorice la conexión con FCM. Los puertos que se van a abrir son: 5228 (el más utilizado), 5229 y 5230.

**iOS**:

Conector HTTP/2: se debe permitir la comunicación con los siguientes servidores:

* api.push.apple.com: puerto 443
* api.development.push.apple.com: puerto 443

>[!NOTE]
>
>Para obtener más información sobre los dos conectores, consulte [Configuración de la aplicación móvil en Adobe Campaign](configuring-the-mobile-application.md).
