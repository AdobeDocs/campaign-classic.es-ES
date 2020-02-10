---
title: Modo de seguimiento web
seo-title: Modo de seguimiento web
description: Modo de seguimiento web
seo-description: null
page-status-flag: never-activated
uuid: 51b889d3-28f8-480a-a614-10c8eb3128ac
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: efeef54b-925d-4654-8601-52a73539b41f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 912507f25c5bc3c1ca7121b0df8182176900f4c0

---


# Modo de seguimiento web{#web-tracking-mode}

Adobe Campaign permite seleccionar un modo de seguimiento web que define la forma en que se procesan los registros de seguimiento en la aplicación.

Existen tres modos de seguimiento Web disponibles: **&quot;Seguimiento de sesión&quot;**,**&quot;Seguimiento permanente&quot;** y **&quot;Seguimiento anónimo&quot;**.

![](assets/s_ncs_install_deployment_wiz_tracking_mode.png)

Cada modo tiene características específicas. El modo de seguimiento web &quot;permanente&quot; incluye las características del modo de seguimiento web &quot;sesión&quot;, mientras que el modo &quot;anónimo&quot; incluye las características de los modos &quot;permanente&quot; y &quot;sesión&quot;.

>[!CAUTION]
>
>El modo de seguimiento web &quot;anónimo&quot; está habilitado de forma predeterminada si el paquete &quot;Posibles clientes&quot; está habilitado. En todos los demás casos, el modo de seguimiento web &quot;sesión&quot; está habilitado de forma predeterminada.
>
>En cualquier momento, el modo predeterminado se puede cambiar en el asistente de implementación de instancias.

Tenga en cuenta que si utiliza el modo de seguimiento web **** permanente o **anónimo** , debe agregar un índice a la columna &quot;sourceID&quot; (uuid230) en las tablas de seguimiento (trackingLogXXX):

1. Identifique las tablas de seguimiento afectadas por el seguimiento permanente.
1. Amplíe los esquemas que coinciden con estas tablas agregando las siguientes líneas:

```
<dbindex name="sourceId">
 <keyfield xpath="@sourceId"/>
</dbindex>
```

**Los modos de seguimiento web permanente** y **anónimo** incluyen dos opciones: Entrega **** forzada y **Última entrega**.

La opción **Entrega** forzada permite especificar el identificador de la entrega (@jobid) durante el seguimiento.

La opción **Última entrega** permite vincular el registro de seguimiento actual al último envío rastreado.

**Características del seguimiento Web de sesiones:**

Este modo crea un registro de seguimiento para las personas con una cookie de sesión. Son personas que hicieron clic en una URL en un mensaje de correo electrónico enviado por Adobe Campaign, lo que nos permite rastrear la siguiente información:

* ID de envío
* ID de contacto
* registro de entrega
* cookie permanente (uuid230)
* URL de seguimiento
* fecha del registro de seguimiento

Con este modo de seguimiento Web, si falta parte de la información, no se creará ningún registro de seguimiento en la aplicación.

Este modo es económico en términos de volumen (número limitado de registros en la tabla trackingLog) y cálculo (sin reconciliación).

**Características del modo de seguimiento web permanente:**

Este modo de seguimiento Web permite crear un registro de seguimiento basado en la presencia de la cookie uuid230 permanente. Si un visitante cierra la sesión, Adobe Campaign utiliza la cookie permanente para recuperar información de los registros de seguimiento anteriores. Adobe Campaign vuelve a insertar un registro de seguimiento si uuid230 de la sesión actual tiene el mismo valor que uuid230 ya almacenado en la tabla de seguimiento.

Esto significa que el visitante debe haberse identificado previamente en Adobe Campaign (mediante una entrega) para habilitar la reconciliación en los valores uuid230.

De forma predeterminada, las búsquedas en los registros de seguimiento anteriores se realizan en la tabla &quot;trackingLog&quot;. Si el paquete Posibles clientes está habilitado, antes de buscar en la tabla &quot;trackingLog&quot;, Adobe Campaign buscará en la tabla &quot;entrantePosible cliente&quot; los registros de registro de seguimiento anteriores.

Este modo es costoso en términos de cálculo durante la reconciliación de registros.

**Características del modo de seguimiento Web anónimo:**

Este modo de seguimiento web permite recuperar un registro de seguimiento vinculado a la navegación anónima en Adobe Campaign. Se crea automáticamente un registro de seguimiento para cada clic en una dirección URL rastreada. Este registro solo tiene el valor de uuid230. Durante una campaña de marketing, se crea automáticamente un registro de seguimiento con toda la información de identificación (consulte el seguimiento de sesión). Adobe Campaign buscará automáticamente en los registros anteriores un valor &quot;uuid230&quot; igual al valor del registro de seguimiento de esta campaña de marketing. Si se encuentran valores idénticos, todos los registros de seguimiento anteriores se introducen con toda la información del registro de seguimiento de campaña de mercadotecnia.

Este modo es el más costoso en términos de cálculo y volumen.

>[!NOTE]
>
>Si el **[!UICONTROL Leads]** paquete está instalado, debe hacer lo mismo con la tabla de actividades (**crm:entranteLead**)

El siguiente esquema resume las funcionalidades de los tres modos de seguimiento Web:

![](assets/s_ncs_install_deployment_wiz_tracking_schema_mode.png)

**Ejemplo de seguimiento web permanente basado en la última entrega:**

Florence recibe un envío, abre el correo electrónico, hace clic en el vínculo, navega por el sitio de venta minorista pero no realiza ninguna compra. Al día siguiente, Florence regresa al sitio de venta minorista, navega y realiza una compra. Dado que el seguimiento web permanente (último envío) está habilitado, todos los registros de su segunda visita estarán vinculados a la entrega que se le envió el día anterior.
