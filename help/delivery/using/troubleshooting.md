---
product: campaign
title: Resolución de problemas push
description: Resolución de problemas push
feature: Push, Troubleshooting
role: User
hide: true
exl-id: 313eae5f-40db-4b1a-b013-f4adf8781763
TQID: https://experienceleague.adobe.com/3T6eC52Edyai-8Bn-ioDxvB5C04iDqBNmlZzuxVturE
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 109
ht-degree: 100%

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
