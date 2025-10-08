---
product: campaign
title: Configuración del árbol de navegación de Campaign Explorer
feature: Application Settings
description: Obtenga información sobre cómo configurar el árbol de navegación del explorador de Campaign
role: Data Engineer, Developer
exl-id: c7ae7240-0c12-4420-bbb3-4268c9ade3e7
source-git-commit: d56038fc8baf766667d89bb73747c20ec041124c
workflow-type: tm+mt
source-wordcount: '1183'
ht-degree: 0%

---

# Configuración del árbol de navegación de Campaign Explorer{#configuration}

Como usuario experto, puede agregar carpetas en el árbol del explorador y personalizarlo.

Obtenga más información acerca de la interfaz de usuario de Campaign en [Documentación de Adobe Campaign v8 (consola)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/new/campaign-ui){target=_blank}.

Los tipos de carpetas usados por la lista de navegación se describen en un documento XML que obedece a la gramática del esquema **xtk:navtree**.

El documento XML se estructura de la siguiente manera:

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

El documento XML contiene el elemento raíz **`<navtree>`** con los atributos **name** y **namespace** para especificar el nombre y el área de nombres del documento. El nombre y el área de nombres conforman la clave de identificación del documento.

Los comandos globales de la aplicación se declaran en el documento a partir del elemento **`<commands>`**.

La declaración de tipos de archivo está estructurada en el documento con los siguientes elementos: **`<model>`** y **`<nodemodel>`**.

## Comandos globales {#global-commands}

Un comando global permite iniciar una acción. Esta acción puede ser un formulario de entrada o una llamada de SOAP.

Los comandos globales son accesibles desde el menú principal **[!UICONTROL Tools]**.

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

La descripción de un comando global se especifica en el elemento **`<command>`** con las siguientes propiedades:

* **name**: nombre interno del comando: el nombre debe ser especificado y único
* **label**: etiqueta del comando.
* **desc**: descripción visible desde la barra de estado de la pantalla principal.
* **formulario**: formulario que se va a iniciar: el valor que se va a escribir es la clave de identificación del formulario de entrada (por ejemplo: &quot;cus:recipient&quot;)
* **rights**: lista de derechos asignados (separados por una coma) que permiten el acceso a este comando. Se puede acceder a la lista de derechos disponibles desde la carpeta **[!UICONTROL Administration > Access management > Named rights]**.
* **promptLabel**: muestra un cuadro de confirmación antes de la ejecución del comando.

Un elemento **`<command>`** puede contener **`<command>`** subelementos. En este caso, el elemento principal permite mostrar un submenú formado por estos elementos secundarios.

Los comandos se muestran en el mismo orden en que se declaran en el documento XML.

Un separador de comandos permite mostrar una barra de separación entre los comandos. Se identifica con el valor **&#39;-&#39;** contenido en la etiqueta de comando.

La presencia opcional de la etiqueta **`<soapcall>`** con sus parámetros de entrada define la llamada de un método SOAP que se va a ejecutar. Para obtener más información sobre la API de SOAP, consulte [Documentación de Campaign JSAPI](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=es).

El contexto del formulario se puede actualizar en la inicialización desde la etiqueta **`<enter>`**. Para obtener más información sobre esta etiqueta, consulte la documentación sobre los formularios de entrada.

**Ejemplo**:

* Declaración de un comando global para iniciar el formulario &quot;xtk:import&quot;:

  ```
  <command desc="Start the data import assistant" form="xtk:import" label="&amp;Data import..." name="import" rights="import,recipientImport"/>
  ```

  Se declara un método abreviado de teclado en el carácter &#39;I&#39; mediante la presencia de **&amp;** en la etiqueta de comando.

* Ejemplo de un submenú con separador:

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

Un tipo de carpeta permite dar acceso a los datos de un esquema. La vista asociada con la carpeta consta de una lista y un formulario de entrada.

La estructura de configuración de tipo de carpeta es la siguiente:

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

La declaración de tipo de carpeta debe especificarse en un elemento **`<model>`**. Este elemento le permite definir una organización jerárquica visible desde el menú **[!UICONTROL Add new folder]**. Un elemento **`<model>`** debe contener **`<nodemodel>`** elementos y otros **`<model>`** elementos.

Los atributos **name** y **label** rellenan el nombre interno del elemento y la etiqueta mostrada en el menú **[!UICONTROL Add new folder]**.

El elemento **`<nodemodel>`** contiene la descripción del tipo de carpeta con las siguientes propiedades:

* **nombre**: nombre interno
* **label**: etiqueta utilizada en el menú **[!UICONTROL Add new folder]** y como etiqueta predeterminada al insertar una carpeta.
* **img**: imagen predeterminada al insertar la carpeta.
* **hiddenCommands**: lista de comandos (separados por una coma) que se van a ocultar. Valores posibles: &quot;adbnew&quot;, &quot;adbsave&quot;, &quot;adbcancel&quot; y &quot;adbdup&quot;.
* **newFolderShortCuts**: lista de métodos abreviados de los modelos (**`<nodemodel>`** separados por una coma) en la creación de carpetas.
* **insertRight**, **editRight**, **deleteRight**: derechos para insertar, editar y eliminar carpetas.

El elemento **`<view>`** bajo el elemento **`<nodemodel>`** contiene la configuración de la lista asociada con la vista. El esquema de la lista se ha especificado en el atributo **schema** del elemento **`<view>`**.

Para editar los registros de la lista, se utiliza implícitamente el formulario de entrada con el mismo nombre que el esquema de lista. El atributo **type** del elemento **`<view>`** afecta a la visualización del formulario. Los valores posibles son:

* **listdet**: muestra el formulario al final de la lista.
* **list**: muestra solo la lista. El formulario se inicia haciendo doble clic o a través de la opción &quot;Abrir&quot; en el menú al seleccionar la lista.
* **formulario**: muestra un formulario de solo lectura.
* **editForm**: muestra un formulario en modo de edición.

>[!NOTE]
>
>El nombre del formulario de entrada se puede sobrecargar al escribir el atributo **form** en el elemento **`<view>`**.

La configuración predeterminada de las columnas de la lista se especifica mediante el elemento **`<columns>`**. Se declara una columna en un elemento **`<node>`** que contiene el atributo **xpath** con el campo al que se hará referencia en su esquema como valor.

**Ejemplo**: declaración de un tipo de carpeta en el esquema &quot;nms:recipient&quot;.

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

Menú de inserción de la carpeta correspondiente:

![](assets/d_ncs_integration_navigation_exemple2.png)

El filtrado y la ordenación se pueden aplicar cuando se carga la lista:

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

Un comando de acceso directo permite iniciar una acción al seleccionar la lista. La acción puede ser un formulario de entrada o una llamada de SOAP.

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

La descripción de un comando se especifica en el elemento **`<command>`** con las siguientes propiedades:

* **name**: nombre interno del comando: el nombre debe ser especificado y único.
* **label**: etiqueta del comando.
* **desc**: descripción visible desde la barra de estado de la pantalla principal.
* **formulario**: formulario que se va a iniciar: el valor que se va a escribir es la clave de identificación del formulario de entrada (por ejemplo: &quot;cus:recipient&quot;).
* **rights**: lista de derechos asignados (separados por una coma) que permiten el acceso a este comando. Se puede acceder a la lista de derechos disponibles desde la carpeta **[!UICONTROL Administration > Access management > Named rights]**.
* **promptLabel**: muestra un cuadro de confirmación antes de la ejecución del comando
* **monoSelection**: fuerza la selección mono (selección múltiple de forma predeterminada).
* **refreshView**: fuerza la recarga de la lista después de la ejecución del comando.
* **enabledIf**: activa el comando en función de la expresión introducida.
* **img**: introduce una imagen que permite el acceso al comando desde la barra de herramientas de la lista.

Un elemento **`<command>`** puede contener **`<command>`** subelementos. En este caso, el elemento principal permite mostrar un submenú formado por estos elementos secundarios.

Los comandos se muestran en el mismo orden en que se declaran en el documento XML.

Un separador de comandos permite mostrar una barra de separación entre los comandos. Se identifica con el valor **&#39;-&#39;** contenido en la etiqueta de comando.

La presencia opcional de la etiqueta **`<soapcall>`** con sus parámetros de entrada define la llamada de un método SOAP que se va a ejecutar. Para obtener más información sobre las API de SOAP, consulte [Documentación de Campaign JSAPI](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=es).

El contexto del formulario se puede actualizar en la inicialización mediante la etiqueta **`<enter>`**. Para obtener más información sobre esta etiqueta, consulte la documentación del formulario de entrada.

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

1. La carpeta es una vista: la lista muestra todos los registros asociados al esquema, con la posibilidad de filtrar el sistema introducidos en las propiedades de la carpeta.
1. La carpeta está vinculada: los registros de la lista se filtran implícitamente en el vínculo de carpeta.

Para una carpeta vinculada, se debe rellenar el atributo **folderLink** en el elemento **`<nodemodel>`**. Este atributo contiene el nombre del vínculo en la carpeta configurada en el esquema de datos.

Ejemplo de declaración de una carpeta vinculada en el esquema de datos:

```
<element default="DefaultFolder('nmsFolder', [@_folder-id])" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="define" revLabel="Recipients" target="xtk:folder" type="link"/>
```

La configuración del **`<nodemodel>`** en el vínculo de la carpeta denominada &quot;folder&quot; es la siguiente:

```
<nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
  img="nms:folder.png" insertRight="folderInsert" label="Recipients" name="nmsFolder">
...
</nodeModel>
```
