---
title: Actualizaciones de documentación de Adobe Campaign Classic
description: Esta página enumera todas las nuevas funciones y actualizaciones de documentación de cada versión de Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 70efc8a7f1fab68d73e36b4373116c4aaaa0af5d
workflow-type: tm+mt
source-wordcount: '7164'
ht-degree: 97%

---


# Actualizaciones de documentación{#documentation-updates}

Esta página enumera todas las nuevas funciones y actualizaciones de la documentación por mes y por versión de Campaign.

También puede consultar las [Notas de la versión de Adobe Campaign Classic](../../rn/using/latest-release.md) para ver más actualizaciones.

## Agosto de 2020 {#aug-2020}

Conozca las prácticas recomendadas relacionadas con el diseño de envíos y el envío con Campaña en una sección dedicada. [Más información](../../delivery/using/delivery-best-practices.md)

Se ha mejorado la página de aterrizaje de prácticas recomendadas sobre la capacidad de ejecución para facilitar el acceso a las subsecciones. [Más información](../../delivery/using/deliverability-key-points.md)

Los vídeos de procedimientos ya están disponibles en los siguientes temas:

* [Cómo configurar la gestión de la fatiga mediante reglas de tipología y filtros predefinidos](../../campaign/using/about-campaign-typologies.md)

* [Cómo crear un correo electrónico en una campaña](../../campaign/using/marketing-campaign-deliveries.md)

* [Cómo crear una newsletter multilingüe con contenido condicional](../../delivery/using/conditional-content.md)

* [Cómo configurar e implementar una Plantilla de envíos](../../delivery/using/creating-a-delivery-template.md)

* [Cómo activar y utilizar AMP para correos electrónicos](../../delivery/using/defining-interactive-content.md)

* [Cómo personalizar correos electrónicos con bloques de contenido dinámico](../../delivery/using/personalization-blocks.md)

* [Cómo personalizar correos electrónicos mediante campos de personalización](../../delivery/using/personalization-fields.md)

* [Cómo administrar semillas y pruebas en un correo electrónico](../../delivery/using/steps-defining-the-target-population.md)

* [Cómo configurar un envío recurrente](../../workflow/using/recurring-delivery.md)

* [Cómo configurar un envío continuo](../../workflow/using/continuous-delivery.md)

Se ha añadido información sobre las comprobaciones y acciones que se deben realizar al obtener el error &quot;No se pudo resolver el nombre de host&quot; después de conectarse a un servidor FTP. [Más información](../../platform/using/sftp-server-usage.md)

Se ha hecho referencia a nuevos casos de uso en la lista de casos [de uso del](../../workflow/using/about-workflow-use-cases.md)flujo de trabajo:

* Automatización de la creación, edición y publicación de contenido
* Configuración de un proceso de aprobación de destinatarios antes de enviar un envío
* Llamada a una variable de instancia en una consulta
* Aplicación de un porcentaje dividido a una población

La sección de **[!UICONTROL AND-join]** actividad se ha enriquecido con información adicional sobre su uso, así como con una nota sobre el uso de variables. [Más información](../../workflow/using/and-join.md)

## Julio de 2020 {#july-2020}

Se ha añadido un caso de uso sobre cómo actualizar automáticamente una lista mediante una consulta incremental de los casos de uso del flujo de trabajo. [Más información](../../workflow/using/about-workflow-use-cases.md)

Las [notas de la versión](../../rn/using/latest-release.md) se han reorganizado: se ha añadido una [página de información general](../../rn/using/latest-release.md) con información sobre los estados de las versiones, el proceso de actualización, las recomendaciones y los vínculos importantes. También se ha añadido una página dedicada a las [versiones de Gold Standard](../../rn/using/gold-standard.md) y se ha integrado la [matriz de compatibilidad](../../rn/using/compatibility-matrix.md).

Se ha añadido una nueva sección con directrices relacionadas con la supervisión de Campaign Classic. [Más información](../../production/using/monitoring-guidelines.md)

La sección Privacidad y consentimiento se ha mejorado con información más detallada y vínculos útiles. [Más información](../../platform/using/privacy-and-recommendations.md).

La página Administración de privacidad en Campaign Classic se ha actualizado con información sobre el campo &quot;Regulación&quot;, que ahora está disponible al utilizar la API y permite configurar el proceso de solicitud de privacidad automática. [Más información](https://helpx.adobe.com/es/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)

Se ha actualizado la página Información general sobre administración de privacidad para incluir información sobre la Ley de Protección de Datos Personales de Tailandia (PDPA) y el Lei Geral de Proteção de Dados (LGPD) de Brasil. [Más información](https://helpx.adobe.com/es/campaign/kb/campaign-privacy-overview.html#whatisgdpr)

Se ha añadido información sobre los registros de subflujos de trabajo y el comportamiento en caso de error. [Más información](../../workflow/using/sub-workflow.md)

Se han añadido las prácticas recomendadas en la **[!UICONTROL Scheduler]** sección actividad. [Más información](../../workflow/using/scheduler.md)

## Junio de 2020 {#june-2020}

Se ha actualizado la sección Eliminación de una dirección en cuarentena. Esto incluye la aclaración de los casos en que las direcciones se quitan automáticamente de la lista de cuarentena. [Más información](../../delivery/using/understanding-quarantine-management.md#removing-a-quarantined-address)

Se han agregado casos de uso sobre cómo [cifrar](../../workflow/using/how-to-use-workflow-data.md#use-case-gpg-encrypt) y [descifrar](../../workflow/using/importing-data.md#use-case-gpg-decrypt) datos mediante el Panel de control de Campaign y los Flujos de trabajo de la campaña.

Tanto los términos &quot;lista blanca&quot; como &quot;lista negra&quot; se han eliminado de la documentación de Adobe Campaign. Podría seguir habiendo algunos casos en los que aparezcan estos términos en la interfaz de usuario del producto, los nombres de opciones y el código interno, pero se reemplazarán en próximas versiones de Campaign con &quot;lista de bloqueados&quot; y &quot;lista de permitidos&quot;.

La página de integración de Experience Cloud Triggers y Adobe Campaign Classic se ha movido [aquí](../../integrations/using/about-triggers.md).

## 20.2 - 08/06/2020{#release-20-2}

**Nuevas funciones incluidas en la versión**

Compatibilidad con emoticonos: [Más información](../../delivery/using/customizing-emoticon-list.md)

Conector de FDA de Azure Synapse: [Más información](../../platform/using/specific-configuration-database.md#configure-access-to-azure-synapse)

Leyes de privacidad de Tailandia y Brasil: [Más información](https://helpx.adobe.com/es/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)

**Otras actualizaciones de la documentación incluidas en la versión**

La nueva opción que permite cancelar la publicación de una plantilla de mensaje transaccional se documenta en
[esta sección](../../message-center/using/template-unpublication.md).

Se han añadido a la lista de opciones de Campaign Classic las nuevas opciones que permiten establecer limitaciones al enviar correos electrónicos que incluyen imágenes descargadas de una URL personalizada y archivos adjuntos. [Más información](../../installation/using/configuring-campaign-options.md#delivery)

La nueva opción **Preparar las piezas de envío en la base de datos** está documentada en [esta sección](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis).

Se ha aclarado y actualizado la sección Validación del envío. [Más información](../../delivery/using/steps-validating-the-delivery.md)

Se han añadido a la sección [Archivo de configuración del servidor](../../installation/using/the-server-configuration-file.md) los parámetros relacionados con el nuevo mecanismo de firma de enlace de seguimiento.

Se ha actualizado la matriz de compatibilidad. [Más información](https://helpx.adobe.com/es/campaign/kb/compatibility-matrix.html)

Se ha actualizado la sección de flujos de trabajo para la limpieza. [Más información](../../production/using/database-cleanup-workflow.md)

Los extremos de la red de Campaign se han movido a esta [sección](../../installation/using/campaign-network-endpoints.md).

La sección de instalación de Spam Assassin se ha actualizado con el nuevo nombre de archivo de instalación. [Más información](../../installation/using/configuring-spamassassin.md#installing-spamassassin)

Se ha actualizado la sección sobre la duplicación de entornos. [Más información](../../production/using/duplicating-environments.md#step-2---export-the-target-environment-configuration--dev-)

## Mayo 2020 {#may-2020}

Se ha movido y mejorado la sección Monitorización de la capacidad de envío. [Más información](../../delivery/using/monitoring-deliverability.md)

Se ha movido y mejorado la sección de Solución de problemas de la capacidad de envío. [Más información](../../delivery/using/deliverability-faq.md)

Se han mejorado las directrices de capacidad de envío al iniciar una nueva sección de plataforma. [Más información](../../delivery/using/starting-new-platform.md)

Se ha movido y actualizado la sección Envío de correos electrónicos transaccionales con archivos adjuntos. [Más información](../../message-center/using/transactional-email-with-attachments.md)

Se ha movido y actualizado la sección Prácticas recomendadas del paquete de datos. [Más información](../../platform/using/working-with-data-packages.md#data-package-best-practices)

## de abril de 2020 {#april-2020}

La tabla de derechos de FDA se ha movido a la documentación de Acceso a una base de datos externa (FDA). [Más información](../../platform/using/remote-database-access-rights.md)

Las preguntas frecuentes se han actualizado con sugerencias sobre cómo borrar la caché en blanco y en disco. [Más información](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear)

Se ha mejorado la sección Prácticas recomendadas del modelo de datos con información adicional sobre índices. [Más información](../../configuration/using/data-model-best-practices.md#indexes)

La sección que describe el modelo de datos integrado de Adobe Campaign se ha actualizado con más detalles en cada tabla. [Más información](../../configuration/using/data-model-description.md)

Los casos de uso del flujo de trabajo se han actualizado y reorganizado en secciones temáticas. [Más información](../../workflow/using/about-workflow-use-cases.md)

Las secciones de [Certificación de correo rechazado ](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification) y [reglas de administración de correo electrónico](../../delivery/using/understanding-delivery-failures.md#email-management-rules) se han mejorado con información actualizada.

Se ha actualizado el artículo de MTA mejorado de Adobe Campaign. Ahora solo se aplica a Campaign Classic. [Más información](https://helpx.adobe.com/es/campaign/kb/acc-campaign-enhanced-mta.html)

## Marzo de 2020 {#march-2020}

La página de prácticas recomendadas del modelo de datos se ha actualizado con nuevas secciones que incluyen [Secuencias](../../configuration/using/data-model-best-practices.md#sequences), [Rendimiento](../../configuration/using/data-model-best-practices.md#performance) y [Tablas grandes](../../configuration/using/data-model-best-practices.md#large-tables), entre otras. [Más información](../../configuration/using/data-model-best-practices.md)

Ahora está disponible una nueva sección que describe el modelo de datos incorporado de Adobe Campaign y la interacción entre tablas. [Más información](../../configuration/using/data-model-description.md)

Se han añadido enlaces clave a la página principal de documentación. [Más información](../../campaign-classic-home.md)

Se ha añadido un caso de uso sobre cómo integrar una oferta dinámica de Adobe Target en un correo electrónico en Adobe Campaign. [Más información](../../integrations/using/inserting-a-dynamic-image.md)

Ya está disponible una nueva sección que detalla los distintos idiomas disponibles en Adobe Campaign. [Más información](../../platform/using/adobe-campaign-workspace.md#languages)

Se ha actualizado las Directrices de gestión de acceso con más información sobre Derechos asignados. [Más información](../../platform/using/access-management.md#named-rights)

## Febrero de 2020 {#february-2020}

Ya está disponible una nueva sección en la que se describen las prácticas recomendadas y las recomendaciones clave al diseñar el modelo de datos de Adobe Campaign. [Más información](../../configuration/using/data-model-best-practices.md)

Hay disponible una nueva sección sobre las configuraciones técnicas de correo electrónico. [Más información](../../installation/using/email-deliverability.md)

El documento de preguntas frecuentes sobre la capacidad de envío se ha actualizado con más detalles sobre el mensaje de error “cuotas satisfechas”. [Más información](https://helpx.adobe.com/es/campaign/kb/acc-deliverability-faq.html#FAQ)

Los nuevos proveedores de correo electrónico ahora admiten AMP para correo electrónico: se ha actualizado la documentación relacionada. [Más información](../../delivery/using/defining-interactive-content.md)

Se ha mejorado la sección de archivado de correo electrónico. [Más información](../../installation/using/email-archiving.md#recommendations-and-limitations)

## 20.1 - 17/02/2020{#release-20-1}

**Nuevas funciones incluidas en la versión**

Conector de FDA de Snowflake: [Más información](../../platform/using/specific-configuration-database.md#configure-access-to-snowflake)

Mejora del conector FDA de Hadoop: [Más información](../../platform/using/specific-configuration-database.md#configure-access-to-hadoop-3)

**Otras actualizaciones de la documentación incluidas en la versión**

Las guías de [instalación](../../installation/using/before-reading.md), [producción](../../production/using/foreword.md) y [configuración](../../configuration/using/additional-parameters.md) se han actualizado con la nueva unidad del sistema utilizada por el inicio del servicio nlserver. Puede seguir utilizando /etc/init.d/nlserver6, pero le recomendamos que ahora utilice el comando systemctl para interactuar con el servicio nlserver.

La guía de instalación se ha actualizado y sincronizado con la última versión de la matriz de compatibilidad. Se han agregado nuevos sistemas admitidos. Se han eliminado las ocurrencias a sistemas obsoletos y no admitidos. [Más información](../../installation/using/before-reading.md)

La matriz de compatibilidad se ha actualizado con los conectores Hadoop 3.0 y Snowflake FDA. [Más información](https://helpx.adobe.com/es/campaign/kb/compatibility-matrix.html)

Se ha añadido una práctica recomendada sobre la afinidad de IP a la guía de instalación. [Más información](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

Se ha actualizado la sección Flujos de trabajo para la limpieza de base de datos. Las cifras por lotes proporcionadas ahora reflejan la implementación del código. [Más información](../../production/using/database-cleanup-workflow.md)

Se ha añadido una limitación de FDA sobre HTTP a la guía de mensajería transaccional. [Más información](../../production/using/database-cleanup-workflow.md)

Se ha añadido información sobre la nueva opción que le permite definir un período de tiempo de espera para las actividades de flujo de trabajo **[!UICONTROL JavaScript code]** y **[!UICONTROL Advanced JavaScript code]**. [Más información](../../workflow/using/sql-code-and-javascript-code.md)

Se ha añadido información sobre la nueva vista **[!UICONTROL Start Pending]** disponible en el nodo **[!UICONTROL Administration]** > **[!UICONTROL Audit]** > **[!UICONTROL Workflows Status]**. [Más información](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

La guía [Envío de notificaciones push](../../delivery/using/about-mobile-app-channel.md) se ha movido, reorganizado y mejorado con información aclarada.

El nuevo parámetro para la configuración de informes de direcciones URL se ha documentado [aquí](../../reporting/using/properties-of-the-report.md#defining-additional-settings).

La página **matriz de funciones locales y alojadas de Campaign Classic** se ha actualizado con los nuevos conectores de FDA. [Más información](https://helpx.adobe.com/es/campaign/kb/acc-on-prem-vs-hosted.html)

Se ha actualizado la página **matriz de funciones de Campaign Classic**. [Más información](https://helpx.adobe.com/es/campaign/kb/compatibility-matrix.html)

El nuevo flujo de trabajo **[!UICONTROL Cleanup of Nmsaddress]** se ha documentado [aquí](../../production/using/database-cleanup-workflow.md#cleanup-of-nmsaddress).

Se ha añadido una limitación al usar una actividad de consulta en un flujo de trabajo. [Más información](../../workflow/using/query.md).

Se ha añadido una nueva sección para detallar las reglas de validación de direcciones de correo electrónico mejoradas a fin de enviar una dirección a cuarentena en caso de error leve. [Más información](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

Está documentado el parámetro del archivo de configuración que indica si una instancia está utilizando el MTA mejorado o no. [Más información](../../installation/using/the-server-configuration-file.md#mta)

## Enero de 2020 {#january-2020}

La sección Capacidad de entrega se ha movido, reorganizado y mejorado con contenido actualizado. [Más información](../../delivery/using/about-deliverability.md)

Ya está disponible una nueva sección que describe los conceptos básicos del modelo de datos de Adobe Campaign Classic y cómo acceder a la descripción de cada tabla. [Más información](../../configuration/using/about-data-model.md)

El artículo de MTA mejorado de Adobe Campaign se ha actualizado con información más detallada sobre la instalación de un paquete de tipología específico en instancias que no agregan los encabezados de MTA mejorados necesarios a cada mensaje. [Más información](https://helpx.adobe.com/es/campaign/kb/acc-campaign-enhanced-mta.html#impacts)

Los casos de uso relacionados con el diseño de consultas se han reorganizado en secciones independientes. [Más información](../../workflow/using/querying-recipient-table.md)

Ya hay disponible una nueva sección sobre sugerencias y trucos para administrar ofertas y utilizar el módulo Interacción en Adobe Campaign Classic. [Más información](../../interaction/using/interaction-best-practices.md#tips-managing-offers)

La documentación de Interacción se ha enriquecido con enlaces a varios vídeos que ayudan a comprender mejor cómo administrar las ofertas. [Más información](../../interaction/using/interaction-and-offer-management.md)

El artículo de prácticas recomendadas sobre cómo optimizar las consultas que se ejecutan en la instancia se ha integrado en la documentación. [Más información](../../workflow/using/query.md#optimizing-queries)

La guía de informes se ha actualizado y reorganizado. [Más información](../../reporting/using/about-adobe-campaign-reporting-tools.md)

Se ha añadido un ejemplo de cómo utilizar una variable de instancia en un flujo de trabajo. [Más información](../../workflow/using/javascript-scripts-and-templates.md)

## Diciembre de 2019 {#december-2019}

La opción &quot;WdbcOptions_TempDbName&quot; se ha agregado a la lista de opciones de Campaign. [Más información](../../installation/using/configuring-campaign-options.md)

La página matriz de la FDA se ha movido [aquí](../../platform/using/remote-database-access-rights.md).

La página matriz de derechos de acceso se ha movido [aquí](https://docs.adobe.com/content/help/es-ES/campaign-classic/using/getting-started/administration-basics/assets/accessrights.pdf).

Se ha movido la sección que describe cómo definir contenido interactivo con AMP. [Más información](../../delivery/using/defining-interactive-content.md)

## 19.2 - 02/12/2019{#release-19-2}

**Nuevas funciones incluidas en la versión**

California Consumer Privacy Act (CCPA): [Más información](https://helpx.adobe.com/es/campaign/kb/acc-privacy.html)

Contenido interactivo con AMP: [Más información](../../delivery/using/defining-interactive-content.md)

Monitoreo en vivo de flujos de trabajo: [Más información](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

Mensajería SMS segura (TLS): [Más información](https://helpx.adobe.com/es/campaign/kb/sms-connector-protocol-and-settings.html)

**Otras actualizaciones de la documentación incluidas en la versión**

Ya está disponible la documentación de MTA mejorada de Adobe Campaign. [Más información](https://helpx.adobe.com/es/campaign/kb/acc-campaign-enhanced-mta.html)

Se ha añadido una nueva sección sobre cómo solucionar problemas de un flujo de trabajo que permanece en el estado &quot;Iniciar lo antes posible&quot; dentro de una campaña. [Más información](../../production/using/workflow-execution.md#start-as-soon-as-possible-in-campaigns)

Las nuevas opciones &quot;NmsOperation_DeliveryPreparationWindow&quot; y &quot;WdbcKillSessionPolicy&quot; se han agregado a la lista de opciones de Campaign. [Más información](../../installation/using/configuring-campaign-options.md)

Ya está disponible un nuevo documento que describe los conceptos básicos del modelo de datos de Adobe Campaign Classic. [Más información](https://helpx.adobe.com/es/campaign/kb/acc-datamodel.html)

La nueva opción **Maximum personalization run time** en las propiedades de entrega se documenta en esta [sección](../../delivery/using/personalization-fields.md#timing-out-personalization).

Se han actualizado los ejemplos de llamadas de API que usan un **HttpServletRequest** con logon() y query(). [Más información](../../configuration/using/web-service-calls.md).

Se ha agregado una recomendación para el atributo **sqlDefault** en la definición del esquema. [Más información](../../configuration/using/elements-and-attributes.md#attribute-description).

Ahora se hace referencia a la integración entre Adobe Campaign y Adobe Real-time Customer Data Platform en la guía **Integración con Adobe Experience Cloud**. [Más información](../../integrations/using/about-campaign-integrations.md).

## Noviembre de 2019 {#november-2019}

Se ha agregado una advertencia a las secciones [Multiplexing the mid-sourcing server](../../installation/using/mid-sourcing-server.md#multiplexing-the-mid-sourcing-server) y [Supporting several control instances](../../message-center/using/transactional-messaging-architecture.md#supporting-several-control-instances) que mencionan que estas implementaciones no son compatibles con clientes totalmente alojados e híbridos.

Se ha añadido una nueva sección para describir cómo forzar la codificación de caracteres utilizada al enviar un correo electrónico. [Más información](../../delivery/using/sending-messages.md#character-encoding)

La sección Administración de acceso se ha actualizado con el **Derecho de datos de privacidad**. [Más información](../../platform/using/access-management.md#named-rights)

Se agregó información para especificar que el contenido de los campos de personalización no puede exceder los 1024 caracteres. [Más información](../../delivery/using/personalization-fields.md)

La documentación del Panel de control se ha integrado en el nuevo conjunto de documentos de colaboración. [Más información](https://docs.adobe.com/content/help/es-ES/control-panel/using/control-panel-home.html)

Se ha actualizado la guía de introducción a las prácticas recomendadas de entrega. [Más información](../../delivery/using/delivery-best-practices.md)

## Octubre de 2019 {#october-2019}

Se ha actualizado la lista de mensajes de error para Campaign Standard y Campaign Classic. [Más información](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

La guía de introducción al RGPD se ha mejorado y enriquecido. Ahora es una documentación de administración de la privacidad que incluye el RGPD y la CCPA. [Más información](https://helpx.adobe.com/content/help/es/campaign/kb/campaign-privacy.html)

Se ha agregado una nueva página de solución de problemas para el seguimiento en Campaign Classic. [Más información](https://helpx.adobe.com/es/campaign/kb/classic-tracking-troubleshooting.html).

Se ha añadido una nueva página de prácticas recomendadas para el conector de datos de Adobe Analytics. [Más información sobre el conector de datos de Adobe Analytics](../../platform/using/adobe-analytics-data-connector.md)

La guía de introducción a las prácticas recomendadas de entrega se ha movido y actualizado. [Más información](../../delivery/using/delivery-best-practices.md)

Se ha agregado una recomendación a la documentación del canal SMS para evitar problemas al utilizar varias cuentas externas que aprovechan el conector SMPP genérico ampliado con la misma cuenta de proveedor. [Más información](../../delivery/using/sms-channel.md#automatic-reply)

Se agregó información en la documentación de actividad del Planificador sobre cómo evitar la ejecución simultánea de un flujo de trabajo. [Más información](../../workflow/using/scheduler.md)

Se han añadido a la documentación los pasos para configurar el procesamiento de la Bandeja de entrada para las instalaciones locales. [Más información](../../delivery/using/inbox-rendering.md#activating-inbox-rendering)

## Septiembre de 2019 {#september-2019}

Se ha agregado una nueva página para proporcionar directrices generales para mantener Campaign Classic. [Más información](../../production/using/monitoring-guidelines.md)

La información relacionada con la monitorización de flujos de trabajo se ha centralizado en una nueva sección dedicada. [Más información](../../workflow/using/monitoring-workflow-execution.md).

Se ha añadido una nueva página sobre las directrices generales para el seguimiento en Adobe Campaign Classic. [Más información](https://helpx.adobe.com/es/campaign/kb/acc-tracking.html).

Se han actualizado las prácticas recomendadas para mejorar el rendimiento de los flujos de trabajo y las entregas. [Obtenga más información sobre los flujos de trabajo](../../workflow/using/workflow-best-practices.md) y [más sobre las entregas](../../delivery/using/monitoring-a-delivery.md#best-practices-performance).

## 19.1 - 30/05/2019{#release-19-1}

**Nuevas funciones incluidas en la versión**

Panel de control: [Más información](https://docs.adobe.com/content/help/es-ES/control-panel/using/control-panel-home.html)

Pista de auditoría: [Más información](../../production/using/audit-trail.md)

**Otras actualizaciones de la documentación incluidas en la versión**

Se ha creado una nueva pregunta frecuente sobre la actualización de la compilación. [Más información](https://helpx.adobe.com/es/campaign/kb/build-upgrade-faq.html)

Se ha actualizado la [matriz de compatibilidad](https://helpx.adobe.com/es/campaign/kb/compatibility-matrix.html). Se ha actualizado la lista de sistemas de base de datos admitidos, así como las versiones de Android/iOS y los SDK relacionados. Se ha archivado la [matriz de compatibilidad 19.0](https://helpx.adobe.com/es/campaign/kb/compatibility-matrix-19-0.html).

Se ha actualizado la página “Funciones obsoletas y eliminadas en Campaign Classic”. [Más información](https://helpx.adobe.com/es/campaign/kb/deprecated-and-removed-features.html)

La descripción del archivo de configuración del servidor se ha agregado a la guía Instalación. [Más información](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_The_server_configuration_file.html)

Se ha añadido una sección que describe los pasos de instalación y configuración para los modelos alojados e híbridos. [Más información](https://docs.campaign.adobe.com/doc/AC/en/INS_Hybrid_and_Hosted_models_Introduction.html)

Se ha agregado una sección que describe los pasos de desinstalación del servidor Campaign. [Más información](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Uninstalling_Campaign.html)

Se han actualizado las guías de introducción a la [seguridad](https://helpx.adobe.com/es/campaign/kb/acc-security.html), la [capacidad de envío](https://docs.adobe.com/content/help/es-ES/campaign-classic/using/sending-messages/deliverability-management/about-deliverability.html) y la [privacidad](https://helpx.adobe.com/es/campaign/kb/acc-privacy.html).

La descripción de la opción de flujo de trabajo previo al proceso se ha actualizado para reflejar los cambios del producto. [Más información](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#Data_loading__file_)

Se ha actualizado la nota técnica Marketing Cloud Triggers. [Más información](https://helpx.adobe.com/es/campaign/kb/triggers-and-campaign.html)

Se ha actualizado la lista de mensajes de error. [Más información](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Se ha agregado más información sobre los métodos de autenticación SOAP para la mensajería transaccional. [Más información](https://docs.campaign.adobe.com/doc/AC/en/MCE_Introduction_Event_description.html)

Se han actualizado los pasos de configuración de Apache. [Más información](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Linux__Integration_into_a_Web_server.html#Configuring_Apache_web_server_in_RHEL)

Se ha agregado una nueva página que incluye la lista de puntos finales de Campaign Standard y Classic. [Más información](https://helpx.adobe.com/es/campaign/kb/campaign-endpoints.html)

Se ha actualizado el artículo Prácticas recomendadas del paquete de datos. [Más información](https://helpx.adobe.com/es/campaign/kb/data-package-best-practices.html)

La documentación de Administración de ofertas se ha actualizado con una nueva sección que enumera las prácticas recomendadas. [Más información](https://docs.campaign.adobe.com/doc/AC/en/ITA_Interaction_Overview_Interaction_best_practices.html)

Se ha creado un nuevo artículo de la base de conocimiento sobre el uso del catálogo de ofertas en Adobe Campaign Classic. [Más información](https://helpx.adobe.com/es/campaign/kb/offer-best-practices.html)

La sección de actividad de subflujo de trabajo se ha mejorado con un ejemplo de uso. [Más información](../../workflow/using/sub-workflow.md)

El artículo de la base de conocimiento de la [matriz de capacidades alojadas y locales de Campaign Classic](https://helpx.adobe.com/es/campaign/kb/acc-on-prem-vs-hosted.html) se ha actualizado con información relacionada con el archivado de correos electrónicos.

La documentación de Mensajería transaccional se ha actualizado con una nota relativa a la publicación de plantillas. [Más información](https://docs.campaign.adobe.com/doc/AC/en/MCE_Template_publication.html)

La sección Correos de devolución sin procesar se ha actualizado con más detalles sobre los campos Dirección de reenvío y Dirección para los errores. [Más información](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Deploying_an_instance.html#Unprocessed_bounce_mails)

Se ha añadido una nueva sección sobre las prácticas recomendadas de planificación del flujo de trabajo. [Más información](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Workflow_best_practices.html#Execution_and_performance)

Se agregaron dos nuevas opciones a la lista de opciones de Campaign: XtkSecurity_Restrict_EditXML y NmsOperation_OperationMgtDebug.
[Más información](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Configuring_Campaign_options.html)

Se ha añadido información sobre las distintas cuentas externas disponibles en Campaign Classic y sobre cómo configurarlas.
[Más información](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_External_accounts.html)

Se ha actualizado la sección Conector de datos de Analytics para reflejar los cambios de la interfaz.
[Más información](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Adobe_Analytics_Data_Connector.html)

Se agregó información sobre el informe Facturación.
[Más información](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#Billing_report)

Se ha actualizado la documentación sobre la integración de audiencias compartidas.
[Más información](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Configuring_shared_audiences_integration_in_Adobe_Campaign.html)

Se han actualizado las siguientes notas técnicas: [protocolo de conector SMS y configuración](https://helpx.adobe.com/es/campaign/kb/sms-connector-protocol-and-settings.html) y [generación automática de secuencia](https://helpx.adobe.com/es/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence).

Se ha actualizado la sección Flujos de trabajo técnicos. [Más información](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_About_technical_workflows.html)

Se ha mejorado y actualizado el procedimiento de configuración del nombre de dominio de Campaign. [Más información](https://helpx.adobe.com/es/campaign/kb/domain-name-delegation.html)

Se ha actualizado el procedimiento de migración de aplicaciones de Android de Google Cloud Messaging (GCM) a Firebase Cloud Messaging (FCM). [Más información](https://helpx.adobe.com/es/campaign/kb/migrate-to-fcm.html)

Se ha actualizado la Guía de cambio de tamaño de hardware de Campaign. [Más información](https://helpx.adobe.com/es/campaign/kb/hardware-sizing-guide.html)

Se agregó información sobre la Banda de consultas para la cuenta externa de Teradata. [Más información](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_External_accounts.html#External_database_external_account)

## Enero de 2019 {#release-doc-16-01-2019}

Se ha actualizado la nota técnica Marketing Cloud Triggers. [Más información](https://helpx.adobe.com/es/campaign/kb/triggers-and-campaign.html)

Se agregó una nota en la sección de aprobación de ofertas para especificar que la mención “Contenido aprobado” indica que se ha logrado el proceso de aprobación de contenido, independientemente de si todas las ofertas se han habilitado/aprobado o no. [Más información](https://docs.campaign.adobe.com/doc/AC/en/ITA_Managing_an_offer_catalog_Approving_and_activating_an_offer.html#Approving_offer_content)

Se agregó una nueva sección en la guía Instalación, que enumera las opciones del nodo Administración / Plataforma / Opciones. [Más información](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Configuring_Campaign_options.html)

Se ha añadido información sobre el uso de las direcciones semilla para proteger la lista de correo. [Más información](https://docs.campaign.adobe.com/doc/AC/en/DLV_Using_seed_addresses_About_seed_addresses.html)

Los pasos clave al crear y enviar una entrega se han reagrupado en una nueva sección, con referencias a los distintos canales cuando es necesario. [Más información](../../delivery/using/steps-about-delivery-creation-steps.md)

La sección [Email archiving](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html) se ha movido, reorganizado y mejorado con información aclarada:

* Se han agregado prácticas recomendadas con respecto a los correos electrónicos por conexión y a los parámetros de IP de entrega de CCO. [Más información](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Best_practices)

* Hemos actualizado los pasos para actualizar al nuevo sistema de archivado de correo electrónico (CCO) si ya estaba utilizando el archivado de correo electrónico con una versión anterior (anterior a Adobe Campaign 17.2 - compilación 8795). [Más información](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Updated_email_archiving_system__BCC_)

Se ha añadido un caso de uso a la guía Automatización con flujos de trabajo: entrega de alertas personalizadas a los operadores. [Más información](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Sending_personalized_alerts_to_operators.html)

Se ha actualizado la sección “Migración a una nueva versión”. La documentación ahora solo detalla los pasos para una migración a Adobe Campaign Classic v7 desde cualquier versión anterior, ya que ya no es posible migrar a Adobe Campaign v6.11. [Más información](https://docs.campaign.adobe.com/doc/AC/en/MIG_Migration_overview_About_migration.html)

Se ha aclarado la sección “Reintentos después de un error temporal de entrega”. [Más información](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_delivery_failures.html#Retries_after_a_delivery_temporary_failure)

Se han agregado enlaces a la sección “Editor de contenido digital” a la sección “Definición del contenido del correo electrónico”. [Más información](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Defining_the_email_content.html#Message_content)

La sección “Arquitectura de mensajería transaccional” se ha actualizado con una advertencia que especifica que las instancias de control y ejecución no se pueden instalar en el mismo equipo. [Más información](https://docs.campaign.adobe.com/doc/AC/en/MCE_Introduction_Transactional_messaging_architecture.html)

La sección “Supervisión del flujo de trabajo” se ha actualizado con una nota para compilaciones entre 8700 y 8977 (18.10), que incluye un enlace a la nota técnica sobre cómo instalar el paquete de workflow HeatMap para estas compilaciones. [Más información](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#About_the_Workflow_HeatMap)

Se ha añadido un caso de uso sobre cómo enviar un correo electrónico con campos de datos personalizados mediante la actividad Enriquecimiento en un flujo de trabajo. [Más información](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Email_enrichment_with_custom_date_fields.html)

Los vídeos de funciones se han movido [aquí](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/overview.html).

Se han añadido dos notas técnicas en [Teradata](https://helpx.adobe.com/es/campaign/kb/campaign_fda_teradata.html) y [MySQL 5.7](https://helpx.adobe.com/es/campaign/kb/campaign_fda_mysql.html).

## 18.10 - 05/11/2018{#release-18-10}

**Nuevas funciones incluidas en la versión**

Mejoras en las notificaciones push: [Más información](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Integrating_the_SDK_into_the_mobile_application)

Actividad de administración de datos SQL: [Más información](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#SQL_Data_Management)

Monitoreo de flujo de trabajo: [Más información](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#Workflow_monitoring)

**Otras actualizaciones de la documentación incluidas en la versión**

Las API de Campaign Classic están ahora disponibles en una [página dedicada](https://docs.campaign.adobe.com/doc/AC/en/jsapi/index.html). Si utilizó el archivo jsapi.chm, debería consultar la nueva versión en línea.

Se ha actualizado la matriz de compatibilidad. [Más información](https://helpx.adobe.com/es/campaign/kb/compatibility-matrix.html)

Se ha actualizado la página “Funciones obsoletas y eliminadas en Campaign Classic”. [Más información](https://helpx.adobe.com/es/campaign/kb/deprecated-and-removed-features.html)

En las [notas de la versión](https://docs.adobe.com/content/help/es-ES/campaign-classic/using/release-notes/latest-release.translate.html) y las [notas de la versión heredadas](https://docs.campaign.adobe.com/doc/AC/en/RN_legacy.html), se ha añadido una advertencia para las compilaciones que se han recuperado. También se han añadido compilaciones acumulativas para 17.9, 18.4 y 18.6.

Se han actualizado las guías de introducción a la [seguridad](https://helpx.adobe.com/es/campaign/kb/acc-security.html), [capacidad de entrega](https://docs.adobe.com/content/help/es-ES/campaign-classic/using/sending-messages/deliverability-management/about-deliverability.html) y [actualización de compilación](https://helpx.adobe.com/es/campaign/kb/acc-build-upgrade.html).

La guía de introducción a la [privacidad](https://helpx.adobe.com/es/campaign/kb/acc-privacy.html) se ha actualizado con información sobre cómo invocar la API externamente y cómo utilizar queryDef para consultar el estado y descargar el archivo RGPD.

Se ha añadido un caso de uso de mensajería transaccional para añadir archivos adjuntos de los correos electrónicos sobre la marcha a las entregas salientes. [Más información](https://docs.campaign.adobe.com/doc/AC/en/MCE_Use_case_Purpose.html)

Se ha actualizado la sección de solución de problemas de umbrales de conexión. [Más información](https://docs.campaign.adobe.com/doc/AC/en/PRO_Troubleshooting_Connection_thresholds.html)

Se ha agregado una sección sobre cómo configurar una conexión proxy. [Más información](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Proxy_connection_configuration)

Se ha actualizado la sección sobre la restricción de comandos externos autorizados. [Más información](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Restricting_authorized_external_commands)

Se ha añadido una sección de solución de problemas relacionada con el uso de SFTP. [Más información](https://docs.campaign.adobe.com/doc/AC/en/PTF_Importing_and_exporting_data_SFTP_server_usage.html)

Se reorganizó la sección de información general de la guía de entrega de mensajes. Se agregó información sobre el proceso global de creación de entregas y los diferentes tipos de entregas. [Más información](https://docs.campaign.adobe.com/doc/AC/en/DLV_About_deliveries_and_channels_Communication_channels.html)

Se ha actualizado la lista de mensajes de error. [Más información](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Se ha movido la sección sobre cómo utilizar las direcciones semilla al capítulo de información general de la guía de entrega de mensajes. [Más información](https://docs.campaign.adobe.com/doc/AC/en/DLV_Using_seed_addresses_About_seed_addresses.html)

Se ha añadido un nuevo caso de uso del flujo de trabajo: administración de actualizaciones de las ejecuciones de flujo de trabajo concomitantes. [Más información](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Coordinating_data_updates.html)

La sección &quot;Procesamiento de la bandeja de entrada&quot; se ha actualizado con más información sobre Litmus y un procedimiento más detallado. [Más información](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_Inbox_rendering.html#Multiplexing_the_mid-sourcing_server)

Se ha mejorado la sección &quot;SpamAssassin&quot;. [Más información](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_SpamAssassin.html)

Se ha añadido un caso de uso a la sección &quot;Gestión de la fatiga comercial con reglas de presión&quot;. [Más información](https://docs.campaign.adobe.com/doc/AC/en/CMP_Campaign_Optimization_Pressure_rules.html#Sending_only_the_highest-weighted_messages)

Ya está disponible un nuevo caso de uso que describe cómo crear un flujo de trabajo de entrega multicanal. [Más información](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Cross-channel_delivery_workflow.html)

Se agregaron algunas recomendaciones a la sección &quot;Archivar correos electrónicos&quot;. [Más información](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_deliverability.html#Activating_emails_BCC_archiving)

Se ha agregado una nueva recomendación con respecto a la resolución mínima de pantalla para el uso óptimo de Adobe Campaign. [Más información](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Adobe_Campaign_workspace.html#Screen_resolution)

La guía de integración de Experience Manager se ha actualizado con algunas aclaraciones agregadas a la configuración de esta integración. [Más información](https://docs.campaign.adobe.com/doc/AC/en/ITG_Adobe_Experience_Manager_About_Adobe_Experience_Manager.html)

Se agregó información sobre la diferencia entre la lista de tipos de grupo y la lista de tipos de lista. [Más información](https://docs.campaign.adobe.com/doc/AC/en/PTF_Profile_management_Creating_and_managing_lists.html#About_lists_in_Adobe_Campaign)

Se ha actualizado el código para enviar un extracto de informe como datos adjuntos por correo electrónico. [Más información](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Sending_a_report_to_a_list.html#Step_3-_Creating_the_workflow)

Se añadió un ejemplo sobre cómo crear una consulta para filtrar los destinatarios que no hayan abierto un correo electrónico en los últimos 7 días. [Más información](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Designing_queries.html#Recipients_who_did_not_open_any_delivery)

Se ha actualizado la guía de integración de Compartir audiencias con Adobe Experience Cloud. [Más información](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Sharing_audiences_with_Adobe_Experience_Cloud.html)

La página de ayuda de preguntas comunes ahora contiene información sobre los idiomas disponibles de Campaign, la traducción de formularios web y los correos electrónicos multilingües. [Más información](../../platform/using/common-questions.md)

La diferencia entre las instancias de inglés de EE. UU. e inglés de Reino Unido ahora se enumera en una sección dedicada. [Más información](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Adobe_Campaign_workspace.html#Formats_and_units)

La página de ayuda [Common questions](../../platform/using/common-questions.md) ahora se vincula a la página de mensajes de error.

Se ha añadido información sobre el modo de seguimiento &quot;Abrir&quot;. [Más información](https://docs.campaign.adobe.com/doc/AC/en/DLV_Tracking_messages_Personalizing_URL_tracking.html)

Agregue información sobre la resolución mínima para aplicaciones web y formularios web. [Más información](https://docs.campaign.adobe.com/doc/AC/en/WEB_Web_forms_About_web_forms.html)

La guía de integración de soluciones de Adobe Experience Cloud y Campaign se ha actualizado y reorganizado. [Más información](../../integrations/using/about-campaign-integrations.md)

Se ha agregado una sección sobre el uso de variables de texto en los formularios web. [Más información](https://docs.campaign.adobe.com/doc/AC/en/WEB_Web_forms_Static_elements_in_a_web_form.html#Using_text_variables)

Los modos de seguimiento de URL en los mensajes ya están detallados. [Más información](https://docs.campaign.adobe.com/doc/AC/en/DLV_Tracking_messages_How_to_configure_tracked_links.html)

Se ha reorganizado la sección de creación de instancias. [Más información](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Creating_an_instance_and_logging_on.html)

La entrega de correos electrónicos en móviles japoneses ahora está documentado en una nueva sección. [Más información](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Defining_the_email_content.html#Sending_emails_on_Japanese_mobiles)

La sección “Optimización de la personalización” se ha actualizado con más información. [Más información](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_fields.html#Optimizing_personalization)

## 18.6 - 09/07/2018{#release-18-6}

**Nuevas funciones incluidas en la versión**

Se ha actualizado la matriz de compatibilidad. [Más información](https://helpx.adobe.com/es/campaign/kb/compatibility-matrix.html)

Se ha actualizado la documentación de JSAPI. [Más información](https://support.neolane.net/webApp/extranetLogin)

Se ha actualizado la página Funciones obsoletas y eliminadas. [Más información](https://helpx.adobe.com/es/campaign/kb/deprecated-and-removed-features.html)

**Otras actualizaciones de la documentación incluidas en la versión**

Se ha cambiado el nombre de las guías de usuario de Campaign Classic para simplificar la navegación, mejorar la experiencia del usuario, acceder a la información y a la autoayuda. [Más información](https://docs.campaign.adobe.com/doc/AC/es/browseAC.html)

Se ha actualizado la lista de funciones disponibles en el editor de expresiones. [Más información](https://docs.campaign.adobe.com/doc/AC/en/PTF_Creating_queries_Defining_filter_conditions.html#List_of_functions)

La guía Introducción a la seguridad se ha actualizado con información sobre cómo proteger las páginas que contienen IP. [Más información](https://helpx.adobe.com/es/campaign/kb/acc-security.html)

Se ha actualizado la lista de mensajes de error. [Más información](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Se ha añadido una sección de solución de problemas en la documentación de integración de IMS. [Más información](https://docs.campaign.adobe.com/doc/AC/en/ITG_Connecting_via_an_Adobe_ID_IMS_troubleshooting.html)

Se ha actualizado la guía de introducción a la actualización de compilación. [Más información](https://helpx.adobe.com/es/campaign/kb/acc-build-upgrade.html)

Se ha actualizado la sección de configuración de afinidad IP. [Más información](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Mid-sourcing_server.html#Multiplexing_the_mid-sourcing_server)

Se ha añadido una sección de solución de problemas de funcionamiento y rendimiento. [Más información](https://docs.campaign.adobe.com/doc/AC/en/PRO_Troubleshooting_Performance_and_throughput_issues.html)

La lista de bloques de personalización integrados se ha actualizado con ejemplos. [Más información](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_blocks.html#Out-of-the-box_personalization_blocks)

Se ha actualizado la lista de motivos de error de entrega. [Más información](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_delivery_failures.html#Delivery_failure_types_and_reasons)

Se ha añadido una nueva sección sobre administración de definiciones de paquetes. [Más información](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_Working_with_data_packages.html#Managing_package_definitions)

Se ha mejorado y reorganizado la integración de Campaign con Adobe Analytics: conector de datos. [Más información](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Adobe_Analytics_Data_Connector.html)

Se ha añadido una nueva sección de tutoriales con vínculos a guías paso a paso y vídeos explicativos. [Más información](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Tutorials.html)

Se ha creado una nueva nota técnica sobre el protocolo y la configuración del conector SMS. [Más información](https://helpx.adobe.com/es/campaign/kb/sms-connector-protocol-and-settings.html)

Se ha actualizado la guía de introducción a las prácticas recomendadas de entrega. [Más información](https://helpx.adobe.com/es/campaign/kb/delivery-best-practices.html)

Se ha actualizado la configuración de cuenta de Microsoft Dynamics 365 con la implementación de API web. [Más información](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_CRM_Connectors.html#Example_for_Microsoft_Dynamics)

Se ha actualizado el procedimiento para instalar Adobe Campaign Classic en una plataforma de Windows. [Más información](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Windows__Installing_the_server.html)

Se ha detallado el periodo para compartir audiencias entre Adobe Experience Cloud y Campaign Classic. [Más información](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Importing_and_exporting_audiences.html)

Se ha actualizado el artículo completo de la base de conocimiento para la lista de Campaign Classic. [Más información](https://helpx.adobe.com/es/campaign/kb/article-list.html)

Se ha publicado una nueva nota técnica sobre la mejora del rendimiento y las prácticas recomendadas. [Más información](https://helpx.adobe.com/es/campaign/kb/best-practices-for-performance-improvement.html)

Se ha actualizado la muestra de prueba A/B. [Más información](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_A-B_testing.html)

Se ha actualizado la página de preguntas frecuentes y preguntas más frecuentes de Campaign Classic. [Más información](../../platform/using/common-questions.md)

## 18.4 - 24/04/2018{#release-18-4}

**Nuevas funciones incluidas en la versión**

Reglamento General de Protección de Datos (RGPD) de la UE: [Más información](https://helpx.adobe.com/es/campaign/kb/acc-privacy.html)

Perfiles activos: [Más información](https://docs.campaign.adobe.com/doc/AC/en/PTF_Profile_management_About_profiles.html#Active_profiles)

Mejora del conector push de Android: [Más información](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Android_connectors)

**Otras actualizaciones de la documentación incluidas en la versión**

Las notas de la versión se han mejorado para mejorar la experiencia del usuario y ahora incluyen todos los parches relacionados con las solicitudes de los clientes.  [Más información](https://docs.adobe.com/content/help/es-ES/campaign-classic/using/release-notes/latest-release.translate.html)

Se ha agregado una nueva página con las preguntas más comunes sobre Campaign Classic. [Más información](../../platform/using/common-questions.md)

Se ha actualizado la lista de mensajes de error. [Más información](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Se ha actualizado la nota técnica Marketing Cloud Triggers. [Más información](https://helpx.adobe.com/es/campaign/kb/triggers-and-campaign.html)

Se ha añadido una nota técnica sobre cómo instalar e implementar el paquete de privacidad (RGPD) en las versiones heredadas de Campaign Classic. [Más información](https://helpx.adobe.com/es/campaign/kb/how-to-install-gdpr-package-on-legacy-versions.html)

Se ha añadido una nota técnica sobre el nuevo mecanismo de generación automática de secuencias. [Más información](https://helpx.adobe.com/es/campaign/kb/sequence_auto_generation.html)

Se actualizó la documentación de JSAPI. [Más información](https://support.neolane.net/webApp/extranetLogin)

Se ha actualizado la matriz de compatibilidad. [Más información](https://helpx.adobe.com/es/campaign/kb/compatibility-matrix.html)

Ya está disponible una nueva página con las funciones y versiones obsoletas. [Más información](https://helpx.adobe.com/es/campaign/kb/deprecated-and-removed-features.html)

Se han añadido algunas limitaciones conocidas y prácticas recomendadas con respecto al RDBMS. [Más información](https://docs.campaign.adobe.com/doc/AC/en/INS_Prerequisites_and_recommendations__Database.html)

Conozca las prácticas recomendadas sobre el uso de SFTP. [Más información](https://docs.campaign.adobe.com/doc/AC/en/PTF_Importing_and_exporting_data_SFTP_server_usage.html)

Se ha actualizado la lista de flujos de trabajo técnicos. [Más información](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_About_technical_workflows.html)

La lista de artículos de la base de conocimiento (anteriormente conocidos como &quot;notas técnicas&quot;) ya está disponible aquí. [Más información](https://helpx.adobe.com/es/campaign/kb/article-list.html)

Se han actualizado los [vídeos de procedimientos](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html).

La documentación de LINE se ha actualizado tras la depreciación del paquete LINE. [Más información](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_LINE_channel.html)

Se ha actualizado la documentación de cálculo del indicador del informe. [Más información](../../reporting/using/indicator-calculation.md)

Se ha añadido información sobre la alineación de archivos de zona horaria con Oracle. [Más información](https://docs.campaign.adobe.com/doc/AC/en/MIG_Configuration_General_configurations.html#Oracle)

Se ha agregado una nueva sección &quot;Seguimiento de entregas&quot; con información actualizada sobre fallos de entrega y administración de cuarentena. [Más información](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Monitoring_a_delivery.html)

Se ha reorganizado la sección &quot;Bloques de personalización&quot; con nueva información sobre los bloques de personalización integrados.
[Más información](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_blocks.html)

Se ha reorganizado la sección de correos electrónicos de archivado con nueva información sobre la configuración del ```config-<instance name>.xml```archivo. [Más información](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Activating_email_archiving__on_premise_)

Se ha actualizado la información sobre el flujo de trabajo técnico del Centro de mensajes (Control). [Más información](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_Message_Center__Control_.html)

Se agregó información sobre las limitaciones de rendimiento al configurar un reenvío SMTP. [Más información](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Personalizing_delivery_parameters)

## 17.12 - 14/12/2017{#release-doc-14-12-2017}

El conjunto de [Documentación de Adobe Campaign Classic](https://helpx.adobe.com/es/support/campaign/classic.html) se ha reorganizado para mejorar el uso.

Se ha añadido una nueva sección de tutoriales para facilitar el acceso a los materiales de ayuda, las instrucciones, las muestras y los vídeos principales de las capacidades de Campaign. [Más información](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Tutorials.html)

Se ha agregado una nueva sección para ayudarle a supervisar el estado de la entrega, pero también para conocer los posibles errores y cómo corregirlos. [Más información](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Monitoring_a_delivery.html)

Se ha actualizado la lista de mensajes de error. [Más información](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Se ha actualizado la nota técnica Marketing Cloud Triggers. [Más información](https://helpx.adobe.com/es/campaign/kb/triggers-and-campaign.html)

La guía de migración de Campaign Classic se ha agregado a la colección. [Más información](https://docs.campaign.adobe.com/doc/AC/en/MIG_Migration_overview_About_migration.html)

Se actualizó la matriz de compatibilidad de Campaign. [Más información](https://helpx.adobe.com/es/campaign/kb/compatibility-matrix.html)

Cuando proceda, las instrucciones de configuración e instalación ahora mencionan a qué modelo de alojamiento se aplican. [Más información](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html)

Nuevo artículo de la Base de conocimiento para resaltar las diferencias de configuración y características entre las implementaciones locales, híbridas y de servicios administrados. [Más información](https://helpx.adobe.com/es/campaign/kb/acc-on-prem-vs-hosted.html)

Se han añadido instrucciones sobre cómo instalar un paquete estándar. [Más información](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Installing_packages.html)

Se han añadido detalles sobre cómo configurar la integración con Audience Manager o el servicio principal Personas. [Más información](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Configuring_shared_audiences_integration_in_Adobe_Campaign.html)

Se ha actualizado la documentación de instalación para indicar que pgcrypto ahora se requiere para la instalación de Campaign si se utiliza PostreSQL. [Más información](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Linux__Prerequisites.html#Database_access_layers)

## 17.9 - 25/09/2017{#release-17-9}

**Nuevas funciones incluidas en la versión**

Mejoras en el conector ACS

Conector SAP HANA: [Más información](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Accessing_an_external_database.html#SAP_HANA)

Conector Hadoop mediante HiveSQL: [Más información](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Accessing_an_external_database.html#Hadoop)

Canal LINE: Mejoras en la mensajería: [más información](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_LINE_channel.html)

**Otras actualizaciones de la documentación incluidas en la versión**

Se agregaron nuevos ejemplos de consultas. [Más información](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Designing_queries.html#Filtering_duplicated_recipients)

Se ha actualizado la guía de prácticas recomendadas de entrega. [Más información](https://helpx.adobe.com/es/campaign/kb/delivery-best-practices.html)

La muestra de prueba A/B se ha actualizado con instrucciones que faltan. [Más información](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_A-B_testing.html)

Se han actualizado los vídeos explicativos. [Más información](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html)

Actualice la sección de archivado de correo electrónico. [Más información](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html)

Aclarar el uso del Planificador en un flujo de trabajo. [Más información](../../workflow/using/scheduler.md)

Práctica recomendada para agregar flujo de trabajo pausado. [Más información](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Executing_a_workflow.html)

Nuevo procedimiento sobre el procesamiento previo de archivos al importar y posprocesar al exportar datos en un flujo de trabajo. Lee [aquí](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html).

La documentación del mecanismo de cuarentena de los mensajes SMS se ha actualizado para reflejar las características específicas de la gestión de errores del conector SMPP genérico ampliado. [Más información](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_quarantine_management.html#SMS_quarantines).

La documentación del canal de aplicaciones móviles se ha mejorado con un procedimiento detallado para enviar notificaciones enriquecidas en Android. [Más información](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Rich_notifications).

Se ha actualizado la documentación de procesamiento de la Bandeja de entrada. [Más información](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_Inbox_rendering.html).

La configuración de la documentación del seguimiento web se ha mejorado con un ejemplo y notas actualizados. [Más información](https://docs.campaign.adobe.com/doc/AC/en/CFG_Setting_up_web_tracking_Additional_parameters.html#Redirection_server_configuration).

La documentación del canal SMS se ha actualizado con algunas aclaraciones agregadas a la sección de respuesta automática que se aplica al conector SMPP genérico ampliado. [Más información](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_SMS_channel.html#Creating_an_SMPP_external_account).

Se ha actualizado la documentación de Social Marketing. [Más información](../../social/using/about-social-marketing.md).

Se ha añadido una nueva nota técnica sobre el calentamiento de la IP. [Más información](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/Technotes/AdobeCampaign_Deliverability_IP_Warming_overview.pdf).

Se ha añadido una nueva introducción a la actualización de la compilación. [Más información](https://helpx.adobe.com/es/campaign/kb/acc-build-upgrade.html).

## Mayo 2017{#release-doc-30-05-2017}

Hay disponible una nueva guía de introducción: presenta algunas de las prácticas recomendadas que se pueden utilizar para ofrecer Adobe Campaign, desde la creación y el establecimiento de objetivos hasta la entrega y la supervisión. [Más información](https://helpx.adobe.com/es/campaign/kb/delivery-best-practices.html)

Se ha actualizado la guía de introducción a la seguridad. [Más información](https://helpx.adobe.com/es/campaign/kb/acc-security.html)

La documentación de [&quot;archivado de correos electrónicos&quot;](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html) se ha actualizado con la sección [&quot;Email BCC&quot;](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Configuring_the_BCC_email_address__on_premise_) y los pasos [detallados para activar la función](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Sending_messages.html#Archiving_emails).

Se han agregado y actualizado algunos vídeos. [Más información](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html)

Obtenga información sobre cómo enviar una entrega a destinatarios cargados desde un archivo externo sin actualizar la base de datos. [Más información](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients)

Se ha actualizado el ejemplo de inclusión doble. [Más información](../../web/using/use-cases--web-forms.md)

## Marzo de 2017{#release-doc-31-03-2017}

Capacidad de entrega: se ha actualizado la [guía de introducción](https://docs.adobe.com/content/help/es-ES/campaign-classic/using/sending-messages/deliverability-management/about-deliverability.html). La documentación sobre la capacidad de entrega ahora incluye una [descripción](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_About_deliverability.html) más detallada y una descripción del [proceso de implementación y los pasos principales](../../delivery/using/deliverability-key-points.md).

La sección “Envío mediante olas” se ha movido y mejorado con ejemplos detallados, recomendaciones y casos de uso.    [Más información](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Sending_messages.html#Sending_using_multiple_waves)

Se ha añadido una tabla que describe los errores específicos de los mensajes SMS a la sección “Gestión de cuarentena”. [Más información](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_quarantine_management.html#SMS_quarantines)

Flujos de trabajo: se ha añadido un nuevo ejemplo de flujo de trabajo multicanal. [Más información](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#Cross-channel_deliveries)

Marketing Cloud Triggers: se ha añadido una nota técnica sobre cómo configurarla y utilizarla con Adobe Campaign. [Más información](https://helpx.adobe.com/es/campaign/kb/triggers-and-campaign.html)

La guía Flujo de trabajo se ha reorganizado y ampliado. Encuentre fácilmente cómo [construir](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Building_a_workflow.html) y [ejecutar](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Executing_a_workflow.html) un flujo de trabajo, cómo [dirigir](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Targeting_data.html) y [gestionar](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Targeting_data.html#Data_Management) sus datos, cómo [importar](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html), y cómo usar los datos de flujo de trabajo para [actualizar la base de datos](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Updating_the_database) o para [enviar entregas](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Delivering_via_a_workflow).

Ya está disponible un ejemplo [importación de flujo de trabajo](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Delivering_via_a_workflow) creado tras las [optimizaciones de importación](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html#Import_best_practices).
La guía de instalación se ha actualizado para esta nueva versión. [Más información](https://docs.campaign.adobe.com/doc/AC/en/INS_Architecture_and_hosting_models_General_architecture.html)

Se ha actualizado la matriz de compatibilidad. [Más información](https://helpx.adobe.com/es/campaign/kb/compatibility-matrix.html)

Los destinatarios obtienen un valor añadido cuando se incluyen cupones en las entregas de correo electrónico. [Más información](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalized_coupons.html)

## Adobe Campaign v7: 16/03/2017{#release-17-2}

**Nuevas funciones incluidas en la versión**

Conector ACS

API web para Microsoft Dynamics: [Más información](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_CRM_Connectors.html#Example_for_Microsoft_Dynamics)

Método CCO de archivado de correo electrónico: [Más información](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Updated_email_archiving_system__BCC_)

Conector Amazon Simple Storage Service (S3): [Más información](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Event_activities.html#File_transfer)

