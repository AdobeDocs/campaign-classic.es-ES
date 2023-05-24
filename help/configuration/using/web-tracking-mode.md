---
product: campaign
title: Modo de seguimiento web
description: Obtenga información sobre cómo seleccionar el modo de seguimiento web
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: b0f30c1f-cdc9-4ad2-8a6c-19d5aae4feb3
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '681'
ht-degree: 1%

---

# Modo de seguimiento web{#web-tracking-mode}



Adobe Campaign permite seleccionar un modo de seguimiento web que define la forma en que se procesan los registros de seguimiento en la aplicación.

Hay tres modos de seguimiento web disponibles: **&quot;Seguimiento de sesión&quot;**,**&quot;Seguimiento permanente&quot;** y **&quot;Seguimiento anónimo&quot;**.

![](assets/s_ncs_install_deployment_wiz_tracking_mode.png)

Cada modo tiene características específicas. El modo de seguimiento web &quot;permanente&quot; incluye las características del modo de seguimiento web &quot;sesión&quot;, mientras que el modo &quot;anónimo&quot; incluye las características de los modos &quot;permanente&quot; y &quot;sesión&quot;.

>[!IMPORTANT]
>
>El modo de seguimiento web &quot;anónimo&quot; está habilitado de forma predeterminada si el paquete &quot;Posibles clientes&quot; está habilitado. En todos los demás casos, el modo de seguimiento web de &quot;sesión&quot; está habilitado de forma predeterminada.
>
>El modo predeterminado se puede cambiar en cualquier momento en el asistente de implementación de instancias.

Tenga en cuenta que si utiliza la variable **web permanente** o **anónimo** en el modo de seguimiento, debe añadir un índice a la columna &quot;sourceID&quot; (uuid230) en las tablas de seguimiento (trackingLogXXX):

1. Identifique la(s) tabla(s) de seguimiento relacionada con el seguimiento permanente.
1. Amplíe los esquemas que coinciden con estas tablas agregando las siguientes líneas:

```
<dbindex name="sourceId">
 <keyfield xpath="@sourceId"/>
</dbindex>
```

**Permanente** y **Anónimo** Los modos de seguimiento web incluyen dos opciones: **Envío forzado** y **Última entrega**.

El **Envío forzado** Esta opción permite especificar el identificador de la entrega (@jobid) durante el seguimiento.

El **Última entrega** Esta opción permite vincular el registro de seguimiento actual al último envío rastreado.

**Características del seguimiento web de sesión:**

Este modo crea un registro de seguimiento para las personas con una cookie de sesión. Son personas que hicieron clic en una dirección URL de un correo electrónico enviado por Adobe Campaign, lo que nos permite realizar un seguimiento de la siguiente información:

* ID de envío
* ID de contacto
* registro de envío
* cookie permanente (uuid230)
* URL de seguimiento
* fecha del registro de seguimiento

Con este modo de seguimiento web, si falta parte de la información, no se creará ningún registro de seguimiento en la aplicación.

Este modo es económico en términos de volumen (número limitado de registros en la tabla trackingLog) y cálculo (sin reconciliación).

**Características del modo de seguimiento web permanente:**

Este modo de seguimiento web permite crear un registro de seguimiento basado en la presencia de la cookie uuid230 permanente. Si un visitante cierra su sesión, Adobe Campaign utiliza la cookie permanente para recuperar información sobre él de los registros de seguimiento anteriores. Adobe Campaign vuelve a insertar un registro de seguimiento si el uuid230 de la sesión actual tiene el mismo valor que un uuid230 ya almacenado en la tabla de seguimiento.

Esto significa que el visitante debe haberse identificado previamente en Adobe Campaign (a través de una entrega) para habilitar la reconciliación en los valores uuid230.

De forma predeterminada, las búsquedas en registros de seguimiento anteriores se realizan en la tabla &quot;trackingLog&quot;. Si el paquete de posibles clientes está habilitado, antes de buscar en la tabla &quot;trackingLog&quot;, Adobe Campaign busca en la tabla &quot;incomingLead&quot; registros de registro de seguimiento anteriores.

Este modo es costoso en términos de cálculo durante la reconciliación de registros.

**Características del modo de seguimiento web anónimo:**

Este modo de seguimiento web permite recuperar un registro de seguimiento vinculado a la exploración anónima en Adobe Campaign. Se crea automáticamente un registro de seguimiento para cada clic en una dirección URL rastreada. Este registro solo tiene el valor de uuid230. Durante una campaña de marketing, se crea automáticamente un registro de seguimiento con toda la información de identificación (consulte Seguimiento de sesiones). Adobe Campaign buscará automáticamente en los registros anteriores un valor &quot;uuid230&quot; igual al valor del registro de seguimiento de esta campaña de marketing. Si se encuentran valores idénticos, se introducen todos los registros de seguimiento anteriores con toda la información del registro de seguimiento de la campaña de marketing.

Este modo es el más costoso en términos de cálculo y volumen.

>[!NOTE]
>
>Si la variable **[!UICONTROL Leads]** está instalado, debe hacer lo mismo con la tabla de actividades (**crm:incomingLead**)

El siguiente esquema resume las funcionalidades de los tres modos de seguimiento web:

![](assets/s_ncs_install_deployment_wiz_tracking_schema_mode.png)

**Ejemplo de seguimiento web permanente basado en el último envío:**

Florence recibe una entrega, abre el correo electrónico, hace clic en el vínculo y navega por el sitio de venta al por menor, pero no realiza ninguna compra. Al día siguiente, Florence vuelve al sitio de venta al por menor, navega y realiza una compra. Dado que el seguimiento web permanente (último envío) está habilitado, todos los registros de su segunda visita se vincularán al envío que se le envió el día anterior.
