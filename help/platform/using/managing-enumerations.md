---
title: Administración de enumeraciones
seo-title: Administración de enumeraciones
description: Administración de enumeraciones
seo-description: null
page-status-flag: never-activated
uuid: 23ad4cae-237f-48e5-b111-cfe88cf0b864
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: administration-basics
discoiquuid: 7674c856-2b64-4a85-9ffa-3e14a142028e
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '879'
ht-degree: 67%

---


# Administración de enumeraciones{#managing-enumerations}

## Acerca de las enumeraciones {#about-enumerations}

Una enumeración (también conocida como “lista desglosada”) es una lista de valores sugeridos por el sistema para llenar ciertos campos. Las enumeraciones permiten estandarizar los valores de estos campos y ayudar con la entrada o el uso de los datos en las consultas.

La lista de valores aparece como una lista desplegable desde la que puede seleccionar el valor que se va a introducir en el campo. La lista desplegable también permite la entrada predictiva, en la que el operador introduce las primeras letras y la aplicación rellena el resto.

Algunos de los campos de la consola se han definido con este tipo de enumeraciones. Las enumeraciones se denominan “abiertas” si se pueden agregar valores mediante entrada directa en el campo correspondiente.

## Acceso a valores {#access-to-values}

The values for this type of field are defined and overall administration of these fields (adding/deleting a value) is performed via the **[!UICONTROL Administration > Platform > Enumerations]** node of the tree.

![](assets/s_ncs_user_itemized_list_node.png)

* La sección superior ofrece una lista de campos para los que se ha definido una lista detallada.
* En la sección inferior se enumeran los valores propuestos. Estos valores se repiten en los editores que utilicen este campo.

   ![](assets/s_ncs_user_itemized_list_values.png)

   To create a new enumeration value, click **[!UICONTROL Add]**.

   ![](assets/s_ncs_user_itemized_list.png)

   If the **[!UICONTROL Open]** option is selected, the user can add a new itemized list value directly in the corresponding field. Un mensaje de confirmación le permite crear este valor.

   ![](assets/s_ncs_user_itemized_list_new_value.png)

* If the **[!UICONTROL Closed]** option is selected, users will not be able to create new values, but merely choose from the values available.

## Estandarización de datos {#standardizing-data}

### Acerca de la limpieza de alias {#about-alias-cleansing}

En los campos de lista desglosada se pueden introducir valores distintos a los valores de enumeración. Pueden almacenarse tal cual o se puede ejecutar una limpieza.

>[!CAUTION]
>
>La limpieza de datos es un proceso esencial que afecta a los datos de la base de datos. Adobe Campaign realiza actualizaciones de datos masivas que pueden dar lugar a la eliminación de algunos valores. Por lo tanto, esta operación queda reservada para usuarios expertos.

Por tanto, el valor introducido:

* Added to the itemized list values: in this case the **[!UICONTROL Open]** option must be selected,
* o sustituido automáticamente por su correspondiente: En este caso, este caso debe definirse en la ficha **[!UICONTROL Alias]** Alias de la lista de elementos.
* o se debe almacenar en la lista de alias: se le asigna un alias más adelante.

   >[!NOTE]
   >
   >If you need to use data cleansing capabilities, select the **[!UICONTROL Alias cleansing]** option in the itemized list.

### Uso de alias {#using-aliases}

The option **[!UICONTROL Alias cleansing]** makes it possible to use aliases for the selected itemized list. Cuando se selecciona esta opción, la pestaña **[!UICONTROL Alias]** aparece en la parte inferior de la ventana.

![](assets/s_ncs_user_itemized_list_alias_option.png)

#### Creación de un alias {#creating-an-alias}

To create an alias, click **[!UICONTROL Add]**.

![](assets/s_ncs_user_itemized_list_alias_create.png)

Introduzca el alias que desea convertir y el valor que se va a aplicar y haga clic en **[!UICONTROL Ok]**.

![](assets/s_ncs_user_itemized_list_alias_create_2.png)

Compruebe los parámetros antes de confirmar esta operación.

>[!CAUTION]
>
>Una vez confirmado este paso, es posible que los valores introducidos anteriormente no se puedan recuperar: se han sustituido.

![](assets/s_ncs_user_itemized_list_alias_create_3.png)

Por lo tanto, cuando un usuario introduce el valor **NEILSEN** en un campo “empresa” (en la consola de Adobe Campaign o en un formulario), este se sustituye automáticamente por el valor **NIELSEN Ltd**. El flujo de trabajo de **Limpieza de alias** lleva a cabo el reemplazo del valor. Consulte [Ejecución de la limpieza de datos](#running-data-cleansing).

![](assets/s_ncs_user_itemized_list_alias_use.png)

#### Conversión de valores en alias {#converting-values-into-aliases}

To convert an enumeration value into an alias, right-click in the list of values and choose **[!UICONTROL Convert values into aliases...]**.

![](assets/s_ncs_user_itemized_list_alias_detail.png)

Choose the values you want to convert and click **[!UICONTROL Next]**.

![](assets/s_ncs_user_itemized_list_alias_transform.png)

Click **[!UICONTROL Start]** to run the conversion.

![](assets/s_ncs_user_itemized_list_alias_detail1.png)

Una vez finalizada la ejecución, el alias se añade a la lista de alias.

![](assets/s_ncs_user_itemized_list_alias_detail2.png)

#### Recuperación de visitas de alias {#retrieving-alias-hits}

Los valores introducidos por los usuarios se pueden convertir en alias. De hecho, cuando el usuario introduce un valor que no está incluido en la lista desglosada, el valor se almacena en la pestaña **[!UICONTROL Alias]**.

El flujo de trabajo técnico de **Limpieza de alias** recupera estos valores cada noche a fin de actualizar la lista desglosada. Consulte [Ejecución de la limpieza de datos](#running-data-cleansing)

If necessary, the **[!UICONTROL Hits]** column can display the number of times this value was entered. El cálculo de este valor puede consumir tiempo y memoria. Para obtener más información, consulte [Cálculo de ocurrencias de entrada](#calculating-entry-occurrences).

### Ejecución de la limpieza de datos {#running-data-cleansing}

Data cleansing is performed by the **[!UICONTROL Alias cleansing]** technical workflow. Las configuraciones definidas para las enumeraciones se aplican durante la ejecución. Consulte [Flujo de trabajo de limpieza de alias](#alias-cleansing-workflow).

Cleansing can be triggered via the **[!UICONTROL Cleanse values...]** link.

![](assets/s_ncs_user_itemized_list_alias_start_normalize.png)

The **[!UICONTROL Advanced parameters...]** link lets you set the date starting from which collected values are taken into account.

![](assets/s_ncs_user_itemized_list_alias_normalize.png)

Click the **[!UICONTROL Start]** button to run data cleansing.

#### Cálculo de las apariciones de una entrada {#calculating-entry-occurrences}

La subpestaña **[!UICONTROL Alias]** de una lista desglosada puede mostrar el número de apariciones de un alias entre todos los valores introducidos. This information is an estimate and will be displayed in the **[!UICONTROL Hits]** column.

>[!CAUTION]
>
>El cálculo de las apariciones de las entradas de un alias puede llevar mucho tiempo. Por eso se debe tener precaución al utilizar esta función.

You can run hit calculation manually via the **[!UICONTROL Cleanse values...]** link. To do this, click the **[!UICONTROL Advanced parameters...]** link and select the desired option(s).

![](assets/s_ncs_user_itemized_list_alias_hits.png)

* **[!UICONTROL Update the number of alias hits]**:: esto le permite actualizar las visitas que ya se han calculado, en función de la fecha introducida.
* **[!UICONTROL Recalculate the number of alias hits from the start]**:: permite ejecutar el cálculo en toda la plataforma de Adobe Campaign.

Asimismo, se puede crear un flujo de trabajo dedicado para que el cálculo se ejecute automáticamente durante un periodo determinado, por ejemplo, una vez por semana.

To do this, create a copy of the **[!UICONTROL Alias cleansing]** workflow, change the scheduler and use the following settings in the **[!UICONTROL Enumeration value cleansing]** activity:

* **-updateHits** para actualizar el número de visitas de alias,
* **-updateHits:full** para volver a calcular todas las visitas de alias.

#### Flujo de trabajo de limpieza de alias {#alias-cleansing-workflow}

El flujo de trabajo de **Limpieza de alias** ejecuta la limpieza de los valores de las enumeraciones. Se ejecuta a diario de forma predeterminada.

Se accede a él a través del **[!UICONTROL Administration > Production > Technical workflows]** nodo.

![](assets/s_ncs_user_itemized_list_alias_wf.png)

