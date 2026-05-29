---
product: campaign
title: Cómo utilizar los datos de flujo de trabajo
description: Descubra cómo utilizar los datos de flujo de trabajo
feature: Workflows, Data Management
hide: true
exl-id: 5354d608-2fea-45f9-a0aa-11c7e965ab04
TQID: https://experienceleague.adobe.com/xasYSu6WyHC0T6CpKn51bZ5K7WlspJAbB0R45AeXb8M
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: e0eb8757-182f-49f3-94a4-1587d16f5094id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
feature_v2: []
subfeature_v2: id: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 410
ht-degree: 88%

---

# Cómo utilizar los datos de flujo de trabajo{#how-to-use-workflow-data}



## Actualización de la base de datos {#updating-the-database}

Todos los datos recopilados pueden utilizarse para actualizar la base de datos o en las entregas. Por ejemplo, puede enriquecer las posibilidades de personalización del contenido del mensaje (incluir el número de contratos en el mensaje, especificar el carro de compras promedio durante el último año, etc.) o indique la población objetivo (envíe un mensaje a los cotitulares del contrato, diríjase a los 1000 mejores suscriptores de los servicios en línea, etc.). Estos datos también se pueden exportar o archivar en una lista.

### Listas y actualizaciones directas {#lists-and-direct-updates}

Los datos de la base de datos de Adobe Campaign y de las listas existentes pueden actualizarse mediante dos actividades específicas:

* La actividad **[!UICONTROL List update]** permite almacenar tablas de trabajo en una lista de datos.

  Puede seleccionar una lista existente o crearla. En este caso, se calculan el nombre y, posiblemente, la carpeta de registros.

  ![](assets/s_user_create_list.png)

  Consulte [Actualización de listas](list-update.md).

* La actividad **[!UICONTROL Update data]** realiza una actualización en masa de los campos de la base de datos.

  Para obtener más información, consulte [Actualización de datos](update-data.md).

### Gestión de suscripciones y bajas {#subscription-unsubscription-management}

Para obtener información sobre las suscripciones y las bajas de un servicio informativo para los destinatarios a través de un flujo de trabajo, consulte [Servicios de suscripción](subscription-services.md).

## Envío a través de un flujo de trabajo {#sending-via-a-workflow}

### Actividad de envío {#delivery-activity}

La actividad de envío aparece detallada en [Envío](delivery.md).

### Enriquecimiento y establecimiento de objetivos de las entregas {#enriching-and-targeting-deliveries}

Los envíos pueden procesar datos de flujos de trabajo para personalizar el contenido o dentro del marco de selección de la población objetivo.

Por ejemplo, en el marco de una entrega de correo directo, puede incluir los datos adicionales, tomados de la manipulación de datos llevada a cabo en el flujo de trabajo, en el archivo de extracción:

![](assets/s_advuser_add_data_postal_mail.png)

Además de los campos de personalización habituales, puede añadir campos de personalización desde las fases del flujo de trabajo al contenido de la entrega. Los datos adicionales definidos en las actividades de flujo de trabajo se pueden conservar y se puede conceder acceso a ellos en el asistente de envíos, como se muestra en el ejemplo siguiente, para definir el nombre del archivo de salida dentro del marco de trabajo del envío de correo directo:

![](assets/s_advuser_using_additional_data.png)

Los datos contenidos en la tabla de flujo de trabajo se identifican con su nombre: siempre se compone del vínculo **targetData.** Para obtener más información, consulte [Datos de destinatario](data-life-cycle.md#target-data).

Dentro del marco de una entrega de correo electrónico, los campos de personalización también pueden utilizar datos de la extensión de grupo objetivo realizada en las fases del flujo de trabajo de objetivos, como se muestra en el ejemplo siguiente:

![](assets/s_advuser_add_data_email.png)

Si se especifica un código de segmento en una actividad de objetivo, se añade a una columna específica de la tabla de flujo de trabajo y se ofrece junto con los campos de personalización. Para mostrar todos los campos de personalización, haga clic en el enlace **[!UICONTROL Target extension > Other...]** al que se puede acceder con el botón de personalización.

![](assets/s_advuser_segment_code_select.png)
