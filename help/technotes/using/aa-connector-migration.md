---
product: campaign
title: Migración al conector de Adobe Analytics
description: 'Campaign: Preguntas frecuentes sobre el conector de Analytics'
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 5bf61654-3d68-4560-a93f-7a768a2c5be4
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '858'
ht-degree: 6%

---

# Migración de las integraciones de Genesis existentes al conector de Adobe Analytics {#acc-aa-faq}



A partir de la versión 21.1.3 de Campaign Classic v7, el conector de datos de Adobe Analytics queda obsoleto. [Más información](https://experienceleague.adobe.com/docs/analytics/import/dataconnectors/data-connectors-eol.html)

El 1 de agosto de 2021, Adobe Campaign Classic se ha eliminado de la IU heredada de Data Connectors, pero las integraciones de Campaign existentes seguirán recopilando y pasando datos a Adobe Analytics hasta el 17 de agosto de 2022. Después de esta fecha, la integración deja de recopilar y pasar datos a Adobe Analytics.

Usted **debe implementar** la nueva integración del conector de Adobe Analytics en Adobe Exchange, que sustituye a la integración heredada de Data Connectors. Para obtener más información sobre Adobe Analytics Connector, consulte [esta página](../../platform/using/adobe-analytics-connector.md).

Si tiene alguna duda acerca de estos cambios, lea la [FAQ](#faq-aa). Para obtener más información, póngase en contacto con [Adobe del Servicio de atención al cliente](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

>[!NOTE]
>
>Si está migrando desde un conector de datos de Adobe Analytics existente (anteriormente conocido como integración de Genesis) y utiliza la nueva arquitectura de clasificación en Adobe Analytics, necesita versiones de compilación a partir de la versión 7.3.1 u 8.4.1 para poder migrar al nuevo conector de Adobe Analytics.

## ¿Qué ha cambiado?

Ya está disponible una nueva integración entre Campaign Classic v7 y Adobe Analytics. A continuación se enumeran los cambios más importantes.

* El **Fecha de contacto** La clasificación, que solía ser de tipo fecha, ha quedado obsoleta para Adobe Analytics. Para las integraciones migradas, seguirá siendo del mismo tipo. Para cualquier **Fecha de contacto** creado por Campaign, el tipo es **Cadena**.

* **Reglas de procesamiento** son creados por Adobe Campaign como parte de nuevas integraciones. Cualquiera **Reglas de procesamiento** debe crearse manualmente desde Adobe Analytics o utilizar directamente la implementación de Javascript del lado del cliente. **Reglas de procesamiento** permanecerá intacto para las integraciones existentes.

* Los flujos de trabajo técnicos integrados y su comportamiento siguen siendo los mismos. Solo se han cambiado las API back-end utilizadas por los flujos de trabajo para insertar/extraer datos en Adobe Analytics.

* Tenga en cuenta que la variable `nlserver` El proceso debe configurarse con el usuario de cuenta técnica de IMS para que funcione el nuevo conector. Este cambio debe hacerse por Adobe. Para implementar esto, póngase en contacto con [Adobe del Servicio de atención al cliente](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

* Si utilizaba las API de Adobe Genesis en flujos de trabajo personalizados para extraer y extraer datos de Adobe Analytics, ahora necesita utilizar las nuevas API de Adobe Analytics 1.4/2.0. [Más información](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360047148832-Replacements-for-Data-Connector-API-calls)

## ¿Se ha visto afectado?

Si está utilizando el conector de datos de Adobe Analytics existente (anteriormente conocido como integración de Genesis) y la integración se implementó en una versión inferior a la de Campaign 21.1.3, se verá afectado.

Obtenga información sobre cómo comprobar su versión [en esta sección](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## ¿Cómo realizar la actualización?

Debe actualizar a Campaign 21.1.3 (o más) **antes del 17 de agosto de 2022**.

Como cliente alojado, Adobe trabajará con usted para actualizar las instancias a la versión más reciente. A continuación, podrá utilizar [Conector de Adobe Analytics](../../platform/using/adobe-analytics-connector.md).

Como cliente on-premise/híbrido, debe actualizar a una de las versiones más recientes para beneficiarse de la nueva integración.
Una vez que todas las instancias se hayan actualizado, podrá [implementación de la nueva integración](../../platform/using/adobe-analytics-provisioning.md) a Adobe Analytics Connector y garantice una transición sin problemas.

## Preguntas frecuentes{#faq-aa}

**¿Cómo puedo obtener registros?**

La configuración de la interfaz de usuario y los flujos de trabajo están equipados con **detallado** registro.

En el modo detallado, los encabezados de solicitud y respuesta también se imprimen para cada solicitud de API a Adobe Analytics.

Como usuario On-Premise, puede implementar el modo detallado de la siguiente manera:

* Para habilitar el modo detallado en la interfaz de usuario: vuelva a ejecutar el `web` procesar en modo detallado.
* Para habilitar el modo detallado para **webAnalytics** flujos de trabajo: seleccione **Ejecutar en el motor** en las propiedades del flujo de trabajo y vuelva a ejecutar `wfserver` en modo detallado.

**¿Qué significa el error &quot;Propietario de integración no es administrador&quot;?**

Más información sobre Data Connectors `Integration Owner Not Admin` Error en [esta página](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360035167932-Adobe-Analytics-Data-Connectors-Integration-Owner-Not-Admin-Error).

**Una vez completada la migración al nuevo conector, ¿qué sucede con los datos antiguos y los grupos de informes?**

Después de la migración, un nuevo conector (migrado desde el conector antiguo) empezará a insertar datos en el mismo grupo de informes y los datos existentes no se verán afectados: se añadirá a los datos existentes.

**Algunas eVars, eventos o grupos de informes existentes presentes en Analytics no son visibles en Campaign. ¿Qué debo hacer?**

La integración se basa en los datos del token de cuenta técnica para el funcionamiento diario. Si falta permiso para acceder a una dimensión, métrica o grupo de informes desde el perfil de producto asociado al usuario de cuenta técnica, las API que usemos simplemente flaquearán para esas solicitudes.

Si leemos los detalles de un componente de Analytics (como métricas, dimensiones, segmentos o grupos de informes), la API no devolverá estos componentes en el resultado (que puede parecer que algo se eliminó en Analytics o no está presente). La API de Analytics rechazará esas solicitudes y se producirá un error.

La solución es actualizar el **Perfil del producto** en el contexto de usuario de Analytics del token de usuario técnico con los componentes recién creados o que faltan al agregar estos componentes en [Adobe Admin Console](https://adminconsole.adobe.com/){_blank}. Para obtener más información, póngase en contacto con [Adobe del Servicio de atención al cliente](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Vínculos útiles

* [Actualice su entorno](../../production/using/build-upgrade.md)
* [Preguntas frecuentes sobre la actualización de versiones](../../platform/using/faq-build-upgrade.md)
* [Descargar versión de Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/es/campaign.html)
* [Hacer que la nueva consola de cliente esté disponible para los usuarios](../../installation/using/client-console-availability-for-windows.md)
* [Instalación de la consola del cliente de Campaign](../../installation/using/installing-the-client-console.md)
