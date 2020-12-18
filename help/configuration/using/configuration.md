---
solution: Campaign Classic
product: campaign
title: Configuración
description: Configuración
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
translation-type: tm+mt
source-git-commit: 6e0741d13aa954e81fe6416663399ffd1a81012f
workflow-type: tm+mt
source-wordcount: '1161'
ht-degree: 2%

---


# Configuración{#configuration}

Los tipos de carpetas que utiliza la lista de navegación se describen en un documento XML que obedece la gramática del esquema **xtk:navtree**.

El documento XML está estructurado de la siguiente manera:

```
<navtree name="name" namespace="name_space">
  <!-- Global commands -->
  <commands>
      ...
  </commands>
  
  <!-- Structured space for adding a folder -->
  <model name="<name>" label="<Label>">
    <!-- Folder type -->
    <nodeModel>
      ...
    </nodeModel>
<model name="<name>" label="<Sub model>">
      ...
    </model>
  </model> 
</navtree>
```

El documento XML contiene el elemento raíz **`<navtree>`** con los atributos **name** y **Área de nombres** para especificar el nombre y la Área de nombres del documento. El nombre y la Área de nombres constituyen la clave de identificación del documento.

Los comandos globales de la aplicación se declaran en el documento desde el elemento **`<commands>`**.

La declaración de tipos de archivo está estructurada en el documento con los siguientes elementos: **`<model>`** y **`<nodemodel>`**.

## Comandos globales {#global-commands}

Un comando global permite iniciar una acción. Esta acción puede ser un formulario de entrada o una llamada SOAP.

Se puede acceder a los comandos globales desde el menú principal **[!UICONTROL Tools]**.

La estructura de configuración de comandos es la siguiente:

```
<commands>
  <!-- Description of a command -->
  <command name="<name>" label="<label>" desc="<Description>" form="<form>" rights="<rights>">
    <soapCall name="<name>" service="<schema>">
      <param type="<type>" exprIn="<xpath>"/>  
        ...
    </soapCall>
    <enter>
      ...
    </enter>
  </command>
  <!-- Separator -->
  <command label="-" name="<name>"/>
  <!-- Command structure -->
  <command name="<name>" label="<Label>">
    <command...
  </command>
</commands>
```

La descripción de un comando global se introduce en el elemento **`<command>`** con las siguientes propiedades:

* **name**: nombre interno del comando: debe introducirse el nombre y ser único
* **label**: del comando.
* **desc**: descripción visible desde la barra de estado de la pantalla principal.
* **formulario**: formulario que se va a iniciar: el valor que se debe introducir es la clave de identificación del formulario de entrada (p. ej. &quot;cus:destinatario&quot;)
* **derechos**: lista de derechos asignados (separados por coma) que permiten el acceso a este comando. Se puede acceder a la lista de derechos disponibles desde la carpeta **[!UICONTROL Administration > Access management > Named rights]**.
* **promptLabel**: muestra un cuadro de confirmación antes de ejecutar el comando.

Un elemento **`<command>`** puede contener subelementos **`<command>`**. En este caso, el elemento principal permite mostrar un submenú compuesto por estos elementos secundarios.

Los comandos se muestran en el mismo orden en que se declaran en el documento XML.

Un separador de comandos permite mostrar una barra de separación entre comandos. Se identifica mediante el valor **&#39;-&#39;** contenido en la etiqueta de comando.

La presencia opcional de la etiqueta **`<soapcall>`** con sus parámetros de entrada define la llamada de un método SOAP que se va a ejecutar. Para obtener más información sobre la API de SOAP, consulte la [documentación de JSAPI de Campaña](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html).

El contexto del formulario se puede actualizar al inicializarlo desde la etiqueta **`<enter>`**. Para obtener más información sobre esta etiqueta, consulte la documentación sobre los formularios de entrada.

**Ejemplo**:

* Declaración de un comando global para iniciar el formulario &quot;xtk:import&quot;:

   ```
   <command desc="Start the data import wizard" form="xtk:import" label="&amp;Data import..." name="import" rights="import,recipientImport"/>
   ```

   Se declara un método abreviado de teclado en el carácter &#39;I&#39; mediante la presencia de **&amp;** en la etiqueta de comando.

* Ejemplo de un submenú con un separador:

   ![](assets/d_ncs_integration_navigation_exemple1.png)

   ```
   <command label="Administration" name="admin">
     <command name="cmd1" label="Example 1" form="cus:example1"/>
     <command name="sep" label="-"/>
     <command name="cmd1" label="Example 2" form="cus:example2">
       <enter>
         <set xpath="@type" expr="1"/>
       </enter>
     </command>
   </command>
   ```

* Ejecución de un método SOAP:

   ```
   <command name="cmd3" label="Example 3" promptLabel="Do you really want to execute the command?">
     <soapCall name="Execute" service="xtk:sql"/>
   </command>
   ```

## Tipo de carpeta {#folder-type}

Un tipo de carpeta permite dar acceso a los datos de un esquema. La vista asociada a la carpeta consta de una lista y un formulario de entrada.

La estructura de configuración del tipo de carpeta es la siguiente:

```
<!-- Structured location to add the folder -->
<model name="name" label="Labelled">
  <!-- Type of folder -->
  <nodeModel name="<name>" label="<Labelled>" img="<image>">
    <view name="<name>" schema="<schema>" type="<listdet|list|form|editForm>">
      <columns>
        <node xpath="<field1>"/>
        ...
    </columns>
    </view> 
  </nodeModel>
  <model name="<name>" label="<Sous modèle>">
    ...
  </model>
</model>
```

La declaración de tipo de carpeta debe introducirse en un elemento **`<model>`**. Este elemento permite definir una organización jerárquica visible desde el menú **[!UICONTROL Add new folder]**. Un elemento **`<model>`** debe contener **`<nodemodel>`** elementos y otros **`<model>`** elementos.

Los atributos **name** y **label** rellenan el nombre interno del elemento y la etiqueta mostrada en el menú **[!UICONTROL Add new folder]**.

El elemento **`<nodemodel>`** contiene la descripción del tipo de carpeta con las siguientes propiedades:

* **name**: nombre interno
* **label**: se utiliza en el  **[!UICONTROL Add new folder]** menú y como etiqueta predeterminada al insertar una carpeta.
* **img**: imagen predeterminada al insertar una carpeta.
* **hiddenCommands**: lista de comandos (separados por coma) que se van a enmascarar. Valores posibles: &quot;adbnew&quot;, &quot;adbsave&quot;, &quot;adbcancel&quot; y &quot;adbdup&quot;.
* **newFolderShortCuts**: lista de accesos directos en modelos (**`<nodemodel>`** separados por coma) en la creación de carpetas.
* **insertRight**,  **editRight**,  **deleteRight**: derechos para insertar, editar y eliminar carpetas.

El elemento **`<view>`** del elemento **`<nodemodel>`** contiene la configuración de la lista asociada con la vista. El esquema de la lista se introduce en el atributo **esquema** del elemento **`<view>`**.

Para editar los registros de la lista, se utiliza implícitamente el formulario de entrada con el mismo nombre que el esquema de lista. El atributo **type** del elemento **`<view>`** afecta a la visualización del formulario. Los valores posibles son:

* **listdet**: muestra el formulario en la parte inferior de la lista.
* **lista**: muestra la lista sola. El formulario se inicia haciendo clic con el doble o mediante la opción &quot;Abrir&quot; del menú al seleccionar la lista.
* **formulario**: muestra un formulario de solo lectura.
* **editForm**: muestra un formulario en modo de edición.

>[!NOTE]
>
>El nombre del formulario de entrada se puede sobrecargar introduciendo el atributo **form** en el elemento **`<view>`**.

La configuración predeterminada de las columnas de lista se introduce mediante el elemento **`<columns>`**. Se declara una columna en un elemento **`<node>`** que contiene el atributo **xpath** con el campo al que se hará referencia en su esquema como su valor.

**Ejemplo**: declaración de un tipo de carpeta en el esquema &quot;nms:destinatario&quot;.

```
<model label="Profiles and targets" name="nmsProfiles">
  <nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
             img="nms:folder.png" insertRight="folderInsert" label="Recipients"
             name="nmsFolder">
    <view name="listdet" schema="nms:recipient" type="listdet">
      <columns>
        <node xpath="@firstName"/>
        <node xpath="@lastName"/>
        <node xpath="@email"/>
        <node xpath="@account"/>
      </columns>
    </view>
  </nodeModel>
  <nodeModel name="nmsGroup" label="Groups"...
</model>
```

El menú de inserción de carpetas correspondiente:

![](assets/d_ncs_integration_navigation_exemple2.png)

El filtrado y la ordenación se pueden aplicar al cargar la lista:

```
<view name="listdet" schema="nms:recipient" type="listdet">
  <columns>
    ...
  </columns>

  <orderBy>
    <node expr="@lastName" desc="true"/>
</orderBy>
  <sysFilter>
    <condition expr="@type = 1"/>
  </sysFilter>
</view>  
```

### Comandos de acceso directo {#shortcut-commands}

Un comando de método abreviado permite iniciar una acción al seleccionar la lista. La acción puede ser un formulario de entrada o una llamada SOAP.

Se puede acceder a los comandos desde el menú **[!UICONTROL Action]** de la lista o desde el botón de menú asociado.

La estructura de configuración de comandos es la siguiente:

```
<nodeModel...
  ...
  <command name="<name>" label="<label>" desc="<Description>" form="<form>" rights="<rights>">
    <soapCall name="<name>" service="<schema>">
      <param type="<type>" exprIn="<xpath>"/>  
        ...
    </soapCall>
    <enter>
      ...
    </enter>
  </command>
</nodeModel>
```

La descripción de un comando se introduce en el elemento **`<command>`** con las siguientes propiedades:

* **name**: nombre interno del comando: el nombre debe escribirse y ser único.
* **label**: del comando.
* **desc**: descripción visible desde la barra de estado de la pantalla principal.
* **formulario**: formulario que se va a iniciar: el valor que se debe introducir es la clave de identificación del formulario de entrada (p. ej. &quot;cus:destinatario&quot;).
* **derechos**: lista de derechos asignados (separados por coma) que permiten el acceso a este comando. Se puede acceder a la lista de derechos disponibles desde la carpeta **[!UICONTROL Administration > Access management > Named rights]**.
* **promptLabel**: muestra un cuadro de confirmación antes de ejecutar el comando
* **monoSelection**: fuerza la selección mono (selección múltiple de forma predeterminada).
* **refreshView**: fuerza la recarga de la lista después de ejecutar el comando.
* **enabledIf**: activa el comando en función de la expresión introducida.
* **img**: introduce una imagen que permite acceder al comando desde la barra de herramientas de lista.

Un elemento **`<command>`** puede contener subelementos **`<command>`**. En este caso, el elemento principal permite mostrar un submenú compuesto por estos elementos secundarios.

Los comandos se muestran en el mismo orden en que se declaran en el documento XML.

Un separador de comandos permite mostrar una barra de separación entre comandos. Se identifica mediante el valor **&#39;-&#39;** contenido en la etiqueta de comando.

La presencia opcional de la etiqueta **`<soapcall>`** con sus parámetros de entrada define la llamada de un método SOAP que se va a ejecutar. Para obtener más información sobre las API de SOAP, consulte [documentación de JSAPI de Campaña](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html).

El contexto del formulario se puede actualizar al inicializarlo mediante la etiqueta **`<enter>`**. Para obtener más información sobre esta etiqueta, consulte la documentación del formulario de entrada.

**Ejemplo**:

```
<command desc="Cancel execution of the job" enabledIf="EV(@status, 'running')"
         img="nms:difstop.bmp" label="Cancel..." name="cancelJob" 
         promptLabel="Do you really want to cancel this job?" refreshView="true">
  <soapCall name="Cancel" service="xtk:jobInterface"/>
</command>
<command label="-" name="sep1"/>
<command desc="Execute selected template" form="cus:form" lmonoSelection="true" name="executeModel"
         rights="import,export,aggregate">
  <enter>
    <set expr="0" xpath="@status"/>
  </enter>
</command>
```

### Carpeta vinculada {#linked-folder}

Existen dos tipos de operaciones de administración de carpetas:

1. La carpeta es una vista: la lista muestra todos los registros asociados con el esquema, con la posibilidad de que el sistema filtre los datos introducidos en las propiedades de la carpeta.
1. La carpeta está vinculada: los registros de la lista se filtran implícitamente en el vínculo de la carpeta.

Para una carpeta vinculada, debe rellenarse el atributo **folderLink** del elemento **`<nodemodel>`**. Este atributo contiene el nombre del vínculo de la carpeta configurada en el esquema de datos.

Ejemplo de declaración de una carpeta vinculada en el esquema de datos:

```
<element default="DefaultFolder('nmsFolder')" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="own" revLabel="Recipients" target="xtk:folder" type="link"/>
```

La configuración de **`<nodemodel>`** en el vínculo de la carpeta denominada &quot;folder&quot; es la siguiente:

```
<nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
  img="nms:folder.png" insertRight="folderInsert" label="Recipients" name="nmsFolder">
...
</nodeModel>
```

