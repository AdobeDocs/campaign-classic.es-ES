---
title: Realización de la computación agregada
description: Aprenda a realizar computación agregada en consultas.
page-status-flag: never-activated
uuid: 0556d53e-0fdf-47b3-b1e0-b52e85e0c662
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 7e5605c8-78f2-4011-b317-96a59c699848
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '225'
ht-degree: 100%

---


# Realización de la computación agregada {#performing-aggregate-computing}

En este ejemplo, se desea contar el número de destinatarios que residen en Londres, según el sexo.

* ¿Qué tabla se debe seleccionar?

   La tabla de destinatario (**nms:recipient**).

* ¿Qué campos se deben seleccionar en la columna de salida?

   Clave principal (con recuento) y Género.

* ¿En qué condiciones se basa la información?

   Se basa en los destinatarios que residen en Londres.

Para crear este ejemplo, aplique los pasos siguientes:

1. En **[!UICONTROL Data to extract]**, defina un recuento para la clave principal (como se muestra en el ejemplo anterior). Añada el campo **[!UICONTROL Gender]** en la columna de salida. Marque la opción **[!UICONTROL Group]** en la columna **[!UICONTROL Gender]**. De este modo, los destinatarios se agrupan por género.

   ![](assets/query_editor_nveau_27.png)

1. En la ventana **[!UICONTROL Sorting]**, haga clic en **[!UICONTROL Next]**: no es necesario realizar una ordenación aquí.
1. Configure el filtrado de datos. En este caso, se desea restringir la selección a contactos que residen en Londres.

   ![](assets/query_editor_22.png)

   >[!NOTE]
   >
   >Los valores distinguen entre mayúsculas y minúsculas. Si el valor “Londres” se introduce en la condición sin inicial mayúscula y la lista de destinatarios contiene la palabra “Londres” con una inicial mayúscula, la consulta falla.

1. En la ventana **[!UICONTROL Data formatting]**, haga clic en **[!UICONTROL Next]**: no se requiere formato para este ejemplo.
1. En la ventana de vista previa, haga clic en **[!UICONTROL Launch data preview]**.

   Existen tres valores distintos para cada clasificación por sexo: **2** para las mujeres, **1** para los hombres y **0** cuando se desconoce el sexo. En este ejemplo, la lista contiene 10 mujeres, 16 hombres y 2 personas cuyo sexo no se conoce.

   ![](assets/query_editor_agregat_04.png)
