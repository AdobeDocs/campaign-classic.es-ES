---
solution: Campaign Classic
product: campaign
title: Configuración de Adobe I/O para los activadores de Adobe Experience Cloud
description: Descubra más información sobre cómo configurar Adobe I/O para los activadores de Adobe Experience Cloud
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0abdbbc33350cf6ec85488483dadb177e685818b
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 100%

---


# Configuración de Adobe I/O para los activadores de Adobe Experience Cloud {#configuring-adobe-io}

>[!CAUTION]
>
>Si utiliza una versión anterior de la integración de los activadores mediante autenticación oAuth, **debe pasar a Adobe I/O como se describe a continuación**. El modo de autenticación oAuth heredado se eliminará el 30 de abril de 2021. [Más información](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)

## Requisitos previos {#adobe-io-prerequisites}

Esta integración solo se aplica a partir de **la versión 20.3 de Campaign Classic**.

Antes de iniciar esta implementación, compruebe lo siguiente:

* un IMSOrgID válido: el identificador de organización de Identity Management System (IMS) es el identificador único de Adobe Experience Cloud que se utiliza, por ejemplo, para el servicio VisitorID y el inicio de sesión único (SSO) de IMS; y
* un acceso de desarrollador a la organización de IMS.

>[!NOTE]
>
>Si tiene que solicitar los privilegios de administrador del sistema de la organización de IMS, siga el procedimiento detallado [en esta página](https://helpx.adobe.com/ca/enterprise/admin-guide.html/ca/enterprise/using/manage-developers.ug.html) para que todos los perfiles del producto tengan acceso.


## Paso 1: Crear/actualizar proyecto de Adobe I/O {#creating-adobe-io-project}

1. Acceda a Adobe I/O e inicie sesión con el administrador del sistema correspondiente a IMSorg.

   >[!NOTE]
   >
   > Asegúrese de haber iniciado sesión en el portal de IMSorg correcto.

1. Extraiga el ID del cliente de integración existente del archivo de configuración de instancia ims/authIMSTAClientId. El atributo no existente o vacío indica que el ID del cliente no está configurado.

   >[!NOTE]
   >
   >Si el ID del cliente está vacío, directamente puede **[!UICONTROL Create a New project]** en Adobe I/O.

1. Identifique el proyecto existente mediante el ID de cliente extraído. Busque proyectos existentes con el mismo ID de cliente que el extraído en el paso anterior.

   ![](assets/do-not-localize/adobe_io_8.png)

1. Seleccione **[!UICONTROL + Add to Project]** y elija **[!UICONTROL API]**.

   ![](assets/do-not-localize/adobe_io_1.png)

1. En la ventana **[!UICONTROL Add an API]** seleccione **[!UICONTROL Adobe Analytics]**.

   ![](assets/do-not-localize/adobe_io_2.png)

1. Elija **[!UICONTROL Service Account (JWT)]** como el tipo de autenticación.

   ![](assets/do-not-localize/adobe_io_3.png)

1. Si el ID del cliente está vacío, seleccione **[!UICONTROL Generate a key pair]** para crear un par de claves pública y privada.

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

Para añadir las credenciales del proyecto en Adobe Campaign, ejecute el siguiente comando como usuario neolano en todos los contenedores de la instancia de Adobe Campaign para insertar las credenciales de la **[!UICONTROL Technical Account]** en el archivo de configuración de instancia.

```
nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID[/Client_Secret[/Base64_encoded_Private_Key]]
```

>[!NOTE]
>
>Debe codificar la clave privada en formato UTF-8 base64. Recuerde quitar la nueva línea de la clave antes de codificarla, excepto de la clave privada. La clave privada debe ser la misma que se utilizó para crear la integración.

## Paso 3: Actualización de la etiqueta canalizada {#update-pipelined-tag}

Para actualizar la etiqueta [!DNL pipelined], debe actualizar el tipo de autenticación del proyecto de Adobe I/O en el archivo de configuración **config-&lt; instance-name >.xml** como se indica a continuación:

```
<pipelined ... authType="imsJwtToken"  ... />
```
