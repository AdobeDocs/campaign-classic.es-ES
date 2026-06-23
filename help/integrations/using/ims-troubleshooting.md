---
product: campaign
title: Solución de problemas de IMS
description: Solución de problemas de IMS
feature: Configuration
badge-v7-prem: label="On-premise/híbrido solo" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 1ce89c3a-1fe6-4ed6-9547-2eb9713a0ec3
TQID: https://experienceleague.adobe.com/cUoMAlp8ExhammApiilFqRyrOkyyqxk1om0AifZVxb0
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
  - id: df0d6518-6f49-46e2-b46e-3bcc513f553f
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 501
ht-degree: 100%

---

# Solución de problemas de IMS{#ims-troubleshooting}


Las siguientes sugerencias para la solución de problemas ayudarán a los clientes **locales** e **híbridos** a resolver los problemas más comunes que se producen al utilizar la integración con IMS. Para clientes **alojados**, póngase en contacto con Adobe.

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

En la cuenta externa de **Adobe Marketing Cloud** de Campaign, asegúrese de que **[!UICONTROL IMS Server URL]** sea `adobeid-na1.services.adobe.com` o `ims-na1.adobelogin.com`. Asegúrese de que las instancias de ensayo y de producción indiquen el mismo punto final de producción IMS.

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

La **URL de devolución de llamada** debe agregarse a la lista de permitidos y al inicio con &quot;https://&quot;. Compruebe que la **URL de devolución de llamada** esté vinculada a la instancia correspondiente. Por ejemplo, la instancia de producción debe redirigir a la URL de producción.

**ID de cliente y secreto**

La ID del cliente coincide con la cuenta externa de Campaign y la suministrada por IMS.

Compruebe que el secreto del cliente introducido sea correcto.

**Reinicio del servidor**

Reinicie el servidor si se realizan cambios en la configuración anterior en la cuenta externa de la campaña.

**Tipos de errores comunes y posibles soluciones**

* Se redirige al usuario a la página de adobe.com:

  Hay algún problema con **[!UICONTROL Callback URL]**. Consulte los pasos anteriores para comprobar la configuración de **[!UICONTROL Callback URL]**.

* Mensaje “Ningún derecho del inicio de sesión se corresponde con la expresión”:

  Consulte los pasos anteriores para comprobar las configuraciones de **[!UICONTROL Association Mask]** y de los grupos de operadores.

* El usuario no puede acceder a la página de inicio de sesión de Adobe ID:

  Consulte los pasos anteriores para comprobar la configuración del ámbito.

**Problemas de caché de WebView2**

Si tiene problemas al iniciar sesión en **[!UICONTROL Client Console]** con su Adobe ID, intente borrar la caché local de WebView2. En la mayoría de los casos, esto resuelve el problema. Siga estos pasos:

1. Cierre la **[!UICONTROL Client Console]** y detenga cualquier proceso `nlclient` en ejecución.

1. Elimine todas las carpetas `webview2` y `webview2Cache` de las siguientes ubicaciones:

   * `C:\ProgramData\Neolane\NL_5\nlclient\`
   * `C:\Users\<username>\AppData\Roaming\Neolane\NL_5\nlclient\`

1. Reinicie la **[!UICONTROL Client Console]** e inicie sesión con su Adobe ID. Las carpetas de caché se volverán a crear automáticamente la próxima vez que reinicie la aplicación.
