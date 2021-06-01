---
product: campaign
title: Acerca de este caso de uso
description: Obtenga información sobre cómo realizar pruebas A/B mediante un caso de uso dedicado.
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: 4eb139a0-5342-4084-9f6d-d736e05bf1c6
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 100%

---

# Acerca de este caso de uso {#about-use-case}

En este caso de uso, se desea comparar dos contenidos de entrega por correo electrónico a través de un flujo de trabajo de objetivo. El mensaje y el texto son idénticos en ambos envíos: solo cambia el diseño.

La población objetivo se divide en tres: dos grupos de prueba y la población restante. Se envía una versión diferente a cada grupo de prueba.

Después del envío, se configura un periodo de espera de 5 días antes de recoger los resultados de las mejores tasas de apertura. El contenido del envío con la puntuación más alta se recupera mediante una secuencia de comandos y se envía a la población no utilizada como grupo de prueba.

Tenga en cuenta que los criterios que determinan cuál entrega es el mejor se pueden alterar para satisfacer las necesidades. Puede ser la tasa de apertura, la tasa de clics, la tasa de suscripción, la reactividad, etc.

Además, la prueba detallada en este caso de uso implica solo dos envíos, pero se pueden probar tantas versiones como sea necesario. Simplemente, agregue actividades al flujo de trabajo.

Los pasos principales para realizar este caso de uso son los siguientes:

* [Paso 1: Creación de un flujo de trabajo de segmentación](../../delivery/using/a-b-testing-uc-targeting-workflow.md)
* [Paso 2: Configuración de muestras de población](../../delivery/using/a-b-testing-uc-population-samples.md)
* [Paso 3: Creación de dos plantillas de envío](../../delivery/using/a-b-testing-uc-delivery-templates.md)
* [Paso 4: Configuración de los envíos en el flujo de trabajo](../../delivery/using/a-b-testing-uc-configuring-deliveries.md)
* [Paso 5: Creación de la secuencia de comando](../../delivery/using/a-b-testing-uc-script.md)
* [Paso 6: Definición del envío final](../../delivery/using/a-b-testing-uc-final-delivery.md)
* [Paso 7: Inicio del flujo de trabajo](../../delivery/using/a-b-testing-uc-start-workflow.md)
* [Paso 8: Análisis del resultado](../../delivery/using/a-b-testing-uc-analyzing.md)

**Temas relacionados:**

* [Introducción a las pruebas A/B](../../delivery/using/get-started-a-b-testing.md)
* [Configuración de las pruebas A/B](../../delivery/using/configuring-a-b-testing.md)
