---
product: campaign
title: Configuración de entregas
description: Obtenga información sobre cómo realizar pruebas A/B mediante un caso de uso dedicado
badge-v7: label="v7" type="Informative" tooltip="Se aplica a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="También se aplica a Campaign v8"
feature: A/B Testing
exl-id: 809de30b-7d08-40de-bf3e-dc80d62eae80
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 100%

---

# Prueba AB: configuración de los envíos en el flujo de trabajo {#step-4--configuring-the-deliveries-in-the-workflow}

Una vez que [se hayan creado las poblaciones](a-b-testing-uc-population-samples.md), puede configurar las entregas. En este caso de uso, las dos primeras entregas permiten enviar contenido diferente a las poblaciones A y B. La tercera es la opción alternativa: se envía a los destinatarios que no pertenecen a A ni B. Su contenido se calcula mediante una secuencia de comandos y es idéntico a A o B, dependiendo de cuál obtuvo la tasa de apertura más alta. Es necesario configurar un periodo de espera para la tercera entrega, para averiguar el resultado de los envíos A y B. Esta es la razón por la que la tercera entrega incluye una actividad **[!UICONTROL Wait]**.

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

Ahora puede crear la secuencia de comandos. [Más información](a-b-testing-uc-script.md).
