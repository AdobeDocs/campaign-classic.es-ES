---
solution: Campaign Classic
product: campaign
title: Nota técnica
description: Nota técnica
hide: true
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 248c74485e8e5889ca630c8f60ac2fa085204c51
workflow-type: tm+mt
source-wordcount: '896'
ht-degree: 16%

---


# Actualizaciones de configuración de Adobe Campaign: marzo de 2021 {#acc-config-updates}

Debe mantener la infraestructura y la configuración actualizadas con las últimas versiones y correcciones de productos. Estas correcciones son obligatorias para garantizar la continuidad y seguridad del servicio.

Los usuarios de Campaign deben actualizar a una de las versiones más recientes a continuación:

* Gold Standard 11. [Obtenga más información](../rn/using/gold-standard.md)
* Versión 21.1.1 de Campaign. [Obtenga más información](../rn/using/latest-release.md)
* Versión 20.3.3 de Campaign. [Obtenga más información](../rn/using/release--20-3.md)
* Versión 20.2.4 de Campaign. [Obtenga más información](../rn/using/release--20-2.md)
* Versión 20.1.4 de Campaign. [Obtenga más información](../rn/using/release--20-1.md)
* Versión 19.2.4 de Campaign. [Obtenga más información](../rn/using/release--19-2.md)
* Versión 19.1.8 de Campaign. [Obtenga más información](../rn/using/release--19-1.md)

Estas compilaciones garantizan la continuidad de ciertos servicios de Campaign: Integración de Déclencheur de Experience Cloud, autenticación APNS y el nuevo protocolo de conexión que afecta al mecanismo de autenticación del servicio Identity Management de Adobe (IMS).

Como cliente alojado, no es necesario realizar ninguna acción: Adobe es propietario de las actualizaciones de actualización y configuración de la compilación.

Como cliente local/híbrido, debe actualizar a una de las versiones anteriores. Además, debe realizar algunas tareas manuales para asegurarse de que el entorno sea seguro y esté listo para los próximos cambios de sistemas de Adobe o de terceros.

## Actualizaciones de seguridad

Las últimas versiones de Campaign incluyen una corrección de seguridad que refuerza la protección contra los problemas de falsificación de solicitudes del lado del servidor (SSRF). Obtenga más información [en esta página](https://helpx.adobe.com/security/products/campaign/apsb21-04.html).

**¿Estás afectado?**

Si su entorno se encuentra en una compilación inferior a Campaign 21.1, se verá afectado.

**¿Cómo se actualiza?**

Debe actualizar a una de las compilaciones más recientes que se enumeran arriba.

* Como cliente híbrido, Adobe actualizará la instancia de intermediario a la nueva versión y se le recomienda actualizar también su instancia de marketing.

   La nueva compilación es compatible con al menos la versión 17.9 de Campaign Classic, pero para evitar lagunas de seguridad, Adobe recomienda encarecidamente actualizar todas las instancias a una nueva versión. 

* Como cliente local, se le solicita que actualice las instancias de marketing y intermediario a una nueva versión.

>[!CAUTION]
>
>Si no puede actualizar por ahora, **debe ponerse en contacto con el equipo de atención al cliente de Adobe para aplicar manualmente una corrección de seguridad en sus instancias**.


## Actualización de la consola del cliente de Campaign

La última versión de Gold Standard 11 corrige una regresión que impedía el uso de algunos componentes de la consola, como el selector de fechas y la administración de imágenes en los envíos. La actualización de la consola es obligatoria.

[Más información](../rn/using/gold-standard.md).

## Conectarse a Campaign a través de IMS

El servicio de identidad de Adobe (IMS) dejará de admitir versiones antiguas de Internet Explorer a partir del 30 de junio de 2021. [Más información](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html). La consola de Campaign se ha actualizado para garantizar la compatibilidad con IMS.

**¿Estás afectado?**

Si se está conectando a Campaign [a través de un Adobe ID](../integrations/using/about-adobe-id.md), a través del servicio de identidad de Adobe (IMS), la actualización a una de las nuevas versiones enumeradas anteriormente es obligatoria. Esta versión incluye un nuevo protocolo de conexión: la actualización es obligatoria para que el servidor de Campaign y la consola del cliente puedan conectarse a Campaign después del **30 de junio de 2021**.

**¿Cómo se actualiza?**

Como cliente alojado, no es necesario realizar ninguna acción: Adobe ya ha actualizado las instancias a una versión más reciente.

Como cliente local/híbrido, debe actualizar a una de las versiones más recientes para beneficiarse de la nueva consola de cliente y garantizar una transición sin problemas **antes del 30 de junio de 2021**.

Una vez que todas las instancias se hayan actualizado, la consola de cliente también deberá actualizarse a esta versión.

* Obtenga información sobre cómo acceder a [Adobe Software Distribution](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en).

* [Obtenga información sobre cómo instalar la consola de cliente de Campaign](../installation/using/installing-the-client-console.md).

## Integración con Déclencheur de Experience Cloud

El servicio de autenticación oAuth heredado ha llegado al final de su vida útil. La autenticación de integración de déclencheur, basada originalmente en la configuración de autenticación oAUTH para acceder a la canalización, se ha trasladado a Adobe I/O. Se retirará el 30 de junio de 2021. [Más información](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411).

**¿Estás afectado?**

Si utiliza una versión anterior de la integración de Déclencheur mediante autenticación oAuth, **debe pasar a Adobe I/O**.

**¿Cómo se actualiza?**

Una vez que las instancias se actualizan a una versión más reciente, todos los clientes deben seguir el procedimiento [para pasar al nuevo modo de autenticación](../integrations/using/configuring-adobe-io.md). Esto requiere generar el nuevo token de Adobe I/O y utilizarlo en la implementación.  

Además, en el caso de entornos híbridos, los clientes deben asegurarse de que la canalización esté configurada en una instancia intermediaria. [Más información](../integrations/using/configuring-pipeline.md).

[Descubra más información sobre cómo migrar a Adobe I/O](../integrations/using/configuring-adobe-io.md).

## API de proveedor de APNS basada en HTTP/2

A partir del 31 de marzo de 2021, el servicio de notificaciones push de Apple (APN) ya no admitirá el protocolo binario heredado. [Obtenga más información](https://developer.apple.com/news/?id=c88acm2b).

**¿Estás afectado?**

Si las instancias se ejecutan en una versión anterior a Campaign 21.1 y envían notificaciones push con el protocolo binario heredado de Apple, debe actualizar a la API del proveedor de APNS basada en HTTP/2.

**¿Cómo se actualiza?**

Como cliente alojado, no es necesario realizar ninguna acción: Adobe ya ha actualizado sus instancias a la API basada en HTTP/2.

Como cliente local/alojado, debe actualizar su configuración. [Aprenda a migrar a HTTP/2](https://helpx.adobe.com/es/campaign/kb/migrate-to-apns-http2.html)

## Actualizaciones de certificados raíz de APNS

El 29 de marzo de 2021, la actualización de la infraestructura del servicio de notificaciones push de Apple (APNS) afectará al canal iOS de Adobe Campaign Classic. Un cambio en la configuración del sistema operativo es **obligatorio** para evitar la interrupción del canal push de iOS.

Obtenga más información sobre los cambios de APNS [en esta página](https://developer.apple.com/news/?id=7gx0a2lp).

**¿Estás afectado?**

Si utiliza Campaign para enviar notificaciones push a dispositivos iOS, se verá afectado.

**¿Cómo se actualiza?**

Como cliente alojado, no es necesario realizar ninguna acción: Adobe ya ha incorporado el nuevo certificado raíz a su entorno.

Como cliente local/híbrido, debe actualizar la configuración para garantizar una transición sin problemas **antes del 29 de marzo de 2021**.

[Aprenda a incorporar el nuevo certificado](ios-certificate-update.md).
