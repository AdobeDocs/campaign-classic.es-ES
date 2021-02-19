---
solution: Campaign Classic
product: campaign
title: Inserción de un código de barras en un correo electrónico
description: Inserción de un código de barras en un correo electrónico
audience: delivery
content-type: reference
topic-tags: sending-emails
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 100%

---


# Inserción de un código de barras en un correo electrónico{#inserting-a-barcode-in-an-email}

El módulo de generación de códigos de barras permite crear varios tipos de códigos de barras que cumplan con muchos estándares habituales, incluidos códigos de barras 2D.

Es posible generar dinámicamente un código de barras como mapa de bits que utilice un valor definido con criterios de cliente. Se pueden incluir códigos de barras personalizados en las campañas de correo electrónico. El destinatario puede imprimir el mensaje y mostrarlo a la empresa emisora para escanearlo (por ejemplo, durante la comprobación).

Para insertar un código de barras en un correo electrónico, coloque el cursor en el contenido en el que desea mostrarlo y, a continuación, haga clic en el botón de personalización. Seleccione **[!UICONTROL Include > Barcode...]**.

![](assets/barcode_insert_14.png)

A continuación, configure los siguientes elementos para adaptarlos a sus necesidades:

1. Seleccione el tipo de código de barras.

   * Para el formato 1D, los siguientes tipos están disponibles en Adobe Campaign: Codabar, Code 128, GS1-128 (anteriormente EAN-128), UPC-A, UPC-E, ISBN, EAN-8, Code39, Interleaved 2 de 5, POSTNET y Royal Mail (RM4SCC).

      Ejemplo de código de barras 1D:

      ![](assets/barcode_insert_08.png)

   * Los tipos DataMatrix y PDF417 están relacionados con el formato 2D.

      Ejemplo de código de barras 2D:

      ![](assets/barcode_insert_09.png)

   * Para insertar un código QR, seleccione este tipo e introduzca la tasa de corrección de errores que desee aplicar. Esta velocidad define la cantidad de información repetida y la tolerancia ante el deterioro.

      ![](assets/barcode_insert_06.png)

      Ejemplo de código QR:

      ![](assets/barcode_insert_12.png)

1. Introduzca el tamaño del código de barras que desea insertar en el correo electrónico: la configuración de la escala permite aumentar o reducir el tamaño del código de barras, de x1 a x10.
1. El campo **[!UICONTROL Value]** permite definir el valor del código de barras. Un valor puede coincidir con una oferta especial y puede ser la función de un criterio, puede ser el valor de un campo de base de datos vinculado a los clientes.

   Este ejemplo muestra un código de barras de tipo EAN-8 al que se ha añadido el número de cuenta de un destinatario. Para ello, haga clic en el botón de personalización a la derecha del campo **[!UICONTROL Value]** y seleccione **[!UICONTROL Recipient > Account number]**:

   ![](assets/barcode_insert_15.png)

1. El campo **[!UICONTROL Height]** permite configurar la altura del código de barras sin cambiar su anchura, modificando la cantidad de espacio entre cada barra.

   No hay ningún control de entrada restrictivo en función del tipo de código de barras. Si un valor de código de barras es incorrecto, solo se puede ver en el modo de **Preview** donde el código de barras aparece tachado en rojo.

   >[!NOTE]
   >
   >El valor asignado a un código de barras depende de su tipo. Por ejemplo, un tipo EAN-8 debe tener exactamente 8 números.
   >
   >El botón de personalización situado a la derecha del campo **[!UICONTROL Value]** permite añadir datos además del propio valor. Esto enriquece el código de barras, siempre que el estándar de código de barras lo acepte.
   >
   >Por ejemplo, si está utilizando un código de barras de tipo GS1-128 y desea introducir el número de cuenta de un destinatario además del valor, haga clic en el botón de personalización y seleccione **[!UICONTROL Recipient > Account number]**. Si el número de cuenta del destinatario seleccionado se introduce correctamente, el código de barras lo tiene en cuenta.

Una vez configurados estos elementos, puede finalizar su el correo electrónico y enviarlo. Para evitar errores, asegúrese siempre de que el contenido se muestra correctamente antes de realizar una entrega haciendo clic en la pestaña **[!UICONTROL Preview]**.

![](assets/barcode_insert_10.png)

>[!NOTE]
>
>Si el valor de un código de barras es incorrecto, su mapa de bits se muestra tachado en rojo.

![](assets/barcode_insert_11.png)
