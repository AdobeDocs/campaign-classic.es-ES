---
product: campaign
title: Preguntas más frecuentes sobre la configuración de campañas
description: Preguntas frecuentes sobre Campaign Classic
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 50bed489-2a0f-4123-a326-3d68c8295662
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '758'
ht-degree: 100%

---

# Preguntas más frecuentes sobre la configuración de campañas {#settings-faq}

Aprenda las configuraciones clave para configurar la instancia de Campaign y adaptarla a sus necesidades.

## ¿Puedo cambiar el idioma de la interfaz de Campaign? {#can-i-change-the-language-of-campaign-interface-}

El idioma de Campaign se selecciona al crear la instancia. No puede cambiarlo posteriormente. Para obtener más información, consulte [esta sección](../../installation/using/creating-an-instance-and-logging-on.md).

La interfaz de usuario de Adobe Campaign está disponible en 4 idiomas: inglés, francés, alemán y japonés. Tenga en cuenta que la consola del cliente y el servidor deben estar configurados en el mismo idioma. Cada instancia de Campaign solo puede ejecutarse en un idioma.

Para inglés, al instalar Campaign, puede seleccionar inglés de EE. UU. o inglés de Reino Unido: difieren en los formatos de fecha y hora. Para obtener más información sobre estas diferencias, consulte [esta sección](../../platform/using/adobe-campaign-workspace.md#date-and-time).

## ¿Puedo utilizar la versión Campaign Classic con otras soluciones de Adobe? {#can-i-use-campaign-classic-with-other-adobe-solutions-}

Puede combinar las funcionalidades de entrega y las funcionalidades avanzadas de gestión de campañas de Adobe Campaign con un conjunto de soluciones creadas para ayudarle a personalizar su experiencia de usuario.

Haga clic aquí para [aprender cómo trabajar con otras soluciones de Adobe](../../integrations/using/about-campaign-integrations.md) y [cómo configurar IMS en Campaign](../../integrations/using/about-adobe-id.md).

## ¿Cómo puedo configurar las funcionalidades de seguimiento en mi instancia de Campaign? {#how-can-i-set-up-tracking-capabilities-on-my-campaign-instance-}

Como usuario experto, puede configurar las funcionalidades de seguimiento en la instancia de Campaign.

[Haga clic aquí para obtener más información](../../installation/using/deploying-an-instance.md#tracking-configuration).

## ¿Cómo configurar la entrega del correo electrónico? {#how-to-configure-email-deliverability-}

Además de la sección de la [Guía de prácticas recomendadas de entrega de Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=es), lea las recomendaciones técnicas de la capacidad de envío para comprender cómo configurar la instancia a fin de maximizar las capacidades de envío de Campaign.

[Haga clic aquí para obtener más información](../../delivery/using/about-deliverability.md).

## ¿Cómo puedo implementar la aprobación de contenido? {#how-can-i-implement-content-approval-}

Campaign permite configurar los procesos de aprobación para las etapas principales de la campaña de marketing en modo de colaboración. Para cada campaña, puede aprobar el objetivo de envío, los contenidos y los costes. Los operadores de Adobe Campaign responsables de la aprobación pueden ser notificados por correo electrónico y aceptar o rechazar la aprobación a través de la consola o de una conexión web.

[Haga clic aquí para obtener más información](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries) y descubrir pasos para implementar la aprobación de su contenido de entrega en Campaign.

## ¿Cómo puedo acceder a los datos almacenados en una base de datos externa? {#how-can-i-access-data-stored-in-an-external-database-}

Adobe Campaign proporciona la opción Acceso de datos federados (FDA) para procesar la información almacenada en una o más bases de datos externas: puede acceder a datos externos sin cambiar la estructura de los datos de Adobe Campaign.

[Haga clic aquí para obtener más información](../../installation/using/connecting-to-database.md).

## ¿A qué bases de datos externas puedo conectar Campaign? {#which-external-databases-can-i-connect-campaign-to-}

Las bases de datos externas compatibles con Campaign mediante el Acceso de datos federados (FDA) se muestra en la [matriz de Compatibilidad](../../rn/using/compatibility-matrix.md).

## ¿Se puede integrar Adobe Campaign con LDAP? {#can-adobe-campaign-integrate-with-ldap-}

Como cliente local/híbrido, puede integrar Campaign Classic con su directorio LDAP.

[Haga clic aquí para aprender cómo](../../installation/using/connecting-through-ldap.md).

## ¿Cómo puedo configurar los conectores de CRM en Campaign? {#how-can-i-set-up-crm-connectors-in-campaign-}

Adobe Campaign ofrece varios conectores CRM para vincular la plataforma de Adobe Campaign a los sistemas de terceros. Estos conectores de CRM le permiten sincronizar contactos, cuentas, compras, etc., para facilitar la integración de la aplicación con diversas aplicaciones de terceros y de negocios.

Estos conectores permiten una integración de datos rápida y sencilla: Adobe Campaign proporciona un asistente dedicado para recopilar y seleccionar de las tablas disponibles en CRM. De este modo, se garantiza la sincronización bidireccional para garantizar que los datos estén actualizados en todo momento a lo largo de los sistemas.

Consulte [Configure CRM connectors](../../platform/using/crm-connectors.md) para aprender a sincronizar su herramienta CRM con Adobe Campaign.

![](assets/do-not-localize/how-to-video.png) Vea este vídeo de caso de uso sobre la [integración de Adobe Campaign y Microsoft Dynamics 365](https://helpx.adobe.com/campaign/kt/acc/using/acc-integrate-dynamics365-with-acc-feature-video-set-up.html).

## ¿Cómo hacer el borrado de caché de software cuando los problemas son específicos del equipo o del usuario? {#perform-soft-cache-clear}

Si tiene problemas como que los nuevos logotipos se reflejen correctamente, que permiten exportar correctamente los datos específicos del equipo o del usuario, es posible que deba hacer una limpieza de caché de software con Windows (Windows 7, Windows XP, Windows 10).

Una vez que haya iniciado sesión, vaya a **[!UICONTROL File]** > **[!UICONTROL Clear the local cache]**. Después de esto, cierre la sesión y vuelva a iniciarla.

![](assets/faq_soft_cache.png)

Si con esto no ayuda, intente limpiar la caché de disco duro siguiendo los pasos a continuación:

## ¿Cómo realizar borrado de caché de disco duro cuando los problemas son específicos del equipo o del usuario? {#perform-hard-cache-clear}

Si tiene problemas como que los nuevos logotipos se reflejen correctamente, que permiten exportar correctamente los datos específicos del equipo o del usuario, es posible que deba hacer una limpieza de la caché de disco duro con Windows (Windows 7, Windows XP, Windows 10).

1. En la consola del cliente, seleccione **[!UICONTROL File]** > **[!UICONTROL Clear the local cache]**.

1. Cierre la sesión y la consola de cliente (cliente enriquecido).

1. Según la versión del sistema operativo, vaya a las siguientes ubicaciones:

   * Windows 7: C:\Users\ &lt; Username > \AppData\Roaming\Neolane\NL_5\
   * Windows XP: C:\Documents and Settings\ &lt; Username > \Application Data\Neolane\NL_5

   Aquí puede ver varios archivos xml llamados nlclient-config-&lt; alphanumerical value >.xml.

1. Elimine estos archivos XML y las carpetas asociadas.

   >[!IMPORTANT]
   >
   >No elimine el archivo nlclient_cnx.xml.

1. Inicie sesión en la consola del cliente.
