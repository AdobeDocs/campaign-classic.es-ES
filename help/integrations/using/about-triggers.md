---
product: campaign
title: Acerca de los activadores de Adobe Experience Cloud
description: Introducción a la implementación de los activadores de Adobe Experience Cloud
feature: Triggers
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
audience: integrations
content-type: reference
level: Intermediate, Experienced
exl-id: 0e337620-a49f-4e14-8c67-9279d74736f1
TQID: https://experienceleague.adobe.com/gWgUCcgsqeMw-mzVdhVodcp91lgTCCL7XGWp0f2ItKo
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
  - id: df0d6518-6f49-46e2-b46e-3bcc513f553f
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 392
ht-degree: 95%

---

# Uso de activadores de Campaign y de Experience Cloud{#about-adobe-experience-triggers}

[!DNL Triggers] es una integración entre Adobe Campaign y Adobe Analytics que utiliza la canalización. La canalización recupera las acciones o activadores de los usuarios desde el sitio web. El abandono del carro de compras es un ejemplo de activador. Los activadores se procesan en Adobe Campaign para enviar correos electrónicos en tiempo casi real.

>[!CAUTION]
>
>Esta capacidad no está disponible de forma predeterminada como parte del producto. Para esta implementación, trabaje con su representante de Adobe/Servicio de atención al cliente. A continuación, podrá seguir los pasos detallados en esta [página](../../integrations/using/configuring-pipeline.md#prerequisites).

[!DNL Triggers] ejecutan acciones de marketing en un corto intervalo de tiempo tras la acción de un usuario. El tiempo de respuesta típico es inferior a una hora.

Permite integraciones más ágiles, ya que la configuración es mínima y no participa un tercero.
También admite grandes volúmenes de tráfico sin afectar el rendimiento de las actividades de marketing. Por ejemplo, la integración puede procesar un millón de déclencheur por hora.

![](assets/do-not-localize/book.png) Descubra cómo [crear un activador de Experience Cloud](https://experienceleague.adobe.com/docs/experience-cloud/triggers/create.html?lang=es) e identificar, definir y monitorizar los comportamientos críticos del consumidor.

## Arquitectura de los [!DNL Triggers] {#triggers-architecture}

El [!DNL pipelined] proceso siempre se está ejecutando en el servidor de marketing de Adobe Campaign. Se conecta a la canalización, recupera los eventos y los procesa inmediatamente.

![](assets/triggers_2.png)

El proceso [!DNL pipelined] inicia sesión en Experience Cloud mediante un servicio de autenticación y envía una clave privada. El servicio de autenticación devuelve un token. El token se utiliza para autenticarse al recuperar los eventos.

## Requisitos previos {#adobe-io-prerequisites}

Antes de iniciar esta implementación, compruebe lo siguiente:

* **Un identificador de organización** válido: el identificador de organización es el identificador único de Adobe Experience Cloud que se utiliza, por ejemplo, para el servicio VisitorID y el inicio de sesión único (SSO) de IMS. [Más información](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=es)
* un **acceso para desarrolladores** para su organización. El administrador del sistema de la organización debe seguir el procedimiento **Adición de desarrolladores a un único perfil de producto** detallado [en esta página](https://helpx.adobe.com/es/enterprise/using/manage-developers.html) para proporcionar acceso de desarrollador al perfil `Analytics - {tenantID}` del producto de Adobe Analytics asociado a activadores.

## Pasos de implementación {#implement}

Para implementar Campaign y los activadores de Experience Cloud, siga estos pasos:

1. Cree un proyecto de OAuth. [Más información](oauth-technical-account.md#oauth-service)

1. Añada las credenciales del proyecto OAuth en Adobe Campaign. [Más información](oauth-technical-account.md#add-credentials)

1. Actualice el tipo de autenticación en el proyecto de Developer Console en el archivo de configuración **config-&lt; nombre_instancia >.xml** como sigue:

   ```
   <pipelined ... authType="imsJwtToken"  ... />
   ```

   A continuación, ejecute un `config -reload` y un reinicio del [!DNL pipelined] para que se tengan en cuenta los cambios.

