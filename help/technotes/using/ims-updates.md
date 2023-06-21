---
product: campaign
title: 'Nota técnica: Actualice su entorno para conectarse a Adobe Campaign con IMS'
description: 'Campaign: actualizaciones de IMS'
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: ecb5a258-a150-46a3-8b83-2b2c06d873ee
source-git-commit: 403d0b7df74b2c958bea9a2d718a15f597ca0d9c
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 11%

---

# Cómo actualizar su entorno para conectarse a Adobe Campaign con IMS {#acc-ims-faq}



El 30 de junio de 2021 se realizarán cambios en [Adobe Identity Management System](https://helpx.adobe.com/es/enterprise/using/identity.html) Funciones de inicio de sesión de (IMS) que podrían afectar a la capacidad para seguir utilizando Adobe Campaign. Aprenda a asegurarse de seguir utilizando Adobe Campaign Classic v7 sin interrupciones.

## ¿Qué ha cambiado?

El servicio Identity Management de Adobe (IMS) dejó de admitir versiones antiguas de Internet Explorer en **30 de junio de 2021**. [Más información](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html).

Adobe desea conservar la funcionalidad de IMS para todos los clientes a partir del 30 de junio de 2021. IMS forma parte del marco de seguridad que permite a los usuarios iniciar sesión en la consola del cliente, por lo tanto en Adobe Campaign.

Para conservar esta funcionalidad, los clientes deben actualizar la consola de cliente en cada equipo de los usuarios y garantizar la última actualización de sus [Versión de Windows](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems), con **Internet Explorer 11** integrado, se instala en el equipo de cada usuario.

## ¿Se ha visto afectado?

Si se está conectando a Campaign [a través de una Adobe ID](../../integrations/using/about-adobe-id.md), a través del servicio Identity Management de Adobe (IMS) y ejecutando una versión de Campaign anterior a las enumeradas a continuación, se verá afectado.

Si ya ha actualizado pero utiliza una versión antigua de Microsoft Internet Explorer, debe actualizar a Internet Explorer 11.

## ¿Cómo realizar la actualización?

* Como cliente alojado, Adobe ya ha actualizado las instancias a la versión más reciente.

* Como cliente on-premise/híbrido, debe actualizar a una de las versiones más recientes enumeradas anteriormente para beneficiarse de la nueva consola de cliente y garantizar una transición sin problemas **antes del 30 de junio de 2021**.

  Es obligatorio actualizar a una de las nuevas versiones que se enumeran a continuación:

   * Gold Standard 11. [Más información](../../rn/using/gold-standard.md)
   * Versión 21.1.3 de Campaign. [Más información](../../rn/using/latest-release.md)
   * Versión 20.2.5 de Campaign.
   * Versión 20.1.4 de Campaign.
   * Versión 19.2.4 de Campaign.

  Estas versiones incluyen un nuevo protocolo de conexión. La actualización es obligatoria tanto para el servidor de Campaign como para la consola del cliente: una vez actualizadas todas las instancias, la consola del cliente debe actualizarse a esta versión para poder conectarse a Campaign después de **30 de junio de 2021**.

Además, asegúrese de que dispone de la última actualización de [Versión de Windows](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems), con **Internet Explorer 11** integrado, se instala en el equipo de cada usuario.

## Preguntas frecuentes

**¿Cómo puedo comprobar mi versión de Campaign?**

Obtenga información sobre cómo comprobar su versión [en esta sección](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).


**¿Cómo puedo comprobar si uso IMS?**

Para comprobar el modo de conexión, puede:

* Inicie la consola del cliente de Campaign y acceda a la configuración de conexión de la instancia. Si la variable **Conexión con un Adobe ID** está seleccionada, está utilizando Adobe IMS.

  ![](../../integrations/using/assets/ims_1.png)

o

* Inicie la consola del cliente de Campaign y compruebe la ventana de conexión. Si se está conectando con un Adobe ID, como se muestra en la pantalla siguiente, está utilizando IMS.

  ![](../../integrations/using/assets/adobeID.png)

**Mensaje de advertencia de conexión**

El siguiente mensaje de advertencia es visible para los usuarios si necesitan actualizar su consola de cliente o utilizar una versión antigua de Microsoft Internet Explorer: **Debe instalar la última actualización para Windows o sus aplicaciones de Adobe.**

![](../../integrations/using/assets/do-not-localize/errorMsg.png)

Si aparece esta advertencia, asegúrese de instalar las actualizaciones más recientes del sistema operativo que está utilizando. [Más información](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html)

Si no actualizó la versión de Internet Explorer, verá el siguiente mensaje y ya no podrá conectarse a Adobe Campaign:

![](../../integrations/using/assets/do-not-localize/errorUpdateReq.png)

>[!NOTE]
>
>En caso de que tenga preguntas acerca de estos cambios, póngase en contacto con el [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
>

## Vínculos útiles

* [Actualice su entorno](../../production/using/build-upgrade.md)
* [Preguntas frecuentes sobre la actualización de versiones](../../platform/using/faq-build-upgrade.md)
* [Hacer que la nueva consola de cliente esté disponible para los usuarios](../../installation/using/client-console-availability-for-windows.md)
* [Instalación de la consola del cliente de Campaign](../../installation/using/installing-the-client-console.md)
* [Acceso a distribución de software de Adobe](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=es)
* [Descargar versión de Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/es/campaign.html)
