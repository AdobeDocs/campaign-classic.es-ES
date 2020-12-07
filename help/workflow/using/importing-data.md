---
solution: Campaign Classic
product: campaign
title: Importación de datos
description: Obtenga información sobre cómo importar datos en Adobe Campaign
audience: workflow
content-type: reference
topic-tags: -general-operation
translation-type: tm+mt
source-git-commit: 49f3c123cb8e91b3a2a2a1eb6bd593a242b8bbfe
workflow-type: tm+mt
source-wordcount: '2476'
ht-degree: 99%

---


# Importación de datos{#importing-data}

>[!CAUTION]
>
>Tenga en cuenta los límites de almacenamiento SFTP, almacenamiento de la base de datos y perfil activo según el contrato de Adobe Campaign al importar datos.

## Recopilación de datos {#how-to-collect-data}

### Uso de datos de una lista: Lista de lectura {#using-data-from-a-list--read-list}

Los datos enviados en un flujo de trabajo pueden provenir de listas, por lo que los datos se han preparado y estructurado previamente.

Esta lista puede haberse creado directamente en Adobe Campaign o importado mediante la opción **[!UICONTROL Import a list]**. Para obtener más información sobre esta opción, consulte esta [página](../../platform/using/generic-imports-and-exports.md).

Para obtener más información sobre el uso de la actividad de la lista de lectura en un flujo de trabajo, consulte [Lista de lectura](../../workflow/using/read-list.md).

### Carga de datos de un archivo {#loading-data-from-a-file}

Los datos procesados en un flujo de trabajo se pueden extraer de un archivo estructurado para que se puedan importar en Adobe Campaign.

Puede encontrar una descripción de la actividad de datos de carga en la sección [Data loading (file)](../../workflow/using/data-loading--file-.md).

Ejemplo de archivo estructurado para importar:

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

## Prácticas recomendadas al importar datos {#best-practices-when-importing-data}

Tenga cuidado y siga las sencillas reglas detalladas debajo, ya que le pueden ayudar a garantizar la coherencia de los datos en la base de datos y a evitar errores comunes durante la actualización o las exportaciones de datos.

### Uso de plantillas de importación {#using-import-templates}

La mayoría de los flujos de trabajo de importación deben contener las siguientes actividades: **[!UICONTROL Data loading (file)]**, **[!UICONTROL Enrichment]**, **[!UICONTROL Split]**, **[!UICONTROL Deduplication]**, **[!UICONTROL Update data]**.

El uso de plantillas de importación facilita la preparación de importaciones similares y la coherencia de los datos en la base de datos. Consulte cómo puede crear plantillas de flujo de trabajo en la sección [Workflow templates](../../workflow/using/building-a-workflow.md#workflow-templates).

En muchos proyectos, las importaciones se crean sin actividad de **[!UICONTROL Deduplication]** porque los archivos utilizados en el proyecto no tienen duplicados. Los duplicados aparecen en ocasiones al importar archivos diferentes. En este caso, la deduplicación resulta difícil. Por lo tanto, la deduplicación es una buena precaución en todos los flujos de trabajo de importación.

No dé por hecho que los datos entrantes son coherentes y correctos, o que el departamento de TI o el iniciador de Adobe Campaign se pueden encargar de ello. Durante el proyecto, tenga en cuenta la limpieza de los datos. Deduplique, reconcilie y mantenga la coherencia al importar datos.

Hay un ejemplo de plantilla de importación disponible en la sección [Setting up a recurring import](#setting-up-a-recurring-import).

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

Para obtener una mejor eficiencia, utilice siempre **[!UICONTROL Data Loading (File)]** la actividad en los flujos de trabajo de gestión de datos.

### Importación en modo Delta {#importing-in-delta-mode}

Las importaciones regulares deben realizarse en modo delta. Esto significa que solo se envían datos modificados o nuevos a Adobe Campaign, en lugar de toda la tabla de una sentada.

Las importaciones completas deben utilizarse únicamente para la carga inicial.

Importación de datos mediante la gestión de datos en lugar de JavaScript.

### Mantenimiento de la coherencia {#maintaining-consistency}

Para mantener la coherencia de los datos en la base de datos de Adobe Campaign, siga los principios siguientes:

* Si los datos importados coinciden con una tabla de referencia de Adobe Campaign, se deben reconciliar con esa tabla en el flujo de trabajo. Los registros que no coinciden deben ser rechazados.
* Asegúrese de que los datos importados siempre estén **&quot;normalizados&quot;** (correo electrónico, número de teléfono, dirección de correo postal) y que esta normalización sea fiable y no cambie con los años. Si no es así, es probable que algunos duplicados aparezcan en la base de datos y, como Adobe Campaign no proporciona herramientas para establecer correspondencias &quot;difusas&quot;, resulta muy difícil administrarlos y eliminarlos.
* Los datos de transacciones deben tener una clave de reconciliación y se deben reconciliar con los datos existentes para evitar la creación de duplicados.
* **Importación de archivos relacionados en orden**.

   Si la importación está compuesta por varios archivos que dependen unos de otros, el flujo de trabajo debe asegurar que los archivos se importen en el orden correcto. Si un archivo falla, los demás archivos no se importan.

* **Deduplique**, reconcilie y mantenga la coherencia al importar datos.

## Caso de uso: configuración de una importación recurrente {#setting-up-a-recurring-import}

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

1. Configure la actividad **[!UICONTROL Data Loading (file)]**:

   * Cargue un archivo de muestra para definir la estructura que desee. El archivo de muestra debe contener tan solo unas pocas líneas, pero todas las columnas necesarias para la importación. Compruebe y edite el formato del archivo para asegurarse de que el tipo de cada columna está correctamente definido: texto, fecha, entero, etc. Por ejemplo:

      ```
      lastname;firstname;birthdate;email;crmID
      Smith;Hayden;23/05/1989;hayden.smith@mailtest.com;123456
      ```

   * En la sección **[!UICONTROL Name of the file to load]** , seleccione **[!UICONTROL Upload a file from the local machine]** y deje el campo en blanco. Cada vez que cree un nuevo flujo de trabajo a partir de esta plantilla, puede especificar aquí el archivo que desee, siempre que se corresponda con la estructura definida.

      Puede utilizar cualquiera de las opciones, pero debe modificar la plantilla según corresponda. Por ejemplo, si selecciona **[!UICONTROL Specified in the transition]**, puede añadir una actividad de **[!UICONTROL File Transfer]** antes de recuperar el archivo de importación de un servidor FTP/SFTP. Con la conexión S3 o SFTP, también puede importar datos de segmentos a Adobe Campaign con la plataforma de datos del cliente en tiempo real de Adobe. Para obtener más información, consulte [Documentación](https://docs.adobe.com/content/help/es-ES/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html).

      ![](assets/import_template_example1.png)

1. Configure la actividad **[!UICONTROL Enrichment]**. El objetivo de esta actividad en este contexto es identificar los datos entrantes.

   * En la pestaña **[!UICONTROL Enrichment]**, seleccione **[!UICONTROL Add data]** y defina un vínculo entre los datos importados y la dimensión de segmentación de los destinatarios. En este ejemplo, el campo personalizado **CRM ID** se utiliza para crear la condición de unión. Utilice el campo o la combinación de campos que necesite siempre que permita identificar registros únicos.
   * En la pestaña **[!UICONTROL Reconciliation]** , deje la opción **[!UICONTROL Identify the document from the working data]** sin seleccionar.

   ![](assets/import_template_example2.png)

1. Configure la actividad **[!UICONTROL Split]** para recuperar los destinatarios reconciliados en una transición, y los destinatarios que no pudieron ser reconciliados, pero que tengan datos suficientes en una segunda transición.

   La transición con los destinatarios reconciliados se puede utilizar después para actualizar la base de datos. La transición con destinatarios desconocidos se puede utilizar para crear nuevas entradas de destinatario en la base de datos si en el archivo hay un conjunto mínimo de información disponible.

   Los destinatarios que no se pueden reconciliar y no tienen datos suficientes se seleccionan en una transición saliente de complemento y se pueden exportar en un archivo independiente, o sencillamente se ignoran.

   * En la pestaña **[!UICONTROL General]** de la actividad, seleccione **[!UICONTROL Use the additional data only]** como ajuste de filtro y asegúrese de que el valor **[!UICONTROL Targeting dimension]** se establece automáticamente como **[!UICONTROL Enrichment]**.

      Marque la opción **[!UICONTROL Generate complement]** para ver si algún registro no se puede insertar en la base de datos. Si lo necesita, puede seguir procesando los datos complementarios: exportación de archivo, actualización de lista, etc.

   * En el primer subconjunto de la pestaña **[!UICONTROL Subsets]**, añada una condición de filtrado a la población entrante para seleccionar solo los registros cuya clave principal del destinatario sea distinta a 0. De esta forma, los datos del archivo que se reconcilien con los destinatarios de la base de datos se seleccionan dentro de ese subconjunto.

      ![](assets/import_template_example3.png)

   * Añada un segundo subconjunto que seleccione registros no reconciliados con datos suficientes como para poder insertarlos en la base de datos. Por ejemplo: dirección de correo electrónico, nombre y apellidos.

      Los subconjuntos se procesan por orden de creación, lo que significa que cuando se procesa este segundo subconjunto, todos los registros que ya existen en la base de datos están seleccionados en el primer subconjunto.

      ![](assets/import_template_example3_2.png)

   * Todos los registros que no están seleccionados en los dos primeros subconjuntos se seleccionan en la **[!UICONTROL Complement]**.

1. Configure la actividad **[!UICONTROL Update data]** ubicada después de la primera transición saliente de la actividad **[!UICONTROL Split]** configurada anteriormente.

   * Seleccione **[!UICONTROL Update]** como **[!UICONTROL Operation type]**, ya que la transición de entrada solo contiene destinatarios ya presentes en la base de datos.
   * En la sección **[!UICONTROL Record identification]**, seleccione **[!UICONTROL Using reconciliation keys]** y defina una clave entre la dimensión de segmentación y el vínculo creado en **[!UICONTROL Enrichment]**. En este ejemplo, se utiliza el campo personalizado **CRM ID**.
   * En la sección **[!UICONTROL Fields to update]**, indique los campos de la dimensión de destinatarios que desea actualizar con el valor de la columna correspondiente del archivo. Si los nombres de las columnas del archivo son idénticos o casi idénticos a los nombres de los campos de dimensión de los destinatarios, puede utilizar el botón de varita mágica para hacer coincidir automáticamente los diferentes campos.

      ![](assets/import_template_example6.png)

1. Configure la actividad **[!UICONTROL Deduplication]** ubicada después de la transición que contiene los destinatarios no reconciliados:

   * Seleccione **[!UICONTROL Edit configuration]** y establezca la dimensión de segmentación en el esquema temporal generado a partir de la actividad **[!UICONTROL Enrichment]** del flujo de trabajo.

      ![](assets/import_template_example4.png)

   * En este ejemplo, el campo de correo electrónico se utiliza para buscar perfiles únicos. Puede utilizar cualquier campo que esté rellenado y que forme parte de una combinación única.
   * En la pantalla **[!UICONTROL Deduplication method]**, seleccione **[!UICONTROL Advanced parameters]** y marque la opción **[!UICONTROL Disable automatic filtering of 0 ID records]** para asegurarse de que no se excluyan los registros que tengan una clave principal igual a 0 (que deberían ser todos los registros de esta transición).

   ![](assets/import_template_example7.png)

1. Configure la actividad **[!UICONTROL Update data]** ubicada después de la actividad **[!UICONTROL Deduplication]** configurada anteriormente.

   * Seleccione **[!UICONTROL Insert]** como **[!UICONTROL Operation type]**, ya que la transición entrante solo contiene destinatarios que no están presentes en la base de datos.
   * En la sección **[!UICONTROL Record identification]** , seleccione **[!UICONTROL Directly using the targeting dimension]** y elija la dimensión **[!UICONTROL Recipients]** .
   * En la sección **[!UICONTROL Fields to update]**, indique los campos de la dimensión de destinatarios que desea actualizar con el valor de la columna correspondiente del archivo. Si los nombres de las columnas del archivo son idénticos o casi idénticos a los nombres de los campos de dimensión de los destinatarios, puede utilizar el botón de varita mágica para hacer coincidir automáticamente los diferentes campos.

      ![](assets/import_template_example8.png)

1. Después de la tercera transición de la actividad **[!UICONTROL Split]**, añada una actividad **[!UICONTROL Data extraction (file)]** y una actividad **[!UICONTROL File transfer]** si desea realizar un seguimiento de los datos que no se insertan en la base de datos. Configure las actividades para exportar la columna que necesite y para transferir el archivo en un servidor FTP o SFTP desde donde pueda recuperarlo.
1. Añada una actividad **[!UICONTROL End]** y guarde la plantilla de flujo de trabajo.

Ahora la plantilla se puede utilizar y está disponible para cada nuevo flujo de trabajo. A continuación, es necesario especificar el archivo que contiene los datos que se van a importar en la actividad **[!UICONTROL Data loading (file)]** .

![](assets/import_template_example9.png)

## Descompresión o desencriptado de un archivo antes de procesarlo {#unzipping-or-decrypting-a-file-before-processing}

### Acerca de las etapas de preprocesamiento {#about-pre-processing-stages}

Adobe Campaign permite importar archivos comprimidos o encriptados. Antes de que se puedan leer en una actividad [Data loading (file)](../../workflow/using/data-loading--file-.md), puede definir un procesamiento previo para descomprimir o desencriptar el archivo.

Para poder hacerlo:

1. Utilice el [Panel de control de Campaign](https://docs.adobe.com/content/help/es-ES/control-panel/using/instances-settings/gpg-keys-management.html#decrypting-data) para generar un par de claves pública y privada.

   >[!NOTE]
   >
   >Panel de control de Campaign está disponible para todos los clientes alojados en AWS (excepto para los clientes que alojan sus instancias de marketing on-Premise).

1. Si Adobe aloja la instalación de Adobe Campaign contáctese con atención al cliente de Adobe para que instalen las herramientas necesarias en el servidor.
1. Si la instalación de Adobe Campaign está in situ: instale la utilidad que desee utilizar (por ejemplo: GPG, GZIP) así como las claves necesarias (clave de cifrado) en el servidor de aplicaciones.

A continuación, puede utilizar los comandos de preprocesamiento deseados en los flujos de trabajo:

1. Añada y configure una actividad **[!UICONTROL File transfer]** en el flujo de trabajo.
1. Añada una actividad **[!UICONTROL Data loading (file)]** y defina el formato de archivo.
1. Marque la opción **[!UICONTROL Pre-process the file]**.
1. Especifique el comando de preprocesamiento que desee aplicar.
1. Añada otras actividades para administrar los datos que provengan del archivo.
1. Guarde y ejecute el flujo de trabajo.

A continuación se muestra un ejemplo en el caso de uso.

**Temas relacionados:**

* [Actividad de carga de datos (archivos)](../../workflow/using/data-loading--file-.md).
* [Comprimir o encriptar un archivo](../../workflow/using/how-to-use-workflow-data.md#zipping-or-encrypting-a-file).

### Caso de uso: importación de datos cifrados con una clave generada por el Panel de control de Campaign{#use-case-gpg-decrypt}

En este caso de uso, crearemos un flujo de trabajo para importar datos cifrados en un sistema externo utilizando una clave generada en el Panel de control de Campaign.

![](assets/do-not-localize/how-to-video.png) [Descubra esta función en vídeo](#video)

Los pasos para realizar este caso de uso son los siguientes:

1. Utilice el Panel de control de Campaign para generar un par de claves (pública/privada). Encontrará los pasos detallados en la documentación [del](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#decrypting-data) Panel de control de Campaign.

   * La clave pública se comparte con el sistema externo, que la utiliza para cifrar los datos que se enviarán a Campaign.
   * Campaign Classic utiliza la clave privada para descifrar los datos cifrados entrantes.

   ![](assets/gpg_generate.png)

1. En el sistema externo, utilice la clave pública descargada del Panel de control de Campaign para cifrar los datos que se van a importar a Campaign Classic.

1. En Campaign Classic, cree un flujo de trabajo para importar los datos cifrados y desencriptarlos con la clave privada que se ha instalado mediante el Panel de control de Campaign. Para ello, crearemos un flujo de trabajo de la siguiente manera:

   ![](assets/gpg_import_workflow.png)

   * **[!UICONTROL File transfer]** actividad: transfiere el archivo de un origen externo a Campaign Classic. En este ejemplo, queremos transferir el archivo desde un servidor SFTP.
   * **[!UICONTROL Data loading (file)]** actividad: carga los datos del archivo en la base de datos y los descifra utilizando la clave privada generada en el Panel de control de Campaign.

1. Abra la actividad **[!UICONTROL File transfer]** y especifique la cuenta externa desde la que desea importar el archivo .gpg cifrado.

   ![](assets/gpg_key_transfer.png)

   Los conceptos globales sobre cómo configurar la actividad están disponibles en [esta sección](../../workflow/using/file-transfer.md).

1. Abra la actividad **[!UICONTROL Data loading (file)]** y configúrela según sus necesidades. Los conceptos globales sobre cómo configurar la actividad están disponibles en [esta sección](../../workflow/using/data-loading--file-.md).

   Añada una fase de preprocesamiento a la actividad para descifrar los datos entrantes. Para ello, seleccione la opción **[!UICONTROL Pre-process the file]** y copie y pegue este comando de descifrado en el **[!UICONTROL Command]** campo:

   `gpg --batch --passphrase passphrase --decrypt <%=vars.filename%>`

   ![](assets/gpg_load.png)

   >[!CAUTION]
   >
   >En este ejemplo, utilizamos la frase de contraseña utilizada de forma predeterminada por Panel de control de Campaign, que es &quot;frase de contraseña&quot;.
   >
   >Si ya ha instalado las claves GPG en su instancia a través de una solicitud a Atención al cliente en el pasado, la frase de contraseña puede haber cambiado y ser diferente de la predeterminada.

1. Haga clic en **[!UICONTROL OK]** para confirmar esta configuración.

1. Ahora puede ejecutar el flujo de trabajo. Una vez ejecutada, puede registrar en los registros de flujo de trabajo que el descifrado se ha ejecutado y que los datos del archivo se han importado.

   ![](assets/gpg_run.png)

### Tutorial video {#video}

Este vídeo muestra cómo utilizar una clave GPG para descifrar datos.

>[!VIDEO](https://video.tv.adobe.com/v/36482?quality=12)

Hay disponibles más vídeos de procedimientos para Campaign Classic [aquí](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=es).
