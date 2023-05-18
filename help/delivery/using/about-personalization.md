---
product: campaign
title: Introducción a la personalización
description: Obtenga información sobre cómo personalizar mensajes y utilizar contenido condicional en Campaign
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Personalization
exl-id: 555082a2-1b62-4aa4-b80c-77b1a1ef9491
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: ht
source-wordcount: '138'
ht-degree: 100%

---

# Introducción a la personalización{#about-personalization}



Los mensajes enviados por Adobe Campaign pueden personalizarse de varias formas diferentes, teniendo en consideración el contenido o el aspecto de los mensajes. Estas formas se pueden combinar de acuerdo con criterios tomados especialmente de los perfiles de destinatario. En el caso de las entregas de correo electrónico, se pueden definir los elementos y las condiciones de personalización de una entrega directamente en JavaScript desde la pestaña **[!UICONTROL Source]**. En general, Adobe Campaign le permite:

* Personalizar el formato del mensaje. Consultar [Contenido del mensaje](defining-the-email-content.md#message-content).
* Insertar campos personalizados dinámicos. Consultar [Personalización de campos](personalization-fields.md).
* Insertar bloques de personalización predefinidos. Consultar [Bloques de personalización](personalization-blocks.md).
* Cree contenido condicional. Consulte la sección [Contenido condicional](conditional-content.md).

>[!CAUTION]
>
>Las siguientes variables son variables internas que pueden utilizarse para la personalización pero que no deben modificarse: **delivery**, **message**, **dataSource**, **targetData**, **provider**, **coupon**, **couponValue**, **proposition**.
