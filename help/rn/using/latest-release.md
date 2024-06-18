---
product: campaign
title: Último lanzamiento
description: Notas de la versión más reciente de Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: d31aa28da06e65664da655b6b082563767b35f7a
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 19%

---

# Último lanzamiento {#latest-release}

Esta página lista las nuevas funcionalidades, mejoras y correcciones que se proporcionan con la **última versión de Campaign Classic v7**. Cada nueva compilación viene con un estado que se materializa con un color. Obtenga más información sobre los estados de compilación de Campaign Classic v7 en [esta página](rn-overview.md).

## Versión 7.4.1, compilación 9383 {#release-7-4-1}

[!BADGE Disponibilidad general]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=es#rn-statuses" tooltip="Disponibilidad general"}

_miércoles, 18 de junio de 2024_

### Cambios y mejoras {#release-7-4-1-changes}

* Con la credencial de cuenta de servicio (JWT) obsoleta por el Adobe, las integraciones salientes de Campaign con soluciones de Adobe y aplicaciones ahora dependen de la credencial de servidor a servidor de OAuth. Si ha implementado integraciones salientes, como la de Campaign-Analytics o la de Experience Cloud Déclencheur, debe actualizar su entorno de Campaign a la versión 7.4.1 y migrar su cuenta técnica a oAuth antes del 27 de enero de 2025. [Más información](../../integrations/using/oauth-technical-account.md)

* Una vez que haya [se han migrado los operadores técnicos de Campaign a Developer Console](../../technotes/using/ims-migration.md) y [Se ha realizado la transición a IMS para la autenticación del usuario final](../../technotes/using/migrate-users-to-ims.md), ahora puede habilitar la interfaz de usuario y las restricciones de la API para eliminar opciones y funcionalidades específicas de la autenticación nativa. [Más información](../../technotes/using/impact-ims-migration.md)



### Actualizaciones de compatibilidad {#release-7-4-1-compat}

El [matriz de compatibilidad para Adobe Campaign](compatibility-matrix.md) se ha actualizado con los cambios que se proporcionan con esta nueva versión y se enumera a continuación.

* Adobe Campaign ahora es compatible con **Microsoft Server 2022** y **RHEL 9** como sistemas operativos.

* Adobe Campaign ahora es compatible con **Microsoft SQL Server 2022** y **Oracle 23c** como Relation Database Management Systems y en el acceso de datos federado (FDA).

* Adobe Campaign ahora requiere al menos un kit de desarrollo de Java (JDK) 11. En Windows, el JRE debe estar disponible como se describe en [esta sección](../../installation/using/application-server.md#jdk).

* El SDK de Campaign (Neolane) para aplicaciones móviles ya no se utiliza. Ahora debe realizar la transición al SDK de Adobe Experience Platform. [Más información](deprecated-features.md).

  Mientras tanto, para garantizar la continuidad del servicio, Campaign v7.4 incluye:

   * un nuevo SDK de Campaign 1.0.27 para iOS, compatible con iOS 16 y 17, y la última versión [Requisitos de solicitud de privacidad de Apple iOS](https://developer.apple.com/news/?id=r1henawx){target="_blank"}.
   * un nuevo SDK de Campaign para Android 14.


### Parches {#release-7-4-1-patches}

Esta versión incluye las siguientes correcciones:

NEO-74754, NEO-73174, NEO-72504, NEO-71534, NEO-71473, NEO-70195, NEO-69663, NEO-69651, NEO-67620, NEO-67235, NEO-66797, NEO-64680, NEO-63706, NEO-63657, NEO-62964, NEO-62575, NEO-58734, NEO-40531, NEO-36189, NEO-29592

