---
product: campaign
title: 'Nota técnica: Actualizaciones del sistema de Adobe Campaign'
description: Actualización del sistema de Adobe Campaign
feature: Technote, Upgrade
hide: true
hidefromtoc: true
exl-id: 78949d94-60b3-44f1-8e5a-d61b5b723e87
source-git-commit: 62fc46e45078fce56eadda3518251e61244bf5d0
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 4%

---

# Actualizaciones del entorno de Adobe Campaign 2023 {#ac-system-upgrade}

La infraestructura de Campaign se basa en sistemas de terceros que deben actualizarse regularmente con las últimas versiones y correcciones. Estas actualizaciones son obligatorias para garantizar la continuidad del servicio y proteger los entornos de Campaign de los riesgos de seguridad. Además, se requiere una actualización de Campaign para garantizar la compatibilidad con los cambios del sistema de terceros.

Como **cliente de Cloud Services hospedado o administrado**, Adobe le informa sobre estas actualizaciones cuando son necesarias. Se le pedirá que actualice sus entornos de acuerdo con las recomendaciones para garantizar el cumplimiento.

Como **cliente On-Premise o híbrido**, Adobe le recomienda encarecidamente que actualice su sistema y las versiones de Campaign según el mismo calendario.

Por razones de seguridad, debe [instalar la última compilación de Campaign](#ac-upgrade) y luego actualizar su [sistema operativo](#os-upgrade) y/o su [Sistema de administración de bases de datos de relación (RDBMS)](#pg-upgrade).

>[!NOTE]
>
>Si tiene alguna pregunta sobre estos cambios, comuníquese con el [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Consulte también las [preguntas frecuentes sobre la actualización de la compilación](../../platform/using/faq-build-upgrade.md).
>

## Actualización de compilación de Campaign {#ac-upgrade}

**¿Se ha visto afectado?**

Si se ve afectado por la [actualización del sistema operativo](#os-upgrade) y/o la [actualización del sistema de base de datos](#pg-upgrade) detallada a continuación, debe actualizar los entornos de Campaign a [la última versión de la versión 7.3.2](../../rn/using/latest-release.md#release-7-3-2), que es compatible con estos sistemas.

**¿Cómo realizar la actualización?**

* Como cliente de Cloud Services alojados o administrados, Adobe se pondrá en contacto con usted y actualizará la versión de Campaign.
* Como cliente híbrido, Adobe le informará de las fechas de actualización de la compilación programadas para su entorno de intermediario. También debe actualizar el entorno de marketing a esa misma versión.
* Como cliente On-Premise, se le solicita que actualice sus entornos de Campaign a la última versión 7.3.2.


## Actualización del sistema operativo {#os-upgrade}

**¿Se ha visto afectado?**

Si está ejecutando Campaign en un sistema operativo Debian, para beneficiarse de las últimas actualizaciones de seguridad de Debian, debe mover su infraestructura de Campaign a **Debian 11**. Tenga en cuenta que la compatibilidad con la seguridad de Debian 9 estará disponible hasta el 30 de junio de 2023.

**¿Cómo realizar la actualización?**

* Como cliente de Cloud Services alojados o administrados, Adobe se pondrá en contacto con usted y actualizará su entorno.
* Como cliente híbrido, Adobe le informará de las fechas de actualización programadas para su entorno de intermediario. Si su entorno de marketing también se está ejecutando en Debian, debe actualizarlo a Debian 11 también.
* Como cliente on-premise, se le solicita que actualice sus entornos a Debian 11.

## Actualización del sistema de base de datos {#pg-upgrade}

**¿Se ha visto afectado?**

Si el sistema de base de datos de Campaign es PostgreSQL, para beneficiarse de las últimas innovaciones y actualizaciones de seguridad de PostgreSQL, debe actualizar a **PostgreSQL 14**. Tenga en cuenta que PostgreSQL 11 llegará al fin de su vida útil el 9 de noviembre de 2023.

**¿Cómo realizar la actualización?**

* Como cliente de Cloud Services alojados o administrados, Adobe se pondrá en contacto con usted y actualizará su sistema de base de datos de PostgreSQL 11 a PostgreSQL 14.
* Como cliente híbrido, si el sistema de base de datos de marketing es PostgreSQL, debe actualizarlo a PostgreSQL 14.
* Como cliente On-Premise, se le solicita que actualice su sistema de base de datos a PostgreSQL 14.


## Vínculos útiles

* [Actualice su entorno](../../production/using/build-upgrade.md)
* [Preguntas frecuentes sobre la actualización de versiones](../../platform/using/faq-build-upgrade.md)
* [Descargar la última versión de Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/es/campaign.html)
* [Hacer que la nueva consola de cliente esté disponible para los usuarios](../../installation/using/client-console-availability-for-windows.md)
