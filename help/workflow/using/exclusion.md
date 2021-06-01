---
product: campaign
title: Exclusión
description: Descubra más información sobre la actividad del flujo de trabajo Exclusión
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: f4fe97d9-6571-4aa5-8022-b0af9d5a6a13
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 100%

---

# Exclusión{#exclusion}

Una actividad de tipo **exclusión** permite crear un objetivo basado en un objetivo principal del que se extraen uno o más objetivos.

Para configurar esta actividad, introduzca su etiqueta y seleccione el grupo de destinatarios principal: la población del conjunto principal le permite construir el resultado. Se excluirán los perfiles compartidos por el conjunto principal y al menos una de las actividades de entrada.

![](assets/s_user_segmentation_exclu.png)

>[!NOTE]
>
>Para obtener más información sobre la configuración y el uso de la actividad de exclusión, consulte [Exclusión de una población (Exclusión)](../../workflow/using/targeting-data.md#excluding-a-population--exclusion-).

Seleccione la opción **[!UICONTROL Generate complement]** si desea utilizar la población restante. El complemento contendrá la población entrante principal menos la población saliente. A continuación, se agregará una transición de salida adicional a la actividad de la siguiente manera:

![](assets/s_user_segmentation_exclu_compl.png)

## Ejemplos de exclusión {#exclusion-examples}

En el ejemplo siguiente, se busca compilar una lista de destinatarios que tengan entre 18 y 30 años, al tiempo que se excluyen los residentes de París.

1. Inserte y abra una actividad de tipo **[!UICONTROL Exclusion]** que siga dos consultas. La primera consulta se dirige a los destinatarios que viven en París. La segunda consulta se aplica a los objetivos que tengan entre 18 a 30 años.
1. Introduzca el conjunto principal. En este caso, el conjunto principal es la consulta de **18-30 años de edad.** Los elementos pertenecientes al segundo conjunto se excluirán del resultado final.
1. Marque la opción **[!UICONTROL Generate complement]** si desea explotar los datos que quedan después de la exclusión. En este caso, el complemento está compuesto por destinatarios de entre 18 y 30 años que viven en París.
1. Apruebe la configuración de exclusión y, a continuación, inserte una actividad de lista de actualización en el resultado. También puede insertar una actualización de lista adicional al complemento donde sea necesario.
1. Ejecución de un flujo de trabajo. En este ejemplo, el resultado está compuesto por destinatarios de entre 18 y 30 años, pero los que viven en París se excluyen y envían al complemento.

   ![](assets/exclusion_example.png)

## Parámetros de entrada {#input-parameters}

* tableName
* esquema

Cada evento entrante debe especificar un objetivo definido por estos parámetros.

## Parámetros de salida {#output-parameters}

* tableName
* esquema
* recCount

Este conjunto de tres valores identifica el destino resultante de la exclusión. **[!UICONTROL tableName]** es el nombre de la tabla que registra los identificadores de destinatario, **[!UICONTROL schema]** es el esquema de la población (normalmente nms:recipient) y **[!UICONTROL recCount]** es el número de elementos de la tabla.

La transición asociada al complemento tiene los mismos parámetros.
