---
product: campaign
title: Definición del envío final
description: Obtenga información sobre cómo realizar pruebas A/B mediante un caso de uso dedicado
exl-id: bc23a444-a872-48fb-8bba-64b301541089
source-git-commit: 90c52ec144a6a3c1b534a80507e38fa3ed64fc83
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 100%

---

# Definición de la entrega final {#step-6--defining-the-final-delivery}

![](../../assets/common.svg)

Una vez que la secuencia de comandos se ha creado para seleccionar el ganador de la prueba A/B, se puede definir los parámetros de la entrega final.

1. Conecte la actividad **[!UICONTROL JavaScript code]** a la actividad restante **[!UICONTROL Delivery]**.
1. Abra la actividad **[!UICONTROL Delivery]**.
1. Anule la selección de la opción **[!UICONTROL Generate an outbound transition]** para finalizar el flujo de trabajo con esta actividad.
1. Deje las demás opciones en sus valores predeterminados.

   ![](assets/ab_test_final_delivery.png)

Al preparar la entrega especificada en la transición (definida a través de la actividad **[!UICONTROL Javascript Code]**), se puede aprobar dicha actividad y comenzar la entrega, tal y como se describe en el paso siguiente.

Ahora puede iniciar el flujo de trabajo. [Más información](a-b-testing-uc-start-workflow.md).
