---
solution: Campaign Classic
product: campaign
title: Acerca de este caso de uso
description: Obtenga información sobre cómo realizar pruebas A/B mediante un caso de uso dedicado.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 346b72d522c947b2a2552176b910ded8d622f3ab
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 52%

---


# Acerca de este caso de uso {#about-use-case}

En este caso de uso, se desea comparar dos contenidos de entrega por correo electrónico a través de un flujo de trabajo de objetivo. El mensaje y el texto son idénticos en ambos envíos: solo cambia el diseño.

La población objetivo se divide en tres: dos grupos de prueba y la población restante. Se envía una versión diferente a cada grupo de prueba.

Después de la entrega, se configura un periodo de espera de 5 días antes de recolectar los resultados de las mejores tasas de apertura. El contenido del envío con la puntuación más alta se recupera mediante una secuencia de comandos y se envía a la población que no se utilizó como grupo de prueba.

Tenga en cuenta que los criterios que determinan cuál entrega es el mejor se pueden alterar para satisfacer las necesidades. Puede ser la tasa de apertura, la tasa de clics, la tasa de suscripción, la reactividad, etc.

Además, la prueba detallada en este caso de uso se relaciona solamente con dos envíos, pero puede probar tantas versiones como sea necesario. Simplemente, agregue actividades al flujo de trabajo.

Los pasos principales para realizar este caso de uso son:

* [Paso 1: Crear un flujo de trabajo de objetivo](#step-1--creating-a-targeting-workflow)
* [Paso 2: Configurar muestras de población](#step-2--configuring-population-samples)
* [Paso 3: Crear dos Plantillas de envíos](#step-3--creating-two-delivery-templates)
* [Paso 4: Configurar los envíos en el flujo de trabajo](#step-4--configuring-the-deliveries-in-the-workflow)
* [Paso 5: Creación de la secuencia de comandos](#step-5--creating-the-script)
* [Paso 7: Inicio del flujo de trabajo](#step-7--starting-the-workflow)
* [Paso 8: Analizar el resultado](#step-8--analyzing-the-result).

**Temas relacionados:**

* [Introducción a la prueba A/B](../../delivery/using/get-started-a-b-testing.md)
* [Configuración de la prueba A/B](../../delivery/using/configuring-a-b-testing.md)
