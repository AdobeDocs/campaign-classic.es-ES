---
solution: Campaign Classic
product: campaign
title: Modo de seguimiento web
description: Modo de seguimiento web
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 1%

---


# Modo de seguimiento web{#web-tracking-mode}

Adobe Campaign permite seleccionar un modo de seguimiento web que define la forma en que se procesan los registros de seguimiento en la aplicación.

Hay tres modos de Seguimiento web disponibles: **&quot;Seguimiento de sesiones&quot;**,**&quot;Seguimiento permanente&quot;** y **&quot;Seguimiento anónimo&quot;**.

![](assets/s_ncs_install_deployment_wiz_tracking_mode.png)

Cada modo tiene características específicas. El modo de Seguimiento web &quot;permanente&quot; incluye las características del modo de Seguimiento web &quot;sesión&quot;, mientras que el modo &quot;anónimo&quot; incluye las características de los modos &quot;permanente&quot; y &quot;sesión&quot;.

>[!IMPORTANT]
>
>El modo de Seguimiento web &quot;anónimo&quot; está habilitado de forma predeterminada si el paquete &quot;Posibles clientes&quot; está habilitado. En todos los demás casos, el modo de Seguimiento web &quot;sesión&quot; está activado de forma predeterminada.
>
>En cualquier momento, el modo predeterminado se puede cambiar en el asistente de implementación de instancias.

Tenga en cuenta que si utiliza el modo de seguimiento **web permanente** o **anónimo**, debe agregar un índice a la columna &quot;sourceID&quot; (uuid230) en las tablas de seguimiento (trackingLogXXX):

1. Identifique las tablas de seguimiento afectadas por el seguimiento permanente.
1. Amplíe los esquemas que coinciden con estas tablas agregando las líneas siguientes:

```
<dbindex name="sourceId">
 <keyfield xpath="@sourceId"/>
</dbindex>
```

**Los modos de seguimiento** permanente y  **** AnonymousWeb incluyen dos opciones:  **Entrega forzada** y  **último envío**.

La opción **envío forzado** permite especificar el identificador del envío (@jobid) durante el seguimiento.

La opción **Último envío** permite vincular el registro de seguimiento actual al último envío rastreado.

**Características del Seguimiento web de la sesión:**

Este modo crea un registro de seguimiento para las personas con una cookie de sesión. Son personas que hicieron clic en una URL en un mensaje de correo electrónico enviado por Adobe Campaign, lo que nos permite rastrear la siguiente información:

* ID de envío
* ID de contacto
* Registro de envíos
* cookie permanente (uuid230)
* URL de seguimiento
* fecha del registro de seguimiento

Con este modo de Seguimiento web, si falta parte de la información, no se creará ningún registro de seguimiento en la aplicación.

Este modo es económico en términos de volumen (número limitado de registros en la tabla trackingLog) y cálculo (sin reconciliación).

**Características del modo de Seguimiento web permanente:**

Este modo de Seguimiento web le permite crear un registro de seguimiento basado en la presencia de la cookie uuid230 permanente. Si un visitante cierra la sesión, Adobe Campaign utiliza la cookie permanente para recuperar información de registros de seguimiento anteriores. Adobe Campaign vuelve a insertar un registro de seguimiento si uuid230 de la sesión actual tiene el mismo valor que uuid230 ya almacenado en la tabla de seguimiento.

Esto significa que el visitante debe haberse identificado previamente en Adobe Campaign (mediante un envío) para habilitar la reconciliación en los valores uuid230.

De forma predeterminada, las búsquedas en registros de seguimiento anteriores se realizan en la tabla &quot;trackingLog&quot;. Si el paquete Posibles clientes está habilitado, antes de buscar en la tabla &quot;trackingLog&quot;, Adobe Campaign buscará en la tabla &quot;entrantePosible cliente&quot; los registros de registro de seguimiento anteriores.

Este modo es costoso en términos de cálculo durante la reconciliación de registros.

**Características del modo de Seguimiento web anónimo:**

Este modo de Seguimiento web permite recuperar un registro de seguimiento vinculado a la navegación anónima en Adobe Campaign. Se crea automáticamente un registro de seguimiento por cada clic en una dirección URL rastreada. Este registro solo tiene el valor de uuid230. Durante una campaña de marketing, se crea automáticamente un registro de seguimiento con toda la información de identificación (consulte el seguimiento de sesiones). Adobe Campaign buscará automáticamente en los registros anteriores un valor &quot;uuid230&quot; igual al valor del registro de seguimiento de esta campaña de mercadotecnia. Si se encuentran valores idénticos, todos los registros de seguimiento anteriores se introducen con toda la información del registro de seguimiento de campañas de marketing.

Este modo es el más costoso en términos de cálculo y volumen.

>[!NOTE]
>
>Si el paquete **[!UICONTROL Leads]** está instalado, debe hacer lo mismo con la tabla de actividad (**crm:entranteLead**)

El siguiente esquema resume las funcionalidades de los tres modos de Seguimiento web:

![](assets/s_ncs_install_deployment_wiz_tracking_schema_mode.png)

**Ejemplo de seguimiento web permanente basado en el último envío:**

Florence recibe un envío, abre el correo electrónico, hace clic en el vínculo, navega por el sitio minorista pero no realiza ninguna compra. Al día siguiente, Florence regresa al sitio de venta minorista, navega y realiza una compra. Dado que el seguimiento web permanente (último envío) está habilitado, todos los registros de su segunda visita estarán vinculados al envío que le fue enviado el día anterior.
