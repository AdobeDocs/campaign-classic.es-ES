---
product: campaign
title: Configuración de Adobe I/O para los activadores de Adobe Experience Cloud
description: Descubra más información sobre cómo configurar Adobe I/O para los activadores de Adobe Experience Cloud
audience: integrations
content-type: reference
index: y
internal: n
snippet: y
exl-id: ab30f697-3022-4a29-bbdb-14ca12ec9c3e
source-git-commit: 98a67e5b6e3f8cf8ba596db1fadd61fff821be30
workflow-type: ht
source-wordcount: '717'
ht-degree: 100%

---

# Configuración de Adobe I/O para los activadores de Adobe Experience Cloud {#configuring-adobe-io}

![](../../assets/v7-only.svg)

>[!CAUTION]
>
>Si utiliza una versión anterior de la integración de los activadores mediante autenticación oAuth, **debe pasar a Adobe I/O como se describe a continuación**.
>Tenga en cuenta que durante este cambio a [!DNL Adobe I/O], es posible que se pierdan algunos activadores entrantes.
>
>El modo de autenticación oAuth heredado en Campaign se ha eliminado el **20 de agosto de 2021**. Los entornos alojados se benefician de una extensión hasta el **25 de mayo de 2022**. Como cliente local o híbrido, póngase en contacto con el servicio de atención al cliente de Adobe para ampliar la asistencia hasta **mayo de 2022**. Debe [proporcionar el AppID de la aplicación OAuth](../../integrations/using/configuring-pipeline.md?lang=en#step-optional) a Adobe.

## Requisitos previos {#adobe-io-prerequisites}

Esta integración solo se aplica a partir de **las versiones de Campaign Classic 20.2.4, 19.1.8 y Gold Standard 11**.

Antes de iniciar esta implementación, compruebe lo siguiente:

* **Un identificador de organización** válido: el identificador de organización es el identificador único de Adobe Experience Cloud que se utiliza, por ejemplo, para el servicio VisitorID y el inicio de sesión único (SSO) de IMS. [Más información](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=es)
* un **acceso para desarrolladores** para su organización. El administrador del sistema de la organización debe seguir el procedimiento **Adición de desarrolladores a un único perfil de producto** detallado [en esta página](https://helpx.adobe.com/es/enterprise/using/manage-developers.html) para proporcionar acceso de desarrollador al perfil `Analytics - {tenantID}` del producto de Adobe Analytics asociado a activadores.

## Paso 1: Crear/actualizar proyecto de Adobe I/O {#creating-adobe-io-project}

1. Acceda a [!DNL Adobe I/O] e inicie sesión con el acceso de desarrollador de la organización.

   >[!NOTE]
   >
   > Asegúrese de haber iniciado sesión en el portal correcto de la organización.

1. Extraiga el ID del cliente de integración existente del archivo de configuración de instancia ims/authIMSTAClientId. El atributo no existente o vacío indica que el identificador del cliente no está configurado.

   >[!NOTE]
   >
   >Si el ID del cliente está vacío, puede usar directamente la opción **[!UICONTROL Create a New project]** en Adobe I/O.

1. Identifique el proyecto existente mediante el ID de cliente extraído. Busque proyectos existentes con el mismo ID de cliente que el extraído en el paso anterior.

   ![](assets/do-not-localize/adobe_io_8.png)

1. Seleccione **[!UICONTROL + Add to Project]** y elija **[!UICONTROL API]**.

   ![](assets/do-not-localize/adobe_io_1.png)

1. En la ventana **[!UICONTROL Add an API]** seleccione **[!UICONTROL Adobe Analytics]**.

   ![](assets/do-not-localize/adobe_io_2.png)

1. Elija **[!UICONTROL Service Account (JWT)]** como el tipo de autenticación.

   ![](assets/do-not-localize/adobe_io_3.png)

1. Si el ID del cliente está vacío, seleccione **[!UICONTROL Generate a key pair]** para crear un par de claves pública y privada.

   Las claves se descargan automáticamente con una fecha de caducidad predeterminada de 365 días. Una vez caducado, deberá crear un nuevo par de claves y actualizar la integración en el archivo de configuración. Con la Opción 2, puede elegir crear y cargar manualmente su **[!UICONTROL Public key]** con una fecha de caducidad más larga.

   Para obtener una guía paso a paso sobre cómo reemplazar pares de claves de certificado que caducan, consulte [esta página](https://developer.adobe.com/developer-console/docs/guides/email-alerts/cert-expiry/#a-step-by-step-guide-to-replacing-expiring-certificate-key-pairs).


   >[!CAUTION]
   >
   >Debe guardar el archivo config.zip cuando aparezca el mensaje de descarga, ya que no podrá volver a descargarlo.

   ![](assets/do-not-localize/adobe_io_4.png)

1. Haga clic en **[!UICONTROL Next]**.

   ![](assets/do-not-localize/adobe_io_5.png)

1. Elija cualquier **[!UICONTROL Product profile]** existente o cree uno nuevo si es necesario. No se requiere permiso para este **[!UICONTROL Product profile]**. Para obtener más información sobre [!DNL Analytics] **[!UICONTROL Product Profiles]**, consulte la [Documentación de Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html?lang=es#admin-console).

   A continuación, haga clic en **[!UICONTROL Save configured API]**.

   ![](assets/do-not-localize/adobe_io_6.png)

1. En el proyecto, seleccione **[!UICONTROL Adobe Analytics]** y copie la siguiente información en **[!UICONTROL Service Account (JWT)]**:

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/do-not-localize/adobe_io_7.png)

>[!CAUTION]
>
>El certificado de Adobe I/O caducará pasados 12 meses. Debe generar un nuevo par de claves cada año.

## Paso 2: Adición de las credenciales del proyecto en Adobe Campaign {#add-credentials-campaign}

>[!NOTE]
>
>Este paso no es necesario si el identificador de cliente no estaba vacío en el [Paso 1: Crear/actualizar proyecto de Adobe I/O](#creating-adobe-io-project).

La clave privada debe codificarse en formato UTF-8 base64. Para ello:

1. Utilice la clave privada generada en el [Paso 1: Creación o actualización de la sección Proyecto de Adobe I/O](#creating-adobe-io-project). La clave privada debe ser la misma que se utilizó para crear la integración.

1. Codifique la clave privada mediante el siguiente comando: `base64 ./private.key > private.key.base64`. Esto guardará el contenido de base64 en un nuevo archivo `private.key.base64`.

   >[!NOTE]
   >
   >A veces, se pueden añadir automáticamente líneas adicionales al copiar/pegar la clave privada. Recuerde eliminarlas antes de codificar la clave privada.

1. Copie el contenido del archivo `private.key.base64`.

1. Inicie sesión mediante SSH en cada contenedor donde esté instalada la instancia de Adobe Campaign y añada las credenciales del proyecto en Adobe Campaign ejecutando el siguiente comando como usuario `neolane`. Esto insertará las credenciales **[!UICONTROL Technical Account]** en el archivo de configuración de instancia.

   ```
   nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
   ```

## Paso 3: Actualización de la etiqueta canalizada {#update-pipelined-tag}

>[!NOTE]
>
>Este paso no es necesario si el identificador de cliente no estaba vacío en el [Paso 1: Crear/actualizar proyecto de Adobe I/O](#creating-adobe-io-project).

Para actualizar la etiqueta [!DNL pipelined], debe actualizar el tipo de autenticación del proyecto de Adobe I/O en el archivo de configuración **config-&lt; instance-name >.xml** como se indica a continuación:

```
<pipelined ... authType="imsJwtToken"  ... />
```

A continuación, ejecute un `config -reload` y un reinicio del [!DNL pipelined] para que se tengan en cuenta los cambios.
