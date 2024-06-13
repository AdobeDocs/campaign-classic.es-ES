---
product: campaign
title: Acerca de los activadores de Adobe Experience Cloud
description: Introducción a la implementación de los activadores de Adobe Experience Cloud
feature: Triggers
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
audience: integrations
content-type: reference
exl-id: 0e337620-a49f-4e14-8c67-9279d74736f1
source-git-commit: 271e0f9fde0cbfb016e201c8390b26673d8fc696
workflow-type: ht
source-wordcount: '258'
ht-degree: 100%

---

# Uso de activadores de Campaign y de Experience Cloud{#about-adobe-experience-triggers}

[!DNL Triggers] es una integración entre Adobe Campaign y Adobe Analytics que utiliza la canalización. La canalización recupera las acciones o activadores de los usuarios desde el sitio web. El abandono del carro de compras es un ejemplo de activador. Los activadores se procesan en Adobe Campaign para enviar correos electrónicos en tiempo casi real.

>[!CAUTION]
>
>Esta capacidad no está disponible de forma predeterminada como parte del producto. Para esta implementación, trabaje con su representante de Adobe/Servicio de atención al cliente. A continuación, podrá seguir los pasos detallados en esta [página](../../integrations/using/configuring-pipeline.md#prerequisites).

[!DNL Triggers] ejecutan acciones de marketing en un corto intervalo de tiempo tras la acción de un usuario. El tiempo de respuesta típico es inferior a una hora.

Permite integraciones más ágiles, ya que la configuración es mínima y no participa un tercero.
También admite grandes volúmenes de tráfico sin afectar el rendimiento de las actividades de marketing. Como ejemplo, la integración puede procesar un millón de activadores por hora.

![](assets/do-not-localize/book.png) Descubra cómo [crear un activador de Experience Cloud](https://experienceleague.adobe.com/docs/experience-cloud/triggers/create.html?lang=es) e identificar, definir y monitorizar los comportamientos críticos del consumidor.

## Arquitectura de los [!DNL Triggers] {#triggers-architecture}

El [!DNL pipelined] proceso siempre se está ejecutando en el servidor de marketing de Adobe Campaign. Se conecta a la canalización, recupera los eventos y los procesa inmediatamente.

![](assets/triggers_2.png)

El proceso [!DNL pipelined] inicia sesión en Experience Cloud mediante un servicio de autenticación y envía una clave privada. El servicio de autenticación devuelve un token. El token se utiliza para autenticarse al recuperar los eventos.

Para obtener más información sobre la autenticación, consulte esta [página](../../integrations/using/configuring-adobe-io.md).
