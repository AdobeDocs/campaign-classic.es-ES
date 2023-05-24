---
product: campaign
title: Actualización del nuevo servidor de envío
description: Obtenga información sobre cómo actualizar al nuevo servidor de envío de Campaign
exl-id: bc62ddb9-beff-4861-91ab-dcd0fa1ed199
source-git-commit: 50ef144950ca9e79b1b3acdf587ffc13e0beeec4
workflow-type: tm+mt
source-wordcount: '1319'
ht-degree: 20%

---

# Actualización del nuevo servidor de envío {#acc-deliverability}

Inicio [Versión v7.2.2](../../rn/using/latest-release.md#release-7-2-2), Adobe Campaign se basa en un nuevo servidor de capacidad de entrega que ofrece alta disponibilidad y aborda los problemas de cumplimiento de la seguridad. Campaign Classic ahora sincroniza las reglas de envío, los broadlogs y la dirección de supresión desde y hacia el nuevo servidor de envío. El antiguo servidor de capacidad de entrega se desactivará el 31 de agosto de 2022.

Como cliente Campaign Classic, debe implementar el nuevo servidor de capacidad de entrega **antes del 31 de agosto de 2022**.

>[!NOTE]
>
>Para obtener más información sobre estos cambios, consulte la [FAQ](#faq), o contacto [Adobe del Servicio de atención al cliente](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank}.

## ¿Qué ha cambiado?{#acc-deliverability-changes}

El Adobe está retirando los centros de datos más antiguos por motivos de cumplimiento de la seguridad. Los clientes de Adobe Campaign Classic deben migrar al nuevo servicio de capacidad de entrega, alojado en Amazon Web Service (AWS).

Este nuevo servidor garantiza una alta disponibilidad (99.9)&#x200B; y proporciona puntos de conexión seguros y autenticados para permitir que los servidores de campaña recuperen los datos necesarios: en lugar de conectarse a la base de datos para cada solicitud, el nuevo servidor de capacidad de entrega almacena en caché los datos para servir las solicitudes siempre que sea posible. Este mecanismo mejora el tiempo de respuesta&#x200B;

## ¿Se ha visto afectado?{#acc-deliverability-impacts}

Todos los clientes se ven afectados y deben actualizar a [Campaign v7.2.2](../../rn/using/latest-release.md#release-7-2-2) (o más) e implemente su entorno para beneficiarse del nuevo servidor de capacidad de entrega.

## ¿Cómo realizar la actualización?{#acc-deliverability-update}

As a **cliente alojado**, el Adobe colaborará con usted para actualizar las instancias a la versión más reciente y crear el proyecto en la consola de Adobe Developer.

Como un **cliente on-premise/híbrido**, debe actualizar a [Campaign v7.2.2](../../rn/using/latest-release.md#release-7-2-2) (o más) para beneficiarse del nuevo servidor de capacidad de entrega. Una vez que todas las instancias se hayan actualizado, debe [implementación de la nueva integración](#implementation-steps) al servidor de envío de Adobe y garantizar una transición sin problemas.

## Pasos de implementación {#implementation-steps}

Como parte de la nueva integración del servidor de entrega, Campaign debe comunicarse con Adobe Shared Services a través de una autenticación basada en Identity Management Service (IMS). La forma preferida es utilizar el token de puerta de enlace basado en Adobe Developer (también llamado token de cuenta técnica o JWT de E/S de Adobe).

>[!WARNING]
>
>Estos pasos solo deben llevarse a cabo para implementaciones híbridas y locales.

### Requisitos previos{#prerequisites}

Antes de iniciar la implementación, compruebe la configuración de la instancia.

1. Abra la consola del cliente de Campaign e inicie sesión en Adobe Campaign como administrador.
1. Navegar a **Administración > Plataforma > Opciones**.
1. Compruebe que la variable `DmRendering_cuid` el valor de opción está rellenado.

   * Si la opción está rellenada, puede iniciar la implementación.
   * Si no se rellena ningún valor, póngase en contacto con [Adobe del Servicio de atención al cliente](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank} para obtener su CUID.

   Esta opción debe rellenarse en todas las instancias de Campaign (MKT, MID, RT, EXEC) con el valor correcto. Como cliente híbrido, póngase en contacto con Adobe para que establezca la opción en las instancias MID, RT y EXEC.

Como cliente On-Premise, también debe comprobar que una **[!UICONTROL Product profile]** está disponible para su organización de. Para ello, siga los pasos a continuación:

1. Como administrador, conéctese a [Adobe Admin Console](https://adminconsole.adobe.com/){_blank}.
1. Acceda a la **Productos y servicios** y marque **Adobe Campaign** aparece en la lista.
Si no puede ver **Adobe Campaign** contacto [Adobe del Servicio de atención al cliente](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank} para que se añada.
1. Clic **Adobe Campaign** y seleccione su Organización.
   **Precaución**: Si tiene más de una organización, asegúrese de seleccionar la correcta. Más información sobre las Organizaciones [en esta página](https://experienceleague.adobe.com/docs/control-panel/using/faq.html#ims-org-id){_blank}.

1. Compruebe que una **[!UICONTROL Product profile]** existe. Si no es así, créela. No se requiere permiso para este **[!UICONTROL Product profile]**.


>[!CAUTION]
>
>Como cliente On-Premise, si hay un cortafuegos implementado de su parte, debe añadir esta URL `https://deliverability-service.adobe.io` a su lista de permitidos. [Más información](../../installation/using/url-permissions.md).


### Paso 1: Crear/actualizar su proyecto de Adobe Developer {#adobe-io-project}

1. Acceso [Consola de Adobe Developer](https://developer.adobe.com/console/home) e inicie sesión con el acceso de desarrollador de su organización. Asegúrese de haber iniciado sesión en el portal correcto de la organización.
   **Precaución**: Si tiene más de una organización, asegúrese de seleccionar la correcta. Más información sobre las Organizaciones [en esta página](https://experienceleague.adobe.com/docs/control-panel/using/faq.html#ims-org-id){_blank}.
1. Seleccione **[!UICONTROL Create new project]**.
   ![](assets/New-Project.png)

   >[!CAUTION]
   >
   >Si ya está utilizando la funcionalidad de autenticación JWT de E/S de Adobe para otra integración, como el conector de Analytics o las Déclencheur de Adobe, debe actualizar el proyecto añadiendo **API de Campaign** a ese proyecto.

1. Elija **[!UICONTROL Add API]**.
   ![](assets/Add-API.png)
1. En la ventana **[!UICONTROL Add an API]** seleccione **[!UICONTROL Adobe Campaign]**.
   ![](assets/AC-API.png)
1. Si el ID del cliente está vacío, seleccione **[!UICONTROL Generate a key pair]** para crear un par de claves pública y privada.
   ![](assets/Generate-a-key-pair.png)

   Las claves se descargan automáticamente con una fecha de caducidad predeterminada de 365 días. Una vez caducado, deberá crear un nuevo par de claves y actualizar la integración en el archivo de configuración. Con la Opción 2, puede elegir crear y cargar manualmente su **[!UICONTROL Public key]** con una fecha de caducidad más larga.
   ![](assets/New-key-pair.png)

   >[!CAUTION]
   >
   >Debe guardar la variable `config.zip` cuando aparezca el mensaje de descarga, ya que no podrá volver a descargarlo.

1. Haga clic en **[!UICONTROL Next]**.
1. Elija cualquier **[!UICONTROL Product profile]** existente o cree uno nuevo si es necesario. No se requiere permiso para este **[!UICONTROL Product profile]**. Para obtener más información sobre **[!UICONTROL Product Profiles]**, consulte [esta página](https://helpx.adobe.com/es/enterprise/using/manage-developers.html){_blank}.
   ![](assets/Product-Profile-API.png)

   A continuación, haga clic en **[!UICONTROL Save configured API]**.

1. En el proyecto, seleccione **[!UICONTROL Adobe Campaign]** y copie la siguiente información en **[!UICONTROL Service Account (JWT)]**

   ![](assets/Config-API.png)

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

>[!CAUTION]
>
>El certificado de Adobe Developer caducará pasados 12 meses. Debe generar un nuevo par de claves cada año.

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

   ```sql
   nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
   ```

1. Debe detener y reiniciar el servidor para que se tenga en cuenta la modificación. También puede ejecutar una `config -reload` comando.

### Paso 3: Habilitar el nuevo servidor de envío

Ahora puede habilitar el nuevo servidor de envío. Para realizar esto:

1. Abra la consola del cliente e inicie sesión en Adobe Campaign como administrador.
1. Navegar a **Administración > Plataforma > Opciones**.
1. Acceda a la `NewDeliverabilityServer_FeatureFlag` y establezca el valor en `1`. Esta configuración debe realizarse en todas las instancias de Campaign (MKT, MID, RT, EXEC). Como cliente híbrido, póngase en contacto con Adobe para que establezca la opción en las instancias MID, RT y EXEC.

### Paso 4: Validar la configuración

Para comprobar que la integración se ha realizado correctamente, siga los pasos a continuación:

1. Abra la consola del cliente e inicie sesión en Adobe Campaign.
1. Navegar a **Administration > Production > Technical workflows**.
1. Reinicie el **Actualizar la entrega** Flujo de trabajo (deliverabilityUpdate). Esto debe realizarse en todas las instancias de Campaign (MKT, MID, RT, EXEC). Como cliente híbrido, póngase en contacto con el Adobe de para que se reinicie el flujo de trabajo en las instancias MID, RT y EXEC.
1. Comprobar registros: el flujo de trabajo se debe ejecutar sin errores.

>[!CAUTION]
>
>Después de la actualización, la variable **Actualizar la red semilla para la renderización de la bandeja de entrada (updateRenderingSeeds)** el flujo de trabajo debe detenerse, ya que ya no se aplicará y fallará.

## Preguntas frecuentes {#faq}

### ¿Cuál es la cronología de la actualización?

La transición al nuevo servidor de capacidad de entrega, que permite añadir estas funciones mejoradas y reforzar la seguridad, comenzará el 22 de julio para los clientes alojados (Campaign Managed Services). Todos los clientes alojados se actualizarán a finales de agosto.

Los clientes locales e híbridos deben realizar la transición durante el mismo periodo de tiempo.

### ¿Qué sucede si no actualizo mi entorno?

Cualquier instancia de Campaign que no se haya actualizado antes del 31 de agosto ya no podrá conectarse al servidor de entrega de Campaign. Como consecuencia, la variable **Actualizar la entrega** (deliverabilityUpdate) El flujo de trabajo fallará, y esto afectará a su capacidad de entrega.

Si no actualiza su entorno, la configuración de correo electrónico dejará de sincronizarse (reglas de administración MX, reglas de correo electrónico entrante, reglas de administración de dominio y reglas de calificación de devoluciones). Esto podría afectar a la capacidad de envío con el tiempo. Si se realiza un cambio significativo en estas reglas, deberán aplicarse manualmente a partir de este punto.

Solo para instancias de MKT [Lista global de supresión](../../campaign-opt/using/filtering-rules.md#default-deliverability-exclusion-rules) se ve afectado.
