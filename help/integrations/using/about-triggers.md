---
title: Acerca de Adobe Experience Manager
seo-title: Acerca de Adobe Experience Manager
description: Acerca de Adobe Experience Manager
seo-description: null
page-status-flag: never-activated
uuid: c523822f-8178-4989-bd88-ab402470e540
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 0d617f1c-0d0b-489f-9027-a92b1f1eee37
translation-type: tm+mt
source-git-commit: d15e953740b0a4dd8073b36fd59b4c4e44906340
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 75%

---


# Acerca de los activadores de Adobe Experience Cloud{#about-adobe-experience-triggers}

[!DNL Triggers] es una integración entre Adobe Campaign y Adobe Analytics que utiliza la canalización. La canalización recupera las acciones o activadores de los usuarios desde el sitio web. El abandono del carro de compras es un ejemplo de activador. Los activadores se procesan en Adobe Campaign para enviar correos electrónicos en tiempo casi real.

[!DNL Triggers] ejecutar acciones de marketing en un corto intervalo de tiempo tras la acción de un usuario. El tiempo de respuesta típico es inferior a una hora.

Permite integraciones más ágiles, ya que la configuración es mínima y no participa un tercero.
También admite grandes volúmenes de tráfico sin afectar el rendimiento de las actividades de marketing. Como ejemplo, la integración puede procesar un millón de activadores por hora.

## [!DNL Triggers] arquitectura {#triggers-architecture}

El [!DNL pipelined] proceso siempre se está ejecutando en el servidor de marketing de Adobe Campaign. Se conecta a la canalización, recupera los eventos y los procesa inmediatamente.

![](assets/triggers_2.png)

El proceso [!DNL pipelined] inicia sesión en Experience Cloud mediante un servicio de autenticación y envía una clave privada. El servicio de autenticación devuelve un token. El token se utiliza para autenticarse al recuperar los eventos.

For more information on authentication, refer to this [page](../../integrations/using/configuring-adobe-io.md).

>[!NOTE]
>
>El procesamiento posterior de eventos se realiza como parte del paquete ACX proporcionado fuera de la implementación predeterminada. El evento recibido se procesa inmediatamente mediante código JavaScript. Se guarda en una tabla de base de datos sin ningún otro procesamiento en tiempo real. Los activadores se utilizan para la segmentación mediante un flujo de trabajo de campaña que envía correos electrónicos. La campaña está configurada para que el cliente que ha activado el evento reciba un correo electrónico.
