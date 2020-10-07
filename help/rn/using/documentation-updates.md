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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '3704'
ht-degree: 98%

---


# Actualizaciones de documentación{#documentation-updates}

Esta página enumera todas las nuevas funciones y actualizaciones de la documentación por mes y por versión de Campaign.

También puede consultar las [Notas de la versión de Adobe Campaign Classic](../../rn/using/latest-release.md) para ver más actualizaciones.

## Septiembre de 2020 {#september-2020}

Se ha agregado una nota para especificar que el recuento de perfiles activos solo está disponible para las instancias de Marketing. [Más información](../../platform/using/about-profiles.md#active-profiles)

Se ha añadido una nueva muestra sobre la edición de esquema para vincular un campo a una tabla de referencia existente. [Más información](../../configuration/using/examples-of-schemas-edition.md#uc-link)

Se ha añadido una nota sobre el uso de datos adicionales con direcciones semilla en envíos. [Más información](../../delivery/using/creating-seed-addresses.md#defining-addresses)

## Agosto de 2020 {#aug-2020}

Conozca las prácticas recomendadas relacionadas con el diseño de envíos y el envío con Campaign en una sección dedicada. [Más información](../../delivery/using/delivery-best-practices.md)

Se ha mejorado la página de aterrizaje de prácticas recomendadas sobre la capacidad de entrega para facilitar el acceso a las subsecciones. [Más información](../../delivery/using/deliverability-key-points.md)

Los vídeos de procedimientos ya están disponibles para los siguientes temas:

* [Configuración de la gestión de la fatiga mediante reglas de tipología y filtros predefinidos](../../campaign/using/about-campaign-typologies.md)

* [Creación de un correo electrónico en una campaña](../../campaign/using/marketing-campaign-deliveries.md)

* [Creación de una newsletter multilingüe con contenido condicional](../../delivery/using/conditional-content.md)

* [Configuración e implementación de una plantilla de envíos](../../delivery/using/creating-a-delivery-template.md)

* [Activación y uso de AMP para correos electrónicos](../../delivery/using/defining-interactive-content.md)

* [Cómo personalizar correos electrónicos con bloques de contenido dinámico](../../delivery/using/personalization-blocks.md)

* [Personalización de correos electrónicos mediante campos de personalización](../../delivery/using/personalization-fields.md)

* [Administración de fuentes y pruebas en un correo electrónico](../../delivery/using/steps-defining-the-target-population.md)

* [Configuración de un envío recurrente](../../workflow/using/recurring-delivery.md)

* [Configuración de un envío continuo](../../workflow/using/continuous-delivery.md)

Se ha añadido información sobre las comprobaciones y acciones que se deben realizar al obtener el error &quot;No se pudo resolver el nombre de host&quot; después de conectarse a un servidor FTP. [Más información](../../platform/using/sftp-server-usage.md)

Se ha hecho referencia a nuevos casos de uso en la lista de [casos de uso del flujo de trabajo](../../workflow/using/about-workflow-use-cases.md):

* Automatización de la creación, edición y publicación de contenido
* Configuración de un proceso de aprobación de destinatarios antes de enviar un envío
* Llamada a una variable de instancia en una consulta
* Aplicación de un porcentaje dividido a una población

La sección de la actividad **[!UICONTROL AND-join]** se ha enriquecido con información adicional sobre su uso, así como con una nota sobre el uso de variables. [Más información](../../workflow/using/and-join.md)

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

## july 2020 {#release-20-2}

**Nuevas funciones incluidas en la versión 20.2**

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

## Enero de 2020 {#release-20-1}

**Nuevas funciones incluidas en la versión 20.1**

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

**Nuevas funciones incluidas en la versión 19.2**

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

## Mayo 2019 {#release-19-1}

**Nuevas funciones incluidas en la versión 19.1**

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

Los vídeos de funciones se han movido [aquí](https://docs.adobe.com/content/help/es-ES/campaign-classic-learn/tutorials/overview.html).

Se han añadido dos notas técnicas en [Teradata](https://helpx.adobe.com/es/campaign/kb/campaign_fda_teradata.html) y [MySQL 5.7](https://helpx.adobe.com/es/campaign/kb/campaign_fda_mysql.html).
