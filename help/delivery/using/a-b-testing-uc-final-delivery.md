---
product: campaign
title: Definición de la entrega final
description: Obtenga información sobre cómo realizar pruebas A/B mediante un caso de uso dedicado
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
feature: A/B Testing
role: User
exl-id: bc23a444-a872-48fb-8bba-64b301541089
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 100%

---

# Prueba AB: definición del envío final {#step-6--defining-the-final-delivery}

Una vez que la secuencia de comandos se ha creado para seleccionar el ganador de la prueba A/B, se puede definir los parámetros de la entrega final.

1. Conecte la actividad **[!UICONTROL JavaScript code]** a la actividad restante **[!UICONTROL Delivery]**.
1. Abra la actividad **[!UICONTROL Delivery]**.
1. Anule la selección de la opción **[!UICONTROL Generate an outbound transition]** para finalizar el flujo de trabajo con esta actividad.
1. Deje las demás opciones en sus valores predeterminados.

   ![](assets/ab_test_final_delivery.png)

Al preparar la entrega especificada en la transición (definida a través de la actividad **[!UICONTROL Javascript Code]**), se puede aprobar dicha actividad y comenzar la entrega, tal y como se describe en el paso siguiente.

Ahora puede iniciar el flujo de trabajo. [Más información](a-b-testing-uc-start-workflow.md).
