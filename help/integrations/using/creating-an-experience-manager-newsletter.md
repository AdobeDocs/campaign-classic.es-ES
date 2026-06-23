---
product: campaign
title: Creación de un newsletter de Experience Manager
description: Creación de un newsletter de Experience Manager
feature: Experience Manager Integration
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
audience: integrations
content-type: reference
exl-id: 9fa3ce08-3007-4c65-9841-bad339428b7c
TQID: https://experienceleague.adobe.com/-5orLjm8w8PjA4t4Swox55NP2MTw3rGZzGq42JwuzeQ
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2: id: cbcf4d90-26be-46e2-b16a-aebc529dc41eid: df0d6518-6f49-46e2-b46e-3bcc513f553fid: eb007b6d-6e57-46ab-9485-3f24d6102304id: b1fd1501-3105-4d6b-b4d4-9af53126df75
topic_v2: id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 288
ht-degree: 100%

---

# Creación de una newsletter de Experience Manager{#creating-an-experience-manager-newsletter}



Esta integración puede utilizarse, por ejemplo, para crear un “newsletter” en Adobe Experience Manager para su uso posterior en Adobe Campaign como parte de una campaña de correo electrónico.

**Desde Adobe Experience Manager:**

1. En la instancia de autor de AEM, haga clic en el logotipo de **Adobe Experience** en la parte superior izquierda de la página y seleccione **[!UICONTROL Sites]**.

   ![](assets/aem_uc_1.png)

1. Seleccione **[!UICONTROL Campaigns > Name of your brand (here We.Retail) > Main Area > Email campaigns]**.
1. Haga clic en el botón **[!UICONTROL Create]** situado en la parte superior derecha de la página y seleccione **[!UICONTROL Page]**.

   ![](assets/aem_uc_2.png)

1. Seleccione la plantilla de **[!UICONTROL Adobe Campaign Email (AC 6.1)]** y asigne un nombre al newsletter.
1. Una vez creada la página, acceda al menú **[!UICONTROL Page information]** y haga clic en **[!UICONTROL Open Properties]**.

   ![](assets/aem_uc_3.png)

1. En la pestaña **[!UICONTROL Cloud Services]**, seleccione **[!UICONTROL Adobe Campaign]** como **[!UICONTROL Cloud service configuration]** y la instancia de Adobe Campaign en la segunda lista desplegable.

   ![](assets/aem_uc_4.png)

1. Edite su contenido del correo electrónico añadiendo componentes como, por ejemplo, campos de personalización de Adobe Campaign.
1. Cuando el correo electrónico esté listo, acceda al menú **[!UICONTROL Page information]** y haga clic en **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_5.png)

1. En la primera lista desplegable, seleccione **[!UICONTROL Publish to Adobe Campaign]** como modelo de flujo de trabajo y haga clic en **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_6.png)

1. A continuación, como en el paso anterior, ejecute el flujo de trabajo **[!UICONTROL Approve for Campaign]**.
1. Se muestra un aviso legal en la parte superior de la página. Haga clic en **[!UICONTROL Complete]** para confirmar la revisión y, a continuación, en **[!UICONTROL Ok]**.

   ![](assets/aem_uc_7.png)

1. Haga clic nuevamente en **[!UICONTROL Complete]** y seleccione **[!UICONTROL Newsletter approval]** en la **[!UICONTROL Next Step]** lista desplegable.

   ![](assets/aem_uc_8.png)

El boletín ya está listo y sincronizado en Adobe Campaign.

**Desde Adobe Campaign:**

1. En la pestaña **[!UICONTROL Campaigns]** , haga clic en **[!UICONTROL Deliveries]** luego **[!UICONTROL Create]**.

   ![](assets/aem_uc_9.png)

1. En la lista desplegable **[!UICONTROL Delivery template]** , seleccione la plantilla **[!UICONTROL Email delivery with AEM content (mailAEMContent)]** .

   ![](assets/aem_uc_10.png)

1. Añada a la entrega una **[!UICONTROL Label]** y haga clic en **[!UICONTROL Continue]**.
1. Haga clic en el botón **[!UICONTROL Synchronize]**.

   Si este botón no aparece en la interfaz, haga clic en el botón **[!UICONTROL Properties]** y seleccione la pestaña **[!UICONTROL Advanced]**. El campo **[!UICONTROL Content editing mode]** debe configurarse como **[!UICONTROL AEM]** con la instancia AEM en el campo **[!UICONTROL AEM account]**.

   ![](assets/aem_uc_11.png)

1. Seleccione la entrega creada anteriormente en Adobe Experience Manager y haga clic en **[!UICONTROL Ok]**.
1. Haga clic en el botón **[!UICONTROL Refresh content]** en cuanto se realicen algunos cambios en la entrega de AEM.

   ![](assets/aem_uc_12.png)

El correo electrónico está listo para enviarlo a su público.
