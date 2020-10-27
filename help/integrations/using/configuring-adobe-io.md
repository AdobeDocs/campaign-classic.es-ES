---
title: Configuración de la E/S de Adobe para Adobe Experience Cloud Triggers
seo-title: Configuración de la E/S de Adobe para Adobe Experience Cloud Triggers
description: Configuración de la E/S de Adobe para Adobe Experience Cloud Triggers
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d15e953740b0a4dd8073b36fd59b4c4e44906340
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---


# Configuración de la E/S de Adobe para Adobe Experience Cloud Triggers {#configuring-adobe-io}

Las configuraciones de requisitos previos son:

* Adobe Campaign Classic genera ACC-19.1.9 o ACC-20.2.1 y versiones posteriores.
* un IMSOrgID válido.
* un acceso de desarrollador a la organización IMS. Debe solicitar los privilegios de administrador del sistema de la organización IMS para seguir el procedimiento detallado en esta [página](https://helpx.adobe.com/ca/enterprise/admin-guide.html/ca/enterprise/using/manage-developers.ug.html) y así proporcionar este acceso a todos los Perfiles del producto.

## Paso 1: Crear/actualizar proyecto de E/S de Adobe {#creating-adobe-io-project}

1. Acceda a la E/S de Adobe e inicie sesión con el administrador del sistema correspondiente a IMSorg.

   >[!NOTE]
   >
   > Asegúrese de haber iniciado sesión en el portal de IMSorg correcto.

1. Extraiga el ID de cliente de integración existente del archivo de configuración de instancia ims/authIMSTAClientId. El atributo no existente o vacío indica que el ID de cliente no está configurado.

   >[!NOTE]
   >
   >Si el ID de cliente está vacío, puede hacerlo directamente **[!UICONTROL Create a New project]** en E/S de Adobe.

1. Ahora debe identificar el proyecto existente mediante el ID de cliente extraído. Busque proyectos existentes con el mismo ID de cliente que el extraído en el paso anterior.

   ![](assets/adobe_io_8.png)

1. Seleccione **[!UICONTROL + Add to Project]** y elija **[!UICONTROL API]**.

   ![](assets/adobe_io_1.png)

1. In the window **[!UICONTROL Add an API]**, select **[!UICONTROL Adobe Analytics]**.

   ![](assets/adobe_io_2.png)

1. Elija **[!UICONTROL Service Account (JWT)]** como tipo de autenticación.

   ![](assets/adobe_io_3.png)

1. Si el ID de cliente está vacío, seleccione **[!UICONTROL Generate a key pair]** para crear un par de claves pública y privada.

   ![](assets/adobe_io_4.png)

1. Cargue la clave pública y haga clic en **[!UICONTROL Next]**.

   ![](assets/adobe_io_5.png)

1. Elija el perfil del producto llamado **Analytics-&lt; Nombre de la organización >** y haga clic en **[!UICONTROL Save configured API]**.

   ![](assets/adobe_io_6.png)

1. En el proyecto, seleccione **[!UICONTROL Service Account (JWT)]** y copie la siguiente información:
   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/adobe_io_7.png)

## Paso 2: Añadir las credenciales del proyecto en Adobe Campaign {#add-credentials-campaign}

Para agregar las credenciales del proyecto en Adobe Campaign, ejecute el siguiente comando como usuario neolano en todos los contenedores de la instancia de Adobe Campaign para insertar las **[!UICONTROL Technical Account]** credenciales en el archivo de configuración de instancia.

```
nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID[/Client_Secret[/Base64_encoded_Private_Key]]
```

>[!NOTE]
>
>Debe codificar la clave privada en formato UTF-8 base64. Recuerde quitar la nueva línea de la clave antes de codificarla, excepto la clave privada. La clave privada debe ser la misma que se utilizó para crear la integración.

## Paso 3: Actualizar etiqueta canalizada {#update-pipelined-tag}

Para actualizar [!DNL pipelined] la etiqueta, debe actualizar el tipo de autenticación al proyecto de E/S de Adobe en el archivo de configuración **config-&lt; instance-name >.xml** como se indica a continuación:

```
<pipelined ... authType="imsJwtToken"  ... />
```

>[!NOTE]
>
>Si está utilizando la versión anterior de la integración de desencadenadores mediante tokens JWT heredados, también debe agregar la API de E/S de Adobe para [!DNL Adobe Analytics] obtener información detallada en el primer paso para migrar automáticamente a la nueva autenticación de activadores.
