---
product: campaign
title: Migrar al conector de Adobe Analytics
description: 'Campaign: Preguntas más frecuentes sobre el conector de Analytics'
exl-id: 5bf61654-3d68-4560-a93f-7a768a2c5be4
source-git-commit: c072cb5b2d33f93ff395e4670507744b0d20c9bc
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 6%

---

# Cómo migrar las integraciones de Genesis existentes a Adobe Analytics Connector {#acc-aa-faq}

![](../../assets/v7-only.svg)

A partir de la versión 7.21.1.3 de Campaign Classic, el conector de datos de Adobe Analytics queda obsoleto. [Más información](https://experienceleague.adobe.com/docs/analytics/import/dataconnectors/data-connectors-eol.html)

El 1 de agosto de 2021, Adobe Campaign Classic se eliminó de la IU de Data Connectors heredada. Sin embargo, las integraciones de Campaign existentes seguirán recopilando y pasando datos a Adobe Analytics hasta el 17 de agosto de 2022. Después de esta fecha, la integración dejará de recopilar y pasar datos a Adobe Analytics.

You **debe implementarse** la nueva integración de Adobe Analytics Connector en Adobe Exchange que sustituye a la integración de Data Connectors heredada. Para obtener más información sobre Adobe Analytics Connector, consulte [esta página](../../platform/using/adobe-analytics-connector.md).

>[!NOTE]
>
>Para cualquier pregunta sobre estos cambios, lea la [Preguntas frecuentes](#faq-aa). Para obtener más información, póngase en contacto con [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## ¿Qué ha cambiado?

Ya está disponible una nueva integración entre Campaign Classic v7 y Adobe Analytics. A continuación se enumeran los principales cambios.

* La variable **Fecha de contacto** Adobe Analytics ha desaprobado la clasificación, que solía ser de tipo fecha. Para las integraciones migradas, seguirá siendo del mismo tipo. Para cualquier **Fecha de contacto** creado por Campaign, el tipo **Cadena**.

* **Reglas de procesamiento** son creados por Adobe Campaign como parte de nuevas integraciones. Cualquiera **Reglas de procesamiento** debe crearse manualmente desde Adobe Analytics o utilizar directamente la implementación de Javascript del lado del cliente. **Reglas de procesamiento** permanecerá intacto para las integraciones existentes.

* Los flujos de trabajo técnicos integrados y su comportamiento siguen siendo el mismo. Solo se han cambiado las API back-end utilizadas por los flujos de trabajo para insertar o extraer datos de Adobe Analytics.

* Tenga en cuenta que `nlserver` debe configurarse con el usuario de cuenta técnica de IMS para que funcione el nuevo conector. Este cambio debe hacerse por Adobe. Para que esto se implemente, póngase en contacto con [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

* Si era API de Adobe Genesis en flujos de trabajo personalizados para extraer y extraer los datos de Adobe Analytics, ahora debe utilizar las nuevas API de Adobe Analytics 1.4/2.0. [Más información](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360047148832-Replacements-for-Data-Connector-API-calls)

## ¿Se ha visto afectado?

Si utiliza el conector de datos de Adobe Analytics existente (anteriormente conocido como integración de Genesis) y la integración se ha implementado en una versión anterior a Campaign 21.1.3, su impacto se verá afectado.

Descubra cómo comprobar su versión [en esta sección](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## ¿Cómo realizar la actualización?

Debe actualizar a Campaign 21.1.3 (o más) **antes del 17 de agosto de 2022**.

Como cliente alojado, el Adobe trabajará con usted para actualizar sus instancias a la versión más reciente. Podrá utilizar [Conector de Adobe Analytics](../../platform/using/adobe-analytics-connector.md).

Como cliente local/híbrido, debe actualizar a una de las versiones más recientes para beneficiarse de la nueva integración.
Una vez que se actualicen todas las instancias, podrá [implementar la nueva integración](../../platform/using/adobe-analytics-provisioning.md) al conector de Adobe Analytics y asegúrese de que la transición sea fluida.

## Preguntas frecuentes{#faq-aa}

**¿Cómo puedo obtener registros?**

La configuración y los flujos de trabajo de la interfaz de usuario están equipados con **verbose** registro.

En modo detallado, los encabezados de solicitud y respuesta también se imprimen para cada solicitud de API a Adobe Analytics.

Como usuario local, puede implementar el modo detallado de la siguiente manera:

* Para habilitar el modo detallado para la interfaz de usuario: vuelva a ejecutar el `web` procesar en modo detallado.
* Para habilitar el modo detallado para **webAnalytics** flujos de trabajo: seleccione **Ejecutar en el motor** de las propiedades del flujo de trabajo y volver a ejecutar `wfserver` en modo detallado.

**¿Qué significa el error &quot;Propietario de la integración no administrador&quot;?**

Obtenga más información sobre los Data Connectors `Integration Owner Not Admin` Error en [esta página](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360035167932-Adobe-Analytics-Data-Connectors-Integration-Owner-Not-Admin-Error).

**Una vez completada la migración al nuevo conector, ¿qué ocurre con los datos antiguos y los grupos de informes?**

Después de la migración, un conector nuevo (migrado desde el conector antiguo) empezará a insertar los datos en ese mismo grupo de informes y los datos existentes no se verán afectados: se agregará a los datos existentes.

**Algunos evars, eventos o grupos de informes existentes presentes en Analytics no son visibles en Campaign. ¿Qué debo hacer?**

La integración depende de los datos del token de cuenta técnica para el funcionamiento diario. Si falta permiso para acceder a un grupo de informes/dimensiones desde el perfil de producto asociado con el usuario de cuenta técnica, las API que usemos simplemente fallarán para esas solicitudes.

Si leemos los detalles de un componente de Analytics (como métricas, dimensiones, segmentos o grupos de informes), la API no devolverá estos componentes en el resultado (que pueden parecer que algo se ha eliminado en Analytics o no está presente). La API de Analytics rechazará esas solicitudes y se eliminarán los errores.

La solución es actualizar el **Perfil del producto** en el contexto de usuario de Analytics del token de usuario técnico con los componentes recién creados/faltantes al añadir estos componentes en [Adobe Admin Console](https://adminconsole.adobe.com/). Para obtener más información, póngase en contacto con [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Vínculos útiles

* [Actualice su entorno](../../production/using/build-upgrade.md)
* [Preguntas frecuentes sobre la actualización de versiones](../../platform/using/faq-build-upgrade.md)
* [Descargar compilación del Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/es/campaign.html)
* [Poner la nueva consola de cliente a disposición de los usuarios](../../installation/using/client-console-availability-for-windows.md)
* [Instalación de la consola del cliente de Campaign](../../installation/using/installing-the-client-console.md)
