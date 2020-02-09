---
title: Carga de datos (archivos)
description: Obtenga más información sobre la actividad de carga de datos (archivo).
page-status-flag: never-activated
uuid: c064aa23-412e-49b4-a51d-b0e8ca572f2e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: dcb5b8e8-be38-4d89-908d-f57c2413a9bc
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2e16d4de068f8cb1e61069aa53626f7bf7021466

---


# Carga de datos (archivos){#data-loading-file}

## Uso {#use}

The **[!UICONTROL Load (File)]** activity lets you directly access a source of external data and use it in Adobe Campaign. De hecho, todos los datos necesarios para las operaciones objetivos no se encuentran siempre en la base de datos de la campaña de Adobe: pueden estar disponibles en archivos externos.

El archivo que se va a cargar se puede especificar mediante la transición o se calcula durante la ejecución de esta actividad. Por ejemplo, puede ser la lista de los 10 productos favoritos de un cliente, cuyas compras se administran en una base de datos externa.

La sección superior de la ventana de configuración de esta actividad permite definir el formato de archivo. Para esto, utilice un archivo de muestra con el mismo formato que el que se va a importar. Este archivo se puede almacenar localmente o en el servidor.

>[!CAUTION]
>
>Solo se admiten archivos de estructura “plana” (por ejemplo, CSV, TXT, etc.). No se recomienda utilizar el formato XML.

![](assets/s_advuser_wf_etl_file.png)

Puede definir un proceso previo para que se ejecute durante la importación de archivos, por ejemplo, para que no tenga que descomprimir el archivo en el servidor (y, por lo tanto, ahorrar espacio para el archivo descomprimido), y para incluir la descompresión en el procesamiento de archivos. Seleccione la **[!UICONTROL Pre-process the file]** opción y elija una de las tres opciones: **[!UICONTROL None]**, **[!UICONTROL Decompression]** (zcat) o **[!UICONTROL Decrypt]** (gpg).

## Definición del formato del archivo {#defining-the-file-format}

Al cargar un archivo, el formato de columna se detecta automáticamente con los parámetros predeterminados para cada tipo de datos. Puede modificar estos parámetros predeterminados para especificar los procesos concretos que se aplican a los datos, especialmente cuando hay un error o un valor vacío.

Para ello, seleccione **[!UICONTROL Click here to change the file format...]** en la ventana principal de la **[!UICONTROL Data loading (file)]** actividad. A continuación, se abrirá la ventana de detalles de formato.

![](assets/file_loading_columns_format.png)

A continuación, puede modificar el formato general del archivo y el de cada columna.

El formato del archivo general permite definir la forma en que se reconocerán las columnas (codificación de archivos, separadores utilizados, etc.).

El formato de columna permite definir el valor de procesamiento de cada columna:

* **[!UICONTROL Ignore column]**:: no procesa esta columna durante la carga de datos.
* **[!UICONTROL Data type]**:: especifica el tipo de datos esperados para cada columna.
* **[!UICONTROL Allow NULLs]**:: especifica cómo administrar valores vacíos.

   * **[!UICONTROL Adobe Campaign default]**:: genera un error solo para los campos numéricos; de lo contrario, inserta un valor NULL.
   * **[!UICONTROL Empty value allowed]**:: autoriza valores vacíos. Por lo tanto, se inserta el valor NULL.
   * **[!UICONTROL Always populated]**:: genera un error si un valor está vacío.

* **[!UICONTROL Length]**:: especifica el número máximo de caracteres para el tipo de datos de **cadena** .
* **[!UICONTROL Format]**:: define el formato de fecha y hora.
* **[!UICONTROL Data transformation]**:: define si es necesario aplicar un proceso de mayúsculas y minúsculas a una **cadena**.

   * **[!UICONTROL None]**:: la cadena importada no se modifica.
   * **[!UICONTROL First letter in upper case]**:: la primera letra de cada palabra de la cadena comienza con una letra en mayúsculas.
   * **[!UICONTROL Upper case]**:: todos los caracteres de la cadena están en mayúsculas.
   * **[!UICONTROL Lower case]**:: todos los caracteres de la cadena están en minúsculas.

* **[!UICONTROL White space management]**:: especifica si determinados espacios deben ignorarse en una cadena. The **[!UICONTROL Ignore spaces]** value only allows spaces at the beginning and at the end of a string to be ignored.
* **[!UICONTROL Error processings]**:: define el comportamiento si se encuentra un error.

   * **[!UICONTROL Ignore the value]**:: se omite el valor. Se genera una advertencia en el registro de ejecución del flujo de trabajo.
   * **[!UICONTROL Reject line]**:: la línea completa no se procesa.
   * **[!UICONTROL Use a default value in case of error]**:: reemplaza el valor que causa el error por un valor predeterminado, definido en el **[!UICONTROL Default value]** campo.
   * **[!UICONTROL Reject the line when there is no remapping value]**:: la línea completa no se procesa a menos que se haya definido una asignación para el valor erróneo (consulte la **[!UICONTROL Mapping]** opción siguiente).
   * **[!UICONTROL Use a default value in case the value is not remapped]**:: reemplaza el valor que causa el error por un valor predeterminado, definido en el **[!UICONTROL Default value]** campo, a menos que se haya definido una asignación para el valor erróneo (consulte la **[!UICONTROL Mapping]** opción siguiente).

* **[!UICONTROL Default value]**:: especifica el valor predeterminado según el procesamiento de errores elegido.
* **[!UICONTROL Mapping]**: este campo solo está disponible en la configuración de los detalles de la columna (a los que se accede mediante un doble clic o a través de las opciones de la lista de la columna). Esto transforma ciertos valores cuando se importan. Por ejemplo, se puede transformar “tres” en “3”.

## Example: Collecting data and loading it in the database {#example--collecting-data-and-loading-it-in-the-database}

El ejemplo siguiente permite recopilar un fichero en el servidor todos los días, cargar su contenido y actualizar los datos en la base de datos según la información que contenga. El archivo que se va a recopilar contiene información sobre los clientes que pueden haber realizado compras (de más o menos de 3000 euros), los que solicitaron un reembolso por una compra o realizaron una visita sin comprar nada. En función de esta información, se aplicarán varios procesos a sus perfiles en la base de datos.

![](assets/s_advuser_load_file_sample_0.png)

1. El recolector de archivos permite recuperar ficheros almacenados en un directorio, según la frecuencia dada.

   The **[!UICONTROL Directory]** tab contains information on the file(s) to be recovered. En nuestro ejemplo, se recuperarán todos los ficheros con formato de texto cuyos nombres contengan la palabra “customers” y que se almacenen en el directorio tmp/Adobe/Data/files del servidor.

   El uso del **[!UICONTROL File collector]** se detalla en la sección del selector [Archivo](../../workflow/using/file-collector.md) .

   ![](assets/s_advuser_load_file_sample_1.png)

   The **[!UICONTROL Schedule]** tab lets you schedule the execution of the collector, i.e. to specify the frequency with which the presence of these files will be checked.

   En este caso, deseamos activar el recolector todos los días a las 9 p. m.

   ![](assets/s_advuser_load_file_sample_2.png)

   To do this, click the **[!UICONTROL Change...]** button located in the lower right-hand section of the editing tool and configure the schedule.

   For more on this, refer to [Scheduler](../../workflow/using/scheduler.md).

1. A continuación, configure la actividad de carga de datos (archivos) para indicar cómo se deben leer los ficheros recopilados. Para esto, seleccione un fichero de muestra con la misma estructura que los ficheros que se van a cargar.

   ![](assets/s_advuser_load_file_sample_3.png)

   En este caso, el archivo contiene cinco columnas:

   * la primera columna contiene un código que coincide con el evento: compra (más o menos que 3000 euros), sin compras ni reembolsos en una o más compras.
   * Las cuatro columnas siguientes contienen el nombre, apellido, correo electrónico y número de cuenta del cliente.
   La configuración del formato del archivo que se va a cargar coincide con el definido durante una importación de datos en Adobe Campaign. Para obtener más información, consulte [esta sección](../../platform/using/importing-data.md#step-2---source-file-selection).

1. En la actividad dividida, especifique los subconjuntos que desea crear, según el valor de la columna **Event**.

   La actividad dividida se detalla en la sección.

   ![](assets/s_advuser_load_file_sample_4.png)

   Para cada subconjunto, especifique uno de los valores en la columna **Event**.

   ![](assets/s_advuser_load_file_sample_5.png)

   The **[!UICONTROL Split]** activity will therefore contain the following information:

   ![](assets/s_advuser_load_file_sample_6.png)

1. A continuación, especifique los procesos que se van a realizar para cada tipo de población. In our example, we are going to **[!UICONTROL Update the data]** in the database. To do this, place an **[!UICONTROL Update data]** activity at the end of each outbound transition from the split activity.

   La **[!UICONTROL Update data]** actividad se detalla en la sección [Actualizar datos](../../workflow/using/update-data.md) .

