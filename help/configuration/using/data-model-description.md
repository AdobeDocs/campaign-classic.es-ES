---
product: campaign
title: Descripción del modelo de datos de Adobe Campaign Classic
description: Este documento describe el modelo de datos de Adobe Campaign
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
feature: Data Model
exl-id: fc0fd23c-f9ea-4e30-b47b-a84143d882ca
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '2381'
ht-degree: 2%

---

# Descripción del modelo de datos de Campaign{#data-model-description}


Adobe Campaign viene con un modelo de datos predefinido. En esta sección se proporcionan algunos detalles sobre las tablas integradas del modelo de datos de Adobe Campaign y su interacción.

Para acceder a la descripción de cada tabla, vaya a **[!UICONTROL Admin > Configuration > Data schemas]**, seleccione un recurso de la lista y haga clic en **[!UICONTROL Documentation]** pestaña.

![](assets/data-model_documentation-tab.png)

>[!NOTE]
>
>La estructura física y lógica de los datos que se llevan en la aplicación se describe en XML. Obedece a una gramática específica de Adobe Campaign, denominada esquema. Para obtener más información sobre los esquemas de Adobe Campaign, lea [esta sección](../../configuration/using/about-schema-reference.md).

## Descripción de las tablas principales {#description-main-tables}

Adobe Campaign se basa en una base de datos relacional que contiene tablas vinculadas entre sí.

En el diagrama siguiente se muestran las uniones entre las principales tablas de negocio del modelo de datos de Adobe Campaign con los campos principales de cada una.

<!--![](assets/data-model_diagram.png)-->

![](assets/data-model_simplified-diagram.png)

El modelo de datos predefinido de Adobe Campaign incluye las tablas principales que se enumeran a continuación.

### NmsRecipient {#NmsRecipient}

Esta tabla coincide con el **nms:destinatario** esquema.

Es la tabla predeterminada que se usa para **destinatarios de envíos**. Como resultado, contiene la información necesaria para las entregas a través de los distintos canales:

* sEmail: email address.
* iEmailFormat: formato preferido para los correos electrónicos (1 para texto, 2 para HTML y 0 si no se define).
* sAddress1, sAddress2, sAddress3, sAddress4, sZipCode, sCity se utilizan para crear la dirección postal (de acuerdo con el estándar AFNOR XPZ 10-011 de mayo de 1997).
* sPhone, sMobilePhone, sFax contienen los números de teléfono, teléfono móvil y fax respectivamente.
* iBlackList es el indicador de exclusión predeterminado utilizado para los perfiles (1 significa &quot;sin suscripción&quot;, 0 en caso contrario).

El campo iFolderId es la clave externa que vincula al destinatario con su carpeta de ejecución. Para obtener más información, consulte [XtkFolder](#XtkFolder).

El campo sCountryCode es el código ISO 3166-1 Alpha 2 (2 caracteres) del país asociado con el destinatario. Este campo es en realidad una clave externa en la tabla de referencia de país (NmsCountry), que contiene las etiquetas de país y otros datos de código de país. Si el país no está rellenado, se almacena el valor &quot;XX&quot; (y se utiliza en lugar de un registro de ID cero).

Para obtener más información sobre la tabla de destinatarios, consulte [esta sección](../../configuration/using/about-data-model.md#default-recipient-table).

### NmsGroup {#NmsGroup}

Esta tabla coincide con el **nms:grupo** esquema.

Le permite crear **grupos estáticos de destinatarios**. Existe una relación &quot;varios a varios&quot; entre los destinatarios y los grupos. Por ejemplo, un destinatario puede pertenecer a varios grupos y un grupo puede contener varios destinatarios. Los grupos se pueden crear manualmente, mediante una importación o mediante objetivos de entrega. Los grupos suelen utilizarse como objetivos de envío. Hay un índice único en el campo que representa el nombre interno del grupo sName. El grupo está vinculado a una carpeta (la clave es iFolderId. Para obtener más información, consulte [XtkFolder](#XtkFolder)).

### NmsRcpGrpRel {#NmsRcpGrpRel}

La tabla de relación NmsRcpGrpRel solo contiene los dos campos correspondientes a los identificadores de las tablas vinculadas iRecipientId e iGroupId.

### NmsService {#NmsService}

Esta tabla coincide con el **nms:servicio** esquema.

En Adobe Campaign, puede crear y administrar suscripciones a los servicios informativos (temas). La tabla NmsService almacena la definición de los servicios informativos (temas) a los que ofrece a sus destinatarios suscribirse (por ejemplo, un boletín informativo).

Los servicios son entidades similares a los grupos (agrupaciones estáticas de destinatarios), excepto por el hecho de que circulan más información y permiten una administración sencilla de las suscripciones y las bajas de suscripción a través de formularios.

Hay un índice único en el campo que representa el nombre interno del servicio sName. El servicio está vinculado a una carpeta (la clave es iFolderId. Para obtener más información, consulte [XtkFolder](#XtkFolder)). Finalmente, el campo iType especifica el canal de entrega de este servicio (0 para correo electrónico, 1 para SMS, 2 para teléfono, 3 para correo postal y 4 para fax).

### NmsSubscription {#NmsSubscription}

Esta tabla coincide con el **nms:subscription** esquema.

Permite administrar las suscripciones de los destinatarios a los servicios informativos.

### NmsSubHisto {#NmsSubHisto}

Esta tabla coincide con el **nms:subHisto** esquema.

Si las suscripciones se administran mediante formularios web o la interfaz de la aplicación, todas las suscripciones y bajas de suscripción se historian en la tabla NmsSubHisto. El campo iAction especifica la acción (0 para la baja y 1 para la suscripción) realizada en la fecha almacenada en el campo tsDate.

### NmsDelivery {#NmsDelivery}

Esta tabla coincide con el **nms:delivery** esquema.

Cada registro de esta tabla representa un **acción de envío** o una **plantilla de envíos**. Contiene todos los parámetros necesarios para realizar envíos (el destinatario, el contenido, etc.). Los registros de envío (difusión) (NmsBroadLog) y las URL de seguimiento asociadas (NmsTrackingUrl) se crean durante la fase de análisis (consulte a continuación para obtener más información sobre ambas tablas).

Hay un índice único en el campo que representa el nombre interno de la entrega o el escenario de sInternalName. La entrega está vinculado a una carpeta de ejecución (la clave externa es iFolderProcessId. Para obtener más información, consulte [XtkFolder](#XtkFolder)).

### XtkFolder {#XtkFolder}

Contiene **todas las carpetas del árbol** visible en el **Navegación** de la consola.

Las carpetas están escritas: el valor del campo sModel especifica el tipo de datos que se pueden contener en la carpeta. Este campo también permite a la consola del cliente mostrar los datos correctamente con los formularios correspondientes. Los valores posibles de este campo se definen en navTree.

El árbol se administra mediante los campos iParentId e iChildCount. El campo sFullName indica la ruta completa de la carpeta en el árbol. Finalmente, hay un índice único en el campo que representa el nombre interno de la carpeta sName.

## Envío y seguimiento {#delivery-and-tracking}

Este conjunto de tablas está vinculado al **Envío** , que permite supervisar los envíos y los problemas que puedan ser detectados cuando se envían mensajes. Para obtener más información, consulte [Seguimiento de entregas](../../delivery/using/about-delivery-monitoring.md). Para obtener más información sobre el seguimiento, consulte [Seguimiento de mensajes](../../delivery/using/about-message-tracking.md).

![](assets/data-model_delivery.png)

**NmsBroadLogMsg**: Esta tabla coincide con el **nms:broadLogMsg** esquema. Es una extensión de la tabla de registro de envíos.

## Administración de campañas {#campaign-management}

Este conjunto de tablas está vinculado al **Campañas de marketing** , que permite definir, optimizar, ejecutar y analizar las comunicaciones y las campañas de marketing. Para obtener más información, consulte [Acerca de las campañas de marketing](../../campaign/using/designing-marketing-campaigns.md).

![](assets/data-model_campaign.png)

* **NmsOperation**: Esta tabla coincide con el **nms:operation** esquema. Contiene los datos de las campañas de marketing.
* **NmsDeliveryOutline**: Esta tabla coincide con el **nms:deliveryOutline** esquema. Contiene las propiedades ampliadas del envío (descripción del envío).
* **NmsDlvOutlineItem**: Esta tabla coincide con el **nms:dlvOutlineItem** esquema. Contiene los artículos de una descripción del envío.
* **NmsDeliveryCustomization**: Esta tabla coincide con el **nms:deliveryCustomization** esquema. Contiene los campos de personalización de una entrega.
* **NmsBudget**: Esta tabla coincide con el **nms:budget** esquema. Contiene los datos de un presupuesto sobre una campaña, un plan, un programa, una tarea o envíos.
* **NmsDocument**: Esta tabla coincide con el **nms:documento** esquema. Contiene los documentos de marketing de la campaña en forma de archivos (imágenes, archivos de Excel o Word, etc.)
* **XtkWorkflow**: Esta tabla coincide con el **xtk:workflow** esquema. Contiene objetivos de campaña.
* **NmsTask**: Esta tabla coincide con el **nms:task** esquema. Contiene la definición de una tarea de marketing.
* **NmsAsset**: Esta tabla coincide con el **nms:asset** esquema. Contiene la definición de un recurso de marketing.

## Coherencia de comunicación {#communication-consistency}

Este conjunto de tablas está vinculado al **Optimización de campaña** , que permite controlar, filtrar y monitorizar la entrega de envíos. Para obtener más información, consulte [Acerca de las tipologías de campaña](../../campaign-opt/using/about-campaign-typologies.md).

![](assets/data-model_typology.png)

* **NmsTypologyRule**: Esta tabla coincide con el **nms:typologyRule** esquema. Contiene las reglas que se aplican a las entregas según las tipologías.
* **NmsTypology**: Esta tabla coincide con el **nms:tipología** esquema. Contiene el conjunto de reglas que se deben aplicar a los envíos que coinciden con la tipología.
* **NmsTypologyRuleRel**: Esta tabla coincide con el **nms:typologyRuleRel** esquema. Contiene las relaciones entre las tipologías y sus reglas.
* **NmsVolumeLine**: Esta tabla coincide con el **nms:volumeLine** esquema. Contiene el conjunto de líneas de disponibilidad de las reglas de capacidad.
* **NmsVolumeConsumed**: Esta tabla coincide con el **nms:volumeConsumed** esquema. Contiene todas las líneas de consumo de las reglas de capacidad.

## Gestión de respuestas {#response-management}

Este conjunto de tablas está vinculado al **Gestor de respuestas** , que permite medir el éxito y la rentabilidad de las campañas de marketing u ofrecer propuestas para todos los canales de comunicación. Para obtener más información, consulte [Acerca del gestor de respuestas](../../response/using/about-response-manager.md).

![](assets/data-model_response.png)

### NmsRemaHypothesis {#NmsRemaHypothesis}

Esta tabla coincide con el **nms:remaHypothesis** esquema. Contiene la definición de la hipótesis de medición.

Esta tabla contiene información significativa almacenada en XML, como:

**Contexto de ejecución (información almacenada en XML)**

El contexto de ejecución rellena las tablas y campos que se deben tener en cuenta para el cálculo de la medición, a saber:
* El esquema de almacenamiento del registro de reacción nms:remaMatchRcp.
* El esquema de tabla de transacción (compras por ejemplo).
* El esquema de consulta, que le permite definir la tabla de inicio de las condiciones de hipótesis.
* Los vínculos a personas, que le permiten identificar a la persona en función del esquema de consulta.
* La fecha de transacción. Este campo no es obligatorio, pero se recomienda utilizarlo para restringir el perímetro de cálculo.
* The transaction amount: es un campo opcional para calcular automáticamente los indicadores de ingresos.

**Perímetro de la hipótesis (información almacenada en XML)**

El perímetro de la hipótesis consiste en filtrar la hipótesis en función de la tabla del esquema de consulta.

**Script de sobrecarga de hipótesis (información almacenada en XML)**

El script de sobrecarga de hipótesis es un código JavaScript que permite sobrecargar el contenido de la hipótesis durante la ejecución.

**Indicadores de medición**

Los siguientes indicadores se actualizan automáticamente durante la ejecución de hipótesis:

* Número de reacciones: **iTransaction**. Número de líneas de la tabla de registros de reacción.
* Número de contactos: **iContactReacted**. Número distinto de contactos objetivo en la hipótesis.
* Recuento de grupos de control: **iProofReacted**. Distinto número de contactos de grupo de control objetivo en la hipótesis.
* Tasa de respuesta contactada: **dContactReactedRate**. Tasa de respuesta de los contactos objetivo en la hipótesis.
* Tasa de respuesta del grupo de control: **dProofReactedRate**. Tasa de respuesta del grupo de control de la hipótesis.
* Ingresos totales de la población contactada: **dContactReactedTotalAmount**. Ingresos totales de los contactos objeto de la hipótesis.
* Ingresos medios del grupo de control: **dContactReactedAvgAmount**. Ingresos promedio de los contactos del grupo de control objetivo en la hipótesis.
* Ingresos totales del grupo de control: **dProofReactedTotalAmount**. Ingresos totales del grupo de control de la hipótesis.
* Ingresos medios del grupo de control: **dProofReactedAvgAmount**. Ingresos medios del grupo de control de hipótesis.
* Margen total por contacto: **dContactReactedTotalMargin**. Margen total por contacto previsto en la hipótesis.
* Margen promedio por contacto: **dContactReactedAvgMargin**. Margen promedio por contacto previsto en la hipótesis.
* Margen total del grupo de control: **dProofReactedTotalMargin**. Margen total del grupo de control objeto de la hipótesis.
* Margen medio del grupo de control: **dProofReactedAvgMargin**. Margen medio del grupo de control objeto de la hipótesis.
* Ingresos adicionales: **AdditionalAmount**. (Average revenue of contacted - Average revenue of control group) * Número de contactos.
* Margen adicional: **AdditionalMargin**. (Average margin of contacted: margen medio del grupo de control)/número de contactos.
* Coste medio por contacto (expresión SQL). Coste calculado de la entrega/número de contactos.
* ROI (expresión SQL). Coste calculado de la entrega / Margen total de los contactos.
* ROI efectivo (expresión SQL). Coste calculado de la entrega/margen adicional.
* Relevancia: **iSignificativy** (expresión SQL). Contiene valores de 0 a 3 según la importancia de la campaña.

### NmsRemaMatchRcp {#NmsRemaMatchRcp}

Esta tabla coincide con el **nms:remaMatchRcp** esquema.

Contiene un registro que representa la reacción de un individuo a una hipótesis determinada. Estos registros se crearon durante la ejecución de hipótesis.

## Simulación y envío {#simulation-and-delivery}

Este conjunto de tablas está vinculado al **Simulación** , que permite probar la distribución de ofertas pertenecientes a una categoría o a un entorno antes de enviar la propuesta a los destinatarios. Para obtener más información, consulte [Simulación de ofertas](../../interaction/using/about-offers-simulation.md).

![](assets/data-model_simulation.png)

* **NmsSimulation**: Esta tabla coincide con el **nms:simulation** esquema. Representa una simulación para un conjunto de envíos u ofertas en una población determinada.
* **NmsDlvSimulationRel**: Esta tabla coincide con el **nms:dlvSimulationRel** esquema. Contiene la lista de envíos que se tienen en cuenta en la simulación. El ámbito de la simulación se almacena en XML.
* **NmsOfferSimulationRel**: Esta tabla coincide con el **nms:offerSimulationRel** esquema. Permite vincular una simulación con una oferta.

## Módulo de interacción {#interaction-module}

Este conjunto de tablas está vinculado al **Interacción** , que permite responder en tiempo real durante una interacción con un contacto determinado mediante la realización de una o varias ofertas adaptadas. Para obtener más información, consulte [Interacción y gestión de ofertas](../../interaction/using/interaction-and-offer-management.md).

* **NmsOffer**: Esta tabla coincide con el **nms:oferta** esquema. Contiene la definición de cada oferta de marketing.
* **NmsPropositionRcp**: Esta tabla coincide con el **nms:propositionRcp** esquema. Contiene el registro en canales múltiples de las propuestas de marketing enviadas a cada individuo. El registro se crea cuando se prepara o se realiza una propuesta a un individuo de forma eficaz.
* **NmsOfferSpace**: Esta tabla coincide con el **nms:offerSpace** esquema. Contiene la definición de las ubicaciones en las que se realizan las propuestas.
* **NmsOfferContext**: Esta tabla coincide con el **nms:offerContext** esquema. Contiene criterios adicionales sobre la aplicabilidad de la propuesta y la definición de la fórmula de cálculo del peso.
* **NmsOfferView**: Esta tabla coincide con el **nms:offerView**. Contiene las representaciones de la oferta.
* **NmsOfferCategory**: Esta tabla coincide con el **nms:offerCategory**. Contiene las categorías de oferta.
* **NmsOfferEnv**: Esta tabla coincide con el **nms:offerEnv**. Contiene los entornos de oferta.

## Módulo del centro de mensajes {#message-center-module}

El siguiente conjunto de tablas está vinculado al **Mensajería transaccional** (Message Center), que permite gestionar comunicaciones individuales y únicas enviadas a un usuario y generadas a partir de eventos activados desde sistemas de información. Para obtener más información, consulte [Acerca de la mensajería transaccional](../../message-center/using/about-transactional-messaging.md).

### NmsRtEvent {#NmsRtEvent}

![](assets/data-model_message-center_rt.png)

Esta tabla coincide con el **nms:rtEvent** esquema. Contiene una definición de eventos en tiempo real.

### NmsBatchEvent {#NmsBatchEvent}

![](assets/data-model_message-center_batch.png)

Esta tabla coincide con el **nms:batchEvent** esquema. Contiene la definición de eventos por lote.

<!--## Microsites Module {#microsites-module}

This set of tables is linked to the **Web applications** functionality, which allows to create and publish dynamic and interactive web applications with data from the database and content adapted to the rights of the connected user. For more on this, see [About web applications](../../web/using/about-web-applications.md).

![](assets/data-model_microsites.png)

* **NmsTrackingUrl**: This table matches the **nms:trackingUrl** schema.

* **NmsPurl**: This table matches the **nms:purl** schema.-->

## Módulo NMAC {#nmac-module}

Este conjunto de tablas está vinculado al **Canal de aplicaciones móviles**, que permite enviar notificaciones personalizadas a terminales iOS y Android a través de aplicaciones. Para obtener más información, consulte [Acerca del canal de aplicaciones móviles](../../delivery/using/about-mobile-app-channel.md).

* **NmsMobileApp**: Esta tabla coincide con el **nms:mobileApp** esquema. Contiene las aplicaciones móviles definidas en Adobe Campaign.
* **NmsAppSubscription**: Esta tabla coincide con el **nms:appSubscription** esquema. Contiene la información de los suscriptores sobre una o más aplicaciones.
* **NmsAppSubscriptionRcp**: Esta tabla coincide con el **nms:appSubscriptionRcp** esquema. Permite vincular a los visitantes que se han suscrito a una aplicación con la tabla de destinatarios.
* **NmsExcludeLogAppSubRcp**: Esta tabla coincide con el **nms:excludeLogAppSubRcp** esquema.
* **NmsTrackingLogAppSubRcp**: Esta tabla coincide con el **nms:trackingLogAppSubRcp** esquema.
* **NmsBroadLogAppSubRcp**: Esta tabla coincide con el **nms:broadLogAppSubRcp** esquema.

## Módulo de marketing social {#social-marketing-module}

Este conjunto de tablas está vinculado al **Administración de redes sociales** , que permite interactuar con los clientes y clientes potenciales a través de Facebook y Twitter. Para obtener más información, consulte [Acerca del marketing social](../../social/using/about-social-marketing.md).

![](assets/data-model_social.png)

* **NmsVisitor**: Esta tabla coincide con el **nms:visitor** esquema. Contiene información sobre los visitantes.
* **NmsVisitorSub**: Esta tabla coincide con el **nms:visitorSub** esquema. Permite vincular a un visitante a los servicios a los que se ha suscrito (Twitter o Facebook).
* **NmsFriendShipRel**: Esta tabla coincide con el **nms:friendRel** esquema. Permite vincular visitantes con sus amigos en el contexto del servicio de Facebook.
* **NmsVisitorInterestRel**: Esta tabla coincide con el **nms:visitorInterestRel** esquema. Permite vincular los visitantes y sus intereses.
* **NmsInterest**: Esta tabla coincide con el **nms:interest** esquema. Contiene la lista de intereses de cada visitante.
