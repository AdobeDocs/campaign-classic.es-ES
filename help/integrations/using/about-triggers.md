---
product: campaign
title: Acerca de los activadores de Adobe Experience Cloud
description: Introducción a la implementación de los activadores de Adobe Experience Cloud
audience: integrations
content-type: reference
exl-id: 0e337620-a49f-4e14-8c67-9279d74736f1
source-git-commit: 0a59b0dbdbe70cf8993ce7153b8f3c049c1f1108
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 88%

---

# Uso de activadores de Campaign y de Experience Cloud{#about-adobe-experience-triggers}

![](../../assets/common.svg)

[!DNL Triggers] es una integración entre Adobe Campaign y Adobe Analytics que utiliza la canalización. La canalización recupera las acciones o activadores de los usuarios desde el sitio web. El abandono del carro de compras es un ejemplo de activador. Los activadores se procesan en Adobe Campaign para enviar correos electrónicos en tiempo casi real.

>[!CAUTION]
>
>Esta capacidad no está disponible de forma predeterminada como parte del producto. Para esta implementación, primero debe abrir un ticket con Soporte de Adobe. A continuación, podrá seguir los pasos detallados en esta [página](../../integrations/using/configuring-pipeline.md#prerequisites).

[!DNL Triggers] ejecutar acciones de marketing en un corto intervalo de tiempo tras la acción de un usuario. El tiempo de respuesta típico es inferior a una hora.

Permite integraciones más ágiles, ya que la configuración es mínima y no participa un tercero.
También admite grandes volúmenes de tráfico sin afectar el rendimiento de las actividades de marketing. Como ejemplo, la integración puede procesar un millón de activadores por hora.

## Arquitectura de los [!DNL Triggers] {#triggers-architecture}

El [!DNL pipelined] proceso siempre se está ejecutando en el servidor de marketing de Adobe Campaign. Se conecta a la canalización, recupera los eventos y los procesa inmediatamente.

![](assets/triggers_2.png)

El proceso [!DNL pipelined] inicia sesión en Experience Cloud mediante un servicio de autenticación y envía una clave privada. El servicio de autenticación devuelve un token. El token se utiliza para autenticarse al recuperar los eventos.

Para obtener más información sobre la autenticación, consulte esta [página](../../integrations/using/configuring-adobe-io.md).
