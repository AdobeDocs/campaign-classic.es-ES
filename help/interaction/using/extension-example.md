---
product: campaign
title: Ejemplo de extensión
description: Ejemplo de extensión
feature: Interaction, Offers
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: d4acf99b-cef4-48f7-b4cd-c032ec12592f
TQID: https://experienceleague.adobe.com/TQZaYrJop03HAw47XPFqgmoxb073iC-xztTp-f-5dEk
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b6fcaf36-3bc4-4604-94f3-81b5d3f41ecf
subfeature_v2:
  - id: e739ee2b-6228-412e-878f-45de0791417d
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 160
ht-degree: 79%

---

# Ejemplo de extensión{#extension-example}



En el caso de un contacto entrante (centro de llamadas o sitio web), las ofertas más relevantes se sugieren a un contacto determinado mediante un conjunto de reglas de elegibilidad. Para enriquecer los criterios de idoneidad de sus ofertas, amplíe el esquema **nms:interaction**.

* Para agregar un nuevo contexto de interacción, amplíe el esquema **nms:interaction** y cree tantos elementos **attribute** como sea necesario en el esquema.

  En el siguiente ejemplo, los criterios añadidos son el código de país y la última página visitada.

  ![](assets/s_ncs_configuration_offer_schemas.png)

* A continuación, se puede utilizar los atributos creados previamente al realizar la definición de criterios de idoneidad.

  En el ejemplo siguiente, se puede crear criterios de idoneidad para mostrar una oferta en función del país del usuario o de la última página web que visitó.

  ![](assets/s_ncs_configuration_offer_context.png)

* Al configurar las llamadas SOAP, inserte el elemento XML **context** para hacer referencia a la información contextual añadida en el esquema de interacción. Para obtener más información, consulte [Integración mediante SOAP (servidor)](../../interaction/using/integration-via-soap-server-side.md).
