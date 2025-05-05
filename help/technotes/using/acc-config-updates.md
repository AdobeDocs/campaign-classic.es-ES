---
product: campaign
title: 'Nota técnica: Actualizaciones de configuración de Adobe Campaign'
description: Actualizaciones de configuración de Adobe Campaign
feature: Technote, Upgrade
hide: true
hidefromtoc: true
exl-id: 7db02123-2e2a-40d9-8385-728ff69985e4
source-git-commit: 8de62db2499449fc9966b6464862748e2514a774
workflow-type: tm+mt
source-wordcount: '1103'
ht-degree: 10%

---

# Actualizaciones de configuración de Adobe Campaign de 2021 {#acc-config-updates}



La infraestructura y la configuración deben actualizarse regularmente con las últimas compilaciones y correcciones de productos. Estas correcciones son necesarias para garantizar la continuidad del servicio y la seguridad. Además, se requerirán actualizaciones para alinearse con los cambios de terceros.

Como **cliente alojado o de Managed Services**, Adobe le informará de las actualizaciones de la compilación a intervalos regulares. Se le solicitará que actualice de acuerdo con las recomendaciones para garantizar el cumplimiento.

Como **cliente On-Premise o híbrido**, debe actualizar su implementación a intervalos regulares en línea con las últimas compilaciones publicadas.

Por motivos de seguridad, ahora debe actualizar a una de las versiones enumeradas a continuación. Además de los pasos de actualización estándar, se deben realizar algunas tareas manuales para asegurarse de que su entorno sea seguro y esté listo para los próximos cambios de sistemas de Adobe o de terceros.

>[!NOTE]
>
>En caso de que tenga preguntas acerca de estos cambios, póngase en contacto con el [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
>

## Actualizaciones de seguridad {#acc-security-updates}

Las últimas versiones de Campaign incluyen una corrección de seguridad que refuerza la protección contra los problemas de falsificación de solicitudes del lado del servidor (SSRF). Obtenga más información [en esta página](https://helpx.adobe.com/es/security/products/campaign/apsb21-04.html).

**¿Se ha visto afectado?**

Si su entorno está en una versión inferior a las enumeradas a continuación, se verá afectado:

* Gold Standard 11. [Más información](../../rn/using/gold-standard.md)
* Versión 21.1.1 de Campaign. [Más información](../../rn/using/latest-release.md)
* Versión 20.2.5 de Campaign.
* Versión 20.1.4 de Campaign.
* Versión 19.2.4 de Campaign.
* Versión 19.1.8 de Campaign.

Aprenda a comprobar su versión [en esta sección](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**¿Cómo realizar la actualización?**

Debe actualizar a una de las compilaciones más nuevas enumeradas anteriormente.

* Como cliente híbrido, Adobe le informará de las fechas de actualización programadas para las instancias de intermediario. Adobe recomienda encarecidamente que actualice también la instancia de marketing.

  La nueva versión es compatible con la versión anterior de Campaign Classic 17.9, pero Adobe recomienda encarecidamente una actualización en todas las instancias para abordar las vulnerabilidades de seguridad

* Como cliente On-Premise, se le solicita que actualice las instancias de marketing e intermediarias a la última versión.

>[!CAUTION]
>
>Si no puede actualizar dentro del intervalo de tiempo recomendado, **debe ponerse en contacto con el equipo de atención al cliente de Adobe para aplicar una corrección de seguridad manual a corto plazo en las instancias**.
>

## Actualización de la consola del cliente de Campaign Classic  {#acc-cc-updates}

Las **versiones de consola disponibles** a continuación se deben instalar para resolver una regresión identificada recientemente. Esta regresión impedía el uso de algunos componentes de la consola del cliente, como el selector de fechas y la administración de imágenes en las entregas. **La actualización de la consola** es obligatoria.

* Última versión de Gold Standard 11 9032@10c2709. [Más información](../../rn/using/gold-standard.md)
* Versión 20.1.4 de Campaign.
* Versión 19.2.4 de Campaign.
* Versión 19.1.8 de Campaign.

## Actualización del sistema Identity Management de Adobe (IMS)

El servicio de identidad de Adobe (IMS) dejará de admitir versiones antiguas de Internet Explorer a partir del **30 de junio de 2021**. [Más información](https://helpx.adobe.com/es/x-productkb/global/update-operating-system-and-browser.html).

Se requiere una actualización de la consola del cliente de Campaign para garantizar la compatibilidad con Adobe IMS.

**¿Se ha visto afectado?**

Si se está conectando a Campaign [a través de un Adobe ID](../../integrations/using/about-adobe-id.md), a través del Servicio Identity Management de Adobe (IMS), la actualización a una de las nuevas versiones que se enumeran a continuación es obligatoria:

* Gold Standard 11. [Más información](../../rn/using/gold-standard.md)
* Versión 21.1.1 de Campaign. [Más información](../../rn/using/latest-release.md)
* Versión 20.2.5 de Campaign.
* Versión 20.1.4 de Campaign.
* Versión 19.2.4 de Campaign.
* Versión 19.1.8 de Campaign.

Estas versiones incluyen un nuevo protocolo de conexión: la actualización es obligatoria, tanto para el servidor de Campaign como para la consola del cliente, para poder conectarse a Campaign después del **30 de junio de 2021**.

Aprenda a comprobar su versión [en esta sección](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**¿Cómo realizar la actualización?**

Como cliente alojado, Adobe trabajará con usted para actualizar sus instancias a la versión más reciente en breve.

Como cliente on-premise/híbrido, debe actualizar a una de las versiones más recientes para beneficiarse de la nueva consola de cliente y garantizar una transición sin problemas **antes del 30 de junio de 2021**.

Una vez actualizadas todas las instancias, la consola de cliente también debe actualizarse a esta versión.

* Obtenga información sobre cómo obtener acceso a [Distribución de software de Adobe](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=es).

* [Aprenda a instalar la consola del cliente de Campaign](../../installation/using/installing-the-client-console.md).

## Integración con Déclencheur de Experience Cloud {#acc-triggers-updates}

El servicio de autenticación oAuth heredado ha llegado al final de su vida útil. La autenticación de integración de Déclencheur, basada originalmente en la configuración de autenticación oAUTH para acceder a la canalización, se ha trasladado al Adobe I/O. El modo de autenticación oAuth heredado con Campaign [se ha retirado](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411?profile.language=es) el **septiembre de 2021**. Los entornos alojados se benefician de una extensión hasta el **23 de febrero de 2022**. Como cliente local o híbrido, póngase en contacto con el Servicio de atención al cliente de Adobe para ampliar la asistencia hasta febrero de 2022. Debe proporcionar [el AppID de la aplicación OAuth](../../integrations/using/configuring-pipeline.md#step-optional) a Adobe.

**¿Se ha visto afectado?**

Si las instancias se ejecutan en una versión **anterior a Campaign 19.1.8, 20.2.4, Gold Standard 11**, entonces está usando una versión anterior de la integración de Déclencheur mediante autenticación oAuth: **debe actualizar a una versión más reciente y pasar al Adobe I/O**.

Es obligatorio actualizar a una de las nuevas versiones que se enumeran a continuación:

* Gold Standard 11. [Más información](../../rn/using/gold-standard.md)
* Versión 21.1.1 de Campaign. [Más información](../../rn/using/latest-release.md)
* Versión 20.2.5 de Campaign.
* Versión 19.1.8 de Campaign.

Aprenda a comprobar su versión [en esta sección](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**¿Cómo realizar la actualización?**

Una vez que las instancias se hayan actualizado a una versión más reciente, todos los clientes deberán seguir el [procedimiento para pasar al nuevo modo de autenticación](../../integrations/using/about-triggers.md#implement). Esto requiere que genere el nuevo token de Adobe I/O y lo utilice en la implementación.  

Además, en el caso de entornos híbridos, los clientes deben asegurarse de que la canalización esté configurada en una instancia intermediaria. [Más información](../../integrations/using/configuring-pipeline.md).

[Más información sobre cómo migrar al Adobe I/O](../../integrations/using/about-triggers.md#implement).

## Actualizaciones de APNS {#acc-apns-updates}

### API de proveedor de APN basada en HTTP/2

Desde el **31 de marzo de 2021**, el servicio de notificaciones push de Apple (APN) ya no admite el protocolo binario heredado. [Más información](https://developer.apple.com/news/?id=c88acm2b).

**¿Se ha visto afectado?**

Si las instancias se ejecutan en una versión **anterior a Campaign 21.1,** y envía notificaciones push con el protocolo binario heredado de Apple, debe actualizar a la API de proveedor de APN basada en HTTP/2.

Aprenda a comprobar su versión [en esta sección](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**¿Cómo realizar la actualización?**

Como cliente alojado, si ha actualizado a la nueva versión, Adobe ya ha actualizado sus instancias a la API basada en HTTP/2.

Como cliente on-premise/híbrido, debe actualizar la configuración.

### Actualizaciones de certificado raíz de APNS

El 29 de marzo de 2021, una actualización de la infraestructura del servicio de notificaciones push de Apple (APN) afectó al canal de iOS de Adobe Campaign Classic. Un cambio en la configuración del sistema operativo es **obligatorio** para evitar la interrupción del canal push de iOS.

Obtenga más información acerca de los cambios de APN [en esta página](https://developer.apple.com/news/?id=7gx0a2lp).

**¿Se ha visto afectado?**

Si utiliza Campaign para enviar notificaciones push a dispositivos iOS, se verá afectado.

**¿Cómo realizar la actualización?**

Como cliente alojado, no es necesario realizar ninguna acción: Adobe ya ha incorporado el nuevo certificado raíz a su entorno.

Como cliente on-premise/híbrido, debe actualizar su configuración para garantizar una transición sin problemas **antes del 29 de marzo de 2021**.

[Aprenda a incorporar el nuevo certificado](ios-certificate-update.md).

## Vínculos útiles

* [Actualice su entorno](../../production/using/build-upgrade.md)
* [Preguntas frecuentes sobre la actualización de versiones](../../platform/using/faq-build-upgrade.md)
* [Descargar compilación del Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/es/campaign.html)
* [Hacer que la nueva consola de cliente esté disponible para los usuarios](../../installation/using/client-console-availability-for-windows.md)
