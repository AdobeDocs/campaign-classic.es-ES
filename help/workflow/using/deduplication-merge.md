---
title: Uso de la funcionalidad Combinar de la actividad de anulación de duplicación
description: Aprenda a utilizar la funcionalidad Combinar de la actividad de anulación de duplicación
page-status-flag: never-activated
uuid: 8887574e-447b-48a5-afc6-95783ffa7fb3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 4113c3fe-a279-4fe1-be89-ea43c96edc34
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 32a14eb99847dc04a582623204bc856c29fa4359
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 100%

---


# Uso de la funcionalidad Combinar de la actividad de anulación de duplicación {#deduplication-merge}

## Acerca de este caso de uso {#about-this-use-case}

Este caso de uso describe cómo utilizar la funcionalidad **[!UICONTROL Merge]** en la actividad **[!UICONTROL Deduplication]**.

Para obtener más información sobre esta funcionalidad, consulte [esta sección](../../workflow/using/deduplication.md#merging-fields-into-single-record).

La actividad **[!UICONTROL Deduplication]** se utiliza para eliminar filas de duplicado de un conjunto de datos. En este caso de uso, los datos que se muestran a continuación se duplican en función del campo Correo electrónico.

| Fecha de la última modificación | Nombre | Apellidos | Correo electrónico | Teléfono móvil | Teléfono |
|-----|------------|-----------|-------|--------------|------|
| 19/5/2020 | Robert | Tisner | bob@mycompany.com | 444-444-444 | 777-777-7777 |
| 22/7/2020 | Bobby | Tisner | bob@mycompany.com |  | 777-777-7777 |
| 3/10/2020 | Bob |  | bob@mycompany.com |  | 888-888-8888 |

Con la funcionalidad **[!UICONTROL Merge]** de la actividad de anulación de duplicación, puede configurar un conjunto de reglas para la anulación de duplicación para definir un grupo de campos para combinar en un único registro de datos resultante. Por ejemplo, con un conjunto de registros de duplicado, puede elegir mantener el número de teléfono más antiguo o el nombre más reciente.

## Activación de la funcionalidad Merge {#activating-merge}


Para habilitar la funcionalidad de combinación, primero debe configurar la actividad **[!UICONTROL Deduplication]**. Para ello, siga estos pasos:

1. Abra la actividad y haga clic en el vínculo **[Editar configuración]**.

1. Seleccione el campo de reconciliación que desee utilizar para la anulación de duplicación y haga clic en **[!UICONTROL Next]**. En este ejemplo, queremos anular la duplicación en función del campo de correo electrónico.

   ![](assets/uc_merge_edit.png)

1. Haga clic en el vínculo **[!UICONTROL Advanced parameters]** y active las opciones **[!UICONTROL Merge records]** y **[!UICONTROL Use several record merging criteria]**.

   ![](assets/uc_merge_advanced_parameters.png)

1. La pestaña **[!UICONTROL Merge]** se agrega a la pantalla de configuración **[!UICONTROL Deduplication]**. Utilizaremos esta pestaña para especificar los datos que se combinarán al realizar la anulación de duplicación.

## Configuración de los campos para combinar {#configuring-rules}

Estas son las reglas que queremos utilizar para combinar los datos en un único registro:

* Mantener el nombre más reciente (campos de nombre y apellido),
* Mantener el teléfono móvil más reciente,
* Mantener el número de teléfono más antiguo,
* Todos los campos de un grupo no deben ser nulos para poder acceder al registro final.

Para configurar estas reglas, siga estos pasos:

1. Abra la pestaña **[!UICONTROL Merge]** y, a continuación, haga clic en el botón **[!UICONTROL Add]**.

   ![](assets/uc_merge_add.png)

1. Especifique el identificador y la etiqueta del grupo de campos que se van a combinar.

   ![](assets/uc_merge_identifier.png)

1. Indique las condiciones para seleccionar los registros que deben tenerse en cuenta.

   ![](assets/uc_merge_filter.png)

1. Se ordenan en la fecha de la última modificación para seleccionar el nombre más reciente.

   ![](assets/uc_merge_sort.png)

1. Seleccione los campos que desea combinar. En este ejemplo, queremos mantener los campos de nombre y apellido.

   ![](assets/uc_merge_keep.png)

1. Los campos se agregan al conjunto de datos para combinar y se agrega un nuevo elemento al esquema de flujo de trabajo.

   Repita estos pasos para configurar los campos de teléfono y teléfono móvil.

   ![](assets/dedup8.png)

   ![](assets/dedup9.png)

## Resultados {#results}

Después de configurar estas reglas, se reciben los siguientes datos al final de la actividad **[!UICONTROL Deduplication]**.

| Fecha de modificación | Nombre | Apellidos | Correo electrónico | Teléfono móvil | Teléfono |
-----|------------|-----------|-------|--------------|------|
| 19/5/2020 | Robert | Tisner | bob@mycompany.com | 444-444-444 | 777-777-7777 |
| 22/7/2020 | Bobby | Tisner | bob@mycompany.com |  | 777-777-7777 |
| 3/10/2020 | Bob |  | bob@mycompany.com |  | 888-888-8888 |

El resultado se combina de los tres registros según las reglas configuradas anteriormente. Tras la comparación, se concluye que se utilizan el nombre y el teléfono móvil más recientes, junto con el número de teléfono original.

| Nombre | Apellidos | Correo electrónico | Teléfono móvil | Teléfono |
|------------|-----------|-------|--------------|------|
| Bobby | Tisner | bob@mycompany.com | 444-444-4444 | 888-888-8888 |

>[!NOTE]
>
> Tenga en cuenta que el nombre que se ha combinado es “Bobby”, ya que configuramos una regla de &quot;Nombre&quot; hecha de los campos de nombre y de apellido.
>
>Como resultado, “Bob” (el nombre más reciente) no se pudo tener en cuenta porque el campo de apellido asociado estaba vacío. La combinación más reciente de nombre y apellido se combinó en el registro final.
