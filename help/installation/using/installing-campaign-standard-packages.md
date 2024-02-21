---
product: campaign
title: Instalación de paquetes integrados de Campaign Classic
description: Obtenga información sobre cómo instalar paquetes integrados de Campaign
feature: Installation, Application Settings
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
badge-v7-prem: label="On-Premise e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
exl-id: 2bc077c4-ed65-4157-bfc9-df5d0442f476
source-git-commit: 668cee663890fafe27f86f2afd3752f7e2ab347a
workflow-type: tm+mt
source-wordcount: '1271'
ht-degree: 11%

---

# Instalación de paquetes integrados de Campaign Classic{#installing-campaign-standard-packages}



## Acerca de los paquetes integrados {#campaign-standard-packages}

Los paquetes integrados contienen un conjunto de funciones que se pueden instalar según sus necesidades y según su contrato. La lista completa de paquetes integrados de Campaign está disponible a continuación.

>[!CAUTION]
>
>Solo puede instalar paquetes que correspondan a las opciones mencionadas en su contrato de licencia.
>
>La instalación de un nuevo paquete puede afectar a toda la plataforma: debe probarse y validarse antes de la implementación final.
>
>Una vez instalado un paquete, no se puede desinstalar.
>
>Como cliente alojado o híbrido, póngase en contacto con el Adobe para que implemente un nuevo paquete integrado.

Para instalar un paquete integrado:

1.  En la consola de cliente de Adobe Campaign, acceda al asistente de importación del paquete desde **[!UICONTROL Tools > Advanced > Import package]**.
1. Seleccione **[!UICONTROL Install a standard package]**.
1. En la lista de paquetes, marque los paquetes que desea instalar.
   >[!NOTE]
   >
   >Cuando un paquete aparece en gris, significa que ya está instalado o que no es compatible con su instancia. La compatibilidad se detalla en la tabla siguiente.
1. Haga clic en **[!UICONTROL Next]**, luego en **[!UICONTROL Start]** para iniciar la instalación del paquete.

   Una vez instalados los paquetes, la barra de progreso muestra el **100 %** y puede ver el siguiente mensaje en los registros de instalación: **[!UICONTROL Installation of packages successful]**.

1. **[!UICONTROL Close]** la ventana de instalación.

Los paquetes ya están instalados.

### Lista de paquetes integrados... {#list-of-standard-packages}

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
   <td> Supervisa los envíos y los problemas que se puedan detectar cuando se envían mensajes. <a href="../../delivery/using/about-delivery-monitoring.md">Más información</a><br /> </td> 
   <td> Todas</td> 
  </tr> 
  <tr> 
   <td> Campañas de marketing (Campaign)<br /> </td> 
   <td> Define, optimiza, ejecuta y analiza las comunicaciones y las campañas de marketing. <a href="../../campaign/using/designing-marketing-campaigns.md">Más información</a><br /> </td> 
   <td> Marketing</td>
  </tr> 
  <tr> 
   <td> Recursos de marketing (MRM)<br /> </td> 
   <td> Controla las acciones de marketing de forma cooperativa mediante la administración y el seguimiento de las tareas, los presupuestos y los recursos de marketing. <a href="../../mrm/using/about-marketing-resource-management.md">Más información</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Motor de oferta (interacción)<br /> </td> 
   <td> Responde en tiempo real durante una interacción con un contacto determinado (un cliente o destinatario) mediante la realización de una o varias ofertas adaptadas.  Opcional. <a href="../../interaction/using/interaction-and-offer-management.md#packages-configuration">Más información</a> <br /> </td> 
   <td> Todo<br /> </td> 
  </tr> 
  <tr> 
   <td> Control del motor de oferta con instancia de ejecución. Opcional.<br /> </td> 
   <td> Paquete que se instalará en la instancia de control para el motor de oferta (interacción). <a href="../../interaction/using/distributed-architectures.md#packages-configuration">Más información</a> </td> 
   <td> Marketing<br /> </td>  
  </tr> 
  <tr> 
   <td> Motor de ofertas para instancias de ejecución. Opcional.<br /> </td> 
   <td> Paquete que se va a instalar en instancias de ejecución para el motor de oferta (interacción). <a href="../../interaction/using/distributed-architectures.md">Más información</a> </td> 
   <td> Mid, Execution <br /> </td>  
  </tr> 
  <!--tr> 
   <td> Lead Management (Leads) (deprecated)<br /> </td> 
   <td> Simplifies the process of building and maintaining the entire leads management life cycle. <br /> </td> 
   <td> Yes<br /> </td> 
   <td> Optional, <a href="https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html">Learn More</a> </td> 
  </tr--> 
  <tr> 
   <td> Redes sociales (Marketing social) <br /> </td> 
   <td> Sincroniza Adobe Campaign con X (anteriormente conocido como Twitter) y Facebook. <a href="../../social/using/about-social-marketing.md">Más información</a> <br /> </td> 
   <td> Todas</td> 
  </tr> 
  <tr> 
   <td> Control de mensajes transaccionales (Centro de mensajes - Control)<br /> </td> 
   <td> Gestiona los mensajes de déclencheur generados a partir de eventos activados desde sistemas de información. Opcional. <a href="../../message-center/using/about-transactional-messaging.md">Más información</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Ejecución de mensaje transaccional (Centro de mensajes - Ejecución) <br /> </td> 
   <td> Garantiza una mayor disponibilidad y una mejor gestión de la carga. Opcional. <a href="../../message-center/using/about-transactional-messaging.md">Más información</a><br /> </td> 
   <td> Ejecución<br /> </td>
  </tr> 
  <tr> 
   <td> Canal LINE<br /> </td> 
   <td> Envía envíos mediante el canal LINE con Adobe Campaign. Opcional. La mensajería transaccional (paquete del centro de mensajes) es obligatoria. <a href="../../delivery/using/line-channel.md">Más información</a> <br /> </td> 
   <td> Todo<br /> </td> 
  </tr> 
  <tr> 
   <td> Canal de correo postal<br /> </td> 
   <td> Envía envíos mediante el canal de correo postal con Adobe Campaign. Opcional. <a href="../../delivery/using/about-direct-mail-channel.md">Más información</a><br /> </td> 
   <td> Todo<br /> </td>
  </tr> 
  <tr> 
   <td> Canal móvil (SMS) <br /> </td> 
   <td> Envía envíos mediante el canal móvil/SMS con Adobe Campaign. Opcional. <a href="../../delivery/using/sms-channel.md">Más información</a> <br /> </td> 
   <td> Todo<br /> </td> 
  </tr> 
   <tr> 
   <td> Canal de teléfono<br /> </td> 
   <td> Realiza envíos a través del canal telefónico con Adobe Campaign. Se utiliza para el centro de llamadas. Opcional. <a href="../../delivery/using/communication-channels.md">Más información</a> <br /> </td> 
   <td> Todo<br /> </td> 
  </tr> 
  <tr> 
   <td> Canal de aplicaciones móviles<br /> </td> 
   <td> Utiliza la plataforma Adobe Campaign para enviar notificaciones personalizadas a los terminales iOS y Android a través de aplicaciones. Opcional. <a href="../../delivery/using/about-mobile-app-channel.md">Más información</a> <br /> </td> 
   <td> Todo<br /> </td> 
  </tr> 
  <tr> 
   <td> Administrador de contenido<br /> </td> 
   <td> Crea boletines informativos o sitios web recurrentes y, a continuación, valida y publica los mensajes. <a href="../../delivery/using/about-content-management.md">Más información</a> <br /> </td> 
   <td> </td>
  </tr> 
  <tr> 
   <td> Encuestas en línea (Gestor de encuestas)<br /> </td> 
   <td> Crea y administra formularios en línea para agregar o modificar información de perfil, suscribirse, cancelar la suscripción o un formulario de entrada de competencia. Opcional. <a href="../../surveys/using/about-surveys.md">Más información</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Marketing Analytics<br /> </td> 
   <td> Permite analizar y medir datos, calcular estadísticas y simplificar y optimizar la creación y el cálculo de informes. Además, puede crear informes y generar poblaciones objetivo. Opcional. <a href="../../reporting/using/ac-cubes.md">Más información</a><br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Gestor de respuestas<br /> </td> 
   <td> Mide el éxito y la rentabilidad de las campañas de marketing u ofrece propuestas para todos los canales de comunicación.  Opcional. <a href="../../response/using/about-response-manager.md">Más información</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Acceso a datos externos (acceso de datos federado)<br /> </td> 
   <td> Proporciona la opción Acceso de datos federados (FDA) para procesar la información almacenada en una o más bases de datos externas, de modo que pueda acceder a datos externos sin cambiar la estructura de los datos de Adobe Campaign.  Opcional. <a href="../../workflow/using/accessing-an-external-database-fda.md">Más información</a> <br /> </td> 
   <td> Todo<br /> </td> 
  </tr> 
  <tr> 
   <td> Campaign Optimization (Optimización de la campaña)<br /> </td> 
   <td> Controla, filtra y supervisa la entrega de mensajes para que se ajusten mejor a las necesidades y expectativas de los clientes, de acuerdo con las políticas de comunicación de la empresa. Opcional. <a href="../../campaign-opt/using/about-campaign-typologies.md">Más información</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Monitorización de la capacidad de entrega (capacidad de entrega por correo electrónico)<br /> </td> 
   <td> Mide el éxito de las campañas que llegan a la bandeja de entrada de los destinatarios sin rebotar o marcadas como correo no deseado. Opcional. <a href="../../delivery/using/about-deliverability.md">Más información</a> <br /> </td> 
   <td> Todas </td> 
  </tr> 
  <tr> 
   <td> Administración de cupones<br /> </td> 
   <td> Crea un conjunto de cupones para añadirlos a próximas ofertas de marketing. Opcional. <a href="../../delivery/using/personalized-coupons.md">Más información</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Renderización de la bandeja de entrada (IR)<br /> </td> 
   <td> Permite obtener una vista previa del mensaje enviado en los diferentes contextos en los que se puede recibir y comprobar la compatibilidad en las aplicaciones y los escritorios principales. Opcional. <a href="../../delivery/using/inbox-rendering.md">Más información</a><br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Marketing central/local (Marketing distribuido)<br /> </td> 
   <td> Implementa campañas cooperativas entre entidades centrales (sede central, departamentos de marketing, etc.) y entidades locales (puntos de venta, agencias regionales, etc.). Opcional. <a href="../../distributed/using/about-distributed-marketing.md">Más información</a><br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> Conectores CRM<br /> </td> 
   <td> Proporciona varios conectores CRM para vincular la plataforma de Adobe Campaign a los sistemas de terceros.  <a href="../../platform/using/crm-connectors.md">Más información</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Conectores de análisis web<br /> </td> 
   <td> Permite que Adobe Campaign y Adobe Analytics interactúen mediante el paquete de conectores de Web Analytics. No compatible con mensajes transaccionales (paquete del centro de mensajes). <a href="../../platform/using/adobe-analytics-connector.md">Más información</a><br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> AEM integración de<br /> </td> 
   <td> Le permite administrar el contenido de los envíos de correos electrónicos y los formularios directamente en Adobe Experience Manager AEM para beneficiarse de las funcionalidades de edición de contenido y de las capacidades de envío de Adobe Campaign. <a href="../../integrations/using/about-adobe-experience-manager.md">Más información</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Integración de audiencias compartidas de Adobe Experience Cloud<br /> </td> 
   <td> Permite intercambiar y compartir audiencias y segmentos con las soluciones y los servicios principales de Adobe Experience Cloud. Requiere IMS. <a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Más información</a> <br /> </td> 
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
   <td> Todas</td> 
  </tr> 
  <tr> 
   <td> Transfer to Mid-Sourcing <br /> </td> 
   <td> Detalla la instalación y configuración de un servidor intermediario, así como la implementación de una instancia que permite a terceros enviar mensajes en modo intermediario. Opcional. <a href="../../installation/using/mid-sourcing-server.md">Más información</a> <br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> Mid-sourcing platform<br /> </td> 
   <td> Esta configuración es una solución intermedia óptima entre una configuración alojada (ASP) y la internalización. Los componentes de ejecución salientes se llevan a cabo en un servidor "intermediario" alojado en Adobe Campaign. Opcional. <a href="../../installation/using/mid-sourcing-server.md">Más información</a> <br /> </td> 
   <td> Intermediario </td> 
  </tr> 
  <tr> 
   <td> Compatibilidad con AMP<br /> </td> 
   <td> Permite utilizar la nueva AMP interactiva para el formato de correo electrónico y enviar correos electrónicos dinámicos. Opcional. <a href="../../delivery/using/defining-interactive-content.md">Más información</a> <br /> </td> 
   <td> Todas </td> 
  </tr> 
  <tr> 
   <td> Conector ACS (obsoleto)<br /> </td> 
   <td> Vincula Adobe Campaign v7 y Adobe Campaign Standard. Se trata de una función integrada en Campaign v7 que duplica automáticamente los datos en Campaign Standard, lo que une lo mejor de ambas aplicaciones. Opcional.<br /> </td> 
   <td> Marketing </td> 
  </tr> 
 </tbody> 
</table>

### Paquete de Message Center {#message-center-package}

Debe instalar canales de entrega (correo electrónico, canal móvil, canal de aplicación móvil, LINE, etc.) antes de instalar la mensajería transaccional (paquete del centro de mensajes). Si ha iniciado un proyecto de centro de mensajes solo de correo electrónico y necesita agregar un canal nuevo posteriormente, debe seguir estos pasos:

1. Instale el nuevo canal, por ejemplo, el **Canal móvil**, mediante el asistente de importación de paquetes ( **[!UICONTROL Tools > Advanced > Import package > Adobe Campaign package]**).
1. Importe el archivo ( **[!UICONTROL Tools > Advanced > Import package > File]**) y seleccione:

   ```
   \datakit\nms\[Your language]\package\messageCenter.xml
   ```

1. En el **[!UICONTROL XML data content to import]**, mantenga únicamente la plantilla de envío del Centro de mensajes correspondiente al canal relacionado. Por ejemplo, si ha agregado la variable **Canal móvil**, conserve solo el **entidades** elemento correspondiente a **[!UICONTROL Mobile transactional message]** Plantilla (smsTriggerMessage). Si ha agregado la variable **Canal de aplicaciones móviles**, conserve solo el **Mensaje transaccional de iOS** plantillas (iosTriggerMessage) y **Mensaje transaccional de Android** (androidTriggerMessage).

   ![](assets/messagecenter_install_channel.png)


### [!DNL LINE] configuración de canal{#line-package}

Para configurar el [!DNL LINE] canal, primero debe instalar el [!DNL LINE] paquete.

En el contexto de una configuración intermediaria, debe:

* Instale el [!DNL LINE] en las instancias de Marketing y MID

* Configure las variables [!DNL LINE] cuenta externa en la instancia de mkt para que apunte a la instancia mid cambiando el modo de envío. [Más información](../../delivery/using/line-channel.md#configure-line-external)

* Configure las variables [!DNL LINE] credenciales de en la cuenta externa de la instancia de MID.

>[!CAUTION]
>
>Las plantillas de entrega del Centro de mensajes para [!DNL LINE] El canal no estará disponible si los paquetes del Centro de mensajes se han instalado anteriormente [!DNL LINE].