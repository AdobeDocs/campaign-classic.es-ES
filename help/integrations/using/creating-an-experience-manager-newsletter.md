---
title: Creación de un boletín informativo de Experience Manager
seo-title: Creación de un boletín informativo de Experience Manager
description: Creación de un boletín informativo de Experience Manager
seo-description: null
page-status-flag: never-activated
uuid: 75cf4891-06a6-42d2-9b22-b4d93e0dc64a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 627ade78-96b3-4a6e-9ace-74610a3c8d1a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 56212b320d5077f9b66952e7c11eb8bdcea9e3b4
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 68%

---


# Creación de un boletín informativo de Experience Manager{#creating-an-experience-manager-newsletter}

Esta integración puede utilizarse, por ejemplo, para crear un boletín en Adobe Experience Manager para su uso posterior en Adobe Campaign como parte de una campaña de correo electrónico.

Para ver un ejemplo más detallado sobre cómo utilizar esta integración, consulte esta [guía paso a paso](https://helpx.adobe.com/es/campaign/kb/acc-aem.html).

**Desde Adobe Experience Manager:**

1. En la instancia de autor de AEM, haga clic en el logotipo de **Adobe Experience** en la parte superior izquierda de la página y seleccione **[!UICONTROL Sites]**.

   ![](assets/aem_uc_1.png)

1. Seleccione **[!UICONTROL Campaigns > Name of your brand (here We.Retail) > Main Area > Email campaigns]**.
1. Haga clic en el botón **[!UICONTROL Create]** situado en la parte superior derecha de la página y seleccione **[!UICONTROL Page]**.

   ![](assets/aem_uc_2.png)

1. Select the **[!UICONTROL Adobe Campaign Email (AC 6.1)]** template and name your newsletter.
1. Once your page is created, access the **[!UICONTROL Page information]** menu and click **[!UICONTROL Open Properties]**.

   ![](assets/aem_uc_3.png)

1. In the **[!UICONTROL Cloud Services]** tab, select **[!UICONTROL Adobe Campaign]** as **[!UICONTROL Cloud service configuration]** and your Adobe Campaign instance in the second drop-down.

   ![](assets/aem_uc_4.png)

1. Edite su contenido del correo electrónico añadiendo componentes como, por ejemplo, campos de personalización de Adobe Campaign.
1. When your email is ready, access the **[!UICONTROL Page information]** menu and click **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_5.png)

1. From the first drop-down, select **[!UICONTROL Publish to Adobe Campaign]** as workflow model and click **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_6.png)

1. Then, as the previous step, launch the **[!UICONTROL Approve for Campaign]** workflow.
1. Se muestra un aviso legal en la parte superior de la página. Click **[!UICONTROL Complete]** to confirm the review and click **[!UICONTROL Ok]**.

   ![](assets/aem_uc_7.png)

1. Haga clic nuevamente **[!UICONTROL Complete]** y seleccione **[!UICONTROL Newsletter approval]** en la **[!UICONTROL Next Step]** lista desplegable.

   ![](assets/aem_uc_8.png)

El boletín ya está listo y sincronizado en Adobe Campaign.

**Desde Adobe Campaign:**

1. En la **[!UICONTROL Campaigns]** ficha, haga clic en **[!UICONTROL Deliveries]** luego **[!UICONTROL Create]**.

   ![](assets/aem_uc_9.png)

1. En la **[!UICONTROL Delivery template]** lista desplegable, seleccione la **[!UICONTROL Email delivery with AEM content (mailAEMContent)]** plantilla.

   ![](assets/aem_uc_10.png)

1. Añada a la entrega una **[!UICONTROL Label]** y haga clic en **[!UICONTROL Continue]**.
1. Haga clic en el botón **[!UICONTROL Synchronize]**.

   Si este botón no aparece en la interfaz, haga clic en el botón **[!UICONTROL Properties]** y seleccione la pestaña **[!UICONTROL Advanced]**. The **[!UICONTROL Content editing mode]** field should be set to **[!UICONTROL AEM]** with your AEM instance in the **[!UICONTROL AEM account]** field.

   ![](assets/aem_uc_11.png)

1. Seleccione la entrega creada anteriormente en Adobe Experience Manager y haga clic en **[!UICONTROL Ok]**.
1. Haga clic en el botón **[!UICONTROL Refresh content]** en cuanto se realicen algunos cambios en la entrega de AEM.

   ![](assets/aem_uc_12.png)

El correo electrónico está listo para enviarlo a su audiencia.
