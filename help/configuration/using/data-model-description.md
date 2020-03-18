---
title: Descripción del modelo de datos de Adobe Campaign Classic
description: Este documento describe el modelo de datos de Adobe Campaign Classic.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 828c95aaa4b1d0d9507129edb164ddf978c363c1

---


# Descripción del modelo de datos de campaña{#data-model-description}

Adobe Campaign incluye un modelo de datos predefinido. Esta sección proporciona algunos detalles sobre las tablas integradas del modelo de datos de Adobe Campaign y su interacción.

Para acceder a la descripción de cada tabla, vaya a **[!UICONTROL Admin > Configuration > Data schemas]**, seleccione un recurso de la lista y haga clic en la **[!UICONTROL Documentation]** ficha.

![](assets/data-model_documentation-tab.png)

>[!NOTE]
>
>La estructura física y lógica de los datos que se llevan en la aplicación se describe en XML. Obedece a una gramática específica de Adobe Campaign, denominada esquema. Para obtener más información sobre los esquemas de Adobe Campaign, lea esta [sección](../../configuration/using/about-schema-reference.md).

## Descripción de las tablas principales {#description-main-tables}

Adobe Campaign se basa en una base de datos relacional que contiene tablas vinculadas entre sí.

El diagrama siguiente muestra las uniones entre las tablas comerciales principales del modelo de datos de Adobe Campaign con los campos principales de cada una.

<!--![](assets/data-model_diagram.png)-->

![](assets/data-model_simplified-diagram.png)

El modelo de datos predefinido de Adobe Campaign incluye las siguientes tablas principales.

### NmsRecipient {#NmsRecipient}

Esta tabla coincide con el esquema **nms:destination** .

Es la tabla predeterminada que se utiliza para los **destinatarios de los envíos**. Como resultado, contiene la información necesaria para las entregas a través de los distintos canales:

* sEmail: dirección de correo electrónico.
* iEmailFormat: formato preferido para correos electrónicos (1 para Texto, 2 para HTML y 0 si no está definido).
* sAddress1, sAddress2, sAddress3, sAddress4, sZipCode y sCity se utilizan para generar la dirección postal (de acuerdo con el estándar AFNOR XPZ 10-011 de mayo de 1997).
* sPhone, sMobilePhone, sFax contienen los números de teléfono, teléfono móvil y fax respectivamente.
* iBlackList es el indicador de exclusión predeterminado utilizado para los perfiles (1 significa &quot;sin suscripción&quot;, 0 en caso contrario).

El campo iFolderId es la clave externa que vincula al destinatario con su carpeta de ejecución. For more on this, see [XtkFolder](#XtkFolder).

El campo sCountryCode es el código ISO 3166-1 Alpha 2 (2 caracteres) del país asociado al destinatario. Este campo es en realidad una clave externa en la tabla de referencia de país (NmsCountry), que contiene las etiquetas de país y otros datos de código de país. Si el país no se rellena, el valor &#39;XX&#39; se almacena (y se utiliza en lugar de un registro de ID cero).

Para obtener más información sobre la tabla Destinatario, consulte esta [sección](../../configuration/using/about-data-model.md#default-recipient-table).

### NmsGroup {#NmsGroup}

Esta tabla coincide con el esquema **nms:group** .

Permite crear grupos **estadísticos de destinatarios**. Existe una relación de varios a varios entre destinatarios y grupos. Por ejemplo, un destinatario puede pertenecer a varios grupos y un grupo puede contener varios destinatarios. Los grupos se pueden crear manualmente, mediante una importación o mediante el objetivo de envío. Los grupos suelen utilizarse como objetivos de entrega. Hay un índice único en el campo que representa el nombre interno del grupo sName. El grupo está vinculado a una carpeta (la clave es iFolderId. For more on this, see [XtkFolder](#XtkFolder)).

### NmsRcpGrpRel {#NmsRcpGrpRel}

La tabla de relación NmsRcpGrpRel sólo contiene los dos campos correspondientes a los identificadores de las tablas vinculadas iRecipientId e iGroupId.

### NmsService {#NmsService}

Esta tabla coincide con el esquema **nms:service** .

Los servicios son entidades similares a los grupos (grupos de destinatarios estáticos), con la salvedad de que distribuyen más información y facilitan la gestión de suscripciones y cancelaciones de suscripciones mediante formularios.

Hay un índice único en el campo que representa el nombre interno del servicio sName. El servicio está vinculado a una carpeta (la clave es iFolderId. For more on this, see [XtkFolder](#XtkFolder)). Finalmente, el campo iType especifica el canal de entrega de este servicio (0 para correo electrónico, 1 para SMS, 2 para teléfono, 3 para correo directo y 4 para fax).

### NmsSubscription {#NmsSubscription}

Esta tabla coincide con el esquema **nms:subscription** .

Permite administrar las suscripciones de los destinatarios a los servicios de información.

### NmsSubHisto {#NmsSubHisto}

Esta tabla coincide con el esquema **nms:subHisto** .

Si las suscripciones se administran mediante formularios web o la interfaz de la aplicación, todas las suscripciones y las suscripciones se registran en la tabla NmsSubHisto. El campo iAction especifica la acción (0 para la cancelación de suscripción y 1 para la suscripción) que se realiza en la fecha almacenada en el campo tsDate.

### NmsDelivery {#NmsDelivery}

Esta tabla coincide con el esquema **nms:delivery** .

Cada registro de esta tabla representa una acción **de** entrega o una plantilla **de** entrega. Contiene todos los parámetros necesarios para realizar envíos (el objetivo, el contenido, etc.). Los registros de envío (difusión) (NmsBroadLog) y las direcciones URL de seguimiento asociadas (NmsTrackingUrl) se crean durante la fase de análisis (consulte a continuación para obtener más detalles sobre ambas tablas).

Hay un índice único en el campo que representa el nombre interno de la entrega o escenario sInternalName. La entrega está vinculada a una carpeta de ejecución (la clave externa es iFolderProcessId. For more on this, see [XtkFolder](#XtkFolder)).

### XtkFolder {#XtkFolder}

Contiene **todas las carpetas del árbol** visibles en la ficha **Navegación** de la consola.

Las carpetas están escritas: el valor del campo sModel especifica el tipo de datos que se pueden incluir en la carpeta. Este campo también permite que la consola de cliente muestre los datos correctamente con los formularios correspondientes. Los valores posibles de este campo se definen en navTree.

El árbol se administra mediante los campos iParentId e iChildCount. El campo sFullName proporciona la ruta completa de la carpeta en el árbol. Finalmente, hay un índice único en el campo que representa el nombre interno de la carpeta sName.

## Envío y seguimiento {#delivery-and-tracking}

![](assets/data-model_delivery.png)

**NmsBroadLogMsg**: Esta tabla coincide con el esquema **nms:wideLogMsg** . Es una extensión de la tabla del registro de envíos.

## Administración de campañas {#campaign-management}

![](assets/data-model_campaign.png)

* **NmsOperation**: Esta tabla coincide con el esquema **nms:operation** . Contiene los datos de las campañas de marketing.
* **NmsDeliveryOutline**: Esta tabla coincide con el esquema **nms:deliveryOutline** . Contiene las propiedades extendidas de la entrega (contorno de entrega).
* **NmsDlvOutlineItem**: Esta tabla coincide con el esquema **nms:dlvOutlineItem** . Contiene los artículos de un esquema de entrega.
* **NmsDeliveryCustomization**: Esta tabla coincide con el esquema **nms:deliveryCustomization** . Contiene los campos de personalización de una entrega.
* **NmsBudget**: Esta tabla coincide con el esquema **nms:budget** . Contiene los datos de un presupuesto sobre una campaña, un plan, un programa, una tarea o entregas.
* **NmsDocument**: Esta tabla coincide con el esquema **nms:document** . Contiene los documentos de marketing de la campaña en forma de archivos (imágenes, archivos de Excel o Word, etc.)
* **XtkWorkflow**: Esta tabla coincide con el esquema **xtk:workflow** . Contiene objetivos de campaña.
* **NmsTask**: Esta tabla coincide con el esquema **nms:task** . Contiene la definición de una tarea de marketing.
* **NmsAsset**: Esta tabla coincide con el esquema **nms:asset** . Contiene la definición de un recurso de marketing.

## Coherencia de la comunicación {#communication-consistency}

![](assets/data-model_typology.png)

* **NmsTypologyRule**: Esta tabla coincide con el esquema **nms:typologyRule** . Contiene las reglas que se aplican a las entregas en función de las tipologías.
* **NmsTypology**: Esta tabla coincide con el esquema **nms:typology** . Contiene el conjunto de reglas que se aplicarán a las entregas que coincidan con la tipología.
* **NmsTypologyRuleRel**: Esta tabla coincide con el esquema **nms:typologyRuleRel** . Contiene las relaciones entre las tipologías y sus reglas.
* **NmsVolumeLine**: Esta tabla coincide con el esquema **nms:volumeLine** . Contiene el conjunto de líneas de disponibilidad de las reglas de capacidad.
* **NmsVolumeConsumed**: Esta tabla coincide con el esquema **nms:volumeConsumed** . Contiene todas las líneas de consumo de las reglas de capacidad.

## Administración de respuestas {#response-management}

![](assets/data-model_response.png)

### NmsRemaHypoesis {#NmsRemaHypothesis}

Esta tabla coincide con el esquema **nms:remaHypothe** . Contiene la definición de la hipótesis de medición.

Esta tabla contiene información importante almacenada en XML, que incluye:

**Contexto de ejecución (información almacenada en XML)**

El contexto de ejecución rellena las tablas y los campos que se deben tener en cuenta para el cálculo de la medición, a saber:
* Esquema de almacenamiento del registro de reacción nms:remaMatchRcp.
* Esquema de tabla de transacciones (compras, por ejemplo).
* Esquema de consulta, que permite definir la tabla de inicio de las condiciones de hipótesis.
* Vínculos a individuos que permiten identificar al individuo en función del esquema de consulta.
* La fecha de transacción. Este campo no es obligatorio, pero se recomienda utilizarlo para restringir el perímetro de cálculo.
* El importe de la transacción: es un campo opcional para calcular automáticamente los indicadores de ingresos.

**perímetro de hipótesis (información almacenada en XML)**

El perímetro de hipótesis consiste en filtrar la hipótesis basándose en la tabla del esquema de consulta.

**Secuencia de comandos de sobrecarga de hipótesis (información almacenada en XML)**

La secuencia de comandos de sobrecarga de hipótesis es un código JavaScript que le permite sobrecargar el contenido de la hipótesis durante la ejecución.

**Indicadores de medición**

Los siguientes indicadores se actualizan automáticamente durante la ejecución de la hipótesis:

* Número de reacciones: **iTransaction**. Número de líneas en la tabla de registros de reacciones.
* Número de usuarios contactados: **iContactReaccionó**. Número específico de contactos objetivo en la hipótesis.
* Recuento de grupos de control: **iProofReaccionó**. Número específico de contactos del grupo de control objetivo en la hipótesis.
* Tasa de respuesta de contacto: **dContactReactRate**. Tasa de respuesta de los contactos objetivo en la hipótesis.
* Tasa de respuesta del grupo de control: **dProofReactRate**. Tasa de respuesta del grupo de control de hipótesis.
* Ingresos totales de la población contactada: **dContactReactTotalAmount**. Ingresos totales de los contactos objetivo en la hipótesis.
* Ingresos medios del grupo de control: **dContactReactAvgAmount**. Ingresos medios de los contactos del grupo de control objetivo en la hipótesis.
* Ingresos totales del grupo de control: **dProofReactTotalAmount**. Ingresos totales del grupo de control de hipótesis.
* Ingresos medios del grupo de control: **dProofReactAvgAmount**. Ingresos medios del grupo de control de hipótesis.
* Margen total por contacto: **dContactReactTotalMargin**. Margen total por contacto objetivo en la hipótesis.
* Margen promedio por contacto: **dContactReactAvgMargin**. Margen medio por contacto objetivo en la hipótesis.
* Margen total del grupo de control: **dProofReactTotalMargin**. Margen total del grupo de control objetivo en la hipótesis.
* Margen medio del grupo de control: **dProofReactAvgMargin**. Margen medio del grupo de control objetivo en la hipótesis.
* Ingresos adicionales: **dAdditionalAmount**. (Ingresos medios del grupo de control contactado - Ingresos medios del grupo de control) * Número de usuarios contactados.
* Margen adicional: **dAdditionalMargin**. (Margen medio de contacto - Margen medio del grupo de control) / Número de usuarios contactados.
* Costo promedio por contacto (expresión SQL). Coste calculado de la entrega / Número de personas contactadas.
* ROI (expresión SQL). Coste calculado de la entrega / Margen total de contacto.
* ROI efectivo (expresión SQL). Coste calculado de la entrega / Margen adicional.
* Significado: **iSignificative** (expresión SQL). Contiene valores de 0 a 3 según la importancia de la campaña.

### NmsRemaMatchRcp {#NmsRemaMatchRcp}

Esta tabla coincide con el esquema **nms:remaMatchRcp** .

Contiene un registro que representa la reacción de un individuo a una hipótesis determinada. Estos registros se crearon durante la ejecución de la hipótesis.

## Simulación y entrega {#simulation-and-delivery}

![](assets/data-model_simulation.png)

* **NmsSimulation**: Esta tabla coincide con el esquema **nms:simulation** . Representa una simulación para un conjunto de entregas u ofertas en una población determinada.
* **NmsDlvSimulationRel**: Esta tabla coincide con el esquema **nms:dlvSimulationRel** . Contiene la lista de entregas que se tienen en cuenta en la simulación. El ámbito de la simulación se almacena en XML.
* **NmsOfferSimulationRel**: Esta tabla coincide con el esquema **nms:offerSimulationRel** . Permite vincular una simulación con una oferta.

## Módulo de interacción {#interaction-module}

* **NmsOffer**: Esta tabla coincide con el esquema **nms:offer** . Contiene la definición de cada oferta de mercadotecnia.
* **NmsPropositionRcp**: Esta tabla coincide con el esquema **nms:propositionRcp** . Contiene el registro multicanal de las proposiciones de marketing enviadas a cada individuo. El registro se crea cuando se prepara una propuesta o se hace efectivamente a un individuo.
* **NmsOfferSpace**: Esta tabla coincide con el esquema **nms:offerSpace** . Contiene la definición de los lugares en que se formulan las propuestas.
* **NmsOfferContext**: Esta tabla coincide con el esquema **nms:offerContext** . Contiene criterios adicionales sobre la aplicabilidad de la propuesta, así como la definición de la fórmula de cálculo de peso.
* **NmsOfferView**: Esta tabla coincide con **nms:offerView**. Contiene las representaciones de la oferta.
* **NmsOfferCategory**: Esta tabla coincide con **nms:offerCategory**. Contiene las categorías de ofertas.
* **NmsOfferEnv**: Esta tabla coincide con **nms:offerEnv**. Contiene los entornos de ofertas.

## Módulo de centro de mensajes {#message-center-module}

### NmsRtEvent {#NmsRtEvent}

![](assets/data-model_message-center_rt.png)

Esta tabla coincide con el esquema **nms:rtEvent** . Contiene una definición de eventos en tiempo real.

### NmsBatchEvent {#NmsBatchEvent}

![](assets/data-model_message-center_batch.png)

Esta tabla coincide con el esquema **nms:batchEvent** . Contiene la definición de eventos por lote.

## Módulo de micrositios {#microsites-module}

![](assets/data-model_microsites.png)

* **NmsTrackingUrl**: Esta tabla coincide con el esquema **nms:trackingUrl** .

* **NmsPurl**: Esta tabla coincide con el esquema **nms:purl** .

## Módulo NMAC {#nmac-module}

* **NmsMobileApp**: Esta tabla coincide con el esquema **nms:mobileApp** . Contiene las aplicaciones móviles definidas en Adobe Campaign.
* **NmsAppSubscription**: Esta tabla coincide con el esquema **nms:appSubscription** . Contiene la información de los suscriptores con respecto a una o más aplicaciones.
* **NmsAppSubscriptionRcp**: Esta tabla coincide con el esquema **nms:appSubscriptionRcp** . Permite vincular a los visitantes que se suscribieron a una aplicación con la tabla de destinatarios.
* **NmsExcludeLogAppSubRcp**: Esta tabla coincide con el esquema **nms:excludeLogAppSubRcp** .
* **NmsTrackingLogAppSubRcp**: Esta tabla coincide con el esquema **nms:trackingLogAppSubRcp** .
* **NmsBroadLogAppSubRcp**: Esta tabla coincide con el esquema **nms:wideLogAppSubRcp** .

## Módulo de mercadotecnia social {#social-marketing-module}

![](assets/data-model_social.png)

* **NmsVisitor**: Esta tabla coincide con el esquema **nms:visitor** . Contiene información sobre los visitantes.
* **NmsVisitorSub**: Esta tabla coincide con el esquema **nms:visitorSub** . Le permite vincular a un visitante a los servicios a los que se ha suscrito (Twitter o Facebook).
* **NmsFriendShipRel**: Esta tabla coincide con el esquema **nms:friendlyRel** . Permite vincular a los visitantes con sus amigos en el contexto del servicio de Facebook.
* **NmsVisitorInterestRel**: Esta tabla coincide con el esquema **nms:visitorInterestRel** . Le permite vincular a los visitantes y sus intereses.
* **NmsInterest**: Esta tabla coincide con el esquema **nms:interest** . Contiene la lista de intereses de cada visitante.