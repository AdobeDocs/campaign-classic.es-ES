---
solution: Campaign Classic
product: campaign
title: Descripción del modelo de datos de Adobe Campaign Classic
description: Este documento describe el modelo de datos de Adobe Campaign.
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 87028ec81a8cae6793d45d7c840511b59cd0287c
workflow-type: tm+mt
source-wordcount: '2374'
ht-degree: 1%

---


# Descripción del modelo de datos de Campaign{#data-model-description}

Adobe Campaign viene con un modelo de datos predefinido. Esta sección proporciona algunos detalles sobre las tablas integradas del modelo de datos de Adobe Campaign y su interacción.

Para acceder a la descripción de cada tabla, vaya a **[!UICONTROL Admin > Configuration > Data schemas]**, seleccione un recurso de la lista y haga clic en la pestaña **[!UICONTROL Documentation]**.

![](assets/data-model_documentation-tab.png)

>[!NOTE]
>
>La estructura física y lógica de los datos que se llevan en la aplicación se describe en XML. Obedece a una gramática específica de Adobe Campaign, denominada esquema. Para obtener más información sobre los esquemas de Adobe Campaign, lea [esta sección](../../configuration/using/about-schema-reference.md).

## Descripción de las tablas principales {#description-main-tables}

Adobe Campaign se basa en una base de datos relacional que contiene tablas vinculadas.

El diagrama siguiente muestra las uniones entre las principales tablas comerciales del modelo de datos de Adobe Campaign y los campos principales de cada una.

<!--![](assets/data-model_diagram.png)-->

![](assets/data-model_simplified-diagram.png)

El modelo de datos predefinido de Adobe Campaign incluye las tablas principales que se enumeran a continuación.

### NmsRecipient {#NmsRecipient}

Esta tabla coincide con el esquema **nms:recipient** .

Es la tabla predeterminada utilizada para los **destinatarios de envíos**. Como resultado, contiene la información necesaria para las entregas a través de los distintos canales:

* sEmail: dirección de correo electrónico.
* iEmailFormat: formato preferido para correos electrónicos (1 para texto, 2 para HTML y 0 si no está definido).
* sAddress1, sAddress2, sAddress3, sAddress4, sZipCode, sCity se usan para crear la dirección postal (de acuerdo con el estándar XPZ 10-011 AFNOR de mayo de 1997).
* sPhone, sMobilePhone, sFax contienen los números de teléfono, teléfono móvil y fax, respectivamente.
* iBlackList es el indicador de exclusión predeterminado utilizado para los perfiles (1 significa &quot;cancelar suscripción&quot;, 0 en caso contrario).

El campo iFolderId es la clave externa que vincula el destinatario a su carpeta de ejecución. Para obtener más información, consulte [XtkFolder](#XtkFolder).

El campo sCountryCode es el código ISO 3166-1 Alpha 2 (2 caracteres) del país asociado al destinatario. Este campo es en realidad una clave externa en la tabla de referencia del país (NmsCountry), que contiene las etiquetas del país y otros datos de código del país. Si el país no se rellena, se almacena el valor &quot;XX&quot; (y se utiliza en lugar de un registro de ID cero).

Para obtener más información sobre la tabla de destinatarios, consulte [esta sección](../../configuration/using/about-data-model.md#default-recipient-table).

### NmsGroup {#NmsGroup}

Esta tabla coincide con el esquema **nms:group** .

Permite crear **grupos estáticos de destinatarios**. Existe una relación &quot;varios a varios&quot; entre destinatarios y grupos. Por ejemplo, un destinatario puede pertenecer a varios grupos y un grupo puede contener varios destinatarios. Los grupos se pueden crear manualmente mediante una importación o mediante la segmentación de la entrega. Los grupos suelen utilizarse como objetivos de envío. Hay un índice único en el campo que representa el nombre interno del grupo sName. El grupo está vinculado a una carpeta (la clave es iFolderId. Para obtener más información, consulte [XtkFolder](#XtkFolder)).

### NmsRcpGrpRel {#NmsRcpGrpRel}

La tabla de relación NmsRcpGrpRel solo contiene los dos campos correspondientes a los identificadores de las tablas vinculadas iRecipientId e iGroupId.

### NmsService {#NmsService}

Esta tabla coincide con el esquema **nms:service** .

En Adobe Campaign, puede crear y administrar suscripciones a servicios de información (temas). La tabla NmsService almacena la definición de los servicios informativos (temas) a los que ofrece a sus destinatarios la suscripción (por ejemplo, un boletín informativo).

Los servicios son entidades similares a los grupos (agrupaciones de destinatarios estáticas), excepto que distribuyen más información y permiten una gestión sencilla de suscripciones y bajas de suscripción a través de formularios.

Hay un índice único en el campo que representa el nombre interno del servicio sName. El servicio está vinculado a una carpeta (la clave es iFolderId. Para obtener más información, consulte [XtkFolder](#XtkFolder)). Finalmente, el campo iType especifica el canal de entrega de este servicio (0 para correo electrónico, 1 para SMS, 2 para teléfono, 3 para correo postal y 4 para fax).

### NmsSubscription {#NmsSubscription}

Esta tabla coincide con el esquema **nms:subscription** .

Permite administrar las suscripciones de los destinatarios a los servicios informativos.

### NmsSubHisto {#NmsSubHisto}

Esta tabla coincide con el esquema **nms:subHisto**.

Si las suscripciones se administran mediante formularios web o la interfaz de la aplicación, todas las suscripciones y bajas se registran en la tabla NmsSubHisto. El campo iAction especifica la acción (0 para la baja y 1 para la suscripción) realizada en la fecha almacenada en el campo tsDate .

### NmsDelivery {#NmsDelivery}

Esta tabla coincide con el esquema **nms:delivery** .

Cada registro de esta tabla representa una **acción de envío** o una **plantilla de envío**. Contiene todos los parámetros necesarios para realizar envíos (el objetivo, el contenido, etc.). Los registros de envío (difusión) (NmsBroadLog) y las URL de seguimiento asociadas (NmsTrackingUrl) se crean durante la fase de análisis (consulte a continuación para obtener más información sobre ambas tablas).

Hay un índice único en el campo que representa el nombre interno de la entrega o el escenario de sInternalName. El envío está vinculado a una carpeta de ejecución (la clave externa es iFolderProcessId. Para obtener más información, consulte [XtkFolder](#XtkFolder)).

### XtkFolder {#XtkFolder}

Contiene **todas las carpetas del árbol** visibles en la pestaña **Navigation** de la consola.

Las carpetas están escritas: el valor del campo sModel especifica el tipo de datos que se pueden contener en la carpeta. Este campo también permite que la consola del cliente muestre los datos correctamente con los formularios correspondientes. Los valores posibles de este campo se definen en el navigationTree.

El árbol se administra mediante los campos iParentId e iChildCount . El campo sFullName proporciona la ruta completa de la carpeta en el árbol. Finalmente, hay un índice único en el campo que representa el nombre interno de la carpeta sName.

## Envío y seguimiento {#delivery-and-tracking}

Este conjunto de tablas está vinculado al módulo **Delivery**, que permite monitorizar los envíos y los problemas que puedan ser detectados al enviar los mensajes. Para obtener más información, consulte [Monitorización de envíos](../../delivery/using/about-delivery-monitoring.md). Para obtener más información sobre el seguimiento, consulte [Seguimiento de mensajes](../../delivery/using/about-message-tracking.md).

![](assets/data-model_delivery.png)

**NmsBroadLogMsg**: Esta tabla coincide con el  **nms:** broadLogMsgschema. Es una extensión de la tabla de registro de envíos.

## Administración de campañas {#campaign-management}

Este conjunto de tablas está vinculado al módulo **Marketing campaign** , que permite definir, optimizar, ejecutar y analizar las comunicaciones y las campañas de marketing. Para obtener más información, consulte [Acerca de las campañas de marketing](../../campaign/using/designing-marketing-campaigns.md).

![](assets/data-model_campaign.png)

* **NmsOperation**: Esta tabla coincide con el esquema  **nms:** operationschema. Contiene los datos de las campañas de marketing.
* **NmsDeliveryOutline**: Esta tabla coincide con el esquema  **nms:** deliveryOutlineschema. Contiene las propiedades ampliadas del envío (descripción del envío).
* **NmsDlvOutlineItem**: Esta tabla coincide con  **nms:** dlvOutlineItemschema. Contiene los artículos de un esquema de entrega.
* **NmsDeliveryCustomization**: Esta tabla coincide con el esquema  **nms:** deliveryCustomizationschema. Contiene los campos personalizados de un envío.
* **NmsBudget**: Esta tabla coincide con el  **nms:** budgetschema. Contiene los datos de un presupuesto sobre una campaña, un plan, un programa, una tarea o envíos.
* **NmsDocument**: Esta tabla coincide con el esquema  **nms:** documentschema. Contiene los documentos de marketing de la campaña en forma de archivos (imágenes, archivos de Excel o Word, etc.)
* **XtkWorkflow**: Esta tabla coincide con el esquema de flujo de trabajo  **xtk:** . Contiene objetivos de campaña.
* **NmsTask**: Esta tabla coincide con el esquema  **nms:** taskschema. Contiene la definición de una tarea de marketing.
* **NmsAsset**: Esta tabla coincide con el esquema  **nms:** assetschema. Contiene la definición de un recurso de marketing.

## Coherencia de comunicación {#communication-consistency}

Este conjunto de tablas está vinculado al módulo **Campaign Optimization** , que permite controlar, filtrar y monitorizar los envíos. Para obtener más información, consulte [Acerca de las tipologías de campaña](../../campaign/using/about-campaign-typologies.md).

![](assets/data-model_typology.png)

* **NmsTypologyRule**: Esta tabla coincide con el esquema  **nms:** typologyRuleschema. Contiene las reglas que se aplican a los envíos en función de las tipologías.
* **NmsTypology**: Esta tabla coincide con el esquema de tipología  **nms:** . Contiene el conjunto de reglas que se deben aplicar a los envíos que coinciden con la tipología.
* **NmsTypologyRuleRel**: Esta tabla coincide con el  **nms:** typologyRuleRelschema. Contiene las relaciones entre tipologías y sus reglas.
* **NmsVolumeLine**: Esta tabla coincide con el esquema  **nms:** volumeLineschema. Contiene el conjunto de líneas de disponibilidad de las reglas de capacidad.
* **NmsVolumeConsumed**: Esta tabla coincide con el esquema  **nms:** volumeConsumedschema. Contiene todas las líneas de consumo de las reglas de capacidad.

## Administración de respuestas {#response-management}

Este conjunto de tablas está vinculado al módulo **Response Manager** , que permite medir el éxito y la rentabilidad de las campañas de marketing u ofrecer propuestas para todos los canales de comunicación. Para obtener más información, consulte [Acerca del gestor de respuestas](../../campaign/using/about-response-manager.md).

![](assets/data-model_response.png)

### NmsRemaHypothesis {#NmsRemaHypothesis}

Esta tabla coincide con el esquema **nms:remaHypothesis**. Contiene la definición de la hipótesis de medición.

Esta tabla contiene información importante almacenada en XML, que incluye:

**Contexto de ejecución (información almacenada en XML)**

El contexto de ejecución rellena las tablas y los campos que se deben tener en cuenta para el cálculo de la medición, concretamente:
* Esquema de almacenamiento del registro de reacción nms:remaMatchRcp.
* El esquema de tabla de transacciones (compras por ejemplo).
* El esquema de consulta, que permite definir la tabla de inicio de las condiciones de hipótesis.
* Los vínculos a personas, que permiten identificar al individuo en función del esquema de consulta.
* La fecha de transacción. Este campo no es obligatorio, pero se recomienda utilizarlo para restringir el perímetro de cálculo.
* El importe de la transacción: es un campo opcional para calcular automáticamente los indicadores de ingresos.

**Perímetro de hipótesis (información almacenada en XML)**

El perímetro de la hipótesis consiste en el filtrado de la hipótesis basado en la tabla del esquema de consulta.

**Secuencia de comandos de sobrecarga de hipótesis (información almacenada en XML)**

La secuencia de comandos de sobrecarga de hipótesis es un código JavaScript que permite sobrecargar el contenido de la hipótesis durante la ejecución.

**Indicadores de medición**

Los siguientes indicadores se actualizan automáticamente durante la ejecución de la hipótesis:

* Número de reacciones: **iTransaction**. Número de líneas en la tabla de registros de reacción.
* Número de contactos: **iContactReacted**. Número específico de contactos objetivo en la hipótesis.
* Recuento de grupos de control: **iProofReacted**. Número específico de contactos del grupo de control de destino en la hipótesis.
* Tasa de respuesta contactada: **dContactReactedRate**. Tasa de respuesta de los contactos objetivo en la hipótesis.
* Tasa de respuesta del grupo de control: **dProofReactedRate**. Tasa de respuesta del grupo de control de hipótesis.
* Ingresos totales de la población contactada: **dContactReactedTotalAmount**. Ingresos totales de los contactos objetivo en la hipótesis.
* Ingresos medios del grupo de control: **dContactReactedAvgAmount**. Ingresos promedio de los contactos del grupo de control de destino en la hipótesis.
* Ingresos totales del grupo de control: **dProofReactedTotalAmount**. Ingresos totales del grupo de control de hipótesis.
* Ingresos medios del grupo de control: **dProofReactedAvgAmount**. Ingresos promedio del grupo de control de hipótesis.
* Margen total por contacto: **dContactReactedTotalMargin**. Margen total por contacto objetivo en la hipótesis.
* Media de margen por contacto: **dContactReactedAvgMargin**. Media de margen por contacto segmentado en la hipótesis.
* Margen total del grupo de control: **dProofReactedTotalMargin**. Margen total del grupo de control objetivo en la hipótesis.
* Media de margen del grupo de control: **dProofReactedAvgMargin**. Average margin of the control group targeted in the hypothesis.
* Ingresos adicionales: **dAdditionalAmount**. (Media de ingresos de los contactos - Media de ingresos del grupo de control) * Número de contactos.
* Margen adicional: **dAdditionalMargin**. (Media de ingresos de los contactos - Media de ingresos por grupo de control)/Número de contactos.
* Costo promedio por contacto (expresión SQL). Coste calculado de la entrega/Número de contactos.
* ROI (expresión SQL). Coste calculado de la entrega/Margen total de los contactos.
* ROI efectivo (expresión SQL). Coste calculado de la entrega/Margen adicional.
* Significado: **iSignificativy** (expresión SQL). Contiene valores entre 0 y 3 según la importancia de la campaña.

### NmsRemaMatchRcp {#NmsRemaMatchRcp}

Esta tabla coincide con el esquema **nms:remaMatchRcp**.

Contiene un registro que representa la reacción de un individuo a una hipótesis determinada. Estos registros se crearon durante la ejecución de hipótesis.

## Simulación y envío {#simulation-and-delivery}

Este conjunto de tablas está vinculado al módulo **Simulation**, que permite probar la distribución de ofertas pertenecientes a una categoría o un entorno antes de enviar la propuesta a los destinatarios. Para obtener más información, consulte [Acerca de la simulación de ofertas](../../interaction/using/about-offers-simulation.md).

![](assets/data-model_simulation.png)

* **NmsSimulation**: Esta tabla coincide con el esquema  **nms:** simulationschema. Representa una simulación para un conjunto de envíos u ofertas en una población determinada.
* **NmsDlvSimulationRel**: Esta tabla coincide con el  **nms:** dlvSimulationRelschema. Contiene la lista de envíos que se tienen en cuenta en la simulación. El ámbito de la simulación se almacena en XML.
* **NmsOfferSimulationRel**: Esta tabla coincide con el  **nms:** offerSimulationRelschema. Permite vincular una simulación con una oferta.

## Módulo de interacción {#interaction-module}

Este conjunto de tablas está vinculado al módulo **Interaction**, que permite responder en tiempo real durante una interacción con un contacto determinado mediante la realización de una o varias ofertas adaptadas. Para obtener más información, consulte [Interacción y administración de ofertas](../../interaction/using/interaction-and-offer-management.md).

* **NmsOffer**: Esta tabla coincide con el esquema  **nms:** offer. Contiene la definición de cada oferta de marketing.
* **NmsPropositionRcp**: Esta tabla coincide con el  **nms:** propositionRcpschema. Contiene el registro de canales cruzados de propuestas de marketing enviadas a cada individuo. El registro se crea cuando se prepara una propuesta o se hace de forma eficaz para un individuo.
* **NmsOfferSpace**: Esta tabla coincide con el esquema  **nms:** offerSpaceschema. Contiene la definición de ubicaciones en las que se formulan propuestas.
* **NmsOfferContext**: Esta tabla coincide con el  **nms:** offerContextschema. Contiene criterios adicionales sobre la aplicabilidad de la propuesta, así como la definición de la fórmula de cálculo de peso.
* **NmsOfferView**: Esta tabla coincide con  **nms:offerView**. Contiene las representaciones de la oferta.
* **NmsOfferCategory**: Esta tabla coincide con  **nms:offerCategory**. Contiene las categorías de oferta.
* **NmsOfferEnv**: Esta tabla coincide con  **nms:offerEnv**. Contiene los entornos de oferta.

## Módulo del centro de mensajes {#message-center-module}

El siguiente conjunto de tablas está vinculado al módulo **Transactional messaging** (Message Center), que permite administrar las comunicaciones individuales y únicas enviadas a un usuario y generadas a partir de eventos activados desde sistemas de información. Para obtener más información, consulte [Acerca de la mensajería transaccional](../../message-center/using/about-transactional-messaging.md).

### NmsRtEvent {#NmsRtEvent}

![](assets/data-model_message-center_rt.png)

Esta tabla coincide con el esquema **nms:rtEvent** . Contiene una definición de eventos en tiempo real.

### NmsBatchEvent {#NmsBatchEvent}

![](assets/data-model_message-center_batch.png)

Esta tabla coincide con el esquema **nms:batchEvent** . Contiene la definición de eventos por lote.

<!--## Microsites Module {#microsites-module}

This set of tables is linked to the **Web applications** functionality, which allows to create and publish dynamic and interactive web applications with data from the database and content adapted to the rights of the connected user. For more on this, see [About web applications](../../web/using/about-web-applications.md).

![](assets/data-model_microsites.png)

* **NmsTrackingUrl**: This table matches the **nms:trackingUrl** schema.

* **NmsPurl**: This table matches the **nms:purl** schema.-->

## Módulo NMAC {#nmac-module}

Este conjunto de tablas está vinculado al **Mobile App Channel**, que permite enviar notificaciones personalizadas a los terminales iOS y Android a través de aplicaciones. Para obtener más información, consulte [Acerca del canal de aplicaciones móviles](../../delivery/using/about-mobile-app-channel.md).

* **NmsMobileApp**: Esta tabla coincide con el  **nms:** mobileAppschema. Contiene las aplicaciones móviles definidas en Adobe Campaign.
* **NmsAppSubscription**: Esta tabla coincide con el esquema  **nms:** appSubscriptionschema. Contiene la información de los suscriptores sobre una o más aplicaciones.
* **NmsAppSubscriptionRcp**: Esta tabla coincide con el  **nms:** appSubscriptionRcpschema. Permite vincular a los visitantes que se suscribieron a una aplicación con la tabla de destinatarios.
* **NmsExcludeLogAppSubRcp**: Esta tabla coincide con el  **nms:** excludeLogAppSubRcpschema.
* **NmsTrackingLogAppSubRcp**: Esta tabla coincide con el  **nms:** trackingLogAppSubRcpschema.
* **NmsBroadLogAppSubRcp**: Esta tabla coincide con el  **nms:** broadLogAppSubRcpschema.

## Módulo de marketing social {#social-marketing-module}

Este conjunto de tablas está vinculado al módulo **Administración de redes sociales** , que permite interactuar con clientes y posibles clientes a través de Facebook y Twitter. Para obtener más información, consulte [Acerca del marketing social](../../social/using/about-social-marketing.md).

![](assets/data-model_social.png)

* **NmsVisitor**: Esta tabla coincide con el esquema  **nms:** visitorschema. Contiene información sobre los visitantes.
* **NmsVisitorSub**: Esta tabla coincide con el  **nms:** visitorSubschema. Permite vincular a un visitante a los servicios a los que se ha suscrito (Twitter o Facebook).
* **NmsFriendSendRel**: Esta tabla coincide con el  **nms:** friendlyRelschema. Permite vincular visitantes con sus amigos en el contexto del servicio de Facebook.
* **NmsVisitorInterestRel**: Esta tabla coincide con el  **nms:** visitorInterestRelschema. Permite vincular visitantes con sus intereses.
* **NmsInterest**: Esta tabla coincide con el esquema  **nms:** interestschema. Contiene la lista de intereses de cada visitante.