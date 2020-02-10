---
title: Reglas de filtrado
seo-title: Reglas de filtrado
description: Reglas de filtrado
seo-description: null
page-status-flag: never-activated
uuid: 24238a99-1f0f-4d04-9807-557ec2a5ba16
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: 0d50826e-2211-4c3b-8413-ca1453bba6c4
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Reglas de filtrado{#filtering-rules}

Las reglas de filtrado permiten definir los mensajes que deben excluirse según los criterios definidos en una consulta. Estas reglas están vinculadas a una dimensión objetivo.

Las reglas de filtrado se pueden vincular a otros tipos de reglas (control, presión, etc.) en tipologías o agrupadas en una tipología dedicada de **filtrado.** Para obtener más información sobre esto, consulte [Creación y uso de una tipología](#creating-and-using-a-filtering-typology)de filtrado.

## Creación de una regla de filtrado {#creating-a-filtering-rule}

Por ejemplo, puede filtrar los suscriptores del boletín informativo para evitar que las comunicaciones se envíen a destinatarios menores de edad.

Para definir este filtro, aplique los siguientes pasos:

1. Create a **[!UICONTROL Filtering]** typology rule applicable to all communication channels.

   ![](assets/campaign_opt_create_filter_01.png)

1. Cambie la dimensión de objetivo predeterminada y seleccione las suscripciones (**nms:subscription**).

   ![](assets/campaign_opt_create_filter_02.png)

1. Cree el filtro mediante el **[!UICONTROL Edit the query from the targeting dimension...]** vínculo.

   ![](assets/campaign_opt_create_filter_03.png)

1. Vincule esta regla a una tipología de campaña y guárdela.

   ![](assets/campaign_opt_create_filter_04.png)

Cuando se utiliza esta regla en un envío, se excluye automáticamente a los suscriptores menores de edad. Un mensaje específico indica la aplicación de la regla:

![](assets/campaign_opt_create_filter_05.png)

## Condicionamiento de una regla de filtrado {#conditioning-a-filtering-rule}

Puede restringir el campo de aplicación de la regla de filtrado en función del envío relacionado o la descripción del envío.

To do this, go to the **[!UICONTROL General]** tab of the typology rule, select the type of restriction to apply and create the filter, as shown below:

![](assets/campaign_opt_create_filter_06.png)

En este caso, incluso si la regla está vinculada a todos los envíos, solo se aplica a los que coincidan con los del filtro definido.

>[!NOTE]
>
>Typologies and filtering rules can be used in a workflow, in the **[!UICONTROL Delivery outline]** activity. Para obtener más información, consulte [esta sección](../../workflow/using/delivery-outline.md).

## Creación y uso de una tipología de filtrado {#creating-and-using-a-filtering-typology}

You can create **[!UICONTROL Filtering]** typologies: they only contain filtering rules.

![](assets/campaign_opt_create_typo_filtering.png)

These specific typologies can be linked to a delivery when the target is selected: in the delivery wizard, click the **[!UICONTROL To]** link, then click the **[!UICONTROL Exclusions]** tab.

![](assets/campaign_opt_apply_typo_filtering.png)

A continuación, seleccione el filtro que se aplica al envío. To do this, click the **[!UICONTROL Add]** button and select the typologies to apply.

También puede vincular reglas de filtrado directamente mediante esta pestaña, sin que se agrupen en una tipología. Para ello, utilice la sección inferior de la ventana.

![](assets/campaign_opt_select_typo_filtering.png)

>[!NOTE]
>
>* En la ventana de selección solo están disponibles las reglas de filtrado y de tipologías.
>* Estas configuraciones se pueden definir en la plantilla de envío para que se apliquen automáticamente a todos los envíos nuevos creados con la plantilla.
>



## Reglas de exclusión de envío predeterminadas {#default-deliverability-exclusion-rules}

Two filtering rules are available by default: **[!UICONTROL Exclude addresses]** ( **[!UICONTROL addressExclusions]** ) and **[!UICONTROL Exclude domains]** ( **[!UICONTROL domainExclusions]** ). Durante el análisis del correo electrónico, estas reglas comparan las direcciones de correo de los destinatarios con las direcciones o nombres de dominio prohibidos incluidos en una lista de supresión global encriptada que se administra en la instancia de envío. Si se encuentra una coincidencia, el mensaje no se envía a ese destinatario.

El objetivo de esto es evitar que se añada el servicio a una lista negra de actividad maliciosa, especialmente a través de Spamtrap. Por ejemplo, si se utiliza un Spamtrap para suscribirse a través de uno de sus formularios Web, se envía un mensaje de correo electrónico de confirmación automáticamente a ese Spamtrap y esto hace que añada su dirección automáticamente a la lista negra.

>[!NOTE]
>
>Las direcciones y los nombres de dominio contenidos en la lista de supresión global están ocultos. En los registros de análisis de envío solo se indica el número de destinatarios excluidos.

