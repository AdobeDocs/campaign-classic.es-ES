---
solution: Campaign Classic
product: campaign
title: Instalación de paquetes integrados Campaign Classic
description: Obtenga información sobre cómo instalar los paquetes integrados de Campaña
audience: installation
content-type: reference
topic-tags: initial-configuration
translation-type: tm+mt
source-git-commit: 6d5dbc16ed6c6e5a2e62ceb522e2ccd64b142825
workflow-type: tm+mt
source-wordcount: '1154'
ht-degree: 11%

---


# Instalación de paquetes integrados Campaign Classic{#installing-campaign-standard-packages}

## Acerca de los paquetes integrados {#campaign-standard-packages}

Los paquetes integrados contienen un conjunto de características que se pueden instalar según sus necesidades y según el contrato. La lista completa de los paquetes integrados de Campaña está disponible a continuación.

>[!CAUTION]
>
>Sólo puede instalar los paquetes correspondientes a las opciones mencionadas en su contrato de licencia.
>
>La instalación de un nuevo paquete puede afectar a toda la plataforma: debe probarse y validarse antes de la implementación final.
>
>Una vez instalado un paquete, no podrá desinstalarlo.

Para instalar un paquete integrado:

1.  En la consola de cliente de Adobe Campaign, acceda al asistente de importación del paquete desde **[!UICONTROL Tools > Advanced > Package import...]**.
1. Seleccione **[!UICONTROL Install a standard package]**.
1. En la lista del paquete, compruebe los paquetes que desea instalar.
   >[!NOTE]
   >
   >Cuando un paquete está atenuado, significa que ya está instalado o que no es compatible con su instancia. La compatibilidad se detalla en la tabla siguiente.
1. Haga clic en **[!UICONTROL Next]**, luego en **[!UICONTROL Start]** para iniciar la instalación del paquete.

   Una vez instalados los paquetes, la barra de progreso muestra el **100 %** y puede ver el siguiente mensaje en los registros de instalación: **[!UICONTROL Installation of packages successful]**.

1. **[!UICONTROL Close]** la ventana de instalación.

Los paquetes ya están instalados.

### Lista de paquetes listos para usar {#list-of-standard-packages}

La siguiente tabla lista todos los paquetes integrados de Campaña.

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
   <td> Supervisa los envíos y los problemas que se detectan al enviar mensajes. <a href="../../delivery/using/about-delivery-monitoring.md">Más información</a><br /> </td> 
   <td> Todo</td> 
  </tr> 
  <tr> 
   <td> Campañas de marketing (Campaña)<br /> </td> 
   <td> Define, optimiza, ejecuta y analiza las comunicaciones y las campañas de marketing. <a href="../../campaign/using/designing-marketing-campaigns.md">Más información</a><br /> </td> 
   <td> Mercadotecnia</td>
  </tr> 
  <tr> 
   <td> Recursos de marketing (MRM)<br /> </td> 
   <td> Controla las acciones de mercadotecnia en modo colaborativo proporcionando administración y seguimiento de las tareas, presupuestos y recursos de marketing. <a href="../../campaign/using/about-marketing-resource-management.md">Más información</a> <br /> </td> 
   <td> Mercadotecnia</td> 
  </tr> 
  <tr> 
   <td> Motor de oferta (interacción)<br /> </td> 
   <td> Responde en tiempo real durante una interacción con un determinado contacto (cliente o destinatario) al convertirlos en una o varias ofertas adaptadas.  Opcional. <a href="../../interaction/using/interaction-and-offer-management.md#packages-configuration">Más información</a> <br /> </td> 
   <td> Todo<br /> </td> 
  </tr> 
  <tr> 
   <td> Control del motor de oferta con instancia de ejecución. Opcional.<br /> </td> 
   <td> Paquete que instalar en la instancia de control para el motor de Oferta (interacción). <a href="../../interaction/using/distributed-architectures.md#packages-configuration">Más información</a> </td> 
   <td> Marketing<br /> </td>  
  </tr> 
  <tr> 
   <td> Motor de oferta para instancias de ejecución. Opcional.<br /> </td> 
   <td> Paquete que instalar en instancias de ejecución para motor de Oferta (interacción). <a href="../../interaction/using/distributed-architectures.md">Más información</a> </td> 
   <td> Mid, Ejecución <br /> </td>  
  </tr> 
  <!--tr> 
   <td> Lead Management (Leads) (deprecated)<br /> </td> 
   <td> Simplifies the process of building and maintaining the entire leads management life cycle. <br /> </td> 
   <td> Yes<br /> </td> 
   <td> Optional, <a href="https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html">Learn More</a> </td> 
  </tr--> 
  <tr> 
   <td> Redes sociales (Social Marketing) <br /> </td> 
   <td> Sincroniza Adobe Campaign con Twitter y Facebook. <a href="../../social/using/about-social-marketing.md">Más información</a> <br /> </td> 
   <td> Todo</td> 
  </tr> 
  <tr> 
   <td> Control de mensaje transaccional (Centro de mensajes - Control)<br /> </td> 
   <td> Gestiona los mensajes de activación generados a partir de eventos activados desde sistemas de información. Opcional. <a href="../../message-center/using/about-transactional-messaging.md">Más información</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Ejecución de mensaje transaccional (Centro de mensajes - Ejecución) <br /> </td> 
   <td> Garantiza una mayor disponibilidad y una mejor administración de la carga. Opcional. <a href="../../message-center/using/about-transactional-messaging.md">Más información</a><br /> </td> 
   <td> Ejecución<br /> </td>
  </tr> 
  <tr> 
   <td> Canal LINE<br /> </td> 
   <td> Envía envíos mediante el canal LINE con Adobe Campaign. Opcional. La mensajería transaccional (paquete de centro de mensajes) es obligatoria. <a href="../../delivery/using/line-channel.md">Más información</a> <br /> </td> 
   <td> Todo<br /> </td> 
  </tr> 
  <tr> 
   <td> canal de correo postal<br /> </td> 
   <td> Envía envíos mediante el canal de correo directo con Adobe Campaign. Opcional. <a href="../../delivery/using/about-direct-mail-channel.md">Más información</a><br /> </td> 
   <td> Todo<br /> </td>
  </tr> 
  <tr> 
   <td> Canal móvil (SMS) <br /> </td> 
   <td> Envía envíos mediante el canal móvil/SMS con Adobe Campaign. Opcional. <a href="../../delivery/using/sms-channel.md">Más información</a> <br /> </td> 
   <td> Todo<br /> </td> 
  </tr> 
  <tr> 
   <td> Canal de aplicaciones móviles<br /> </td> 
   <td> Utiliza la plataforma de Adobe Campaign para enviar notificaciones personalizadas a los terminales de iOS y Android mediante aplicaciones. Opcional. <a href="../../delivery/using/about-mobile-app-channel.md">Más información</a> <br /> </td> 
   <td> Todo<br /> </td> 
  </tr> 
  <tr> 
   <td> Content Manager<br /> </td> 
   <td> Crea boletines informativos o sitios web recurrentes y, a continuación, valida y publica los mensajes. <a href="../../delivery/using/about-content-management.md">Más información</a> <br /> </td> 
   <td> </td>
  </tr> 
  <tr> 
   <td> Encuestas en línea (Administrador de Encuestas)<br /> </td> 
   <td> Crea y administra formularios en línea para agregar o modificar información de perfil, para suscribirse, para cancelar la suscripción o para un formulario de entrada de competencia. Opcional. <a href="../../web/using/about-surveys.md">Más información</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Marketing Analytics<br /> </td> 
   <td> Permite analizar y medir datos, calcular estadísticas, simplificar y optimizar la creación y el cálculo de informes. Además, puede crear informes y generar poblaciones de destinatarios. Opcional. <a href="../../reporting/using/about-cubes.md">Más información</a><br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Gestor de respuestas<br /> </td> 
   <td> Mide el éxito y la rentabilidad de las campañas o propuestas de oferta de marketing para todos los canales de comunicación.  Opcional. <a href="../../campaign/using/about-response-manager.md">Más información</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Acceso a datos externos (Acceso de datos federado)<br /> </td> 
   <td> Proporciona la opción Acceso de datos federado (FDA) para procesar la información almacenada en una o varias bases de datos externas, de modo que pueda acceder a los datos externos sin cambiar la estructura de los datos de Adobe Campaign.  Opcional. <a href="../../workflow/using/accessing-an-external-database--fda-.md">Más información</a> <br /> </td> 
   <td> Todo<br /> </td> 
  </tr> 
  <tr> 
   <td> Campaign Optimization (Optimización de la campaña)<br /> </td> 
   <td> Controla, filtros y supervisa el envío de envíos para que los mensajes enviados satisfagan mejor las necesidades y expectativas de los clientes, de acuerdo con las políticas de comunicación de compañía. Opcional. <a href="../../campaign/using/about-campaign-typologies.md">Más información</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Monitorización de la capacidad de entrega (capacidad de entrega por correo electrónico)<br /> </td> 
   <td> Mide el éxito de sus campañas llegando a la bandeja de entrada de sus destinatarios sin rebotar o marcando como correo no deseado. Opcional. <a href="../../delivery/using/about-deliverability.md">Más información</a> <br /> </td> 
   <td> Todo </td> 
  </tr> 
  <tr> 
   <td> Administración de cupones<br /> </td> 
   <td> Crea un conjunto de cupones para agregarlos a las próximas ofertas de marketing. Opcional. <a href="../../delivery/using/personalized-coupons.md">Más información</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Renderización de la bandeja de entrada (IR)<br /> </td> 
   <td> Le permite realizar la previsualización del mensaje enviado en los diferentes contextos en los que puede recibirse y comprobar la compatibilidad en las principales aplicaciones y escritorios. Opcional. <a href="../../delivery/using/inbox-rendering.md">Más información</a><br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Marketing central/local (Distributed Marketing (Marketing distribuido))<br /> </td> 
   <td> Implementa campañas de cooperación entre entidades centrales (sede, departamentos de mercadotecnia, etc.) y entidades locales (puntos de venta, agencias regionales, etc.). Opcional. <a href="../../campaign/using/about-distributed-marketing.md">Más información</a><br /> </td> 
   <td> Mercadotecnia </td> 
  </tr> 
  <tr> 
   <td> Conectores CRM<br /> </td> 
   <td> Proporciona varios conectores CRM para vincular su plataforma Adobe Campaign a sus sistemas de terceros.  <a href="../../platform/using/crm-connectors.md">Más información</a> <br /> </td> 
   <td> Mercadotecnia</td> 
  </tr> 
  <tr> 
   <td> Conectores de Web Analytics<br /> </td> 
   <td> Permite que Adobe Campaign y Adobe Analytics interactúen a través del paquete de conectores de Web Analytics. No es compatible con la mensajería transaccional (paquete de centro de mensajes). <a href="../../platform/using/adobe-analytics-data-connector.md">Más información</a><br /> </td> 
   <td> Mercadotecnia </td> 
  </tr> 
  <tr> 
   <td> Integración de AEM<br /> </td> 
   <td> Le permite administrar el contenido de sus envíos de correo electrónico, así como los formularios directamente en Adobe Experience Manager, para beneficiarse de las funcionalidades de edición de contenido de AEM, así como de las capacidades de envío de Adobe Campaign. <a href="../../integrations/using/about-adobe-experience-manager.md">Más información</a> <br /> </td> 
   <td> Mercadotecnia</td> 
  </tr> 
  <tr> 
   <td> Integración de Audiencias compartidas de Adobe Experience Cloud<br /> </td> 
   <td> Le permite intercambiar y compartir audiencias/segmentos con soluciones y servicios principales de Adobe Experience Cloud. Requiere IMS. <a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Más información</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Integración con Adobe Experience Cloud<br /> </td> 
   <td> Le permite importar y exportar audiencias/segmentos de diferentes soluciones de Adobe Experience Cloud a Adobe Campaign. Opcional. <a href="../../integrations/using/configuring-ims.md#installing-the-package">Más información</a> </td> 
   <td> Mercadotecnia</td> 
  </tr> 
  <tr> 
   <td> Reglamento de protección de datos de privacidad<br /> </td> 
   <td> Contiene funcionalidad adicional para ayudarle con la conformidad con la privacidad en Campaign Classic. <a href="https://helpx.adobe.com/es/campaign/kb/acc-privacy.html">Más información</a> <br /> </td> 
   <td> Todo</td> 
  </tr> 
  <tr> 
   <td> Transferencia al Intermediaria <br /> </td> 
   <td> Detalla la instalación y configuración de un servidor intermediaria, así como la implementación de una instancia que permite a terceros enviar mensajes en modo intermediaria. Opcional. <a href="../../installation/using/mid-sourcing-server.md">Más información</a> <br /> </td> 
   <td> Mercadotecnia </td> 
  </tr> 
  <tr> 
   <td> Mid-sourcing platform<br /> </td> 
   <td> Esta configuración es una solución intermedia óptima entre una configuración alojada (ASP) y la internalización. Los componentes de ejecución orientados hacia el exterior se llevan a cabo en un servidor "intermediaria" alojado en Adobe Campaign. Opcional. <a href="../../installation/using/mid-sourcing-server.md">Más información</a> <br /> </td> 
   <td> Intermediaria </td> 
  </tr> 
  <tr> 
   <td> Compatibilidad con AMP<br /> </td> 
   <td> Permite utilizar la nueva AMP interactiva para formato del correo electrónico y enviar correos electrónicos dinámicos. Opcional. <a href="../../delivery/using/defining-interactive-content.md">Más información</a> <br /> </td> 
   <td> Todo </td> 
  </tr> 
  <tr> 
   <td> Conector ACS<br /> </td> 
   <td> Puente Adobe Campaign v7 y Adobe Campaign Standard. Se trata de una función integrada en Campaign v7 que duplica automáticamente los datos en Campaign Standard, lo que une lo mejor de ambas aplicaciones. Opcional. <a href="../../integrations/using/acs-connector-principles-and-data-cycle.md">Más información</a> <br /> </td> 
   <td> Mercadotecnia </td> 
  </tr> 
 </tbody> 
</table>

### Paquete de centro de mensajes {#message-center-package}

Debe instalar canales de envío (correo electrónico, canal móvil, canal de aplicaciones móviles, etc.) antes de instalar la mensajería transaccional (paquete de centro de mensajes). Si ha iniciado un proyecto de centro de mensajes de solo correo electrónico y necesita agregar un nuevo canal después, debe seguir estos pasos:

1. Instale el nuevo canal, por ejemplo el **canal móvil**, utilizando el asistente de importación del paquete ( **[!UICONTROL Tools > Advanced > Import package > Adobe Campaign package]**).
1. Importe el archivo ( **[!UICONTROL Tools > Advanced > Import package > File]**) y seleccione:

   ```
   \datakit\nms\[Your language]\package\messageCenter.xml
   ```

1. En **[!UICONTROL XML data content to import]**, mantenga sólo la Plantilla de envíos del centro de mensajes correspondiente al canal relacionado. Por ejemplo, si ha agregado el **canal móvil**, mantenga solo el elemento **entidades** correspondiente a la plantilla **[!UICONTROL Mobile transactional message]** (smsTriggerMessage). Si ha agregado el **Canal de aplicaciones móviles**, mantenga solo las plantillas **mensaje transaccional de iOS** (iosTriggerMessage) y **mensaje transaccional de Android** (androidTriggerMessage).

   ![](assets/messagecenter_install_channel.png)

>[!CAUTION]
>
>Las Plantillas de envíos del centro de mensajes para LINE no estarán disponibles si los paquetes del centro de mensajes están instalados antes de LINE

