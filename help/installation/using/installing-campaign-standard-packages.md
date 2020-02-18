---
title: Instalación de paquetes estándar de Campaign Classic
seo-title: Instalación de paquetes estándar de Campaign Classic
description: Instalación de paquetes estándar de Campaign Classic
seo-description: null
page-status-flag: never-activated
uuid: 1cba9487-52fc-442f-ae99-f8a2c157f25e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: dd8f9adf-208c-42d9-b1a7-bfc8a690687e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a37daa8e31afd3d2ab7d5b70bd8ae02c59ce9ee0

---


# Instalación de paquetes estándar de Campaign Classic{#installing-campaign-standard-packages}

## Acerca de los paquetes estándar {#campaign-standard-packages}

Los paquetes son un conjunto de características que se pueden instalar según sus necesidades. Le permitirán agregar más opciones a su instancia.

>[!CAUTION]
>
>Sólo puede instalar los paquetes correspondientes a las opciones mencionadas en su contrato de licencia.
>
>Una vez instalado un paquete, no podrá desinstalarlo. La instalación de un nuevo paquete puede afectar a toda la plataforma: debe probarse y validarse antes de la implementación final.

Para instalar un paquete estándar:

1. Acceda al asistente de importación de paquetes desde **[!UICONTROL Tools > Advanced > Package import...]** la consola de cliente de Adobe Campaign.
1. Select **[!UICONTROL Install a standard package]**.
1. En la lista que aparece, compruebe los paquetes que desea instalar.
   >[!NOTE]
   >
   >Si un paquete está atenuado, no puede instalarlo. Significa que ya está instalado o que no es compatible con su instancia. Por ejemplo, no puede instalar el paquete de plataforma **de** fuentes intermedias en una instancia de marketing. Encontrará esta información en la tabla siguiente.
1. Haga clic en **[!UICONTROL Next]**, luego **[!UICONTROL Start]** para iniciar la instalación del paquete.

   Una vez instalados los paquetes, la barra de progreso muestra el **100%** y puede ver el siguiente mensaje en los registros de instalación: **[!UICONTROL Installation of packages successful]**.

1. **[!UICONTROL Close]** la ventana de instalación.

Los paquetes ya están instalados.

### Lista de paquetes listos para usar {#list-of-standard-packages}

La siguiente tabla enumera todos los paquetes estándar con su descripción, el tipo de instancia en el que pueden instalarse (Marketing, Mid, etc.) e información adicional.

<table> 
 <thead> 
  <tr> 
   <th> Paquete </th> 
   <th> Descripción </th> 
   <th> Tipo de instancia </th> 
   <th> Más información </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Envío<br /> </td> 
   <td> Supervisa las entregas y los problemas que se detectan al enviar mensajes.<br /> </td> 
   <td> Todos</td> 
   <td> <a href="../../delivery/using/monitoring-a-delivery.md">Más información</a></td> 
  </tr> 
  <tr> 
   <td> Campañas de marketing (campaña)<br /> </td> 
   <td> Define, optimiza, ejecuta y analiza las campañas de comunicación y marketing.<br /> </td> 
   <td> Mercadotecnia</td> 
   <td> <a href="../../campaign/using/designing-marketing-campaigns.md">Más información</a> </td> 
  </tr> 
  <tr> 
   <td> Marketing resources (MRM)<br /> </td> 
   <td> Controla las acciones de mercadotecnia en modo colaborativo proporcionando administración y seguimiento de las tareas, presupuestos y recursos de mercadotecnia.<br /> </td> 
   <td> Mercadotecnia</td> 
   <td> <a href="../../campaign/using/about-marketing-resource-management.md">Más información</a> </td> 
  </tr> 
  <tr> 
   <td> Motor de oferta (interacción)<br /> </td> 
   <td> Responds in real time during an interaction with a given contact (a customer or target) by making them a single or several adapted offers. <br /> </td> 
   <td> Todos<br /> </td> 
   <td> Opcional, <a href="../../interaction/using/interaction-and-offer-management.md">Más información</a></td> 
  </tr> 
  <tr> 
   <td> Control del motor de oferta con instancia de ejecución<br /> </td> 
   <td> </td> 
   <td> Mercadotecnia<br /> </td> 
   <td> Opcional</td> 
  </tr> 
  <tr> 
   <td> Motor de oferta para instancias de ejecución<br /> </td> 
   <td> </td> 
   <td> Mid, Ejecución <br /> </td> 
   <td> Opcional</td> 
  </tr> 
  <!--tr> 
   <td> Lead Management (Leads) (deprecated)<br /> </td> 
   <td> Simplifies the process of building and maintaining the entire leads management life cycle. <br /> </td> 
   <td> Yes<br /> </td> 
   <td> Optional, <a href="https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html">Learn More</a> </td> 
  </tr--> 
  <tr> 
   <td> Redes sociales (Social Marketing) <br /> </td> 
   <td> Sincroniza Adobe Campaign con Twitter y Facebook.<br /> </td> 
   <td> Todos</td> 
   <td> <a href="../../social/using/starting-workflows.md">Más información</a> </td> 
  </tr> 
  <tr> 
   <td> Control de mensajes transaccionales (Centro de mensajes - Control)<br /> </td> 
   <td> Gestiona los mensajes de activación generados a partir de eventos activados desde sistemas de información.<br /> </td> 
   <td> Mercadotecnia<br /> </td> 
   <td> Opcional, <a href="../../message-center/using/about-transactional-messaging.md">Más información</a> </td> 
  </tr> 
  <tr> 
   <td> Ejecución de mensajes transaccionales (Centro de mensajes - Ejecución) <br /> </td> 
   <td> Garantiza una mayor disponibilidad y una mejor administración de la carga.<br /> </td> 
   <td> Ejecución<br /> </td> 
   <td> Opcional, <a href="../../message-center/using/about-transactional-messaging.md">Más información</a> </td> 
  </tr> 
  <tr> 
   <td> Canal LINE<br /> </td> 
   <td> Envía entregas mediante el canal LINE con Adobe Campaign,<br /> </td> 
   <td> Todos<br /> </td> 
   <td> Opcional, obligatorio en el centro de mensajes</td> 
  </tr> 
  <tr> 
   <td> Canal de correo directo<br /> </td> 
   <td> Envía entregas mediante el canal de correo directo con Adobe Campaign.<br /> </td> 
   <td> Todos<br /> </td> 
   <td> Opcional, <a href="../../delivery/using/about-direct-mail-channel.md">Más información</a> </td> 
  </tr> 
  <tr> 
   <td> Canal móvil (SMS) <br /> </td> 
   <td> Envía entregas mediante el canal móvil/SMS con Adobe Campaign.<br /> </td> 
   <td> Todos<br /> </td> 
   <td> Opcional, <a href="../../delivery/using/sms-channel.md">Más información</a> </td> 
  </tr> 
  <tr> 
   <td> Canal telefónico<br /> </td> 
   <td> Envía entregas mediante el canal de teléfono con Adobe Campaign.<br /> </td> 
   <td> Todos<br /> </td> 
   <td> Opcional</td> 
  </tr> 
  <tr> 
   <td> Canal de fax<br /> </td> 
   <td> Envía entregas mediante el canal de fax con Adobe Campaign.<br /> </td> 
   <td> Todos<br /> </td> 
   <td> Opcional</td> 
  </tr> 
  <tr> 
   <td> Canal de aplicaciones móviles<br /> </td> 
   <td> Utiliza la plataforma de Adobe Campaign para enviar notificaciones personalizadas a los terminales de iOS y Android mediante aplicaciones. <br /> </td> 
   <td> Todos<br /> </td> 
   <td> Opcional, <a href="../../delivery/using/about-mobile-app-channel.md">Más información</a> </td> 
  </tr> 
  <tr> 
   <td> Content Manager<br /> </td> 
   <td> Crea boletines informativos o sitios web recurrentes y, a continuación, valida y publica los mensajes.<br /> </td> 
   <td> </td> 
   <td> <a href="../../delivery/using/about-content-management.md">Más información</a> </td> 
  </tr> 
  <tr> 
   <td> Encuestas en línea (Administrador de estudios)<br /> </td> 
   <td> Crea y administra formularios en línea para agregar o modificar información de perfil, para suscribirse, cancelar la suscripción o un formulario de entrada de concurso.<br /> </td> 
   <td> Mercadotecnia<br /> </td> 
   <td> Opcional, <a href="../../web/using/about-surveys.md">Más información</a> </td> 
  </tr> 
  <tr> 
   <td> Análisis de marketing<br /> </td> 
   <td> Permite analizar y medir datos, calcular estadísticas, simplificar y optimizar la creación y el cálculo de informes. Además, puede crear informes y generar poblaciones objetivo. <br /> </td> 
   <td> Mercadotecnia<br /> </td> 
   <td> Opcional, <a href="../../reporting/using/about-cubes.md">Más información</a> </td> 
  </tr> 
  <tr> 
   <td> Gestor de respuestas<br /> </td> 
   <td> Mide el éxito y la rentabilidad de las campañas de mercadotecnia o de las propuestas de ofertas para todos los canales de comunicación.<br /> </td> 
   <td> Mercadotecnia<br /> </td> 
   <td> Opcional, <a href="../../campaign/using/about-response-manager.md">Más información</a> </td> 
  </tr> 
  <tr> 
   <td> Acceso a datos externos (Acceso a datos federados)<br /> </td> 
   <td> Provides the Federated Data Access (FDA) option in order to process information stored in one or more external databases so that you can access external data without changing the structure of Adobe Campaign data.<br /> </td> 
   <td> Todos<br /> </td> 
   <td> Opcional, <a href="../../workflow/using/accessing-an-external-database--fda-.md">Más información</a> </td> 
  </tr> 
  <tr> 
   <td> Campaign Optimization (Optimización de la campaña)<br /> </td> 
   <td> Controla, filtra y supervisa el envío de envíos para que los mensajes enviados satisfagan mejor las necesidades y expectativas de los clientes, de acuerdo con las políticas de comunicación de la empresa. <br /> </td> 
   <td> Mercadotecnia<br /> </td> 
   <td> Opcional, <a href="../../campaign/using/about-campaign-typologies.md">Más información</a> </td> 
  </tr> 
  <tr> 
   <td> Supervisión de la capacidad de entrega (capacidad de entrega por correo electrónico)<br /> </td> 
   <td> Mide el éxito de las campañas que llegan a la bandeja de entrada de los destinatarios sin rebotar o marcadas como correo no deseado.<br /> </td> 
   <td> Todos </td> 
   <td> Opcional, <a href="https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html">Más información</a> </td> 
  </tr> 
  <tr> 
   <td> Gestión de cupones<br /> </td> 
   <td> Crea un conjunto de cupones para agregarlos a las próximas ofertas de marketing.<br /> </td> 
   <td> Mercadotecnia<br /> </td> 
   <td> Opcional, <a href="../../delivery/using/personalized-coupons.md">Más información</a> </td> 
  </tr> 
  <tr> 
   <td> Procesamiento de bandeja de entrada (IR)<br /> </td> 
   <td> Permite obtener una vista previa del mensaje enviado en los diferentes contextos en los que se puede recibir y comprobar la compatibilidad en las principales aplicaciones y escritorios. Necesitas una cuenta Litmus.<br /> </td> 
   <td> Mercadotecnia<br /> </td> 
   <td> Opcional, <a href="../../delivery/using/inbox-rendering.md">Más información</a> </td> 
  </tr> 
  <tr> 
   <td> Marketing central/local (marketing distribuido)<br /> </td> 
   <td> Implementa campañas de cooperación entre entidades centrales (sede, departamentos de mercadotecnia, etc.) y entidades locales (puntos de venta, agencias regionales, etc.).<br /> </td> 
   <td> Mercadotecnia </td> 
   <td> Opcional, <a href="../../campaign/using/about-distributed-marketing.md">Más información</a> </td> 
  </tr> 
  <tr> 
   <td> CRM connectors<br /> </td> 
   <td> Provides various CRM connectors for linking your Adobe Campaign platform to your third-party systems.<br /> </td> 
   <td> Mercadotecnia</td> 
   <td> <a href="../../platform/using/crm-connectors.md">Más información</a> </td> 
  </tr> 
  <tr> 
   <td> Conectores de Web Analytics<br /> </td> 
   <td> Permite que Adobe Campaign y Adobe Analytics interactúen a través del paquete de conectores de Web Analytics.<br /> </td> 
   <td> Mercadotecnia </td> 
   <td> No compatible con la mensajería transaccional, <a href="../../platform/using/adobe-analytics-data-connector.md">Más información</a> </td> 
  </tr> 
  <tr> 
   <td> Integración de AEM<br /> </td> 
   <td> Le permite administrar el contenido de sus envíos de correo electrónico, así como los formularios directamente en Adobe Experience Manager, para beneficiarse de las funciones de edición de contenido de AEM y de las capacidades de entrega de Adobe Campaign.<br /> </td> 
   <td> Mercadotecnia</td> 
   <td> <a href="../../integrations/using/about-adobe-experience-manager.md">Más información</a> </td> 
  </tr> 
  <tr> 
   <td> Integración de audiencias compartidas de Adobe Marketing Cloud<br /> </td> 
   <td> Allows you to exchange and share audiences/segments with Adobe Experience Cloud solutions and core services.<br /> </td> 
   <td> Mercadotecnia<br /> </td> 
   <td> Requiere IMS, <a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">más información</a> </td> 
  </tr> 
  <tr> 
   <td> Integración con Adobe Marketing Cloud<br /> </td> 
   <td> Le permite importar y exportar audiencias/segmentos desde diferentes soluciones de Adobe Marketing Cloud a Adobe Campaign. </td> 
   <td> Mercadotecnia</td> 
   <td> Opcional, <a href="../../integrations/using/configuring-ims.md#installing-the-package">Más información</a> </td> 
  </tr> 
  <tr> 
   <td> Reglamento de protección de datos de privacidad<br /> </td> 
   <td> Contiene funcionalidad adicional para ayudarle con su conformidad con la privacidad en Campaign Classic.<br /> </td> 
   <td> Todos</td> 
   <td> <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html">Más información</a> </td> 
  </tr> 
  <tr> 
   <td> Transfer to Mid-Sourcing <br /> </td> 
   <td> Detalles sobre la instalación y configuración de un servidor de fuentes intermedias, así como la implementación de una instancia que permite a terceros enviar mensajes en modo de fuentes intermedias.<br /> </td> 
   <td> Mercadotecnia </td> 
   <td> Opcional, <a href="../../installation/using/mid-sourcing-server.md">Más información</a> </td> 
  </tr> 
  <tr> 
   <td> Mid-sourcing platform<br /> </td> 
   <td> Esta configuración es una solución intermedia óptima entre una configuración alojada (ASP) y la internalización. Los componentes de ejecución orientados hacia el exterior se llevan a cabo en un servidor de "fuentes intermedias" alojado en Adobe Campaign.<br /> </td> 
   <td> Intercambio de recursos </td> 
   <td> Opcional, <a href="../../installation/using/mid-sourcing-server.md">Más información</a> </td> 
  </tr> 
  <tr> 
   <td> Conector ACS<br /> </td> 
   <td> Bridges Adobe Campaign v7 y Adobe Campaign Standard. Se trata de una función integrada en Campaign v7 que duplica automáticamente los datos en Campaign Standard, lo que une lo mejor de ambas aplicaciones. <br /> </td> 
   <td> Mercadotecnia </td> 
   <td> Opcional, <a href="../../integrations/using/acs-connector-principles-and-data-cycle.md">Más información</a> </td> 
  </tr> 
 </tbody> 
</table>

### Paquete de centro de mensajes {#message-center-package}

Para agregar un canal de entrega (canal móvil, canal de aplicaciones móviles, etc.), esto debe realizarse antes de instalar el paquete de Message Center. Si ha iniciado un proyecto de centro de mensajes en el canal de correo electrónico y, a continuación, en mitad del proyecto, decide agregar un nuevo canal, debe seguir estos pasos:

1. Instale el canal que desee, por ejemplo el canal **** Mobile, mediante el asistente para la importación de paquetes ( **[!UICONTROL Tools > Advanced > Import package > Adobe Campaign package]**).
1. Importe el archivo ( **[!UICONTROL Tools > Advanced > Import package > File]**) y seleccione:

   ```
   \datakit\nms\[Your language]\package\messageCenter.xml
   ```

1. En la **[!UICONTROL XML data content to import]**, mantenga solo la plantilla de envío de centro de mensajes correspondiente al canal adjunto. Por ejemplo, si ha agregado el canal **** Mobile, mantenga solo el elemento **entidades** correspondiente a la plantilla **[!UICONTROL Mobile transactional message]** (smsTriggerMessage). If you have added the **Mobile App Channel**, keep only the **iOS transactional message** templates (iosTriggerMessage) and **Android transactional message** (androidTriggerMessage).

   ![](assets/messagecenter_install_channel.png)

### Paquete LINE {#line-package}

Para poder enviar entregas mediante el canal LINE con Adobe Campaign, debe instalar el paquete LINE.

La instalación del paquete LINE es una instalación estándar detallada en la sección [Importación de paquetes](../../platform/using/working-with-data-packages.md#importing-packages) .

![](assets/line_config_1.png)

>[!CAUTION]
>
>Las plantillas de entrega de Message Center para LINE no estarán disponibles si los paquetes de Message Center están instalados antes de LINE.
