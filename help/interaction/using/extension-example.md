---
product: campaign
title: Ejemplo de extensión
description: Ejemplo de extensión
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: d4acf99b-cef4-48f7-b4cd-c032ec12592f
source-git-commit: 07a5742c6f142c786ad8ba2f8774e7e90e8cd191
workflow-type: ht
source-wordcount: '153'
ht-degree: 100%

---

# Ejemplo de extensión{#extension-example}

![](../../assets/common.svg)

En el caso de un contacto entrante (centro de llamadas o sitio web), las ofertas más relevantes se sugieren a un contacto determinado mediante un conjunto de reglas de idoneidad. Para enriquecer los criterios de idoneidad de las ofertas, amplíe el esquema **de nms:interaction**.

* Para añadir un nuevo contexto de interacción, amplíe el esquema **nms:interaction** y cree todos los elementos **attribute** que sean necesarios en el esquema.

   En el siguiente ejemplo, los criterios añadidos son el código de país y la última página visitada.

   ![](assets/s_ncs_configuration_offer_schemas.png)

* A continuación, se puede utilizar los atributos creados previamente al realizar la definición de criterios de idoneidad.

   En el ejemplo siguiente, se puede crear criterios de idoneidad para mostrar una oferta en función del país del usuario o de la última página web que visitó.

   ![](assets/s_ncs_configuration_offer_context.png)

* Al configurar las llamadas SOAP, inserte el elemento XML **context** para hacer referencia a la información contextual añadida en el esquema de interacción. Para obtener más información, consulte [Integración mediante SOAP (servidor)](../../interaction/using/integration-via-soap--server-side-.md).
