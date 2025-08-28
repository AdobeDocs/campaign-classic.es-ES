---
product: campaign
title: 'Nota técnica: Actualice su entorno para conectarse a Adobe Campaign con IMS'
description: 'Campaign: actualizaciones de IMS'
feature: Technote, Upgrade
hide: true
hidefromtoc: true
exl-id: ecb5a258-a150-46a3-8b83-2b2c06d873ee
source-git-commit: 62fc46e45078fce56eadda3518251e61244bf5d0
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 6%

---

# Cómo actualizar su entorno para conectarse a Adobe Campaign con IMS {#acc-ims-faq}



El 30 de junio de 2021 se realizaron cambios en las funcionalidades de inicio de sesión de [Adobe Identity Management System](https://helpx.adobe.com/es/enterprise/using/identity.html) (IMS) que podrían afectar su capacidad para seguir usando Adobe Campaign. Aprenda a asegurarse de seguir utilizando Adobe Campaign Classic v7 sin interrupciones.

## ¿Qué ha cambiado?

El servicio Adobe Identity Management (IMS) dejó de admitir versiones antiguas de Internet Explorer el **30 de junio de 2021**. [Más información](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html).

Adobe quiere conservar la funcionalidad de IMS para todos los clientes a partir del 30 de junio de 2021. IMS forma parte del marco de seguridad que permite a los usuarios iniciar sesión en la consola del cliente, por lo tanto en Adobe Campaign.

Para conservar esta funcionalidad, los clientes deben actualizar la consola de cliente en cada equipo de los usuarios y asegurarse de que la última actualización de su [versión de Windows](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems), con **Internet Explorer 11** integrado, esté instalada en cada equipo de los usuarios.

## ¿Se ha visto afectado?

Si se está conectando a Campaign [a través de un Adobe ID](../../integrations/using/about-adobe-id.md), a través del servicio Adobe Identity Management (IMS) y ejecuta una versión de Campaign anterior a las que se enumeran a continuación, se verá afectado.

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

  Estas versiones incluyen un nuevo protocolo de conexión. La actualización es obligatoria tanto para el servidor de Campaign como para la consola del cliente: una vez actualizadas todas las instancias, la consola del cliente también debe actualizarse a esta versión para poder conectarse a Campaign después del **30 de junio de 2021**.

Además, asegúrese de que la última actualización de su [versión de Windows](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems), con **Internet Explorer 11** integrado, esté instalada en cada equipo de los usuarios.

## Preguntas frecuentes

**¿Cómo puedo comprobar mi versión de Campaign?**

Aprenda a comprobar su versión [en esta sección](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).


**¿Cómo puedo comprobar si uso IMS?**

Para comprobar el modo de conexión, puede:

* Inicie la consola del cliente de Campaign y acceda a la configuración de conexión de la instancia. Si la opción **Conectarse con un Adobe ID** está seleccionada, está usando Adobe IMS.

  ![](../../integrations/using/assets/ims_1.png)

o

* Inicie la consola del cliente de Campaign y compruebe la ventana de conexión. Si se está conectando con un Adobe ID, como se muestra en la pantalla siguiente, está utilizando IMS.

  ![](../../integrations/using/assets/adobeID.png)

**Mensaje de advertencia de conexión**

El siguiente mensaje de advertencia es visible para los usuarios si necesitan actualizar su consola de cliente o usar una versión antigua de Microsoft Internet Explorer: **Debe instalar la última versión actualizada en Windows o en sus aplicaciones de Adobe.**

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
* [Acceder a la distribución de software de Adobe](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=es)
* [Descargar compilación de Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/es/campaign.html)
