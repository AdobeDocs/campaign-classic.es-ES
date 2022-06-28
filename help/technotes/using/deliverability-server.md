---
product: campaign
title: Migrar al nuevo servidor de entrega
description: Obtenga información sobre cómo implementar el servidor de entrega de Campaign
hide: true
hidefromtoc: true
source-git-commit: cd2fa2450f6e8389e9c47c412da8943a5c8bb7f3
workflow-type: tm+mt
source-wordcount: '908'
ht-degree: 32%

---

# Servidor de entrega de Campaign {#acc-deliverability}

A partir de la versión 21.1 de Campaign Classic v7, Adobe Campaign propone un nuevo servidor de capacidad de envío que ofrece alta disponibilidad y aborda los problemas de cumplimiento de normas de seguridad. Ahora, el Campaign Classic sincroniza las reglas de envío, los broadlogs y las direcciones de supresión desde y hacia el nuevo servidor de capacidad de envío.

Como cliente Campaign Classic, debe implementar el nuevo servidor de entrega

>[!NOTE]
>
>Para cualquier pregunta sobre estos cambios, lea la [Preguntas frecuentes](#faq-aa). Para obtener más información, póngase en contacto con [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## ¿Qué ha cambiado?{#acc-deliverability-changes}

El Adobe está retirando los centros de datos más antiguos por motivos de seguridad. Los clientes de Adobe Campaign Classic deben migrar al nuevo servicio de entrega, alojado en el servicio web de Amazon (AWS).

Este nuevo servidor garantiza una alta disponibilidad (99.9) &#x200B; y proporciona extremos seguros y autenticados para permitir que los servidores de campaña recuperen los datos necesarios: en lugar de conectarse a la base de datos para cada solicitud, el nuevo servidor de capacidad de envío almacena en caché los datos para atender las solicitudes siempre que sea posible. Este mecanismo mejora el tiempo de respuesta. &#x200B;


## ¿Se ha visto afectado?{#acc-deliverability-impacts}

Si utiliza el antiguo servidor de capacidad de envío de Adobe Campaign y el entorno se ha implementado en una versión inferior a Campaign 21.1.1, se verá afectado. Debe actualizar a Campaign 21.1 (o más).

Descubra cómo comprobar su versión [en esta sección](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## ¿Cómo realizar la actualización?{#acc-deliverability-update}

Como cliente alojado, el Adobe trabajará con usted para actualizar sus instancias a la versión más reciente.

Como cliente local/híbrido, debe actualizar a una de las versiones más recientes para beneficiarse del nuevo servidor de capacidad de envío .
Una vez que se actualicen todas las instancias, podrá [implementar la nueva integración](#implementation-steps) para almacenar en Adobe el servidor de capacidad de envío y garantizar una transición sin problemas.

## Pasos de implementación (clientes híbridos y locales) {#implementation-steps}

>[!IMPORTANT]
>
>Estos pasos solo deben realizarlos implementaciones híbridas y locales.
>
>Para implementaciones alojadas, póngase en contacto con [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

### Requisitos previos{#prerequisites}

Como parte de la nueva integración del servidor de capacidad de envío, Campaign debe comunicarse con Adobe Shared Services mediante una autenticación basada en Identity Management Service (IMS). La forma preferida es usar el Token de puerta de enlace basado en Adobe Developer (también llamado Token de cuenta técnica o Adobe IO JWT).

### Paso 1: Crear/actualizar el proyecto de Adobe Developer {#adobe-io-project}

1. Acceso [Consola de Adobe Developer](https://developer.adobe.com/console/home) e inicie sesión con el acceso de desarrollador de su organización.

   >[!NOTE]
   >
   > Asegúrese de haber iniciado sesión en el portal correcto de la organización.

1. Seleccione **[!UICONTROL + Add to Project]** y elija **[!UICONTROL API]**.
1. En la ventana **[!UICONTROL Add an API]** seleccione **[!UICONTROL Adobe Campaign]**.
1. Elija **[!UICONTROL Service Account (JWT)]** como el tipo de autenticación.
1. Si el ID del cliente está vacío, seleccione **[!UICONTROL Generate a key pair]** para crear un par de claves pública y privada.

   Las claves se descargan automáticamente con una fecha de caducidad predeterminada de 365 días. Una vez caducado, deberá crear un nuevo par de claves y actualizar la integración en el archivo de configuración. Con la Opción 2, puede elegir crear y cargar manualmente su **[!UICONTROL Public key]** con una fecha de caducidad más larga.

   >[!CAUTION]
   >
   >Debe guardar el archivo config.zip cuando aparezca el mensaje de descarga, ya que no podrá volver a descargarlo.

1. Haga clic en **[!UICONTROL Next]**.
1. Elija cualquier **[!UICONTROL Product profile]** existente o cree uno nuevo si es necesario. No se requiere permiso para este **[!UICONTROL Product profile]**. Para obtener más información, consulte [!DNL Analytics] **[!UICONTROL Product Profiles]**, consulte [este oage](https://helpx.adobe.com/es/enterprise/using/manage-developers.html).

   A continuación, haga clic en **[!UICONTROL Save configured API]**.

1. En el proyecto, seleccione **[!UICONTROL Adobe Campaign]** y copie la siguiente información en **[!UICONTROL Service Account (JWT)]**:

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

>[!CAUTION]
>
>El certificado de Adobe Developer caducará a los 12 meses. Debe generar un nuevo par de claves cada año.

### Paso 2: Adición de las credenciales del proyecto en Adobe Campaign {#add-credentials-campaign}

La clave privada debe codificarse en formato UTF-8 base64.

Para ello:

1. Utilice la clave privada generada en los pasos anteriores.
1. Codifique la clave privada mediante el siguiente comando: `base64 ./private.key > private.key.base64`. Esto guardará el contenido de base64 en un nuevo archivo `private.key.base64`.

   >[!NOTE]
   >
   >A veces, se pueden añadir automáticamente líneas adicionales al copiar/pegar la clave privada. Recuerde eliminarlas antes de codificar la clave privada.

1. Copie el contenido del archivo `private.key.base64`.
1. Inicie sesión mediante SSH en cada contenedor donde esté instalada la instancia de Adobe Campaign y añada las credenciales del proyecto en Adobe Campaign ejecutando el siguiente comando como usuario `neolane`. Esto insertará las credenciales **[!UICONTROL Technical Account]** en el archivo de configuración de instancia.

   ```
   nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
   ```

1. Debe detener y luego reiniciar el servidor para que se tenga en cuenta la modificación. También puede ejecutar un `config -reload` comando.

### Paso 3: Compruebe la configuración

Una vez que haya terminado la configuración, puede comprobar la configuración de la instancia. Siga estos pasos:

1. Abra la consola del cliente e inicie sesión en Adobe Campaign como administrador.
1. Vaya a **Administración > Plataforma > Opciones**.
1. Marque la `DmRendering_cuid` se rellena. Debe rellenarse en todas las instancias de Campaign (MKT, MID, RT, EXEC). Si no se rellena, debe rellenar el valor. Si no se rellena ningún valor, póngase en contacto con [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) para obtener su CUID.

### Paso 4: Habilitar el nuevo servidor de entrega

Ahora puede habilitar el nuevo servidor de capacidad de envío. Para realizar esto:

1. Abra la consola del cliente e inicie sesión en Adobe Campaign como administrador.
1. Vaya a **Administración > Plataforma > Opciones**.
1. Acceda a la `NewDeliverabilityServer_FeatureFlag` y establezca el valor en `1`. Esta configuración debe realizarse en todas las instancias de Campaign (MKT, MID, RT, EXEC).


### Paso 5: Validar la configuración

Para comprobar que la integración se ha realizado correctamente, siga los pasos a continuación:


1. Abra la consola del cliente e inicie sesión en Adobe Campaign.
1. Vaya a **Administración > Producción > Flujos de trabajo técnicos**.
1. Reinicie el **Actualización de la capacidad de entrega** Flujo de trabajo (deliverabilityUpdate). Esto debe realizarse en todas las instancias de Campaign (MKT, MID, RT, EXEC).
1. Registros de comprobación: el flujo de trabajo se debe ejecutar sin errores.

## Preguntas frecuentes{#faq-aa}

P: A:

P: A:



Para obtener más información, póngase en contacto con [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
