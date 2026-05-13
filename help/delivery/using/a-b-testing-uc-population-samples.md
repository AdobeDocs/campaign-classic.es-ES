---
product: campaign
title: Configuración de muestras de población
description: Obtenga información sobre cómo realizar pruebas A/B mediante un caso de uso dedicado
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
feature: A/B Testing
role: User
exl-id: 1ca01cab-734a-4299-b112-04eec51222fb
TQID: https://experienceleague.adobe.com/HWbHtS5F-je1GiNdr25dD17W-MpJ-K3xp-T8kKC-c10
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 185
ht-degree: 100%

---

# Pruebas AB: configuración de muestras de población {#step-2--configuring-population-samples}

## Configurar la actividad Consulta {#configuring-the-query-activity}

* Haga doble clic en la actividad **[!UICONTROL Query]**.

  ![](assets/use_case_abtesting_createrecipients_001.png)

* Haga clic en el vínculo **[!UICONTROL Edit query]** y seleccione los destinatarios a quienes desee dirigirse.

  ![](assets/use_case_abtesting_createrecipients_002.png)

* Vincule la actividad **[!UICONTROL Query]** a la actividad **[!UICONTROL Split]**.

  ![](assets/use_case_abtesting_createrecipients_003.png)

## Configuración de la actividad división {#configuring-the-split-activity}

Esta actividad permite crear varias poblaciones: la que recibe la entrega A, la que recibe la entrega B y la población restante. El uso de la selección aleatoria permite seleccionar solo parte de la población de cada entrega.

1. Creación de la población A:

   * Haga doble clic en la actividad **[!UICONTROL Split]**.

     ![](assets/use_case_abtesting_createrecipients_004.png)

   * En la pestaña existente, cambie la etiqueta a población A.

     ![](assets/use_case_abtesting_createrecipients_005.png)

   * Seleccione la opción **[!UICONTROL Limit the selected records]**.

     ![](assets/use_case_abtesting_createrecipients_006.png)

   * Haga clic en el vínculo **[!UICONTROL Edit]**, seleccione **[!UICONTROL Activate random sampling]** y haga clic en **[!UICONTROL Next]**.

     ![](assets/use_case_abtesting_createrecipients_007.png)

   * Defina el umbral en 10 % y haga clic en **[!UICONTROL Finish]**.

     ![](assets/use_case_abtesting_createrecipients_008.png)

1. Creación de la población B:

   * Haga clic en **[!UICONTROL Add]** para crear una nueva pestaña para la población B.

     ![](assets/use_case_abtesting_createrecipients_009.png)

   * Limite la población al 10% como se mostró anteriormente.

     ![](assets/use_case_abtesting_createrecipients_010.png)

1. Creación de la población restante:

   * Vaya a la pestaña **[!UICONTROL General]**.

     ![](assets/use_case_abtesting_createrecipients_011.png)

   * Seleccione **[!UICONTROL Generate complement]**.

     ![](assets/use_case_abtesting_createrecipients_012.png)

   * Cambie la etiqueta para especificar que esta población no incluye A ni B y haga clic en **[!UICONTROL OK]** para cerrar la actividad.

     ![](assets/use_case_abtesting_createrecipients_013.png)

Ahora puede crear las dos plantillas de envío. [Más información](a-b-testing-uc-delivery-templates.md)).
