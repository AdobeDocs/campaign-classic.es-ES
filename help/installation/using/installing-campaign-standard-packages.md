---
product: campaign
title: Instalación de paquetes integrados de Campaign Classic
description: Obtenga información sobre cómo instalar los paquetes integrados de Campaign
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 2bc077c4-ed65-4157-bfc9-df5d0442f476
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1173'
ht-degree: 16%

---

# Instalación de paquetes integrados de Campaign Classic{#installing-campaign-standard-packages}

## Acerca de los paquetes integrados {#campaign-standard-packages}

Los paquetes integrados contienen un conjunto de funciones que se pueden instalar según sus necesidades y según su contrato. La lista completa de paquetes integrados de Campaign está disponible a continuación.

>[!CAUTION]
>
>Solo puede instalar los paquetes correspondientes a las opciones mencionadas en su contrato de licencia.
>
>La instalación de un nuevo paquete puede afectar a toda la plataforma: debe probarse y validarse antes de la implementación final.
>
>Una vez instalado un paquete, no puede desinstalarlo.

Para instalar un paquete integrado:

1.  En la consola de cliente de Adobe Campaign, acceda al asistente de importación del paquete desde **[!UICONTROL Tools > Advanced > Package import...]**.
1. Seleccione **[!UICONTROL Install a standard package]**.
1. En la lista de paquetes, compruebe los paquetes que desea instalar.
   >[!NOTE]
   >
   >Cuando un paquete aparece atenuado, significa que ya está instalado o que no es compatible con su instancia. La compatibilidad se detalla en la tabla siguiente.
1. Haga clic en **[!UICONTROL Next]**, luego en **[!UICONTROL Start]** para iniciar la instalación del paquete.

   Una vez instalados los paquetes, la barra de progreso muestra el **100 %** y puede ver el siguiente mensaje en los registros de instalación: **[!UICONTROL Installation of packages successful]**.

1. **[!UICONTROL Close]** la ventana de instalación.

Los paquetes ya están instalados.

### Lista de paquetes predeterminados {#list-of-standard-packages}

La siguiente tabla enumera todos los paquetes integrados de Campaign.

<table> 
 <thead> 
  <tr> 
   <th> Paquete </th> 
   <th> Descripción </th> 
   <th> Tipo de instancia </th>
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Entrega<br /> </td> 
   <td> Supervisa los envíos y los problemas que puedan producirse al enviar los mensajes. <a href="../../delivery/using/about-delivery-monitoring.md">Obtenga más información</a><br /> </td> 
   <td> Todo</td> 
  </tr> 
  <tr> 
   <td> Campañas de marketing (Campaign)<br /> </td> 
   <td> Define, optimiza, ejecuta y analiza las comunicaciones y las campañas de marketing. <a href="../../campaign/using/designing-marketing-campaigns.md">Más información</a><br /> </td> 
   <td> Marketing</td>
  </tr> 
  <tr> 
   <td> Recursos de Marketing (MRM)<br /> </td> 
   <td> Controla las acciones de marketing en un modo cooperativo mediante la administración y el seguimiento de las tareas, los presupuestos y los recursos de marketing. <a href="../../campaign/using/about-marketing-resource-management.md">Más información</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Motor de ofertas (interacción)<br /> </td> 
   <td> Responde en tiempo real durante una interacción con un contacto determinado (un cliente o destinatario) mediante la realización de una o varias ofertas adaptadas.  Opcional. <a href="../../interaction/using/interaction-and-offer-management.md#packages-configuration">Más información</a> <br /> </td> 
   <td> Todo<br /> </td> 
  </tr> 
  <tr> 
   <td> Control del motor de oferta con instancia de ejecución. Opcional.<br /> </td> 
   <td> Paquete para instalar en la instancia de control para el motor de oferta (interacción). <a href="../../interaction/using/distributed-architectures.md#packages-configuration">Más información</a> </td> 
   <td> Marketing<br /> </td>  
  </tr> 
  <tr> 
   <td> Motor de oferta para instancias de ejecución. Opcional.<br /> </td> 
   <td> Paquete para instalar en instancias de ejecución para Offer engine (interacción). <a href="../../interaction/using/distributed-architectures.md">Más información</a> </td> 
   <td> Mid, Ejecución <br /> </td>  
  </tr> 
  <!--tr> 
   <td> Lead Management (Leads) (deprecated)<br /> </td> 
   <td> Simplifies the process of building and maintaining the entire leads management life cycle. <br /> </td> 
   <td> Yes<br /> </td> 
   <td> Optional, <a href="https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html">Learn More</a> </td> 
  </tr--> 
  <tr> 
   <td> Redes sociales (Marketing social) <br /> </td> 
   <td> Sincroniza Adobe Campaign con Twitter y Facebook. <a href="../../social/using/about-social-marketing.md">Más información</a> <br /> </td> 
   <td> Todo</td> 
  </tr> 
  <tr> 
   <td> Control de mensajes transaccionales (Centro de mensajes - Control)<br /> </td> 
   <td> Gestiona los mensajes de déclencheur generados a partir de eventos activados desde sistemas de información. Opcional. <a href="../../message-center/using/about-transactional-messaging.md">Más información</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Ejecución de mensaje transaccional (Centro de mensajes - Ejecución) <br /> </td> 
   <td> Garantiza una mayor disponibilidad y una mejor administración de la carga. Opcional. <a href="../../message-center/using/about-transactional-messaging.md">Más información</a><br /> </td> 
   <td> Ejecución<br /> </td>
  </tr> 
  <tr> 
   <td> Canal LINE<br /> </td> 
   <td> Envía envíos utilizando el canal LINE con Adobe Campaign. Opcional. La mensajería transaccional (paquete del centro de mensajes) es obligatoria. <a href="../../delivery/using/line-channel.md">Más información</a> <br /> </td> 
   <td> Todo<br /> </td> 
  </tr> 
  <tr> 
   <td> Canal de correo postal<br /> </td> 
   <td> Envía envíos utilizando el canal de correo postal con Adobe Campaign. Opcional. <a href="../../delivery/using/about-direct-mail-channel.md">Más información</a><br /> </td> 
   <td> Todo<br /> </td>
  </tr> 
  <tr> 
   <td> Canal móvil (SMS) <br /> </td> 
   <td> Envía envíos utilizando el canal móvil/SMS con Adobe Campaign. Opcional. <a href="../../delivery/using/sms-channel.md">Más información</a> <br /> </td> 
   <td> Todo<br /> </td> 
  </tr> 
   <tr> 
   <td> Canal de teléfono<br /> </td> 
   <td> Envía envíos utilizando el canal telefónico con Adobe Campaign. Se utiliza para el centro de llamadas. Opcional. <a href="../../delivery/using/communication-channels.md">Más información</a> <br /> </td> 
   <td> Todo<br /> </td> 
  </tr> 
  <tr> 
   <td> Canal de aplicaciones móviles<br /> </td> 
   <td> Utiliza la plataforma de Adobe Campaign para enviar notificaciones personalizadas a los terminales iOS y Android a través de aplicaciones. Opcional. <a href="../../delivery/using/about-mobile-app-channel.md">Más información</a> <br /> </td> 
   <td> Todo<br /> </td> 
  </tr> 
  <tr> 
   <td> Administrador de contenido<br /> </td> 
   <td> Crea boletines informativos o sitios web recurrentes y después valida y publica los mensajes. <a href="../../delivery/using/about-content-management.md">Más información</a> <br /> </td> 
   <td> </td>
  </tr> 
  <tr> 
   <td> Encuestas en línea (Administrador de encuestas)<br /> </td> 
   <td> Crea y administra formularios en línea para agregar o modificar información de perfil, para suscribirse, cancelar la suscripción o un formulario de entrada de competencia. Opcional. <a href="../../web/using/about-surveys.md">Más información</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Marketing Analytics<br /> </td> 
   <td> Permite analizar y medir datos, calcular estadísticas, simplificar y optimizar la creación y el cálculo de informes. Además, puede crear informes y grupos de destinatarios. Opcional. <a href="../../reporting/using/about-cubes.md">Más información</a><br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Gestor de respuestas<br /> </td> 
   <td> Mide el éxito y la rentabilidad de las campañas de marketing u ofertas propuestas para todos los canales de comunicación.  Opcional. <a href="../../campaign/using/about-response-manager.md">Más información</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Acceso a datos externos (acceso de datos federado)<br /> </td> 
   <td> Proporciona la opción Acceso de Datos Federados (FDA) para procesar la información almacenada en una o más bases de datos externas de modo que pueda acceder a datos externos sin cambiar la estructura de los datos de Adobe Campaign.  Opcional. <a href="../../workflow/using/accessing-an-external-database--fda-.md">Más información</a> <br /> </td> 
   <td> Todo<br /> </td> 
  </tr> 
  <tr> 
   <td> Campaign Optimization (Optimización de la campaña)<br /> </td> 
   <td> Controla, filtra y supervisa el envío de envíos para que los mensajes enviados respondan de la mejor manera a las necesidades y expectativas de los clientes, de acuerdo con las políticas de comunicación de la empresa. Opcional. <a href="../../campaign/using/about-campaign-typologies.md">Más información</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Monitorización de la capacidad de entrega (capacidad de entrega por correo electrónico)<br /> </td> 
   <td> Mide el éxito de las campañas que llegan a la bandeja de entrada de los destinatarios sin rebotar o marcadas como correo no deseado. Opcional. <a href="../../delivery/using/about-deliverability.md">Más información</a> <br /> </td> 
   <td> Todo </td> 
  </tr> 
  <tr> 
   <td> Administración de cupones<br /> </td> 
   <td> Crea un conjunto de cupones para añadirlos a las próximas ofertas de marketing. Opcional. <a href="../../delivery/using/personalized-coupons.md">Más información</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Renderización de la bandeja de entrada (IR)<br /> </td> 
   <td> Permite obtener una vista previa del mensaje enviado en los diferentes contextos en los que se puede recibir y comprobar la compatibilidad en las aplicaciones y los escritorios principales. Opcional. <a href="../../delivery/using/inbox-rendering.md">Más información</a><br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Marketing central/local (Marketing distribuido)<br /> </td> 
   <td> Implementa campañas de cooperación entre entidades centrales (sede central, departamentos de marketing, etc.) y entidades locales (puntos de venta, agencias regionales, etc.). Opcional. <a href="../../campaign/using/about-distributed-marketing.md">Más información</a><br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> Conectores CRM<br /> </td> 
   <td> Proporciona varios conectores CRM para vincular la plataforma de Adobe Campaign a los sistemas de terceros.  <a href="../../platform/using/crm-connectors.md">Más información</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Conectores de análisis web<br /> </td> 
   <td> Permite que Adobe Campaign y Adobe Analytics interactúen mediante el paquete de conectores de Web Analytics. No es compatible con la mensajería transaccional (paquete del centro de mensajes). <a href="../../platform/using/adobe-analytics-data-connector.md">Más información</a><br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> Integración de AEM<br /> </td> 
   <td> Permite administrar el contenido de los envíos de los correos electrónicos y los formularios directamente en Adobe Experience Manager para beneficiarse de AEM funcionalidades de edición de contenido, así como de las capacidades de envío de Adobe Campaign. <a href="../../integrations/using/about-adobe-experience-manager.md">Más información</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Integración de audiencias compartidas de Adobe Experience Cloud<br /> </td> 
   <td> Le permite intercambiar y compartir audiencias y segmentos con soluciones y servicios principales de Adobe Experience Cloud. Requiere IMS. <a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Más información</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Integración con Adobe Experience Cloud<br /> </td> 
   <td> Permite importar y exportar audiencias y segmentos de distintas soluciones de Adobe Experience Cloud en Adobe Campaign. Opcional. <a href="../../integrations/using/configuring-ims.md#installing-the-package">Más información</a> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Reglamento de protección de datos de privacidad<br /> </td> 
   <td> Contiene funcionalidad adicional para ayudarle con el cumplimiento de la privacidad en Campaign Classic. <a href="https://helpx.adobe.com/es/campaign/kb/acc-privacy.html">Más información</a> <br /> </td> 
   <td> Todo</td> 
  </tr> 
  <tr> 
   <td> Transfer to Mid-Sourcing <br /> </td> 
   <td> Detalles sobre la instalación y configuración de un servidor intermediario, así como la implementación de una instancia que permita a terceros enviar mensajes en modo intermediario. Opcional. <a href="../../installation/using/mid-sourcing-server.md">Más información</a> <br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> Mid-sourcing platform<br /> </td> 
   <td> Esta configuración es una solución intermedia óptima entre una configuración alojada (ASP) y la internalización. Los componentes de ejecución orientados al exterior se llevan a cabo en un servidor "intermediario" alojado en Adobe Campaign. Opcional. <a href="../../installation/using/mid-sourcing-server.md">Más información</a> <br /> </td> 
   <td> Mid-sourcing </td> 
  </tr> 
  <tr> 
   <td> Compatibilidad con AMP<br /> </td> 
   <td> Permite utilizar la nueva AMP interactiva para el formato de correo electrónico y enviar correos electrónicos dinámicos. Opcional. <a href="../../delivery/using/defining-interactive-content.md">Más información</a> <br /> </td> 
   <td> Todo </td> 
  </tr> 
  <tr> 
   <td> Conector ACS<br /> </td> 
   <td> Bridges Adobe Campaign v7 y Adobe Campaign Standard. Se trata de una función integrada en Campaign v7 que duplica automáticamente los datos en Campaign Standard, lo que une lo mejor de ambas aplicaciones. Opcional. <a href="../../integrations/using/acs-connector-principles-and-data-cycle.md">Más información</a> <br /> </td> 
   <td> Marketing </td> 
  </tr> 
 </tbody> 
</table>

### Paquete del centro de mensajes {#message-center-package}

Debe instalar canales de envío (correo electrónico, canal móvil, canal de aplicación móvil, etc.) antes de instalar la mensajería transaccional (paquete del centro de mensajes). Si ha iniciado un proyecto de Centro de mensajes solo de correo electrónico y necesita agregar un canal nuevo posteriormente, debe seguir estos pasos:

1. Instale el nuevo canal, por ejemplo el **Mobile channel**, mediante el asistente de importación de paquetes ( **[!UICONTROL Tools > Advanced > Import package > Adobe Campaign package]**).
1. Importe el archivo ( **[!UICONTROL Tools > Advanced > Import package > File]**) y seleccione:

   ```
   \datakit\nms\[Your language]\package\messageCenter.xml
   ```

1. En **[!UICONTROL XML data content to import]**, mantenga solamente la plantilla de envío del Centro de mensajes correspondiente al canal relacionado. Por ejemplo, si ha agregado el **canal móvil**, mantenga solamente el elemento **entidades** correspondiente a la plantilla **[!UICONTROL Mobile transactional message]** (smsTriggerMessage). Si ha añadido el **Mobile App Channel**, mantenga únicamente las plantillas **iOS transactional message** (iosTriggerMessage) y **Android transactional message** (androidTriggerMessage).

   ![](assets/messagecenter_install_channel.png)

>[!CAUTION]
>
>Las plantillas de entrega del Centro de mensajes para LINE no estarán disponibles si los paquetes del Centro de mensajes están instalados antes de LINE
