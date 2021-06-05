---
solution: Campaign Classic
product: campaign
title: Conector de Adobe Analytics
description: Más información sobre el conector Adobe Analytics
feature: Información general
role: Business Practitioner, Administrator
level: Beginner
exl-id: 5bd12f65-f468-41ab-bbae-e59a6592a803
source-git-commit: 46e5cac1df419de933d96a3f35f7ac491a1defa5
workflow-type: tm+mt
source-wordcount: '1532'
ht-degree: 55%

---

# Conector de Adobe Analytics{#adobe-analytics-connector}

## Acerca de la integración de Adobe Analytics Connector {#about-analytics-connector-integration}

>[!CAUTION]
>
>El conector de Adobe Analytics no es compatible con los mensajes transaccionales (Centro de mensajes).

Adobe Analytics Connector permite que Adobe Campaign y Adobe Analytics interactúen mediante el paquete **[!UICONTROL Web Analytics connectors]** . Envía datos a Adobe Campaign en forma de segmentos con respecto al comportamiento del usuario tras una campaña de correo electrónico. Por el contrario, envía indicadores y atributos de las campañas de correo electrónico que Adobe Campaign envía a Adobe Analytics.

Con Adobe Analytics Connector, Adobe Campaign puede medir la audiencia de Internet (Web Analytics). Gracias a estas integraciones, Adobe Campaign puede recuperar los datos del comportamiento del visitante para uno o más sitios después de una campaña de marketing y (después del análisis) ejecutar nuevas campañas con la intención de convertirlos en compradores. Por el contrario, las herramientas de Web Analytics permiten que Adobe Campaign reenvíe indicadores y atributos de campaña a sus plataformas.

Los campos de acción de cada herramienta son los siguientes:

* Función de Web Analytics:

   1. marca las campañas de email iniciadas con Adobe Campaign,
   1. guarda el comportamiento del destinatario en el sitio visitado después de hacer clic en el email de la campaña, en forma de segmentos. Los segmentos se refieren a productos abandonados (vistos, pero no añadidos al carro ni comprados), compras o abandonos del carro de la compra.

* Función de Adobe Campaign:

   1. envía los indicadores y atributos de campaña al conector, que a su vez los reenvía a la herramienta Web Analytics,
   1. recupera y analiza segmentos,
   1. activa una campaña de remarketing.

## Configuración de la integración {#setting-up-the-integration}

Para configurar Data connector, debe conectarse a la instancia de Adobe Campaign y realizar las siguientes operaciones:

1. [Crear un grupo de informes en Adobe Analytics](#report-suite-analytics)
1. [Configurar las variables de conversión y los eventos de éxito](#configure-conversion-success)
1. [Configurar la cuenta externa en Adobe Campaign Classic](#external-account-classic)

### Cree su grupo de informes en Adobe Analytics {#report-suite-analytics}

Para configurar la integración de Adobe Analytics/Adobe Campaign Classic, debe conectarse a la instancia [!DNL Adobe Analytics] y realizar las siguientes operaciones:

1. En [!DNL Adobe Analytics], seleccione **[!UICONTROL Admin tab]** y haga clic en **[!UICONTROL All admin]**.

   ![](assets/analytics_connnector_1.png)

1. Haga clic en **[!UICONTROL Report suites]**.

   ![](assets/analytics_connnector_2.png)

1. En la página **[!UICONTROL Report suite manager]**, haga clic en **[!UICONTROL Create new]** y luego en **[!UICONTROL Report suite]**.

   Para ver el procedimiento detallado sobre la creación de **[!UICONTROL Report suite]**, consulte esta [sección](https://experienceleague.adobe.com/docs/analytics/admin/manage-report-suites/new-report-suite/t-create-a-report-suite.html?lang=en#prerequisites).

   ![](assets/analytics_connnector_3.png)

1. Seleccione una plantilla.

1. Configure su nuevo grupo de informes con la siguiente información:

   * **[!UICONTROL Report Suite ID]**
   * **[!UICONTROL Site Title]**
   * **[!UICONTROL Time Zone]**
   * **[!UICONTROL Go Live Date]**
   * **[!UICONTROL Estimated Page Views Per Day]**

   ![](assets/analytics_connnector_4.png)

1. Cuando esté configurado, haga clic en **[!UICONTROL Create report suite]**.

### Configurar las variables de conversión y los eventos de éxito {#configure-conversion-success}

Después de crear su **[!UICONTROL Report suite]**, debe configurar sus **[!UICONTROL Conversion variables]** y **[!UICONTROL Success events]** de la siguiente manera:

1. Seleccione el **[!UICONTROL Report suite]** configurado anteriormente.

1. En el botón **[!UICONTROL Edit settings]**, seleccione **[!UICONTROL Conversion]** > **[!UICONTROL Conversion variables]**.

   ![](assets/analytics_connnector_5.png)

1. Haga clic en **[!UICONTROL Add new]** para crear los identificadores necesarios para medir el impacto de la campaña de correo electrónico, es decir, el nombre de campaña interno (cid) y el ID de tabla de iNmsBroadlog (bid).

   Para aprender a editar **[!UICONTROL Conversion variables]**, consulte esta [sección](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/conversion-variables/t-conversion-variables-admin.html?lang=en#admin-tools).

   ![](assets/analytics_connnector_6.png)

1. Haga clic en **[!UICONTROL Save]** cuando termine.

1. A continuación, para crear su **[!UICONTROL Success events]**, seleccione **[!UICONTROL Conversion]** > **[!UICONTROL Success events]** en el botón **[!UICONTROL Edit settings]**.

   ![](assets/analytics_connnector_7.png)

1. Haga clic en **[!UICONTROL Add new]** para configurar el siguiente **[!UICONTROL Success events]**:

   * **[!UICONTROL Clicked]**
   * **[!UICONTROL Opened]**
   * **[!UICONTROL Person clicks]**
   * **[!UICONTROL Processed]**
   * **[!UICONTROL Scheduled]**
   * **[!UICONTROL Sent]**
   * **[!UICONTROL Total bounces]**
   * **[!UICONTROL Unique Clicks]**
   * **[!UICONTROL Unique Opens]**
   * **[!UICONTROL Unsubscribed]**

   Para aprender a configurar **[!UICONTROL Success events]**, consulte esta [sección](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/success-events/t-success-events.html?lang=en#admin-tools)

   ![](assets/analytics_connnector_8.png)

1. Haga clic en **[!UICONTROL Save]** cuando termine.

Cuando se configure el grupo de informes, deberá configurar el **[!UICONTROL External accounts]** en Adobe Campaign Classic.

### Configure su cuenta externa en Adobe Campaign Classic {#external-account-classic}

>[!IMPORTANT]
>
> Para que esta integración funcione, debe instalar el paquete **[!UICONTROL Web Analytics connectors]** en Adobe Campaign.
>
>Para obtener más información sobre la instalación del paquete, consulte esta [página](../../installation/using/installing-campaign-standard-packages.md).

Ahora debe configurar la cuenta externa **[!UICONTROL Web Analytics]** en Adobe Campaign para habilitar la sincronización entre las dos soluciones.

Tenga en cuenta que si uno de los **[!UICONTROL Report suite]**, **[!UICONTROL Conversion variables]** o **[!UICONTROL Success events]** no está visible al configurar la cuenta externa, significa que le falta un permiso para este componente recién creado en el **[!UICONTROL Product profile]** asociado al usuario.

Para obtener más información, consulte la página [Perfiles de producto para Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/permissions/product-profile.html?lang=en#product-profile-admins) .

1. Vaya a la carpeta **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External accounts]** del árbol de Adobe Campaign y haga clic en **[!UICONTROL New]**.

   ![](assets/analytics_connnector_9.png)

1. Utilice la lista desplegable para seleccionar el tipo **[!UICONTROL Web Analytics]** y **[!UICONTROL Adobe Analytics]** en la lista desplegable **[!UICONTROL Integration]**.

   ![](assets/analytics_connnector_10.png)

1. Haga clic en **[!UICONTROL Configure]** junto a la lista desplegable **[!UICONTROL Integration]**.

1. Desde la ventana **[!UICONTROL Configure Analytics integration]** , asigne la cuenta externa con el grupo de informes creado anteriormente, con la siguiente información:

   * **[!UICONTROL E-Mail]**
   * **[!UICONTROL IMS Org]**
   * **[!UICONTROL Analytics Company]**
   * **[!UICONTROL Report Suite]**

1. Desde la categoría **[!UICONTROL eVars]**, asigne los dos **[!UICONTROL Conversion variables]** configurados en [!DNL Adobe Analytics].

   ![](assets/analytics_connnector_11.png)

1. Desde la categoría **[!UICONTROL Events]**, asigne los diez **[!UICONTROL Success events]** configurados en [!DNL Adobe Analytics].

1. Haga clic en **[!UICONTROL Submit]** cuando termine. Adobe Campaign creará **[!UICONTROL Data source]**, **[!UICONTROL Calculated metrics]**, **[!UICONTROL Remarketing segments]** y **[!UICONTROL Classifications]** en el Analytics **[!UICONTROL Report Suite]** asignado.

   Una vez finalizada esta sincronización entre [!DNL Adobe Analytics] y Adobe Campaign, puede cerrar la ventana.

1. La configuración se puede ver desde la pestaña **[!UICONTROL Data Settings]** de la ventana **[!UICONTROL Configure Analytics integration]**.

   Con el botón **[!UICONTROL Sync]**, [!DNL Adobe Campaign] sincronizará los cambios de nombre realizados en [!DNL Adobe Analytics]. Si el componente se elimina en [!DNL Adobe Analytics], se tachará en [!DNL Adobe Campaign] o se mostrará con un mensaje **no encontrado**.

   ![](assets/analytics_connnector_12.png)

1. Si es necesario, puede añadir o eliminar segmentos de la pestaña **[!UICONTROL Update Segments]** .

1. En **[!UICONTROL External account]**, haga clic en el enlace **[!UICONTROL Enrich the formula...]** para cambiar la fórmula de cálculo de URL y especificar la información de integración de la herramienta de Web Analytics (ID de campaña) y los dominios de los sitios cuya actividad debe rastrearse.

   ![](assets/analytics_connnector_13.png)

1. Especifique los nombres de dominio de los sitios.

   ![](assets/analytics_connnector_14.png)

1. Haga clic en **[!UICONTROL Next]** y asegúrese de que los nombres de dominio se hayan guardado.

   ![](assets/analytics_connnector_15.png)

1. Si es necesario, puede sobrecargar la fórmula de cálculo. Para ello, marque la casilla y edite la fórmula directamente en la ventana.

   >[!IMPORTANT]
   >
   >Este modo de configuración está reservado para usuarios expertos: cualquier error en esta fórmula puede resultar en envíos de correo electrónico detenidos.

1. La pestaña **[!UICONTROL Advanced]** permite configurar o modificar más ajustes técnicos.

   * **[!UICONTROL Lifespan]**: permite especificar el retraso (en días) después del cual los eventos web se recuperan en Adobe Campaign mediante flujos de trabajo técnicos. Predeterminado: 180 días.
   * **[!UICONTROL Persistence]**: permite especificar el periodo durante el cual se pueden atribuir todos los eventos web (una compra, por ejemplo) a una nueva campaña de marketing. Predeterminado: 7 días.

>[!NOTE]
>
>Si utiliza varias herramientas de medición de audiencia, puede seleccionar **[!UICONTROL Other]** en la lista desplegable **[!UICONTROL Partners]** al crear la cuenta externa. Solo puede hacer referencia a una cuenta externa en las propiedades de entrega: por lo tanto, debe adaptar la fórmula de URL rastreadas agregando los parámetros esperados por las herramientas de medición de Adobe y otras herramientas.

### Flujos de trabajo técnicos de procesos de Web Analytics {#technical-workflows-of-web-analytics-processes}

El intercambio de datos entre Adobe Campaign y Adobe Analytics se gestiona mediante cuatro flujos de trabajo técnicos que funcionan como una tarea en segundo plano.

Están disponibles en el árbol de Adobe Campaign, en la carpeta **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]** > **[!UICONTROL Web analytics process]**.

![](assets/webanalytics_workflows.png)

* **[!UICONTROL Recovering of web events]**: una vez cada hora, este flujo de trabajo descarga segmentos sobre el comportamiento de los usuarios en un sitio determinado, los incluye en la base de datos de Adobe Campaign e inicia el flujo de trabajo de remarketing.
* **[!UICONTROL Event purge]**: este flujo de trabajo permite eliminar todos los eventos de la base de datos en función del periodo configurado en el campo **[!UICONTROL Lifespan]**. Para obtener más información, consulte [Configuración de la cuenta externa en Adobe Campaign Classic](#external-account-classic).
* **[!UICONTROL Identification of converted contacts]**: directorio de los visitantes que realizaron una compra después de una campaña de remarketing. Los datos que recopila este flujo de trabajo se pueden consultar en el informe **[!UICONTROL Re-marketing efficiency]**, consulte esta [página](#creating-a-re-marketing-campaign).
* **[!UICONTROL Sending of indicators and campaign attributes]**: permite enviar indicadores de campaña de correo electrónico a través de Adobe Campaign a Adobe Experience Cloud mediante Adobe Analytics Connector. Este flujo de trabajo se activa a las 4 de la mañana cada día y los datos pueden tardar hasta 24 horas en enviarse a Analytics.

   Tenga en cuenta que este flujo de trabajo no debe reiniciarse o volverá a enviar todos los datos anteriores, lo que puede distorsionar los resultados de Analytics.

   Los indicadores implicados son:

   * **[!UICONTROL Messages to deliver]** (@toDeliver)
   * **[!UICONTROL Processed]** (@processed)
   * **[!UICONTROL Success]** (@success)
   * **[!UICONTROL Total count of opens]** (@totalRecipientOpen)
   * **[!UICONTROL Recipients who have opened]** (@recipientOpen)
   * **[!UICONTROL Total number of recipients who clicked]** (@totalRecipientClick)
   * **[!UICONTROL People who clicked]** (@personClick)
   * **[!UICONTROL Number of distinct clicks]** (@recipientClick)
   * **[!UICONTROL Opt-Out]** (@optOut)
   * **[!UICONTROL Errors]** (@error)

   >[!NOTE]
   >
   >Los datos enviados son la información delta basada en el último resumen que puede generar un valor negativo en los datos de la métrica.

   Los atributos enviados son los siguientes:

   * **[!UICONTROL Internal name]** (@internalName)
   * **[!UICONTROL Label]** (@label)
   * **[!UICONTROL Label]** (operation/@label): sólo si está instalado el paquete de **Campaign**
   * **[!UICONTROL Nature]** (operation/@nature): solo si está instalado el paquete de **Campaign**
   * **[!UICONTROL Tag 1]** (webAnalytics/@tag1)
   * **[!UICONTROL Tag 2]** (webAnalytics/@tag2)
   * **[!UICONTROL Tag 3]** (webAnalytics/@tag3)
   * **[!UICONTROL Contact date]** (scheduling/@contactDate)



## Seguimiento de envíos en Adobe Campaign {#tracking-deliveries-in-adobe-campaign}

Para que Adobe Experience Cloud pueda rastrear la actividad en los sitios una vez Adobe Campaign ha realizado la entrega, debe hacer referencia al conector coincidente en las propiedades de entrega. Para ello, siga los siguientes pasos:

1. Abra la entrega de la campaña a rastrear.

   ![](assets/webanalytics_delivery_properties_003.png)

1. Abra las propiedades de entrega.
1. Vaya a la pestaña **[!UICONTROL Web Analytics]** y seleccione la cuenta externa creada anteriormente. Consulte [Configuración de la cuenta externa en Adobe Campaign Classic](#external-account-classic).

   ![](assets/webanalytics_delivery_properties_002.png)

1. Ahora puede realizar la entrega y acceder a su informe en Adobe Analytics.

## Creación de una campaña de remarketing {#creating-a-re-marketing-campaign}

Para preparar la campaña de remarketing, simplemente cree plantillas de entrega para utilizarlas en campañas de tipo de remarketing. A continuación, configure su campaña de remarketing y vincúlela a un segmento. Cada segmento debe tener una campaña de remarketing diferente.

Las campañas de remarketing se inician automáticamente una vez que Adobe Campaign ha terminado de recuperar los segmentos analizando el comportamiento de las personas a las que se dirigió la campaña inicial. En caso de abandono del carro de compras o de la visualización del producto sin compra, se realiza una entrega a los destinatarios en cuestión para que la navegación por su sitio termine en una compra.

Adobe Campaign proporciona plantillas de entrega personalizadas que puede utilizar o aplicar a bases de datos propias para preparar las campañas.

1. Desde **[!UICONTROL Explorer]**, vaya a la carpeta **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]** del árbol de Adobe Campaign.

1. Duplique la plantilla de **[!UICONTROL Email delivery (re-marketing)]** o los ejemplos de plantilla de remarketing que ofrece Adobe Campaign.

   ![](assets/webanalytics_delivery_model.png)

1. Personalice la plantilla para adaptarla a sus necesidades y guárdela.

1. Cree una nueva campaña y seleccione la plantilla **[!UICONTROL Re-marketing campaign]** en la lista desplegable.

   ![](assets/webanalytics_remarketing_campaign_002.png)

1. Haga clic en el enlace **[!UICONTROL Configure...]** para especificar el segmento y la plantilla de envíos relacionados con la campaña.

1. Seleccione la cuenta externa configurada anteriormente.

   ![](assets/webanalytics_remarketing_campaign_003.png)

1. Seleccione el segmento correspondiente.

   ![](assets/webanalytics_remarketing_campaign_005.png)

1. Seleccione la plantilla de entrega que prefiere usar para esta campaña de remarketing y luego haga clic en **[!UICONTROL Finish]** para cerrar la ventana.

   ![](assets/webanalytics_remarketing_campaign_006.png)

1. Haga clic en **[!UICONTROL OK]** para cerrar la ventana de la campaña.

Puede acceder al informe de **[!UICONTROL Re-marketing efficiency]** a través de la página de informes globales. Permite ver la cantidad de contactos convertidos (por ejemplo: aquellos que han comprado algo) en relación con el número de abandonos del carro de la compra después del relanzamiento de la campaña de marketing de Adobe Campaign. La tasa de conversión se calcula por semana, mes o desde el inicio de la sincronización entre las herramientas de Adobe Campaign y Web Analytics.

![](assets/remarketing_reporting.png)
