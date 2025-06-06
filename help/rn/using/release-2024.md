---
product: campaign
title: Versiones de Campaign Classic 2024
description: Más información sobre las actualizaciones de Campaign Classic 2024
feature: Release Notes
role: User
level: Beginner
exl-id: 8e20391d-3628-4d0c-b413-c34e046ae810
source-git-commit: bf45c8bcdd41e614f9be09bc0fd6385707159841
workflow-type: ht
source-wordcount: '387'
ht-degree: 100%

---

# Versiones de 2024{#release-2024}

## Versión 7.4.1, compilación 9383 {#release-7-4-1}

[!BADGE Disponibilidad general]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=es#rn-statuses" tooltip="Disponibilidad general"}

_18 de junio de 2024_

### Cambios y mejoras {#release-7-4-1-changes}

* Dado que Adobe ha dejado obsoleta la credencial de Cuenta de servicio (JWT), las integraciones de salida de Campaign con aplicaciones y soluciones de Adobe ahora dependen de la credencial OAuth de servidor a servidor. Si ha implementado integraciones de salida, como la integración de Campaign-Analytics o los activadores de Experience Cloud, debe actualizar su entorno de Campaign a la versión 7.4.1 y migrar su cuenta técnica a OAuth antes del 27 de enero de 2025. [Más información](../../integrations/using/oauth-technical-account.md)

* Una vez que haya [migrado los operadores técnicos de Campaign a Developer Console](../../technotes/using/ims-migration.md) y [haya realizado la transición a IMS para la autenticación del usuario final](../../technotes/using/migrate-users-to-ims.md), ahora puede habilitar la interfaz de usuario y las restricciones de la API para quitar opciones y funcionalidades específicas de la autenticación nativa. [Más información](../../technotes/using/impact-ims-migration.md)


### Actualizaciones de compatibilidad {#release-7-4-1-compat}

La [matriz de compatibilidad para Adobe Campaign](compatibility-matrix.md) se ha actualizado con los cambios que se proporcionan con esta nueva versión y se enumeran a continuación.

* Adobe Campaign ahora es compatible con **Microsoft Server 2022** como sistema operativo. 
* Adobe Campaign ahora es compatible con **RHEL 9** como sistema operativo.

  >[!CAUTION]
  >
  >Como cliente On-Premise que usa RHEL 9, si desea usar la autenticación de DKIM (Domain Keys Identified Mail), debe actualizar la configuración del sistema tal como se detalla en [esta sección](../../installation/using/installing-packages-with-linux.md#rhel-9-update).


* Ahora Adobe Campaign es compatible con **Microsoft SQL Server 2022** y **Oracle 23c** como sistemas de gestión de bases de datos relacionales y en el acceso de datos federado (FDA).

* Adobe Campaign ahora requiere al menos un kit de desarrollo de Java (JDK) 11. En Windows, el JRE debe estar disponible tal como se describe en [esta sección](../../installation/using/application-server.md#jdk).

* El SDK de Campaign (Neolane) para aplicaciones móviles ha quedado obsoleto. Ahora debe realizar la transición al SDK de Adobe Experience Platform. [Más información](deprecated-features.md).

  Mientras tanto, para garantizar la continuidad del servicio, Campaign v7.4 incluye:

   * un nuevo SDK de Campaign 1.0.27 para iOS, compatible con iOS 16 y 17, y los últimos [requisitos de solicitud de privacidad de Apple iOS](https://developer.apple.com/news/?id=r1henawx){target="_blank"}.
   * un nuevo SDK de Campaign para Android 14.

### Otros cambios {#release-7-4-1-other}

A partir de la versión 7.4.1, las bibliotecas XML para paquetes RPM de Linux ya no se incluyen en Campaign. Como cliente On-Premise o híbrido, el administrador debe instalar estas bibliotecas. [Más información](../../installation/using/installing-packages-with-linux.md)

### Parches {#release-7-4-1-patches}

Esta versión incluye las siguientes correcciones:

NEO-74754, NEO-73174, NEO-72504, NEO-71534, NEO-71473, NEO-70195, NEO-69663, NEO-69651, NEO-67620, NEO-67235, NEO-66797, NEO-64680, NEO-63706, NEO-63657, NEO-62964, NEO-62575, NEO-58734, NEO-40531, NEO-36189, NEO-29592


