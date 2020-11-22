---
solution: Campaign Classic
product: campaign
title: Configuración de la E/S de Adobe para Adobe Experience Cloud Triggers
description: Obtenga información sobre cómo configurar la E/S de Adobe para Adobe Experience Cloud Triggers
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 33%

---


# Configuring Adobe I/O for Adobe Experience Cloud Triggers {#configuring-adobe-io}

>[!CAUTION]
>
>Si utiliza una versión anterior de la integración de Triggers mediante la autenticación oAuth, **debe pasar a la E/S de Adobe como se describe a continuación**. El modo de autenticación oAuth heredado se retirará el 30 de abril de 2021. [Más información](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)

## Requisitos previos {#adobe-io-prerequisites}

Esta integración solo se aplica a partir de **Campaign Classic 20.3**.

Antes de iniciar esta implementación, compruebe que:

* un IMSOrgID válido: el identificador de organización del sistema Identity Management (IMS) es el identificador único dentro del Adobe Experience Cloud, que se utiliza, por ejemplo, para el servicio VisitorID y el inicio de sesión único (SSO) de IMS,
* un acceso de desarrollador a la organización IMS.

>[!NOTE]
>
>If you need to request the System Administrator privileges of the IMS Org, follow the procedure detailed [in this page](https://helpx.adobe.com/ca/enterprise/admin-guide.html/ca/enterprise/using/manage-developers.ug.html) to provide this access for the all Product Profiles.


## Paso 1: Crear/actualizar proyecto de E/S de Adobe {#creating-adobe-io-project}

1. Acceda a la E/S de Adobe e inicie sesión con el administrador del sistema justo para IMSorg.

   >[!NOTE]
   >
   > Asegúrese de haber iniciado sesión en el portal de IMSorg correcto.

1. Extraiga el ID del cliente de integración existente del archivo de configuración de instancia ims/authIMSTAClientId. El atributo no existente o vacío indica que el ID de cliente no está configurado.

   >[!NOTE]
   >
   >If your Client ID is empty, you can directly **[!UICONTROL Create a New project]** in Adobe I/O.

1. Identifique el proyecto existente mediante el ID de cliente extraído. Busque proyectos existentes con el mismo ID de cliente que el extraído en el paso anterior.

   ![](assets/do-not-localize/adobe_io_8.png)

1. Seleccione **[!UICONTROL + Add to Project]** y elija **[!UICONTROL API]**.

   ![](assets/do-not-localize/adobe_io_1.png)

1. En la ventana **[!UICONTROL Add an API]** seleccione **[!UICONTROL Adobe Analytics]**.

   ![](assets/do-not-localize/adobe_io_2.png)

1. Elija **[!UICONTROL Service Account (JWT)]** como el tipo de autenticación.

   ![](assets/do-not-localize/adobe_io_3.png)

1. If your Client ID was empty, select **[!UICONTROL Generate a key pair]** to create a Public and Private keypair.

   ![](assets/do-not-localize/adobe_io_4.png)

1. Cargue la clave pública y haga clic en **[!UICONTROL Next]**.

   ![](assets/do-not-localize/adobe_io_5.png)

1. Elija el perfil del producto llamado **Analytics-&lt; Org Name >** y haga clic en **[!UICONTROL Save configured API]**.

   ![](assets/do-not-localize/adobe_io_6.png)

1. En el proyecto, seleccione **[!UICONTROL Service Account (JWT)]** y copie la siguiente información:
   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/do-not-localize/adobe_io_7.png)

## Paso 2: Adición de las credenciales del proyecto en Adobe Campaign {#add-credentials-campaign}

To add the project credentials in Adobe Campaign, run the following command as &#39;neolane&#39; user on all the containers of the Adobe Campaign instance to insert the **[!UICONTROL Technical Account]** credentials in the instance configuration file.

```
nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID[/Client_Secret[/Base64_encoded_Private_Key]]
```

>[!NOTE]
>
>Debe codificar la clave privada en formato UTF-8 base64. Recuerde quitar la nueva línea de la clave antes de codificarla, excepto de la clave privada. La clave privada debe ser la misma que se utilizó para crear la integración.

## Paso 3: Actualización de la etiqueta canalizada {#update-pipelined-tag}

To update [!DNL pipelined] tag, you need to update the authentication type to Adobe I/O project in the configuration file **config-&lt; instance-name >.xml** as follows:

```
<pipelined ... authType="imsJwtToken"  ... />
```
