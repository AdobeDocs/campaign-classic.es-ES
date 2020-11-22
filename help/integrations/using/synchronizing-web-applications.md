---
solution: Campaign Classic
product: campaign
title: Sincronización de aplicaciones web
description: Sincronización de aplicaciones web
audience: integrations
content-type: reference
topic-tags: acs-connector
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '790'
ht-degree: 100%

---


# Sincronización de aplicaciones web{#synchronizing-web-applications}

En este ejemplo de uso, se envía una comunicación mediante Campaign Standard en la que se incluye un vínculo a una aplicación web de Campaign v7. Cuando el destinatario hace clic en el vínculo del correo electrónico, la aplicación web muestra un formulario con varios campos precargados con los datos del destinatario, como así también un vínculo de suscripción a un boletín informativo. El destinatario puede actualizar sus datos y suscribirse al servicio. Su perfil se actualiza en Campaign v7 y la información se duplica en Campaign Standard.

Si tiene muchos servicios y aplicaciones web en Campaign v7, puede elegir no recrearlos todos en Campaign Standard. El conector ACS permite utilizar todas las aplicaciones y servicios web de Campaign v7 existentes y los relaciona con una entrega realizada por Campaign Standard.

## Requisitos previos {#prerequisites}

Para lograr esto, es necesario lo siguiente:

* Los destinatarios almacenados en la base de datos de Campaign v7 y sincronizarlos con Campaign Standard. Consulte la sección [Sincronización de perfiles](../../integrations/using/synchronizing-profiles.md).
* Un servicio y una aplicación web creados y publicados en Campaign v7.
* La aplicación web debe contener una actividad **[!UICONTROL Pre-loading]** mediante el método de identificación de **[!UICONTROL Adobe Campaign encryption]**.

## Creación de la aplicación y el servicio web {#creating-the-web-application-and-service}

En Campaign v7 puede crear aplicaciones web que permitan a los destinatarios suscribirse a un servicio. La aplicación y el servicio web están diseñados y almacenados en Campaign v7. Este servicio se puede actualizar a través de una comunicación de Campaign Standard. Para obtener más información sobre las aplicaciones web en Campaign v7, consulte [esta sección](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes).

En Campaign v7 se han creado los siguientes objetos:

* un servicio de boletín informativo,
* una aplicación web que contiene actividades **[!UICONTROL Pre-loading]**, **[!UICONTROL Page]** y **[!UICONTROL Storage]**.

1. Vaya a **[!UICONTROL Resources > Online > Web applications]** y seleccione una aplicación web existente.

   ![](assets/acs_connect_lp_2.png)

1. Edite la actividad **[!UICONTROL Preloading]**. La casilla **[!UICONTROL Auto-load data referenced in the form]** está marcada y el método de identificación **[!UICONTROL Adobe Campaign encryption]** seleccionado. Esto permite que la aplicación web precargue los campos del formulario con los datos almacenados en la base de datos de Adobe Campaign. Consulte [este documento](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data).

   ![](assets/acs_connect_lp_4.png)

1. Edite el **[!UICONTROL Page]**. Se han incluido tres campos (nombre, correo electrónico y teléfono), así como una casilla de verificación para invitar al destinatario a suscribirse a un boletín informativo (servicio de **[!UICONTROL Newsletter]**).

   ![](assets/acs_connect_lp_3.png)

1. Vaya a **[!UICONTROL Profiles and Target > Services and subscriptions]** y abra el servicio **[!UICONTROL Newsletter]**. Este es el servicio que se actualiza desde la comunicación de Campaign Standard. Puede ver que ningún destinatario se ha suscrito a este servicio aún.

   ![](assets/acs_connect_lp_5.png)

1. Vaya a **[!UICONTROL Profiles and Targets > Recipient]** y seleccione un destinatario. Puede ver que aún no se ha suscrito al servicio.

   ![](assets/acs_connect_lp_6.png)

## Duplicación de datos {#replicating-the-data}

Para poder duplicar los datos necesarios entre Campaign v7 y Campaign Standard hay disponibles varias plantillas de flujo de trabajo de duplicación. El flujo de trabajo de **[!UICONTROL Profiles replication]** duplica automáticamente todos los destinatarios de Campaign v7 a Campaign Standard. Consulte [Flujos de trabajo técnicos y de duplicación](../../integrations/using/acs-connector-principles-and-data-cycle.md#technical-and-replication-workflows). El flujo de trabajo **[!UICONTROL Landing pages replication]** permite la duplicación de las aplicaciones web que deseamos utilizar en Campaign Standard.

![](assets/acs_connect_lp_1.png)

Para comprobar que los datos se hayan duplicado correctamente, siga estos pasos en Campaign Standard:

1. En la pantalla de inicio, haga clic en **[!UICONTROL Customer profiles]**.

   ![](assets/acs_connect_lp_7.png)

1. Busque el destinatario de Campaign v7 y compruebe que aparece en Campaign Standard.

   ![](assets/acs_connect_lp_8.png)

1. En la barra superior, haga clic en **[!UICONTROL Marketing activities]** y busque la aplicación web de Campaign v7. Se muestra como una página de destino en Campaign Standard.

   ![](assets/acs_connect_lp_9.png)

1. Haga clic en el logotipo de **[!UICONTROL Adobe Campaign]** en la esquina superior izquierda, luego seleccione **Perfiles y audiencias > Servicios** y compruebe que el servicio del boletín informativo también se encuentra allí.

   ![](assets/acs_connect_lp_10.png)

## Diseño y envío del correo electrónico {#designing-and-sending-the-email}

En esta parte, se muestra cómo incluir en un correo electrónico de Campaign Standard un vínculo a la página de destino duplicada desde una aplicación web de Campaign v7.

Los pasos para crear, diseñar y enviar el correo electrónico son los mismos que para un correo electrónico clásico. Consulte la documentación de [Adobe Campaign Standard](https://helpx.adobe.com/es/support/campaign/standard.html).

1. Cree un nuevo correo electrónico y seleccione uno o más perfiles duplicados como audiencia.
1. Edite el contenido e inserte un **[!UICONTROL Link to a landing page]**.

   ![](assets/acs_connect_lp_12.png)

1. Seleccione la página de destino duplicada desde la aplicación web de Campaign v7.

   ![](assets/acs_connect_lp_13.png)

1. Prepare su correo electrónico, envíe sus pruebas y envíe el correo electrónico final.
1. Uno de los destinatarios abre el correo electrónico y hace clic en el vínculo de suscripción al boletín informativo.

   ![](assets/acs_connect_lp_14.png)

1. Añade el número de teléfono y marca la casilla de suscripción al boletín informativo.

   ![](assets/acs_connect_lp_15.png)

## Recuperación de la información actualizada {#retrieving-the-updated-information}

Cuando el destinatario actualiza sus datos desde la aplicación web, Adobe Campaign v7 recupera de forma sincrónica la información actualizada. A continuación, se duplica desde Campaign v7 a Campaign Standard.

1. En Campaign v7, vaya a **[!UICONTROL Profiles and Target > Services and subscriptions]** y abra el servicio **[!UICONTROL Newsletter]**. Puede ver que el destinatario aparece ahora en la lista de suscriptores.

   ![](assets/acs_connect_lp_16.png)

1. Vaya a **[!UICONTROL Profiles and Targets > Recipient]** y seleccione el destinatario. Puede ver que el número de teléfono ahora está guardado.

   ![](assets/acs_connect_lp_17.png)

1. En la pestaña **[!UICONTROL Subscriptions]** también podemos ver que ha suscrito al servicio de boletín informativo.

   ![](assets/acs_connect_lp_18.png)

1. Espere unos minutos para que se ejecute el flujo de trabajo de duplicación de perfiles.
1. En Campaign Standard, acceda a su perfil de destinatario para comprobar que los datos actualizados se hayan duplicado correctamente desde Campaign v7.

   ![](assets/acs_connect_lp_19.png)

1. Edite el perfil. Puede ver que el número de teléfono está actualizado.

   ![](assets/acs_connect_lp_20.png)

1. Haga clic en la pestaña **[!UICONTROL Subscriptions]**. Ahora aparece el servicio de boletín informativo.

   ![](assets/acs_connect_lp_21.png)

