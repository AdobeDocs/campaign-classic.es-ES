---
title: Solución de problemas de IMS
seo-title: Solución de problemas de IMS
description: Solución de problemas de IMS
seo-description: null
page-status-flag: never-activated
uuid: 5db95afc-8cbf-4ec3-b58f-504486fe4a40
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
discoiquuid: e31db11a-ad8e-4fd0-bab7-0df1079231c9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Solución de problemas de IMS{#ims-troubleshooting}

Las siguientes sugerencias para la solución de problemas ayudarán a los clientes **locales** a resolver los problemas más comunes que se producen al utilizar la integración con IMS. Para clientes **alojados**, póngase en contacto con Adobe.

**Cuenta externa**

Solo debe haber **una** cuenta externa con la siguiente configuración:

* **Nombre** interno: Adobe_Marketing_Cloud
* **Tipo**: Adobe Marketing Cloud

Elimine cualquier cuenta externa duplicada que tenga la misma configuración.

**Contexto del producto**

If the external account has a **Product Context** field, check that its value is set to: **dma_campaign_classic**

Asegúrese de que el contexto del producto sea el mismo para Campaign y Experience Cloud.

Por ejemplo, si el **contexto del producto** no aparece, el contexto predeterminado del producto debe ser **dma_campaign** en Campaign y Experience Cloud. Si aparece el campo de **Contexto del producto**, el contexto predeterminado del producto debe ser **dma_campaign_classic** en Campaign y en Experience Cloud.

**[!UICONTROL IMS Server URL]**

In the Campaign **Adobe Marketing Cloud** external account, check that the **[!UICONTROL IMS Server URL]** is either [adobeid-na1.services.adobe.com](https://adobeid-na1.services.adobe.com/) or [ims-na1.adobelogin.com](http://ims-na1.adobelogin.com/). Asegúrese de que las instancias de ensayo y de producción indiquen el mismo punto final de producción IMS.

**Máscara de asociación**

* Compruebe que el usuario que intenta iniciar sesión forme parte de un grupo de operadores en Enterprise Dashboard.
* Check that the **[!UICONTROL Association Mask]** is a prefix of the user&#39;s operator group name in the Enterprise Dashboard.
* Compruebe que no haya espacios en blanco ni errores ortográficos.
* Compruebe que los nombres de los grupos de operadores en Campaign no hayan cambiado y respete la siguiente sintaxis:

```
<Association Mask> + <Operator Group Name in Campaign> = Complete name of the operator group in Enterprise Dashboard
```

**Ámbito**

Los ámbitos definidos en la cuenta externa de Campaign deben ser un subconjunto de los que proporciona IMS.

**URL de devolución de llamada**

La **URL de devolución de llamada** debe incluirse en la lista blanca y comenzar con “https://”. Compruebe que la **URL de devolución de llamada** esté vinculada a la instancia correspondiente. Por ejemplo, la instancia de producción debe redirigir a la URL de producción.

**ID de cliente y secreto**

La ID del cliente coincide con la cuenta externa de Campaign y la suministrada por IMS.

Compruebe que el secreto del cliente introducido sea correcto.

**Reinicio del servidor**

Reinicie el servidor si se realizan cambios en la configuración anterior en la cuenta externa de la campaña.

**Tipos de errores comunes y posibles soluciones**

* Se redirige al usuario a la página de adobe.com:

   There is a problem with the **[!UICONTROL Callback URL]**. Refer to the previous steps to check the **[!UICONTROL Callback URL]** configuration.

* Mensaje “Ningún derecho del inicio de sesión se corresponde con la expresión”:

   Refer to the previous steps to check the **[!UICONTROL Association Mask]** and operator groups configuration.

* El usuario no puede acceder a la página de inicio de sesión de Adobe ID:

   Consulte los pasos anteriores para comprobar la configuración del ámbito.

