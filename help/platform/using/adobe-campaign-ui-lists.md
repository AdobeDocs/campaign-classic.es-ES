---
solution: Campaign Classic
product: campaign
title: Administración y personalización de listas
description: Aprenda a examinar y configurar listas
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: ht
source-git-commit: d6327cb5307ab5d37c15afa45dfd180ef04cb5a2
workflow-type: ht
source-wordcount: '1151'
ht-degree: 100%

---


# Administración y personalización de listas{#manage-and-customize-lists}

Puede acceder a las listas de registros de la base de datos de Campaign mediante el Explorador. Puede filtrar estas listas, ejecutar búsquedas, añadir información, filtrar y ordenar datos.

## Recuento de registros {#counting-records}

De forma predeterminada, Adobe Campaign carga los 200 primeros registros de una lista. Esto significa que la vista no muestra necesariamente todos los registros de la tabla que está viendo. Puede ejecutar un recuento del número de registros en la lista y cargar más registros.

En la parte inferior derecha de la pantalla de la lista, un **[!UICONTROL counter]** muestra cuántos registros se han cargado y la cantidad total de registros en la base de datos (después de aplicar los filtros):

![](assets/s_ncs_user_nb_200_0.png)

Si aparece un símbolo **?** en lugar del número a la derecha, haga clic en el contador para iniciar el cálculo.

### Carga de más registros {#loading-more-records}

Para cargar (y mostrar) registros adicionales (200 líneas por defecto), haga clic en **[!UICONTROL Continue loading]**.

![](assets/s_ncs_user_load_list.png)

Para cargar todos los registros, haga clic con el botón derecho en la lista y seleccione **[!UICONTROL Load all]**.

>[!CAUTION]
>
>En función del número de registros, el tiempo de carga de la lista completa puede ser largo.

### Cambiar el número predeterminado de registros {#change-default-number-of-records}

Para cambiar el número predeterminado de registros cargados, haga clic en **[!UICONTROL Configure list]** en la esquina inferior derecha de la lista.

![](assets/s_ncs_user_configure_list.png)

En la ventana de configuración de la lista, haga clic en **[!UICONTROL Advanced parameters]** (abajo a la izquierda) y cambie el número de líneas que desea recuperar.

![](assets/s_ncs_user_configurelist_advancedparam.png)

## Configuración de listas {#configuring-lists}

### Insertar columnas {#add-columns}

Existen dos formas de añadir una columna en la lista.

Puede añadir rápidamente una columna a una lista desde el detalle de un registro. Para ello:

1. Desde una pantalla de detalles, haga clic con el botón derecho en el campo que desee mostrar en una columna.
1. Seleccione **[!UICONTROL Add in the list]**.

   La columna se añade a la derecha de las columnas existentes.

![](assets/s_ncs_user_add_in_list.png)

Otra forma de añadir columnas, por ejemplo, si desea mostrar datos que no se muestran en la pantalla de detalles, es utilizar la ventana de configuración de lista. Para ello:

1. Haga clic en **[!UICONTROL Configure list]** que aparece a la derecha de la lista.

   ![](assets/s_ncs_user_configure_list.png)

1. En la ventana de configuración de la lista, haga doble clic en el campo que se añadirá en la lista de **[!UICONTROL Available fields]** para añadirlos a las **[!UICONTROL Output columns]**.

   ![](assets/s_ncs_user_configurelist.png)

   >[!NOTE]
   >
   >De forma predeterminada, no se muestran los campos avanzados. Para mostrarlos, haga clic en **Display advanced fields** a la derecha de la lista de campos disponibles.
   >
   >Las etiquetas se muestran por tabla y luego en orden alfabético.
   >
   >Utilice el campo **Search** para realizar una búsqueda en los campos disponibles. Para obtener más información, consulte [esta sección](#sorting-a-list).
   >
   >Los campos se identifican mediante iconos específicos: campos SQL, tablas vinculadas, campos calculados, etc. La descripción de cada campo seleccionado se muestra en la lista de campos disponibles. [Más información](#configuring-lists).
   >
   >También puede ordenar y filtrar datos. Consulte [esta sección](../../platform/using/filtering-options.md).

1. Repita el proceso para cada columna que desee visualizar.
1. Utilice las flechas para modificar el **orden de visualización**. La columna más alta estará a la izquierda en la lista de registros.

   ![](assets/s_ncs_user_columns_order_down.png)

1. Si lo necesita, puede hacer clic en **[!UICONTROL Distribution of values]** para ver cómo se reparten los valores del campo seleccionado en la carpeta actual.

   ![](assets/s_ncs_user_configurelist_values.png)

1. Haga clic en **[!UICONTROL OK]** para confirmar la configuración y mostrar el resultado.

### Crear una columna nueva {#create-a-new-column}

Puede crear nuevas columnas para mostrar campos adicionales en la lista. Para ello:

1. Haga clic en **[!UICONTROL Configure the list]** en la parte inferior derecha de la lista.
1. Haga clic en **[!UICONTROL Add]** para mostrar un nuevo campo en la lista.

### Eliminar una columna {#remove-a-column}

Puede ocultar una o varias columnas de una lista de registros usando la función **[!UICONTROL Configure list]** situada en la parte inferior derecha de la lista.

![](assets/s_ncs_user_configure_list.png)

En la ventana de configuración de la lista, seleccione la columna que desea ocultar en la zona de **[!UICONTROL Output columns]** y haga clic en el botón eliminar.

![](assets/s_ncs_user_removecolumn_icon.png)

Repita el proceso para cada columna que quiera ocultar. Haga clic en **[!UICONTROL OK]** para confirmar la configuración y mostrar el resultado.

### Ajustar el ancho de las columnas {#adjust-column-width}

Cuando una lista está activa, es decir, cuando se selecciona al menos una línea, puede utilizar F9 para ajustar el ancho de las columnas de modo que todas las columnas se puedan mostrar en pantalla.

### Visualización de datos en subcarpetas {#display-sub-folders-records}

Las listas pueden mostrar:

* Tanto los registros contenidos solo en la carpeta seleccionada,
* como los registros de la carpeta seleccionada y sus subcarpetas.

Para cambiar de un modo de visualización a otro, haga clic en **[!UICONTROL Display sub-levels]** en la barra de herramientas.

![](assets/s_ncs_user_display_children_icon.png)

## Cómo guardar una configuración de lista {#saving-a-list-configuration}

Las configuraciones de la lista se definen localmente en el nivel de la estación de trabajo. Cuando se borra la memoria caché local, las configuraciones locales se desactivan.

De forma predeterminada, los parámetros de visualización definidos se aplican a todas las listas con el tipo de carpeta correspondiente. Por lo tanto, cuando modifique cómo se muestra la lista de destinatarios desde una carpeta, esta configuración se aplicará a todas las otras carpetas de destinatarios.

No obstante, es posible guardar más de una configuración para aplicarla a distintas carpetas del mismo tipo. La configuración se guarda con las propiedades de la carpeta que contienen los datos y se puede volver a aplicar.

Por ejemplo, para una carpeta de entrega es posible configurar la siguiente visualización:

![](assets/s_ncs_user_folder_save_config_1.png)

Para guardar esta configuración de lista de forma que pueda reutilizarse, siga estos pasos:

1. Haga clic con el botón derecho en la carpeta que contiene los datos mostrados.
1. Seleccione **[!UICONTROL Properties]**.
1. Haga clic en **[!UICONTROL Advanced settings]** y, a continuación, especifique un nombre en el campo **[!UICONTROL Configuration]**.

   ![](assets/s_ncs_user_folder_save_config_2.png)

1. Haga clic en **[!UICONTROL OK]** y luego en **[!UICONTROL Save]**.

A continuación, puede aplicar esta configuración a otra carpeta de **entrega**:

![](assets/s_ncs_user_folder_save_config_3.png)

Haga clic en **[!UICONTROL Save]** en la ventana de propiedades de la carpeta. La visualización de la lista se modifica para que coincida con la configuración especificada:

![](assets/s_ncs_user_folder_save_config_5.png)

## Exportación de una lista {#exporting-a-list}

Para exportar datos de una lista, debe utilizar un asistente de exportación. Para acceder a él, seleccione los elementos que desea exportar de la lista, haga clic con el botón derecho del ratón y seleccione **[!UICONTROL Export...]**.

El uso de las funciones de importación y exportación se explica en [Importaciones y exportaciones genéricas](../../platform/using/about-generic-imports-exports.md).

>[!CAUTION]
>
>Los elementos de una lista no se deben exportar mediante la función Copiar/Pegar.

## Ordenación de una lista {#sorting-a-list}

Las listas pueden contener una gran cantidad de datos. Puede clasificar estos datos o aplicar filtros simples o avanzados. La clasificación le permite mostrar los datos en orden ascendente o descendente. Los filtros permiten definir y combinar criterios para mostrar solo los datos seleccionados.

Haga clic en el encabezado de la columna para aplicar un orden ascendente o descendente, o para cancelar la clasificación de datos. El estado de clasificación activo y el orden de clasificación se indican mediante una flecha azul antes de la etiqueta de columna. Un guion rojo antes de la etiqueta de columna significa que la ordenación se aplica a los datos indexados de la base de datos. Este método de clasificación se utiliza para optimizar los trabajos de ordenación.

También puede configurar la ordenación o combinar criterios de clasificación. Para realizar esto, siga los pasos a continuación:

1. Haga clic en **[!UICONTROL Configure list]** en la parte inferior derecha de la lista.

   ![](assets/s_ncs_user_configure_list.png)

1. En la ventana de configuración de la lista, haga clic en la pestaña **[!UICONTROL Sorting]**.
1. Seleccione los campos que desea ordenar y la dirección de clasificación (ascendente o descendente).

   ![](assets/s_ncs_user_configurelist_sort.png)

1. La prioridad de ordenación se define mediante el orden de las columnas de clasificación. Para cambiar la prioridad, utilice los iconos adecuados para cambiar el orden de las columnas.

   ![](assets/s_ncs_user_configurelist_move.png)

   La prioridad de ordenación no afecta a la visualización de las columnas de la lista.

1. Haga clic en **[!UICONTROL Ok]** para confirmar esta configuración y mostrar el resultado en la lista.

### Búsqueda de elementos {#running-a-search}

Puede ejecutar una búsqueda de los campos disponibles en un editor utilizando el campo **[!UICONTROL Search]** situado encima de la lista de campos. Presione **Enter** en el teclado o busque en la lista. Los campos que coincidan con la búsqueda tendrán etiquetas en negrita.

>[!NOTE]
>
>Puede crear filtros para mostrar solo algunos de los datos de una lista. [Más información](../../platform/using/creating-filters.md).
