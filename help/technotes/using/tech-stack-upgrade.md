---
product: campaign
title: 'Nota técnica: Actualizaciones del sistema de Adobe Campaign'
description: Actualización del sistema de Adobe Campaign
hide: true
hidefromtoc: true
exl-id: 78949d94-60b3-44f1-8e5a-d61b5b723e87
source-git-commit: b8bbdb4a0d595ec2bc884e041d1e56b81da8aa3d
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 8%

---

# Actualizaciones del entorno de Adobe Campaign 2023 {#ac-system-upgrade}

La infraestructura de Campaign depende de sistemas de terceros que deben actualizarse regularmente con las versiones y correcciones más recientes. Estas actualizaciones son obligatorias para garantizar la continuidad del servicio y los entornos seguros de Campaign frente a riesgos de seguridad. Además, se requiere una actualización de Campaign para garantizar la compatibilidad con los cambios del sistema de terceros.

Como **Cliente de Cloud Services alojados o administrados**, Adobe le informa de estas actualizaciones cuando las necesita. Será necesario que actualice sus entornos de acuerdo con las recomendaciones para garantizar el cumplimiento.

Como **Cliente On-Premise o Híbrido**, Adobe recomienda encarecidamente que actualice el sistema y las versiones de Campaign según el mismo calendario.

Por motivos de seguridad, debe [instale la última versión de Campaign](#ac-upgrade)y, a continuación, actualice su [sistema operativo](#os-upgrade) y/o [Sistema de administración de bases de datos de relación (RDBMS)](#pg-upgrade).

>[!NOTE]
>
>En caso de que tenga preguntas acerca de estos cambios, póngase en contacto con el [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Consulte también la [Preguntas frecuentes sobre la actualización de versiones](../../platform/using/faq-build-upgrade.md).

## Actualización de la versión de Campaign {#ac-upgrade}

**¿Se ha visto afectado?**

Si se ve afectado por el [actualización del sistema operativo](#os-upgrade) y/o [actualización del sistema de bases de datos](#pg-upgrade) detallado a continuación, debe actualizar los entornos de Campaign a [la última versión 7.3.2](../../rn/using/latest-release.md#release-7-3-2), que es compatible con estos sistemas.

**¿Cómo realizar la actualización?**

* Como cliente alojado o de Cloud Services administrados, el Adobe se pondrá en contacto con usted y actualizará su versión de Campaign.
* Como cliente híbrido, el Adobe le informará de las fechas de actualización de la compilación programada para su entorno de mid-sourcing. También debe actualizar su entorno de marketing a la misma versión.
* Como cliente local, se le solicita que actualice los entornos de Campaign a la última versión 7.3.2.


## Actualización del sistema operativo {#os-upgrade}

**¿Se ha visto afectado?**

Si está ejecutando Campaign en un sistema operativo Debian, para beneficiarse de las últimas actualizaciones de seguridad de Debian, debe mover su infraestructura de Campaign a **Debian 11**. Tenga en cuenta que Debian 9 llegó al final de su vida útil el 30 de junio de 2022 y ya no proporciona correcciones de seguridad.

**¿Cómo realizar la actualización?**

* Como cliente de Cloud Services alojados o administrados, el Adobe se pondrá en contacto con usted y actualizará su entorno.
* Como cliente híbrido, el Adobe le informará de las fechas de actualización programadas para su entorno de mid-sourcing. Si su entorno de marketing también se está ejecutando en Debian, debe actualizarlo a Debian 11 también.
* Como cliente local, se le solicita que actualice sus entornos a Debian 11.

## Actualización del sistema de bases de datos {#pg-upgrade}

**¿Se ha visto afectado?**

Si el sistema de bases de datos para Campaign es PostgreSQL, para beneficiarse de las últimas innovaciones y actualizaciones de seguridad de PostgreSQL, debe actualizar a **PostgreSQL 14**. Tenga en cuenta que PostreSQL 11 llegará al fin de su vida útil el 30 de noviembre de 2022.

**¿Cómo realizar la actualización?**

* Como cliente de Cloud Services alojados o administrados, Adobe se pondrá en contacto con usted y actualizará su sistema de base de datos de PostgreSQL 11 a PostgreSQL 14.
* Como cliente híbrido, si el sistema de base de datos de marketing es PostgreSQL, debe actualizarlo a PostgreSQL 14.
* Como cliente local, se le solicita que actualice el sistema de base de datos a PostgreSQL 14.


## Vínculos útiles

* [Actualice su entorno](../../production/using/build-upgrade.md)
* [Preguntas frecuentes sobre la actualización de versiones](../../platform/using/faq-build-upgrade.md)
* [Descargar la última versión del Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/es/campaign.html)
* [Poner la nueva consola de cliente a disposición de los usuarios](../../installation/using/client-console-availability-for-windows.md)
