---
product: campaign
title: Configuración de Developer Console para los activadores de Adobe Experience Cloud
description: Obtenga más información sobre cómo configurar los activadores de Developer Console Adobe Experience Cloud
feature: Triggers
audience: integrations
content-type: reference
index: y
internal: n
snippet: y
exl-id: ab30f697-3022-4a29-bbdb-14ca12ec9c3e
hide: true
hidefromtoc: true
source-git-commit: 8d15a5666b5768bc0f17a4391061c4fcb9f76811
workflow-type: ht
source-wordcount: '312'
ht-degree: 100%

---

# Configuración de Developer Console para los activadores de Adobe Experience Cloud {#configuring-adobe-io}

<!--
>[!CAUTION]
>
>If you are using an older version of Triggers integration through oAuth authentication, **you need to move to Adobe I/O as described below**. 
>Note that during this move to [!DNL Adobe I/O], some incoming triggers may be lost.
>
>Legacy oAuth authentication mode with Campaign has been retired on **October 20, 2021**. Hosted environments benefit from an extension until **May 25, 2022**. As an on-premise or hybrid customer, contact Adobe Customer Care to extend support to **May 2022**. You must [provide the AppID of the OAuth application](../../integrations/using/configuring-pipeline.md#step-optional) to Adobe.
-->

## Requisitos previos {#adobe-io-prerequisites}

<!--
This integration only applies starting **Campaign Classic 20.2.4 and above, 19.1.8 and Gold Standard 11 releases**.
-->

Antes de iniciar esta implementación, compruebe lo siguiente:

* **Un identificador de organización** válido: el identificador de organización es el identificador único de Adobe Experience Cloud que se utiliza, por ejemplo, para el servicio VisitorID y el inicio de sesión único (SSO) de IMS. [Más información](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=es)
* un **acceso para desarrolladores** para su organización. El administrador del sistema de la organización debe seguir el procedimiento **Adición de desarrolladores a un único perfil de producto** detallado [en esta página](https://helpx.adobe.com/es/enterprise/using/manage-developers.html) para proporcionar acceso de desarrollador al perfil `Analytics - {tenantID}` del producto de Adobe Analytics asociado a activadores.

## Paso 1: Creación/actualización de un proyecto OAuth {#creating-adobe-io-project}

>[!AVAILABILITY]
>
> Adobe va a declarar la credencial Cuenta de servicio (JWT) como obsoleta, las integraciones de Campaign con aplicaciones y soluciones de Adobe ahora dependen de la credencial OAuth de servidor a servidor. </br>
>
> * Si ha implementado integraciones de entrada con Campaign, debe migrar su Cuenta técnica como se detalla en [esta documentación](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#_blank). Las [credenciales de la cuenta de servicio (JWT)](oauth-technical-account.md) existentes seguirán funcionando hasta el 27 de enero de 2025.</br>
>
> * Si ha implementado integraciones de salida, como la integración de Campaign-Analytics o los activadores de Experience Cloud, seguirán funcionando hasta el 27 de enero de 2025. Sin embargo, antes de esa fecha, deberá actualizar el entorno de Campaign a la versión 7.4.1 y migrar la Cuenta técnica a OAuth.

Para proseguir con la configuración del conector de Adobe Analytics, acceda a Adobe Developer Console y cree su proyecto de servidor a servidor OAuth.

Consulte [esta página](oauth-technical-account.md#oauth-service) para ver la documentación detallada.

## Paso 2: Adición de las credenciales del proyecto en Adobe Campaign {#add-credentials-campaign}

Siga los pasos detallados en [esta página](oauth-technical-account.md#add-credentials) para añadir las credenciales del proyecto OAuth en Adobe Campaign.

## Paso 3: Actualización de la etiqueta canalizada {#update-pipelined-tag}

Para actualizar la etiqueta [!DNL pipelined], debe actualizar el tipo de autenticación en el proyecto de Developer Console en el archivo de configuración **config-&lt; instance-name >.xml** como se indica a continuación:

```
<pipelined ... authType="imsJwtToken"  ... />
```

A continuación, ejecute un `config -reload` y un reinicio del [!DNL pipelined] para que se tengan en cuenta los cambios.
