---
product: campaign
title: Creación de plantillas de entrega
description: Obtenga información sobre cómo realizar pruebas A/B mediante un caso de uso dedicado
role: User
badge-v7: label="v7" type="Informative" tooltip="Se aplica a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="También se aplica a Campaign v8"
feature: A/B Testing
exl-id: 77b3a906-b76e-49e1-b524-b6f1ae537259
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: ht
source-wordcount: '100'
ht-degree: 100%

---

# Prueba A/B: creación de plantillas de envío {#step-3--creating-two-delivery-templates}

Ahora, queremos crear dos plantillas de envío. Se hará referencia a cada plantilla en una actividad **[!UICONTROL Email delivery]** vinculada a la actividad **[!UICONTROL Split]**. Para obtener más información, consulte [esta sección](about-templates.md).

1. Examine la carpeta **[!UICONTROL Resources > Delivery template]**.
1. Duplique la plantilla de entrega **[!UICONTROL Email]**.

   ![](assets/use_case_abtesting_deliverymodel_001.png)

1. Cree el contenido que desea utilizar para la entrega A.

   ![](assets/use_case_abtesting_deliverymodel_002.png)

1. Repita este proceso para crear una plantilla para la entrega B.

   ![](assets/use_case_abtesting_deliverymodel_003.png)

Ahora puede configurar las entregas en el flujo de trabajo. [Más información](a-b-testing-uc-configuring-deliveries.md).
