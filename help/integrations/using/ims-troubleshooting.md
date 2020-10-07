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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 95%

---


# Solución de problemas de IMS{#ims-troubleshooting}

Las siguientes sugerencias para la solución de problemas ayudarán a los clientes **locales** a resolver los problemas más comunes que se producen al utilizar la integración con IMS. Para clientes **alojados**, póngase en contacto con Adobe.

**Cuenta externa**

Solo debe haber **una** cuenta externa con la siguiente configuración:

* **Nombre interno**: Adobe_Marketing_Cloud
* **Tipo**: Adobe Marketing Cloud

Elimine cualquier cuenta externa duplicada que tenga la misma configuración.

**Contexto del producto**

Si la cuenta externa tiene un campo **Product Context**, compruebe que su valor esté configurado como: **dma_campaign_classic**

Asegúrese de que el contexto del producto sea el mismo para Campaign y Experience Cloud.

Por ejemplo, si el **contexto del producto** no aparece, el contexto predeterminado del producto debe ser **dma_campaign** en Campaign y Experience Cloud. Si aparece el campo de **Contexto del producto**, el contexto predeterminado del producto debe ser **dma_campaign_classic** en Campaign y en Experience Cloud.

**[!UICONTROL IMS Server URL]**

En la cuenta externa de **Adobe Marketing Cloud** de Campaign, asegúrese de que **[!UICONTROL IMS Server URL]** sea [adobeid-na1.services.adobe.com](https://adobeid-na1.services.adobe.com/) o [ims-na1.adobelogin.com](http://ims-na1.adobelogin.com/). Asegúrese de que las instancias de ensayo y de producción indiquen el mismo punto final de producción IMS.

**Máscara de asociación**

* Compruebe que el usuario que intenta iniciar sesión forme parte de un grupo de operadores en Enterprise Dashboard.
* Compruebe que **[!UICONTROL Association Mask]** sea un prefijo del nombre del grupo de operadores del usuario en Enterprise Dashboard.
* Compruebe que no haya espacios en blanco ni errores ortográficos.
* Compruebe que los nombres de los grupos de operadores en Campaign no hayan cambiado y respete la siguiente sintaxis:

```
<Association Mask> + <Operator Group Name in Campaign> = Complete name of the operator group in Enterprise Dashboard
```

**Ámbito**

Los ámbitos definidos en la cuenta externa de Campaign deben ser un subconjunto de los que proporciona IMS.

**URL de devolución de llamada**

La dirección URL **de** llamada de retorno debe agregarse a la lista de permitidos y al inicio con &quot;https://&quot;. Compruebe que la **URL de devolución de llamada** esté vinculada a la instancia correspondiente. Por ejemplo, la instancia de producción debe redirigir a la URL de producción.

**ID de cliente y secreto**

La ID del cliente coincide con la cuenta externa de Campaign y la suministrada por IMS.

Compruebe que el secreto del cliente introducido sea correcto.

**Reinicio del servidor**

Reinicie el servidor si se realizan cambios en la configuración anterior en la cuenta externa de la campaña.

**Tipos de errores comunes y posibles soluciones**

* Se redirige al usuario a la página de adobe.com:

   There is a problem with the **[!UICONTROL Callback URL]**. Consulte los pasos anteriores para comprobar la configuración de **[!UICONTROL Callback URL]**.

* Mensaje “Ningún derecho del inicio de sesión se corresponde con la expresión”:

   Consulte los pasos anteriores para comprobar las configuraciones de **[!UICONTROL Association Mask]** y de los grupos de operadores.

* El usuario no puede acceder a la página de inicio de sesión de Adobe ID:

   Consulte los pasos anteriores para comprobar la configuración del ámbito.

