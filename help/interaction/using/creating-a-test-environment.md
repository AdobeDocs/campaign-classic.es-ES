---
title: Creación de un entorno de prueba
seo-title: Creación de un entorno de prueba
description: Creación de un entorno de prueba
seo-description: null
page-status-flag: never-activated
uuid: 60ce42d5-6c0c-4a0d-bfd6-c778b42563a7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: advanced-parameters
discoiquuid: 7a92bc51-24cf-4ce6-bd50-a315f8f6e34e
translation-type: tm+mt
source-git-commit: 8fc3e793ec544948049fc122b44b6bffdebecba0
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 80%

---


# Creación de un entorno de prueba{#creating-a-test-environment}

Para crear un entorno de prueba (modo de entorno limitado), siga los siguientes pasos:

>[!IMPORTANT]
>
>Utilice solamente este método de creación de entorno para los entornos de prueba. En todos los demás casos, utilice el asistente de asignación de destino. Para obtener más información, consulte [Creación de un entorno de ofertas](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

1. Inicie el explorador de Adobe Campaign y vaya a la raíz de la instancia.
1. Right-click and add a **[!UICONTROL Generic folder]** using the drop-down menus.

   ![](assets/offer_env_creation_001.png)

1. Next, go to the folder you just created and add an **[!UICONTROL Offer environment]** using the right-click menus.

   ![](assets/offer_env_creation_001bis.png)

1. Aplique el mismo proceso para crear los elementos y las subcarpetas de entorno.
1. Una vez que haya finalizado las pruebas y desee utilizar el entorno en producción, duplique las ofertas y espacios en el entorno de diseño. (Haga clic con el botón derecho > **[!UICONTROL Actions]** > **[!UICONTROL Deploy]** ).

   ![](assets/migration_interaction_5.png)

