---
title: Acerca de la mensajería transaccional
seo-title: Acerca de la mensajería transaccional
description: Acerca de la mensajería transaccional
seo-description: null
page-status-flag: never-activated
uuid: c854daac-8756-44f3-a4e2-be31177ab9d1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: introduction
discoiquuid: 97df4bd5-a8e3-48f4-87c8-fa090ea3f771
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f4ecdab4c17a6ba8deb3b98079f57bb7a9adf4a0
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 100%

---


# Acerca de la mensajería transaccional{#about-transactional-messaging}

La mensajería transaccional (Centro de Mensajes) es un módulo de Campaign diseñado para gestionar mensajes de activación. Estos mensajes se generan a partir de eventos activados desde sistemas de información y pueden ser: una factura, una confirmación de pedido, una confirmación de envío, un cambio de contraseña, una notificación de no disponibilidad del producto, el estado de la cuenta o una creación de cuenta en un sitio web, por ejemplo.

>[!IMPORTANT]
>
>La mensajería transaccional requiere una licencia específica. Compruebe el acuerdo de licencia.

El módulo del Centro de Mensajes de Adobe Campaign está integrado en un sistema de información que devuelve eventos que se deben modificar en mensajes transaccionales personalizados. Estos mensajes se pueden enviar por separado o en serie por correo electrónico, SMS o notificaciones push.

En esta arquitectura específica, la celda de ejecución se separa de la instancia de control, lo que garantiza una mayor disponibilidad y una mejor gestión de la carga.

>[!NOTE]
>
>Para crear nuevos usuarios para las instancias de ejecución del Centro de Mensajes alojadas en Adobe Cloud, debe ponerse en contacto con el servicio de atención al cliente de Adobe. Los usuarios del Centro de Mensajes son operadores específicos que requieren permisos específicos para acceder a las carpetas “Eventos en tiempo real” (nmsRtEvent).
