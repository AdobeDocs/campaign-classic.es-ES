---
solution: Campaign Classic
product: campaign
title: Acerca de los activadores de Adobe Experience Cloud
description: Introducción a la implementación de los activadores de Adobe Experience Cloud
audience: integrations
content-type: reference
translation-type: tm+mt
source-git-commit: d7de46abb71ca25ef765c6fb5443f6e338fba56e
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 100%

---


# Introducción a los activadores de Adobe Experience Cloud{#about-adobe-experience-triggers}

[!DNL Triggers] es una integración entre Adobe Campaign y Adobe Analytics que utiliza la canalización. La canalización recupera las acciones o activadores de los usuarios desde el sitio web. El abandono del carro de compras es un ejemplo de activador. Los activadores se procesan en Adobe Campaign para enviar correos electrónicos en tiempo casi real.

>[!CAUTION]
>
>Esta capacidad no está disponible de forma predeterminada como parte del producto. La implementación requiere la participación de Adobe Consulting. Póngase en contacto con el representante de su Adobe para obtener más información

[!DNL Triggers] ejecutar acciones de marketing en un corto intervalo de tiempo tras la acción de un usuario. El tiempo de respuesta típico es inferior a una hora.

Permite integraciones más ágiles, ya que la configuración es mínima y no participa un tercero.
También admite grandes volúmenes de tráfico sin afectar el rendimiento de las actividades de marketing. Como ejemplo, la integración puede procesar un millón de activadores por hora.

## [!DNL Triggers] arquitectura {#triggers-architecture}

El [!DNL pipelined] proceso siempre se está ejecutando en el servidor de marketing de Adobe Campaign. Se conecta a la canalización, recupera los eventos y los procesa inmediatamente.

![](assets/triggers_2.png)

El proceso [!DNL pipelined] inicia sesión en Experience Cloud mediante un servicio de autenticación y envía una clave privada. El servicio de autenticación devuelve un token. El token se utiliza para autenticarse al recuperar los eventos.

Para obtener más información sobre la autenticación, consulte esta [página](../../integrations/using/configuring-adobe-io.md).
