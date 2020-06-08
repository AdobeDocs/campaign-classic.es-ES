---
title: Personalización de la lista de iconos gestuales
description: Aprenda a personalizar la lista de iconos gestuales al utilizar Adobe Campaign Classic.
page-status-flag: never-activated
uuid: ddcc2e3b-e251-4a7a-a22a-28701522839f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-emails
discoiquuid: 2ea2747f-957f-41a9-a03f-20c03fa99116
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3beb62d0264cfcb03486c291ce79cc7ff582e9c7
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 2%

---


# Personalización de la lista de iconos gestuales {#customize-emoticons}

La lista de iconos gestuales que se muestra en la ventana emergente se rige por una lista desglosada que permite mostrar valores en una lista para restringir las opciones que el usuario tiene para un campo determinado.
El orden de lista de iconos gestuales se puede personalizar y también se pueden agregar otros iconos gestuales a la lista.
Los emoticonos están disponibles para el correo electrónico y para más información, consulte esta [página](../../delivery/using/defining-the-email-content.md#inserting-emoticons).

## Añadir un nuevo icono gestual {#add-new-emoticon}

>[!CAUTION]
>
>La lista de iconos gestuales no puede mostrar más de 81 entradas.

1. Elija el nuevo icono gestual que desee agregar desde esta [página](https://unicode.org/emoji/charts/full-emoji-list.html). Tenga en cuenta que debe ser compatible con las distintas plataformas, como el explorador y el sistema operativo.

1. En el **[!UICONTROL Explorer]**, seleccione **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Enumerations]** y haga clic en la lista desglosada **[!UICONTROL Emoticon list]** lista para usar.

   >[!NOTE]
   >
   >Las listas desglosadas integradas solo pueden ser administradas por un administrador de la consola de Adobe Campaign Classic.

   ![](assets/emoticon_1.png)

1. Haga clic **[!UICONTROL Add]**.

1. Rellene los campos:

   * **[!UICONTROL U+]**:: Código del nuevo icono gestual. Puede encontrar la lista de los códigos de iconos gestuales en esta [página](https://unicode.org/emoji/charts/full-emoji-list.html).
Para evitar problemas de compatibilidad, le recomendamos que elija los iconos gestuales que se admiten en los navegadores y en todos los sistemas operativos.

   * **[!UICONTROL Label]**:: Etiqueta del nuevo icono gestual.
   ![](assets/emoticon_5.png)

1. Haga clic **[!UICONTROL Ok]** y luego **[!UICONTROL Save]** cuando finalice la configuración.
El nuevo icono gestual se colocará automáticamente en la tienda.

1. Para mostrarlo en la **[!UICONTROL Insert emoticon]** ventana de sus envíos, seleccione el icono gestual recién creado haciendo clic en él con el botón doble.

1. Elija en la **[!UICONTROL Display order]** lista desplegable en la que se mostrará el nuevo icono gestual. Tenga en cuenta que al seleccionar un orden de visualización ya asignado, el icono gestual existente se moverá automáticamente a la tienda.

   <br>En este ejemplo, elegimos el número de orden de visualización 61, lo que significa que si una entrada ya tenía este pedido, automáticamente se moverá a la tienda y nuestra nueva entrada ocupará su lugar en la lista de lista desglosada.

   ![](assets/emoticon_2.png)

1. El nuevo icono gestual se ha añadido a la lista desglosada **[!UICONTROL Insert emoticon list]** lista para usar. Puede cambiarlo **[!UICONTROL Display order]** en cualquier momento o moverlo a la tienda si ya no lo necesita.

1. Para que los cambios se tengan en cuenta, desconecte y vuelva a conectarse desde Adobe Campaign Classic. Si el nuevo icono gestual aún no aparece en la ventana **[!UICONTROL Insert emoticon]** emergente, es posible que tenga que borrar la caché. Para obtener más información, consulte [esta sección](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear).

1. El nuevo icono gestual ahora se encuentra en los envíos de la ventana **[!UICONTROL Insert emoticon]** emergente en la posición 61, tal como se configuró en los pasos anteriores. Para obtener más información sobre cómo utilizar los iconos gestuales en los envíos, consulte esta [página](../../delivery/using/defining-the-email-content.md#inserting-emoticons).

   ![](assets/emoticon_4.png)

1. Si los siguientes iconos gestuales aparecen en la ventana **[!UICONTROL Insert emoticon]** emergente, significa que no se han configurado correctamente. Compruebe si su **[!UICONTROL U+]** código o **[!UICONTROL Display order]** es correcto en la **[!UICONTROL Emoticon list]**.

   ![](assets/emoticon_6.png)
