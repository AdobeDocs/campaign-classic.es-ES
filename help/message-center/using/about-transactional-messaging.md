---
solution: Campaign Classic
product: campaign
title: Acerca de la mensajería transaccional
description: 'Envíe mensajes desencadenadores basados en eventos generados a partir de sistemas de información. '
audience: message-center
content-type: reference
topic-tags: introduction
translation-type: tm+mt
source-git-commit: 3139a9bf5036086831e23acef21af937fcfda740
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 88%

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
>Para crear nuevos usuarios para instancias de ejecución de centros de mensajes alojadas en Adobe Cloud, debe ponerse en contacto con [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Los usuarios del Centro de Mensajes son operadores específicos que requieren permisos específicos para acceder a las carpetas “Eventos en tiempo real” (nmsRtEvent).
