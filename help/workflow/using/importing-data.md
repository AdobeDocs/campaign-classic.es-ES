---
title: Importación de datos
description: Obtenga información sobre cómo importar datos en Adobe Campaign Classic
page-status-flag: never-activated
uuid: c8cf2bf1-f7a5-4de4-9e53-a961c9e5beca
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: e53af1c2-b50c-4a8c-b5b8-f23a85bd3211
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2e16d4de068f8cb1e61069aa53626f7bf7021466

---


# Importación de datos{#importing-data}

## Recopilación de datos {#how-to-collect-data}

### Uso de datos de una lista: Lista de lectura {#using-data-from-a-list--read-list}

Los datos enviados en un flujo de trabajo pueden provenir de listas, por lo que los datos se han preparado y estructurado previamente.

This list may have been directly created in Adobe Campaign or imported by the **[!UICONTROL Import a list]** option. Para obtener más información, consulte esta [página](../../platform/using/generic-imports-and-exports.md).

For more on using the read list activity in a workflow, refer to [Read list](../../workflow/using/read-list.md).

### Carga de datos de un archivo {#loading-data-from-a-file}

Los datos procesados en un flujo de trabajo se pueden extraer de un archivo estructurado para que se puedan importar en Adobe Campaign.

A description of the loading data activity can be found in the [Data loading (file)](../../workflow/using/data-loading--file-.md) section.

Ejemplo de archivo estructurado para importar:

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

### Descompresión o desencriptado de un archivo antes de procesarlo {#unzipping-or-decrypting-a-file-before-processing}

Adobe Campaign permite importar archivos comprimidos o encriptados. Before they can be read in a **[!UICONTROL Data loading (file)]** activity, you can define a pre-processing to unzip or to decrypt the file.

Para poder hacerlo:

* Si Adobe aloja la instalación de Adobe Campaign: envíe una solicitud al [equipo de asistencia](https://support.neolane.net) para que instalen las herramientas necesarias en el servidor.
* Si la instalación de Adobe Campaign está in situ: instale la utilidad que desee utilizar (por ejemplo: GPG, GZIP) así como las claves necesarias (clave de cifrado) en el servidor de aplicaciones.

1. Add and configure a **[!UICONTROL File transfer]** activity in your workflow.
1. Add a **[!UICONTROL Data loading (file)]** activity and define the file format.
1. Marque la **[!UICONTROL Pre-process the file]** opción.
1. Especifique el comando de preprocesamiento que desee aplicar. Por ejemplo, para desencriptar un archivo mediante PGP:

   ```
   <path-to_pgp_if-not_global_or_server/>pgp.exe --decrypt --input nl6/var/vp/import/filename.pgp --passphrase "your password" --recipient recipient @email.com --verbose --output nl6/var/vp/import/filename
   ```

1. Añada otras actividades para administrar los datos que provengan del archivo.
1. Guarde y ejecute el flujo de trabajo.

Al exportar un archivo, también puede comprimirlo o encriptarlo. See [Zipping or encrypting a file](../../workflow/using/how-to-use-workflow-data.md#zipping-or-encrypting-a-file).

## Prácticas recomendadas al importar datos {#best-practices-when-importing-data}

Tenga cuidado y siga las sencillas reglas detalladas debajo, ya que le pueden ayudar a garantizar la coherencia de los datos en la base de datos y a evitar errores comunes durante la actualización o las exportaciones de datos.

### Uso de plantillas de importación {#using-import-templates}

La mayoría de los flujos de trabajo de importación deben contener las siguientes actividades: **[!UICONTROL Data loading (file)]**, **[!UICONTROL Enrichment]**, **[!UICONTROL Split]**, **[!UICONTROL Deduplication]**, **[!UICONTROL Update data]**.

El uso de plantillas de importación facilita la preparación de importaciones similares y la coherencia de los datos en la base de datos. Learn how to build workflow templates in the [Workflow templates](../../workflow/using/building-a-workflow.md#workflow-templates) section.

In many projects, imports are built without **[!UICONTROL Deduplication]** activity because the files used in the project do not have duplicates. Los duplicados aparecen en ocasiones al importar archivos diferentes. En este caso, la deduplicación resulta difícil. Por lo tanto, la deduplicación es una buena precaución en todos los flujos de trabajo de importación.

No dé por hecho que los datos entrantes son coherentes y correctos, o que el departamento de TI o el iniciador de Adobe Campaign se pueden encargar de ello. Durante el proyecto, tenga en cuenta la limpieza de los datos. Deduplique, reconcilie y mantenga la coherencia al importar datos.

Hay un ejemplo de plantilla de importación disponible en la sección [Configuración de una importación](#setting-up-a-recurring-import) recurrente.

### Uso de formatos de archivo plano {#using-flat-file-formats}

El formato más eficaz para las importaciones es un archivo plano. Los archivos planos se pueden importar en modo masivo a nivel de base de datos.

Por ejemplo:

* Separador: tabulación o punto y coma
* Primera línea con encabezados
* Sin delimitador de cadenas
* Formato de fecha: AAAA/MM/DD HH:mm:SS

Adobe Campaign no puede importar archivos XML utilizando actividades estándar de importación de archivos. Es posible importar archivos XML utilizando JavaScript, pero solo con volúmenes pequeños: menos de 10 000 registros por archivo.

### Uso de compresión y encriptación {#using-compression-and-encryption}

Utilice archivos comprimidos para importar y exportar cuando sea posible.

En Linux, es posible descomprimir un archivo e importarlo al mismo tiempo mediante una línea de comandos. Por ejemplo:

```
zcat nl6/var/vp/import/filename.gz
```

También es recomendable encriptar los archivos enviados a través de la red si el proceso no es seguro. Se puede utilizar GPG para esto.

### Carga de datos en lote desde archivos {#loading-data-in-batch-from-files}

La carga de datos en lote desde un archivo es más eficaz que cargar las líneas de una en una y en tiempo real (por ejemplo, a través de un servicio Web).

La importación mediante servicios Web no es eficiente. Es mejor utilizar archivos siempre que sea posible.

La llamada a los servicios Web externos para enriquecer perfiles en tiempo real también causa problemas de rendimiento y pérdidas de memoria, ya que funciona al nivel de línea.

Si necesita importar datos, es mejor hacerlo en lote mediante un flujo de trabajo en vez de hacerlo en tiempo real, mediante una aplicación Web o un servicio Web.

### Uso de la gestión de datos {#using-data-management}

La carga en modo iterativo (línea a línea) con JavaScript debe limitarse a los volúmenes pequeños.

For better efficiency, always use the **[!UICONTROL Data Loading (File)]** activity in data management workflows.

### Importación en modo Delta {#importing-in-delta-mode}

Las importaciones regulares deben realizarse en modo delta. Esto significa que solo se envían datos modificados o nuevos a Adobe Campaign, en lugar de toda la tabla de una sentada.

Las importaciones completas deben utilizarse únicamente para la carga inicial.

Importación de datos mediante la gestión de datos en lugar de JavaScript.

### Mantenimiento de la coherencia {#maintaining-consistency}

Para mantener la coherencia de los datos en la base de datos de Adobe Campaign, siga los principios siguientes:

* Si los datos importados coinciden con una tabla de referencia de Adobe Campaign, se deben reconciliar con esa tabla en el flujo de trabajo. Los registros que no coinciden deben ser rechazados.
* Asegúrese de que los datos importados siempre estén **“normalizados”** (correo electrónico, número de teléfono, dirección de correo postal) y que esta normalización sea fiable y no cambie con los años. Si no es así, es probable que algunos duplicados aparezcan en la base de datos y, como Adobe Campaign no proporciona herramientas para establecer correspondencias “difusas”, resulta muy difícil administrarlos y eliminarlos.
* Los datos de transacciones deben tener una clave de reconciliación y se deben reconciliar con los datos existentes para evitar la creación de duplicados.
* **Importación de archivos relacionados en orden**.

   Si la importación está compuesta por varios archivos que dependen unos de otros, el flujo de trabajo debe asegurar que los archivos se importen en el orden correcto. Si un archivo falla, los demás archivos no se importan.

* **Deduplique**, reconcilie y mantenga la coherencia al importar datos.

## Configuración de una importación recurrente {#setting-up-a-recurring-import}

La utilización de una plantilla de importación es una práctica recomendada si necesita importar con regularidad archivos con la misma estructura.

Este ejemplo muestra cómo se puede predefinir un flujo de trabajo para reutilizarlo a la hora de importar perfiles provenientes de un CRM en la base de datos de Adobe Campaign. Para obtener más información sobre todos los ajustes posibles de cada actividad, consulte esta [sección](../../workflow/using/about-activities.md).

1. Cree una nueva plantilla de flujo de trabajo desde **[!UICONTROL Resources > Templates > Workflow templates]**.
1. Añada las siguientes actividades:

   * **[!UICONTROL Data loading (file)]**: Defina la estructura esperada del archivo que contiene los datos que se van a importar.
   * **[!UICONTROL Enrichment]**: Reconcilie los datos importados con los datos de la base de datos.
   * **[!UICONTROL Split]**: Cree filtros para procesar registros de formas diferentes, dependiendo de si se podrían reconciliar o no.
   * **[!UICONTROL Deduplication]**: Deduplique los datos del archivo entrante antes de insertarlos en la base de datos.
   * **[!UICONTROL Update data]**: Actualice la base de datos con los perfiles importados.
   ![](assets/import_template_example0.png)

1. Configure la **[!UICONTROL Data Loading (file)]** actividad:

   * Cargue un archivo de muestra para definir la estructura que desee. El archivo de muestra debe contener tan solo unas pocas líneas, pero todas las columnas necesarias para la importación. Compruebe y edite el formato del archivo para asegurarse de que el tipo de cada columna está correctamente definido: texto, fecha, entero, etc. Por ejemplo:

      ```
      lastname;firstname;birthdate;email;crmID
      Smith;Hayden;23/05/1989;hayden.smith@mailtest.com;123456
      ```

   * En la **[!UICONTROL Name of the file to load]** sección, seleccione **[!UICONTROL Upload a file from the local machine]** y deje el campo en blanco. Cada vez que cree un nuevo flujo de trabajo a partir de esta plantilla, puede especificar aquí el archivo que desee, siempre que se corresponda con la estructura definida.

      Puede utilizar cualquiera de las opciones, pero debe modificar la plantilla según corresponda. For example, if you select **[!UICONTROL Specified in the transition]**, you can add a **[!UICONTROL File Transfer]** activity before to retrieve the file to import from a FTP/SFTP server. Con la conexión S3 o SFTP, también puede importar datos de segmentos a Adobe Campaign con la plataforma de datos del cliente en tiempo real de Adobe. For more on this, refer to this [documentation](https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html).

      ![](assets/import_template_example1.png)

1. Configure la **[!UICONTROL Enrichment]** actividad. El objetivo de esta actividad en este contexto es identificar los datos entrantes.

   * In the **[!UICONTROL Enrichment]** tab, select **[!UICONTROL Add data]** and define a link between the imported data and the recipients targeting dimension. En este ejemplo, el campo personalizado **CRM ID** se utiliza para crear la condición de unión. Utilice el campo o la combinación de campos que necesite siempre que permita identificar registros únicos.
   * En la **[!UICONTROL Reconciliation]** ficha, deje la **[!UICONTROL Identify the document from the working data]** opción sin marcar.
   ![](assets/import_template_example2.png)

1. Configure the **[!UICONTROL Split]** activity to retrieve reconciled recipients in one transition and recipients that could not be reconciled but who have enough data in a second transition.

   La transición con los destinatarios reconciliados se puede utilizar después para actualizar la base de datos. La transición con destinatarios desconocidos se puede utilizar para crear nuevas entradas de destinatario en la base de datos si en el archivo hay un conjunto mínimo de información disponible.

   Los destinatarios que no se pueden reconciliar y no tienen datos suficientes se seleccionan en una transición saliente de complemento y se pueden exportar en un archivo independiente, o sencillamente se ignoran.

   * In the **[!UICONTROL General]** tab of the activity, select **[!UICONTROL Use the additional data only]** as filtering setting and make sure that the **[!UICONTROL Targeting dimension]** is automatically set to **[!UICONTROL Enrichment]**.

      Check the **[!UICONTROL Generate complement]** option to be able to see if any record cannot be inserted in the database. Si lo necesita, puede seguir procesando los datos complementarios: exportación de archivo, actualización de lista, etc.

   * In the first subset of the **[!UICONTROL Subsets]** tab, add a filtering condition on the inbound population to select only records for which the recipient primary key is not equal to 0. De esta forma, los datos del archivo que se reconcilien con los destinatarios de la base de datos se seleccionan dentro de ese subconjunto.

      ![](assets/import_template_example3.png)

   * Añada un segundo subconjunto que seleccione registros no reconciliados con datos suficientes como para poder insertarlos en la base de datos. Por ejemplo: dirección de correo electrónico, nombre y apellidos.

      Los subconjuntos se procesan por orden de creación, lo que significa que cuando se procesa este segundo subconjunto, todos los registros que ya existen en la base de datos están seleccionados en el primer subconjunto.

      ![](assets/import_template_example3_2.png)

   * Todos los registros que no están seleccionados en los dos primeros subconjuntos se seleccionan en la **[!UICONTROL Complement]**.

1. Configure the **[!UICONTROL Update data]** activity located after the first outbound transition of the **[!UICONTROL Split]** activity configured previously.

   * Select **[!UICONTROL Update]** as **[!UICONTROL Operation type]** since the inbound transition only contains recipients already present in the database.
   * In the **[!UICONTROL Record identification]** section, select **[!UICONTROL Using reconciliation keys]** and define a key between the targeting dimension and the link created in the **[!UICONTROL Enrichment]**. En este ejemplo, se utiliza el campo personalizado **CRM ID**.
   * In the **[!UICONTROL Fields to update]** section, indicate the fields from the recipients dimension to update with the value of the corresponding column from the file. Si los nombres de las columnas del archivo son idénticos o casi idénticos a los nombres de los campos de dimensión de los destinatarios, puede utilizar el botón de varita mágica para hacer coincidir automáticamente los diferentes campos.

      ![](assets/import_template_example6.png)

1. Configure the **[!UICONTROL Deduplication]** activity located after the transition containing unreconciled recipients:

   * Select **[!UICONTROL Edit configuration]** and set the targeting dimension to the temporary schema generated from the **[!UICONTROL Enrichment]** activity of the workflow.

      ![](assets/import_template_example4.png)

   * En este ejemplo, el campo de correo electrónico se utiliza para buscar perfiles únicos. Puede utilizar cualquier campo que esté rellenado y que forme parte de una combinación única.
   * In the **[!UICONTROL Deduplication method]** screen, select **[!UICONTROL Advanced parameters]** and check the **[!UICONTROL Disable automatic filtering of 0 ID records]** option to make sure records that have a primary key equal to 0 (which should be all records of this transition) are not excluded.
   ![](assets/import_template_example7.png)

1. Configure the **[!UICONTROL Update data]** activity located after the **[!UICONTROL Deduplication]** activity configured previously.

   * Select **[!UICONTROL Insert]** as **[!UICONTROL Operation type]** since the inbound transition only contains recipients not present in the database.
   * En la **[!UICONTROL Record identification]** sección, seleccione **[!UICONTROL Directly using the targeting dimension]** y elija la **[!UICONTROL Recipients]** dimensión.
   * In the **[!UICONTROL Fields to update]** section, indicate the fields from the recipients dimension to update with the value of the corresponding column from the file. Si los nombres de las columnas del archivo son idénticos o casi idénticos a los nombres de los campos de dimensión de los destinatarios, puede utilizar el botón de varita mágica para hacer coincidir automáticamente los diferentes campos.

      ![](assets/import_template_example8.png)

1. After the third transition of the **[!UICONTROL Split]** activity, add a **[!UICONTROL Data extraction (file)]** activity and a **[!UICONTROL File transfer]** activity if you want to keep track of data not inserted in the database. Configure las actividades para exportar la columna que necesite y para transferir el archivo en un servidor FTP o SFTP desde donde pueda recuperarlo.
1. Add an **[!UICONTROL End]** activity and save the workflow template.

Ahora la plantilla se puede utilizar y está disponible para cada nuevo flujo de trabajo. All is needed is then to specify the file containing the data to import in the **[!UICONTROL Data loading (file)]** activity.

![](assets/import_template_example9.png)

