---
product: campaign
title: Detección de direcciones URL de seguimiento
description: Obtenga más información acerca del patrón recomendado para rastrear direcciones URL
feature: Monitoring
role: User, Developer
exl-id: 7611d6a1-6c55-4ba3-b905-58426c944991
TQID: 'https://experienceleague.adobe.com/F63e0G1uyp-tXDiBk9cau5P-HBHttCkiFD2yw657RBw'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
source-git-commit: d7e5f68c0d2e0b94fd5cfdf2981bed29f33d9f62
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 76%
---
# Detección de direcciones URL de seguimiento

Adobe Campaign detecta las direcciones URL que se deben rastrear en el contenido durante el análisis de envío.

Como parte de la transición de Campaign v7 a v8, el conjunto de documentación de Campaign Classic se ha optimizado y reorganizado. Ahora, las funciones comunes solo están disponibles en el conjunto de documentación de Campaign v8. Para saber cómo se detectan las direcciones URL y qué patrones utilizar, consulte la [documentación de Campaign v8](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/analytics/tracking/personalized-links#url-detection){target=_blank}.

[![imagen](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/analytics/tracking/personalized-links#url-detection){target=_blank}

## Patrón no protegido

Al añadir enlaces personalizados al contenido, evite siempre cualquier personalización en la parte del nombre de host de la dirección URL para evitar posibles lagunas de seguridad. Obtenga más información en [esta página](../../installation/using/privacy.md#url-personalization).

Por ejemplo, la sintaxis `<a href="http://<%=myURL%>">` **no es segura** y debe evitarse.

* El uso de esta sintaxis puede dar lugar a problemas de seguridad si el vínculo generado por Adobe Campaign contiene uno o varios parámetros.
* Tidy puede corregir incorrectamente algunos de los vínculos, lo que puede ocurrir al azar. El síntoma típico es un fragmento de HTML visible en las pruebas de correo electrónico, pero no en la vista previa.
* Hay problemas con el escape de la dirección URL o algunos caracteres de la dirección URL pueden causarlos.
* No se puede tener un parámetro denominado ID en conflicto con el parámetro en la URL de redirección.
* El interés del seguimiento se limita entonces a estadísticas sobre el envío, ya que Adobe Campaign realiza un seguimiento indiferente de todos los valores posibles de myURL.
