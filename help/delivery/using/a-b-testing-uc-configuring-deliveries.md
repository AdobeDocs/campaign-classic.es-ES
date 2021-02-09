---
solution: Campaign Classic
product: campaign
title: Configuración de los envíos
description: Obtenga información sobre cómo realizar pruebas A/B mediante un caso de uso dedicado.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 177b4e74c75e4fcca70dc90b5ff2c0406181e0f7
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 93%

---


# Configuración de los envíos en el flujo de trabajo {#step-4--configuring-the-deliveries-in-the-workflow}

El siguiente paso es configurar los envíos. Están destinados a las tres poblaciones creadas durante la etapa anterior: [Paso 2: Configuración de muestras de población](#step-2--configuring-population-samples). Los dos primeros envíos permiten enviar contenido distinto a las poblaciones A y B. La tercera entrega está destinada a la población que no ha recibido A ni B. Su contenido se calcula mediante una secuencia de comandos y es idéntico a A o B, dependiendo de cuál obtuvo la tasa de apertura más alta. Es necesario configurar un periodo de espera para la tercera entrega, para averiguar el resultado de los envíos A y B. Esta es la razón por la que la tercera entrega incluye una actividad **[!UICONTROL Wait]**.

1. Vaya a la actividad **[!UICONTROL Split]** y vincule la transición destinada a la población A a uno de los envíos de correo electrónico que ya se encuentran en el flujo de trabajo.

   ![](assets/use_case_abtesting_createdeliveries_001.png)

1. Haga doble clic en la entrega para abrirlo.
1. En la lista desplegable, seleccione la plantilla para la entrega A.

   ![](assets/use_case_abtesting_createdeliveries_003.png)

1. Haga clic en **[!UICONTROL Continue]** para ver la entrega y, a continuación, guárdelo.

   ![](assets/use_case_abtesting_createdeliveries_002.png)

1. Vincule la transición de la actividad **[!UICONTROL Split]** de la población B al segundo entrega de correo electrónico.

   ![](assets/use_case_abtesting_createdeliveries_004.png)

1. Abra la entrega, seleccione la plantilla en la entrega B y, a continuación, guarde la entrega.

   ![](assets/use_case_abtesting_createdeliveries_005.png)

1. Vincule la transición destinada a la población restante a la actividad **[!UICONTROL Wait]**.

   ![](assets/use_case_abtesting_createdeliveries_006.png)

1. Abra la actividad **[!UICONTROL Wait]** y configure un periodo de espera de 5 días.

   ![](assets/use_case_abtesting_createdeliveries_007.png)

1. Vincule la actividad **[!UICONTROL Wait]** a la actividad **[!UICONTROL JavaScript code]**.

   ![](assets/use_case_abtesting_createdeliveries_008.png)
