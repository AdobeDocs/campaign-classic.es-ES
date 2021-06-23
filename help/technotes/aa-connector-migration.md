---
product: campaign
title: Migrar al conector de Adobe Analytics
description: 'Campaign: Preguntas más frecuentes sobre el conector de Analytics'
hide: true
hidefromtoc: true
source-git-commit: 248bd7774c01adb44ce33d0499c2b01d013e75bd
workflow-type: tm+mt
source-wordcount: '757'
ht-degree: 6%

---

# Cómo migrar al conector Adobe Analytics {#acc-aa-faq}

A partir de la versión 7.21.1.3 de Campaign Classic, el conector de datos de Adobe Analytics queda obsoleto. [Más información](https://experienceleague.adobe.com/docs/analytics/import/dataconnectors/data-connectors-eol.html)

El 1 de agosto de 2021, Adobe Campaign Classic se eliminará de la interfaz de usuario heredada de Data Connectors. Sin embargo, las integraciones de Campaign existentes seguirán recopilando y pasando datos a Adobe Analytics hasta el 1 de marzo de 2022. El 1 de marzo de 2022, la integración dejará de recopilar y pasar datos a Adobe Analytics.

Debe migrar a la nueva integración de Adobe Analytics Connector en Adobe Exchange, que sustituye a la integración de Data Connectors heredada, tal como se detalla en [esta página](../platform/using/adobe-analytics-connector.md).


>[!NOTE]
>
>En caso de que tenga preguntas acerca de estos cambios, póngase en contacto con el [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).


## ¿Qué ha cambiado?

Ya está disponible una nueva integración entre Campaign Classic y Adobe Analytics. A continuación se enumeran los principales cambios.

* La integración entre la autenticación de Adobe Campaign Classic y Adobe Analytics se ha trasladado de usuario/contraseña a servicio de Identity Management de Adobe (IMS). Como consecuencia, debe implementar el Adobe IMS y conectarse a Campaign [a través de un Adobe ID](../integrations/using/about-adobe-id.md), antes de iniciar la implementación del conector de Analytics.

* La clasificación **Fecha de contacto**, que solía ser de tipo fecha, ha quedado obsoleta por Adobe Analytics. Para las integraciones migradas, seguirá siendo del mismo tipo. Para cualquier **Fecha de contacto** creada por Campaign, el tipo será **String**.

* **Adobe Campaign crea las** reglas de procesamiento como parte de las nuevas integraciones. Las **Reglas de procesamiento** deben crearse manualmente desde Adobe Analytics o directamente deben utilizar la implementación de Javascript del lado del cliente. **Las** reglas de procesamiento permanecerán intactas para las integraciones existentes.

* Los flujos de trabajo técnicos integrados y su comportamiento siguen siendo el mismo. Solo se han cambiado las API back-end utilizadas por los flujos de trabajo para insertar o extraer datos de Adobe Analytics.

* Tenga en cuenta que el proceso `nlserver` debe configurarse con el usuario de cuenta técnica de IMS para que el nuevo conector funcione. Este cambio debe hacerse por Adobe. Para que esto se implemente, póngase en contacto con [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

* Si era API de Adobe Genesis en flujos de trabajo personalizados para extraer y extraer los datos de Adobe Analytics, ahora debe utilizar las nuevas API de Adobe Analytics 1.4/2.0. [Más información](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360047148832-Replacements-for-Data-Connector-API-calls)

## ¿Se ha visto afectado?

Si utiliza el conector de datos de Adobe Analytics existente (anteriormente conocido como integración de Genesis) y la integración se ha implementado en una versión anterior a Campaign 21.1.3, su impacto se verá afectado.

Aprenda a comprobar su versión [en esta sección](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## ¿Cómo realizar la actualización?

Debe actualizar a Campaign 21.1.3 (o más) **antes del 1 de marzo de 2022**.

Como cliente alojado, el Adobe trabajará con usted para actualizar sus instancias a la versión más reciente.

Como cliente local/híbrido, debe actualizar a una de las versiones más recientes para beneficiarse de la nueva integración.

Una vez actualizadas todas las instancias, podrá [implementar la nueva integración](../platform/using/adobe-analytics-connector.md) en el conector de Adobe Analytics y garantizar una transición sin problemas.


## Preguntas frecuentes

**¿Cómo puedo obtener registros?**

La configuración de la interfaz de usuario y los flujos de trabajo están equipados con el registro **detallado**.

En modo detallado, los encabezados de solicitud y respuesta también se imprimen para cada solicitud de API a Adobe Analytics.

Como usuario local, puede implementar el modo detallado de la siguiente manera:

* Para habilitar el modo detallado para la interfaz de usuario: vuelva a ejecutar el proceso `web` en modo detallado.
* Para habilitar el modo detallado para los flujos de trabajo de **webAnalytics**: seleccione la opción **Execute in the engine** en las propiedades del flujo de trabajo y vuelva a ejecutar `wfserver` en modo detallado.

**Propietario de la integración no administrador**

Obtenga más información sobre el error de Data Connectors &quot;Propietario de la integración no administrador&quot; en [esta página](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360035167932-Adobe-Analytics-Data-Connectors-Integration-Owner-Not-Admin-Error).

**Las evars/eventos/grupos de informes existentes presentes en Analytics no están visibles en Campaign**

La integración depende de los datos del token de cuenta técnica para el funcionamiento diario. Si falta permiso para acceder a un grupo de informes/dimensiones desde el perfil de producto asociado con el usuario de cuenta técnica, las API que usemos simplemente fallarán para esas solicitudes.

Si leemos los detalles de un componente de Analytics (como métricas, dimensiones, segmentos o grupos de informes), la API no devolverá estos componentes en el resultado (que pueden parecer que algo se ha eliminado en Analytics o no está presente). La API de Analytics rechazará esas solicitudes y se eliminarán los errores.

La solución es actualizar el perfil de producto en el contexto de usuario de Analytics del token de usuario técnico con los componentes recién creados o que faltan añadiendo estos componentes en [Adobe Admin Console](https://adminconsole.adobe.com/).

## Vínculos útiles

* [Actualice su entorno](../production/using/build-upgrade.md)
* [Preguntas frecuentes sobre la actualización de versiones](../platform/using/faq-build-upgrade.md)
* [Descargar compilación del Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [Poner la nueva consola de cliente a disposición de los usuarios](../installation/using/client-console-availability-for-windows.md)
* [Instalación de la consola del cliente de Campaign](../installation/using/installing-the-client-console.md)
