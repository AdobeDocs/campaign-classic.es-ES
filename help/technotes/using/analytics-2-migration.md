---
product: campaign
title: Migración a la API de Adobe Analytics 2.0
description: Guía de migración de la API de Campaign Classic - Adobe Analytics 2.0
feature: Technote, Analytics Integration
hide: true
source-git-commit: 64460d51b002a7821bba9c2998d9ccccab3046ad
workflow-type: tm+mt
source-wordcount: '874'
ht-degree: 1%
---
# Migración a la API de Adobe Analytics 2.0 {#analytics-2-migration}

Las API de Adobe Analytics 1.4 [están llegando al final de su vida útil](https://developer.adobe.com/analytics-apis/docs/1.4/guides/eol){target="_blank"}. El [conector de Web Analytics](../../integrations/using/gs-aa.md) que vincula su instancia de Campaign a Adobe Analytics depende de estas API, por lo que debe actualizar a una compilación que utilice las nuevas API de Analytics 2.0 para mantener la integración en ejecución.

>[!CAUTION]
>
>Al actualizar se vuelven a importar los dos flujos de trabajo técnicos integrados que alimentan el conector, [!UICONTROL webAnalyticsSendMetrics] y [!UICONTROL webAnalyticsGetWebEvents] (consulte la [referencia de flujos de trabajo de Web Analytics](../../workflow/using/web-analytics.md) para ver qué hace cada uno). Cualquier personalización que haya realizado sobre estos flujos de trabajo se sobrescribirá con la reimportación. Evite modificar estos flujos de trabajo integrados directamente: genere la personalización en un flujo de trabajo personalizado independiente en su lugar, de modo que las futuras actualizaciones no lo sobrescriban. La actualización también actualiza los archivos JavaScript integrados de Analytics: si alguno de los flujos de trabajo personalizados hace referencia a estos archivos, se romperán y deberán adaptarse al nuevo código.

## ¿Se ha visto afectado? {#are-you-impacted}

Se verá afectado si su instancia utiliza la cuenta externa [!UICONTROL Web Analytics] para cualquiera de las siguientes acciones:

* Envío de indicadores y atributos de campañas de correo electrónico a Adobe Analytics como métricas.
* Envío de datos de clasificación a Adobe Analytics.
* El flujo de remarketing (que identifica los contactos convertidos después de una campaña).
* Cuenta externa [!UICONTROL Web Analytics] que planea configurar por primera vez.

¿No está seguro de cuál de estas se aplica a usted? Compruebe cuál de los flujos de trabajo técnicos anteriores está activo en la instancia y revise la configuración de la cuenta externa de [!UICONTROL Web Analytics] en [!UICONTROL Administration > Platform > External accounts] (consulte [Cuenta externa de Web Analytics](../../installation/using/external-accounts.md#web-analytics-external-account)).

## Cómo migrar {#how-to-migrate}

Si está en una instancia **alojada en Adobe**, Adobe se encarga de la configuración de aprovisionamiento de SFTP, la inclusión en la lista de IP permitidas y las claves como parte de la actualización, y solo necesita validar los casos de uso una vez que la nueva compilación esté activa.

Si se encuentra en una implementación **on-premise o híbrida**, complete los siguientes pasos.

1. [Actualice su entorno de Campaign](../../production/using/build-upgrade.md) a una compilación que incluya los cambios de Adobe Analytics 2.0. Puede confirmar la compilación que está ejecutando desde [!UICONTROL Help > About...] (consulte [cómo comprobar la versión de Campaign](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)).
1. Revise cuáles de los casos de uso anteriores se aplican a su instancia, ya que el siguiente paso depende de él.
1. Si utiliza el flujo de remarketing, el flujo de trabajo [!UICONTROL webAnalyticsFindConverted] necesita un canal SFTP específico para intercambiar datos con Adobe Analytics 2.0. Configúrelo como se indica a continuación; de lo contrario, vaya al paso siguiente.
   1. Aprovisionar un servidor SFTP para la instancia mediante autenticación basada en claves, siguiendo las mismas [prácticas recomendadas del servidor SFTP](../../platform/using/sftp-server-usage.md) que aplicaría a cualquier otra integración SFTP externa. Adobe proporciona [script de configuración SFTP de ejemplo](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html?package=/content/software-distribution/en/details.html/content/dam/campaign/public/setup_sftp.zip){target="_blank"} para ayudarle a empezar.
   1. Registre los detalles de conexión de ese servidor en Adobe Analytics ejecutando la secuencia de comandos suministrada con la nueva compilación:

      ```
      nlserver javascript -instance:<instance_name> -arg:host=<sftp_host_url>#user=<sftp_user> -file <path_to_the_file>/aaremarketingLocation.js
      ```

      Ejemplo:

      ```
      nlserver javascript -instance:test_mkt_stage2 -arg:host=test-mkt-stage1.campaign.adobe.com#user=test -file ./nl6/datakit/nms/eng/js/aaremarketingLocation.js
      ```

   1. Incluya Adobe Analytics en la lista de permitidos en su servidor SFTP, ya que las exportaciones de remarketing solo se inician desde un conjunto fijo de intervalos de IP de Adobe:
      * [Busque las direcciones IP actuales de recopilación de datos de Adobe Analytics](https://experienceleague.adobe.com/en/docs/core-services/interface/data-collection/ip-addresses){target="_blank"} y agréguelas a la lista de permitidos del servidor SFTP. Las exportaciones de Analytics basadas en FTP (incluidas las fuentes de datos) solo se originan en direcciones IPv4 de las regiones de Londres, Oregón y Singapur.
      * [Recupere la clave pública de Adobe Analytics](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-18141){target="_blank"} y agréguela al archivo `authorized_keys` de su servidor SFTP para que Analytics pueda autenticarse.
1. Habilite la marca de característica `FEATUREFLAG_USE_ANALYTICS_20_API` en su instancia creando o configurando `longvalue` de la opción en `1` en [!UICONTROL xtkOption], en **[!UICONTROL Administration]> [!UICONTROL Platform] >[!UICONTROL Options]** en el árbol de Campaign Explorer. Este paso es obligatorio independientemente del caso de uso anterior que se le aplique.
1. Valide la migración utilizando cada caso de uso que se aplique a su instancia (envíe una campaña de prueba, compruebe que los indicadores se dirijan a Analytics y confirme los datos de remarketing si corresponde) antes de eliminar cualquier conectividad antigua.

## Configuración de una nueva cuenta externa de Web Analytics {#setting-up-a-new-web-analytics-external-account}

Lo siguiente se aplica tanto si la instancia está alojada en Adobe como si es local/híbrida.

Si está configurando la cuenta externa [!UICONTROL Web Analytics] por primera vez en lugar de migrar una existente, siga los [pasos de configuración de la cuenta externa](../../installation/using/external-accounts.md#web-analytics-external-account) y la guía de introducción al [conector](../../integrations/using/gs-aa.md).

Como Analytics 2.0 introduce una nueva administración de clasificaciones, también debe crear un conjunto de clasificaciones en Adobe Analytics para que la cuenta externa pueda recoger los datos de clasificación del grupo de informes. Este es un nuevo paso: créelo después de configurar las variables de conversión y los eventos de éxito y antes de configurar la cuenta externa en Campaign.

Para crear el conjunto de clasificaciones:

1. En la barra de menú superior [!DNL Adobe Analytics], seleccione **[!UICONTROL Components]** > **[!UICONTROL Classification sets]** y luego haga clic en **[!UICONTROL New]**.

   ![](assets/analytics-classification-set-menu.png)

1. En el diálogo **[!UICONTROL Add New Classification Set]**:

   ![](assets/analytics-classification-set-dialog.png)

   * Escriba un **[!UICONTROL Name]** para el conjunto de clasificaciones.
   * Establezca **[!UICONTROL Type]** en **[!UICONTROL Primary]**.
   * En **[!UICONTROL Job notifications]**, elija a quién se debe notificar si los trabajos del conjunto de clasificación se han realizado correctamente o no y proporcione las direcciones de correo electrónico correspondientes.
   * En **[!UICONTROL Subscriptions]**, seleccione el grupo de informes y la variable de conversión que creó para el nombre de la campaña interna en el paso anterior.

1. Haga clic **[!UICONTROL Save]**.

Campaign descubrirá automáticamente este conjunto de clasificaciones cuando configure la cuenta externa en el siguiente paso. Para obtener más información sobre los conjuntos de clasificaciones, consulte la [documentación de Adobe Analytics](https://experienceleague.adobe.com/en/docs/analytics/components/classifications/sets/create-set){target="_blank"}.

## ¿Necesita ayuda? {#need-help}

Si tiene problemas durante la migración, comuníquese con el [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}.
