---
product: campaign
title: Actualización del nuevo servidor de envío
description: Obtenga información sobre cómo actualizar al nuevo servidor de envío de Campaign
feature: Technote, Deliverability
hide: true
hidefromtoc: true
exl-id: bc62ddb9-beff-4861-91ab-dcd0fa1ed199
source-git-commit: c42d4022587846081442a39d03546c0ef335c7a0
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Actualización del nuevo servidor de envío {#acc-deliverability}

A partir de la versión [v7.2.2](../../rn/using/latest-release.md#release-7-2-2), Adobe Campaign depende de un nuevo servidor de entrega que ofrece alta disponibilidad y soluciona problemas de cumplimiento de seguridad. Campaign Classic ahora sincroniza las reglas de envío, los broadlogs y la dirección de supresión desde y hacia el nuevo servidor de envío. El antiguo servidor de capacidad de entrega se desactivará el 31 de agosto de 2022.

Como cliente Campaign Classic, debe implementar el nuevo servidor de capacidad de entrega **antes del 31 de agosto de 2022**.

>[!NOTE]
>
>Para obtener más información sobre estos cambios, consulta las [preguntas frecuentes](#faq) o ponte en contacto con el [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank}.
>

## ¿Qué ha cambiado?{#acc-deliverability-changes}

El Adobe está retirando los centros de datos más antiguos por motivos de cumplimiento de la seguridad. Los clientes de Adobe Campaign Classic deben migrar al nuevo servicio de capacidad de entrega, alojado en Amazon Web Service (AWS).

Este nuevo servidor garantiza una alta disponibilidad (99.9)&#x200B; y proporciona puntos de conexión seguros y autenticados para permitir que los servidores de campaña recuperen los datos necesarios: en lugar de conectarse a la base de datos para cada solicitud, el nuevo servidor de capacidad de entrega almacena en caché los datos para servir las solicitudes siempre que sea posible. Este mecanismo mejora el tiempo de respuesta&#x200B;

## ¿Se ha visto afectado?{#acc-deliverability-impacts}

Todos los clientes se verán afectados y deberán actualizar a [Campaign v7.2.2](../../rn/using/latest-release.md#release-7-2-2) (o más) e implementar su entorno para beneficiarse del nuevo servidor de entrega.

## ¿Cómo realizar la actualización?{#acc-deliverability-update}

Como **cliente alojado**, Adobe trabajará con usted para actualizar sus instancias a la versión más reciente y crear el proyecto en Adobe Developer Console.

Como **cliente on-premise/híbrido**, debe actualizar a [Campaign v7.2.2](../../rn/using/latest-release.md#release-7-2-2) (o más) para beneficiarse del nuevo servidor de entrega. Una vez que todas las instancias se hayan actualizado, debe [implementar la nueva integración](#implementation-steps) en el servidor de envío de Adobe y garantizar una transición sin problemas.

## Pasos de implementación {#implementation-steps}

>[!WARNING]
>
>Estos pasos solo deben llevarse a cabo para implementaciones híbridas y locales.

Como parte de la nueva integración del servidor de entrega, Campaign debe comunicarse con Adobe Shared Services a través de una autenticación basada en Identity Management Service (IMS). La forma preferida es utilizar el token de puerta de enlace basado en Adobe Developer (también llamado token de cuenta técnica o JWT de E/S de Adobe).

>[!AVAILABILITY]
>
> Adobe va a declarar la credencial Cuenta de servicio (JWT) como obsoleta, las integraciones de Campaign con aplicaciones y soluciones de Adobe ahora dependen de la credencial OAuth de servidor a servidor. </br>
>
> * Si ha implementado integraciones de entrada con Campaign, debe migrar su Cuenta técnica como se detalla en [esta documentación](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#_blank). Las [credenciales de la cuenta de servicio (JWT) existentes](../../integrations/using/oauth-technical-account.md) seguirán funcionando hasta el 27 de enero de 2025. </br>
>
> * Si ha implementado integraciones de salida, como la integración de Campaign-Analytics o los activadores de Experience Cloud, seguirán funcionando hasta el 27 de enero de 2025. Sin embargo, antes de esa fecha, deberá actualizar el entorno de Campaign a la versión 7.4.1 y migrar la Cuenta técnica a OAuth.

### Requisitos previos{#prerequisites}

Antes de iniciar la implementación, compruebe la configuración de la instancia.

1. Abra la consola del cliente de Campaign e inicie sesión en Adobe Campaign como administrador.
1. Vaya a **Administración > Plataforma > Opciones**.
1. Compruebe que el valor de la opción `DmRendering_cuid` esté rellenado.

   * Si la opción está rellenada, puede iniciar la implementación.
   * Si no se rellena ningún valor, póngase en contacto con el [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank} para obtener su CUID.

   Esta opción debe rellenarse en todas las instancias de Campaign (MKT, MID, RT, EXEC) con el valor correcto. Como cliente híbrido, póngase en contacto con Adobe para que establezca la opción en las instancias MID, RT y EXEC.

Como cliente On-Premise, también debe comprobar que haya una campaña **[!UICONTROL Product profile]** disponible para su organización. Para realizar esto, siga los pasos a continuación:

1. Como administrador, conéctese a [Adobe Admin Console](https://adminconsole.adobe.com/){_blank}.
1. Acceda a la sección **Productos y servicios** y verifique que **Adobe Campaign** aparezca en la lista.
Si no puede ver **Adobe Campaign**, comuníquese con el Servicio de atención al cliente de [Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank} para que se lo agreguen.
1. Haga clic en **Adobe Campaign** y seleccione su organización.
   **Precaución**: Si tiene más de una organización, asegúrese de seleccionar la correcta. Obtenga más información acerca de las organizaciones [en esta página](https://experienceleague.adobe.com/docs/control-panel/using/faq.html?lang=es#ims-org-id){_blank}.

1. Compruebe que existe un **[!UICONTROL Product profile]**. Si no es así, créela. No se requiere permiso para este **[!UICONTROL Product profile]**.


>[!CAUTION]
>
>Como cliente On-Premise, si hay un firewall implementado de su parte, debe agregar esta dirección URL `https://deliverability-service.adobe.io` a su lista de permitidos. [Más información](../../installation/using/url-permissions.md).


### Paso 1: Crear/actualizar su proyecto de Adobe Developer {#adobe-io-project}

Para proseguir con la configuración del conector de Adobe Analytics, acceda a Adobe Developer Console y cree su proyecto de servidor a servidor OAuth.

Consulte [esta página](../../integrations/using/oauth-technical-account.md#oauth-service) para ver la documentación detallada.

### Paso 2: Adición de las credenciales del proyecto en Adobe Campaign {#add-credentials-campaign}

Siga los pasos detallados en [esta página](../../integrations/using/oauth-technical-account.md#add-credentials) para añadir las credenciales del proyecto OAuth en Adobe Campaign.

### Paso 3: Validar la configuración

Para comprobar que la integración se ha realizado correctamente, siga los pasos a continuación:

1. Abra la consola del cliente e inicie sesión en Adobe Campaign.
1. Vaya a **Administración > Producción > Flujos de trabajo técnicos**.
1. Reinicie el flujo de trabajo **Actualizar la entrega** (deliverabilityUpdate). Esto debe realizarse en todas las instancias de Campaign (MKT, MID, RT, EXEC). Como cliente híbrido, póngase en contacto con el Adobe de para que se reinicie el flujo de trabajo en las instancias MID, RT y EXEC.
1. Comprobar registros: el flujo de trabajo se debe ejecutar sin errores.

>[!CAUTION]
>
>Después de la actualización, se debe detener el flujo de trabajo **Actualizar la red semilla para la renderización de la bandeja de entrada (updateRenderingSeeds)**, ya que dejará de aplicarse y fallará.

## Preguntas frecuentes {#faq}

### ¿Cuál es la cronología de la actualización?

La transición al nuevo servidor de capacidad de entrega, que permite añadir estas funciones mejoradas y reforzar la seguridad, comenzará el 22 de julio para los clientes alojados (Campaign Managed Services). Todos los clientes alojados se actualizarán a finales de agosto.

Los clientes locales e híbridos deben realizar la transición durante el mismo periodo de tiempo.

### ¿Qué sucede si no actualizo mi entorno?

Cualquier instancia de Campaign que no se haya actualizado antes del 31 de agosto ya no podrá conectarse al servidor de entrega de Campaign. Como consecuencia, el flujo de trabajo **Actualizar la entrega** (deliverabilityUpdate) fallará y esto afectará su capacidad de entrega.

Si no actualiza su entorno, la configuración de correo electrónico dejará de sincronizarse (reglas de administración MX, reglas de correo electrónico entrante, reglas de administración de dominio y reglas de calificación de devoluciones). Esto podría afectar a la capacidad de envío con el tiempo. Si se realiza un cambio significativo en estas reglas, deberán aplicarse manualmente a partir de este punto.

En las instancias de MKT, solo se ve afectada la [lista de supresión global](../../campaign-opt/using/filtering-rules.md#default-deliverability-exclusion-rules).
