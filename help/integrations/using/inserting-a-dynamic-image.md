---
product: campaign
title: Inserción de una imagen dinámica
description: Inserción de una imagen dinámica
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: 6177f57b-534c-4d86-8f73-d96980c48a77
source-git-commit: b6e24c63ece12f25b7dafe3fede9e38b3aab2427
workflow-type: tm+mt
source-wordcount: '825'
ht-degree: 100%

---

# Adición de contenido dinámico de Target {#inserting-a-dynamic-image}

![](../../assets/common.svg)

En esta página, se muestra cómo integrar una oferta dinámica de Adobe Target en un correo electrónico en Adobe Campaign.

El objetivo es crear una entrega con un bloque de imagen que cambie dinámicamente según el país del destinatario: los datos se envían con cada solicitud de mbox y dependen de la dirección IP del destinatario.

En este mensaje, las imágenes pueden variar dinámicamente según las siguientes experiencias del usuario:

* El correo electrónico se abre en Francia.
* El correo electrónico se abre en Estados Unidos.
* Si no se aplica ninguna de estas condiciones, se muestra una imagen predeterminada.

![](assets/target_4.png)

Para ello, siga los siguientes pasos:

1. [Inserción de la oferta dinámica en un correo electrónico](../../integrations/using/inserting-a-dynamic-image.md#inserting-dynamic-offer)
1. [Creación de ofertas de redireccionamiento](../../integrations/using/inserting-a-dynamic-image.md#create-redirect-offers)
1. [Creación de audiencias](../../integrations/using/inserting-a-dynamic-image.md#audiences-target)
1. [Creación de una actividad de segmentación de experiencias ](../../integrations/using/inserting-a-dynamic-image.md#creating-targeting-activity)
1. [Vista previa y envío del correo electrónico](../../integrations/using/inserting-a-dynamic-image.md#preview-send-email)

## Inserción de la oferta dinámica en un correo electrónico {#inserting-dynamic-offer}

En Adobe Campaign, cuando haya terminado de definir el destino y el contenido de su correo electrónico, puede insertar una imagen dinámica desde Target.

Para ello, especifique la URL de la imagen predeterminada, el nombre de la ubicación y los campos que desee transferir al destino.

En Adobe Campaign, hay dos formas de insertar una imagen dinámica desde Target en un mensaje de correo electrónico:

* Si utiliza el editor de contenido digital, elija una imagen existente y seleccione **[!UICONTROL Insert]** > **[!UICONTROL Dynamic image served by Adobe Target]** en la barra de herramientas.

   ![](assets/target_5.png)

* Si está utilizando el editor estándar, coloque el cursor donde desee insertar la imagen y, en el menú desplegable de personalización, seleccione **[!UICONTROL Include]** > **[!UICONTROL Dynamic image served by Adobe Target...]**.

   ![](assets/target_12.png)

### Definición de los parámetros de la imagen {#defining-image-parameters}

* La URL de **[!UICONTROL Default image]**: Esta es la imagen que se muestra cuando no se cumple ninguna de las condiciones. También puede seleccionar una imagen de su biblioteca de activos.
* **[!UICONTROL Target location]**: Introduzca un nombre para la ubicación de su oferta dinámica. Debe seleccionar esta ubicación en la actividad de Target.
* **[!UICONTROL Landing Page]**: Si desea que la imagen predeterminada se redirija a una página de aterrizaje predeterminada. Esta URL es opcional y solo para aquellos casos en que la imagen predeterminada se muestra en el mensaje de correo electrónico final.
* **[!UICONTROL Additional decision parameters]**: especifique la asignación entre los campos definidos en los segmentos de Adobe Target y los campos de Adobe Campaign. Los campos de Adobe Campaign utilizados deben haberse especificado en el “rawbox”. En el ejemplo, añadimos el campo País.

Si utiliza permisos de empresa en la configuración de Adobe Target, añada la propiedad correspondiente en este campo. Obtenga más información sobre los permisos de empresa de Target en [esta página](https://experienceleague.adobe.com/docs/target/using/administer/manage-users/enterprise/properties-overview.html?lang=es).

![](assets/target_13.png)

## Creación de ofertas de redireccionamiento {#create-redirect-offers}

En Target puede crear distintas versiones de la oferta. Según cada experiencia de usuario, se puede crear una oferta de redireccionamiento y puede especificar la imagen que desee mostrar.

En este caso, necesitamos dos ofertas de redirección, la tercera (la predeterminada) se define en Adobe Campaign.

1. Para crear una nueva oferta de redirección en Target Standard, en la pestaña **[!UICONTROL Content]**, haga clic en **[!UICONTROL Code offers]**.

1. Haga clic en **[!UICONTROL Create]**, luego en **[!UICONTROL Redirect Offer]**.

   ![](assets/target_9.png)

1. Introduzca un nombre para la oferta y la URL de su imagen.

   ![](assets/target_6.png)

1. Siga el mismo procedimiento para la oferta de redirección restante. Para obtener más información, consulte [esta página](https://experienceleague.adobe.com/docs/target/using/experiences/offers/offer-redirect.html?lang=es).

## Creación de audiencias {#audiences-target}

En Target, debe crear las dos audiencias en las que se clasifican las personas que visitan la oferta para enviarles los diferentes contenidos. Para cada audiencia, añada una regla para definir quién puede ver la oferta.

1. Para crear una nueva audiencia en Target, en la pestaña **[!UICONTROL Audiences]**, haga clic en **[!UICONTROL Create Audience]**.

   ![](assets/audiences_1.png)

1. Añada un nombre a su audiencia.

   ![](assets/audiences_2.png)

1. Haga clic en **[!UICONTROL Add a rule]** y seleccione una categoría. La regla utiliza criterios específicos para dirigirse a los visitantes. Puede restringir las reglas añadiendo condiciones o creando nuevas reglas en otras categorías.

1. Siga el mismo procedimiento para las audiencias restantes.

## Creación de una actividad de segmentación de experiencias  {#creating-targeting-activity}

En Target, es necesario crear una actividad de segmentación de experiencias, definir las diferentes experiencias y asociarlas a las ofertas correspondientes.

### Definición de la audiencia {#defining-the-audience}

1. Para crear una actividad de segmentación de experiencias, en la pestaña **[!UICONTROL Activities]**, haga clic en **[!UICONTROL Create Activity]** y, a continuación, en **[!UICONTROL Experience Targeting]**.

   ![](assets/target_10.png)

1. Seleccione **[!UICONTROL Form]** como **[!UICONTROL Experience Composer]**.

1. Haga clic en el botón **[!UICONTROL Change audience]** para elegir una audiencia.

   ![](assets/target_10_2.png)

1. Seleccione la audiencia que se creó en los pasos anteriores.

   ![](assets/target_10_3.png)

1. Para crear otra experiencia, haga clic en **[!UICONTROL Add Experience Targeting]**.

### Definición de la ubicación y el contenido {#defining-location-content}

Añada un contenido para cada audiencia:

1. Seleccione el nombre de la ubicación que eligió al insertar la oferta dinámica en Adobe Campaign.

   ![](assets/target_15.png)

1. Haga clic en el botón desplegable y seleccione **[!UICONTROL Change Redirect Offer]**.

   ![](assets/target_content.png)

1. Seleccione la oferta de redirección que había creado anteriormente.

   ![](assets/target_content_2.png)

1. Siga el mismo procedimiento para la segunda experiencia.

### Definición de la actividad {#defining-activity}

La ventana de **[!UICONTROL Target]** resume la actividad. Si es necesario, puede añadir otras experiencias.

![](assets/target_experience.png)

La ventana de **[!UICONTROL Goal & Settings]** permite personalizar la actividad estableciendo una prioridad, un objetivo o una duración.

La sección **[!UICONTROL Reporting Settings]** permite seleccionar una acción y editar los parámetros que determinan cuándo se logra el objetivo.

![](assets/target_experience_2.png)

## Vista previa y envío del correo electrónico {#preview-send-email}

En Adobe Campaign, ahora puede previsualizar el correo electrónico y probar su renderizado en distintos destinatarios. Observe que la imagen cambia según las diferentes experiencias creadas. Para obtener más información sobre la creación de correos electrónicos, consulte esta [página](../../delivery/using/defining-the-email-content.md).

Ya está listo para enviar su correo electrónico, incluida una oferta dinámica de Target.

![](assets/target_20.png)
