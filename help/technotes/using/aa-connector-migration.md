---
product: campaign
title: Migración al conector de Adobe Analytics
description: 'Campaign: Preguntas frecuentes sobre el conector de Analytics'
feature: Technote, Analytics Integration
badge-v7-prem: label="On-premise/híbrido solo" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas v7"
exl-id: 5bf61654-3d68-4560-a93f-7a768a2c5be4
hide: true
hidefromtoc: true
source-git-commit: a1dbef3e1feca1e3347de013db8bd7809d315016
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 3%

---

# Migración de las integraciones de Genesis existentes al conector de Adobe Analytics {#acc-aa-faq}

A partir de la versión 21.1.3 de Campaign Classic v7, el conector de datos de Adobe Analytics queda obsoleto. [Más información](https://experienceleague.adobe.com/docs/analytics/import/dataconnectors/data-connectors-eol.html)

El 1 de agosto de 2021, Adobe Campaign Classic se ha eliminado de la IU heredada de Data Connectors, pero las integraciones de Campaign existentes seguirán recopilando y pasando datos a Adobe Analytics hasta el 17 de agosto de 2022. Después de esta fecha, la integración deja de recopilar y pasar datos a Adobe Analytics.

Usted **debe implementar** la nueva integración de Adobe Analytics Connector en el Adobe Exchange que reemplaza la integración heredada de Data Connectors. Para obtener más información sobre el conector de Adobe Analytics, consulte [esta página](../../integrations/using/gs-aa.md).

Si tiene alguna pregunta sobre estos cambios, lea las [preguntas frecuentes](#faq-aa). Para obtener más información, póngase en contacto con el [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

>[!NOTE]
>
>Si está migrando desde un conector de datos de Adobe Analytics existente (anteriormente conocido como integración de Genesis) y utiliza la nueva arquitectura de clasificación en Adobe Analytics, necesita versiones de compilación a partir de la versión 7.3.1 u 8.4.1 para poder migrar al nuevo conector de Adobe Analytics.

## ¿Qué ha cambiado?

Ya está disponible una nueva integración entre Campaign Classic v7 y Adobe Analytics. A continuación se enumeran los cambios más importantes.

* La clasificación **Fecha de contacto**, que solía ser de tipo fecha, ha quedado obsoleta en Adobe Analytics. Para las integraciones migradas, seguirá siendo del mismo tipo. Para cualquier **fecha de contacto** creada por Campaign, el tipo será **cadena**.

* Adobe Campaign crea **reglas de procesamiento** como parte de nuevas integraciones. **Las reglas de procesamiento** deben crearse manualmente desde Adobe Analytics o usar directamente la implementación de Javascript del lado del cliente. **Reglas de procesamiento** permanecerán intactas para las integraciones existentes.

* Los flujos de trabajo técnicos integrados y su comportamiento siguen siendo los mismos. Solo se han cambiado las API back-end utilizadas por los flujos de trabajo para insertar/extraer datos en Adobe Analytics.

* Tenga en cuenta que el proceso `nlserver` debe configurarse con el usuario de cuenta técnica de IMS para que funcione el nuevo conector. Este cambio debe hacerse por Adobe. Para que esto se implemente, comuníquese con el [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

* Si utilizaba las API de Adobe Genesis en flujos de trabajo personalizados para extraer y extraer datos de Adobe Analytics, ahora necesita utilizar las nuevas API de Adobe Analytics 1.4/2.0. [Más información](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360047148832-Replacements-for-Data-Connector-API-calls)

## ¿Se ha visto afectado?

Si está utilizando el conector de datos de Adobe Analytics existente (anteriormente conocido como integración de Genesis) y la integración se implementó en una versión inferior a la de Campaign 21.1.3, se verá afectado.

Aprenda a comprobar su versión [en esta sección](../../integrations/using/launching-adobe-campaign.md#getting-your-campaign-version).

## ¿Cómo realizar la actualización?

Debe actualizar a Campaign 21.1.3 (o más) **antes del 17 de agosto de 2022**.

Como cliente alojado, Adobe trabajará con usted para actualizar las instancias a la versión más reciente. A continuación, podrá usar [conector Adobe Analytics](../../platform/using/gs-aa.md).

Como cliente on-premise/híbrido, debe actualizar a una de las versiones más recientes para beneficiarse de la nueva integración.
Una vez que todas las instancias se hayan actualizado, podrá [implementar la nueva integración](../../integrations/using/adobe-analytics-provisioning.md) en el conector de Adobe Analytics y garantizar una transición sin problemas.

## Preguntas frecuentes{#faq-aa}

**¿Cómo puedo obtener los registros?**

La configuración de la interfaz de usuario y los flujos de trabajo están equipados con **registro detallado**.

En el modo detallado, los encabezados de solicitud y respuesta también se imprimen para cada solicitud de API a Adobe Analytics.

Como usuario On-Premise, puede implementar el modo detallado de la siguiente manera:

* Para habilitar el modo detallado en la interfaz de usuario: vuelva a ejecutar el proceso `web` en modo detallado.
* Para habilitar el modo detallado para los flujos de trabajo de **webAnalytics**: seleccione la opción **Ejecutar en el motor** de las propiedades del flujo de trabajo y vuelva a ejecutar `wfserver` en el modo detallado.

**¿Qué significa el error &quot;Propietario de la integración no es administrador&quot;?**

Obtenga más información sobre el error de Data Connectors `Integration Owner Not Admin` en [esta página](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360035167932-Adobe-Analytics-Data-Connectors-Integration-Owner-Not-Admin-Error).

**Una vez completada la migración al nuevo conector, ¿qué sucede con los datos antiguos y los grupos de informes?**

Después de la migración, un nuevo conector (migrado desde el conector antiguo) empezará a insertar datos en el mismo grupo de informes y los datos existentes no se verán afectados: se añadirá a los datos existentes.

**Algunas eVars, eventos o grupos de informes existentes presentes en Analytics no son visibles en Campaign. ¿Qué debo hacer?**

La integración se basa en los datos del token de cuenta técnica para el funcionamiento diario. Si falta permiso para acceder a una dimensión, métrica o grupo de informes desde el perfil de producto asociado al usuario de cuenta técnica, las API que usemos simplemente flaquearán para esas solicitudes.

Si leemos los detalles de un componente de Analytics (como métricas, dimensiones, segmentos o grupos de informes), la API no devolverá estos componentes en el resultado (que puede parecer que algo se eliminó en Analytics o no está presente). La API de Analytics rechazará esas solicitudes y se producirá un error.

La solución consiste en actualizar el **Perfil de producto** en el contexto de usuario de Analytics del token de usuario técnico con los componentes recién creados o que faltan agregando estos componentes en [Adobe Admin Console](https://adminconsole.adobe.com/){_blank}. Para obtener más información, comuníquese con el [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Vínculos útiles

* [Actualice su entorno](../../production/using/build-upgrade.md)
* [Preguntas frecuentes sobre la actualización de versiones](../../platform/using/faq-build-upgrade.md)
* [Descargar compilación del Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/es/campaign.html)
* [Hacer que la nueva consola de cliente esté disponible para los usuarios](../../installation/using/client-console-availability-for-windows.md)
* [Instalación de la consola del cliente de Campaign](../../installation/using/installing-the-client-console.md)
