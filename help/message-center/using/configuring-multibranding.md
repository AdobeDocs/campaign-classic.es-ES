---
solution: Campaign Classic
product: campaign
title: Configuración de marcas múltiples
description: Configuración de marcas múltiples
audience: message-center
content-type: reference
topic-tags: instance-configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Configuración de marcas múltiples{#configuring-multibranding}

Esta sección describe una solución para configurar el seguimiento y las direcciones URL de las páginas espejo por marca para los mensajes transacciones en Adobe Campaign.

## Requisitos previos {#prerequisites}

* Todos los anfitriones deben añadirse al archivo de configuración de la instancia (`config-<instance>.xml`).
* A cada marca se le debe asignar un subdominio.
* Se debe tener un certificado HTTPS para todas las marcas si el seguimiento web se realiza en páginas HTTPS.

## Proceso típico {#typical-process}

Para configurar marcas múltiples, es necesario configurar las instancias de ejecución y la instancia de control. En las instancias de ejecución, siga los pasos a continuación:

1. Cree una cuenta externa por marca.

   >[!NOTE]
   >
   >La creación de una cuenta externa de tipo instancia de ejecución se detalla en la sección [Instancia de control](../../message-center/using/creating-a-shared-connection.md#control-instance).

1. Amplíe el esquema nms:extAccount para añadir la URL de seguimiento:

   ```
   <attribute advanced="true" desc="URL of the tracking servers" label="Tracking server URL"
   length="100" name="trackingURL" type="string"/>
   ```

   >[!NOTE]
   >
   >La ampliación de un esquema existente se presenta en la sección [Ampliación de un esquema](../../configuration/using/extending-a-schema.md).

1. Modifique el formulario nms:extAccount:

   ```
   <container label="Message domain branding" type="frame">
        <static type="help"> These parameters are used to override the DNS alias and addresses used during message delivery. When not populated, the values of the 'NmsServer_MirrorPageUrl' and 'NmsEmail_DefaultErrorAddr' options are used.</static>
        <input xpath="@mirrorURL"/>
        <input xpath="@trackingURL"/>
        <input img="nms:sendemail.png" menuId="deliveryMenuBuilder" type="scriptEdit">
               xpath="errorAddress"/>
      </container>
   ```

1. Modifique las opciones NmsTracking_OpenFormula y NmsTracking_ClickFormula para utilizar la cuenta externa en lugar de una opción global.

   Para ello, sustituya:

   ```
   <%@ include option='NmsTracking_ServerUrl' %>
   ```

   con:

   ```
   <%@ value object="provider" xpath="@trackingURL" %>
   ```

   >[!IMPORTANT]
   >
   >Estos cambios podrían provocar conflictos al realizar la actualización. Es posible que deba combinar manualmente estas fórmulas con su nueva versión.

En la instancia de control, se deben vincular las plantillas de envío y las cuentas externas. Para ello, debe:

1. Crear una cuenta externa por marca con el mismo nombre interno que se define en el paso 1.
1. Crear una plantilla de envío predeterminada por cada marca.
1. En **[!UICONTROL Properties]** de la plantilla de envío, configure el enrutamiento en la cuenta externa de la marca.

