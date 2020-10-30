---
title: Ejemplo de extensión
seo-title: Ejemplo de extensión
description: Ejemplo de extensión
seo-description: null
page-status-flag: never-activated
uuid: 6703b6e8-4eac-4a94-a80a-a7cd71b25cdf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: advanced-parameters
discoiquuid: 990b6cbc-9b7b-4278-a635-653d5abafe87
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '155'
ht-degree: 100%

---


# Ejemplo de extensión{#extension-example}

En el caso de un contacto entrante (centro de llamadas o sitio web), las ofertas más relevantes se sugieren a un contacto determinado mediante un conjunto de reglas de idoneidad. Para enriquecer los criterios de idoneidad de las ofertas, amplíe el esquema **de nms:interaction**.

* Para añadir un nuevo contexto de interacción, amplíe el esquema **nms:interaction** y cree todos los elementos **attribute** que sean necesarios en el esquema.

   En el siguiente ejemplo, los criterios añadidos son el código de país y la última página visitada.

   ![](assets/s_ncs_configuration_offer_schemas.png)

* A continuación, se puede utilizar los atributos creados previamente al realizar la definición de criterios de idoneidad.

   En el ejemplo siguiente, se puede crear criterios de idoneidad para mostrar una oferta en función del país del usuario o de la última página web que visitó.

   ![](assets/s_ncs_configuration_offer_context.png)

* Al configurar las llamadas SOAP, inserte el elemento XML **context** para hacer referencia a la información contextual añadida en el esquema de interacción. Para obtener más información, consulte [Integración mediante SOAP (servidor)](../../interaction/using/integration-via-soap--server-side-.md).

