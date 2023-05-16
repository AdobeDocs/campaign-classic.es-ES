---
product: campaign
title: Configuración del árbol de navegación del explorador de Campaign
description: Obtenga información sobre cómo configurar el árbol de navegación del explorador de Campaign
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: c7ae7240-0c12-4420-bbb3-4268c9ade3e7
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1196'
ht-degree: 1%

---

# Configuración del árbol de navegación del explorador de Campaign{#configuration}

Como usuario experto, puede añadir carpetas en el árbol del explorador y personalizarlo.

Obtenga más información sobre el explorador de Campaign y la jerarquía de navegación [en esta sección](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy).

Los tipos de carpetas utilizados por la lista de navegación se describen en un documento XML que sigue la gramática de la variable **xtk:navtree** esquema.

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

El documento XML contiene la variable **`<navtree>`** elemento raíz con la variable **name** y **namespace** atributos para especificar el nombre del documento y el área de nombres. El nombre y el área de nombres constituyen la clave de identificación del documento.

Los comandos globales de la aplicación se declaran en el documento desde el **`<commands>`** elemento.

La declaración de tipos de archivo se estructura en el documento con los siguientes elementos: **`<model>`** y **`<nodemodel>`**.

## Comandos globales {#global-commands}

Un comando global permite iniciar una acción. Esta acción puede ser un formulario de entrada o una llamada SOAP.

Los comandos globales son accesibles desde el **[!UICONTROL Tools]** para abrir el Navegador.

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

La descripción de un comando global se introduce en la variable **`<command>`** con las siguientes propiedades:

* **name**: nombre interno del comando: debe introducirse el nombre y ser único
* **label**: etiqueta del comando.
* **desc**: descripción visible desde la barra de estado de la pantalla principal.
* **formulario**: formulario que se va a iniciar: el valor que se va a introducir es la clave de identificación del formulario de entrada (p. ej. &quot;cus:recipient&quot;)
* **derechos**: lista de derechos asignados (separados por una coma) que permiten el acceso a este comando. Se puede acceder a la lista de derechos disponibles desde la **[!UICONTROL Administration > Access management > Named rights]** carpeta.
* **pointerLabel**: muestra un cuadro de confirmación antes de ejecutar el comando.

A **`<command>`** el elemento puede contener **`<command>`** subelementos. En este caso, el elemento principal permite mostrar un submenú compuesto por estos elementos secundarios.

Los comandos se muestran en el mismo orden en que se declaran en el documento XML.

Un separador de comandos permite mostrar una barra de separación entre los comandos. Se identifica mediante la variable **&#39;-&#39;** valor contenido en la etiqueta de comando.

La presencia opcional del **`<soapcall>`** con sus parámetros de entrada define la llamada de un método SOAP que se va a ejecutar. Para obtener más información sobre la API de SOAP, consulte [Documentación de JSAPI de Campaign](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=es).

El contexto del formulario se puede actualizar en la inicialización desde el **`<enter>`** etiqueta. Para obtener más información sobre esta etiqueta, consulte la documentación sobre los formularios de entrada.

**Ejemplo**:

* Declaración de un comando global para iniciar el formulario &quot;xtk:import&quot;:

   ```
   <command desc="Start the data import wizard" form="xtk:import" label="&amp;Data import..." name="import" rights="import,recipientImport"/>
   ```

   La presencia de **&amp;** en la etiqueta de comando.

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

La declaración de tipo de carpeta debe introducirse en una **`<model>`** elemento. Este elemento permite definir una organización jerárquica visible desde el **[!UICONTROL Add new folder]** para abrir el Navegador. A **`<model>`** El elemento debe contener **`<nodemodel>`** elementos y otros **`<model>`** elementos.

La variable **name** y **label** los atributos rellenan el nombre interno del elemento y la etiqueta mostrada en la variable **[!UICONTROL Add new folder]** para abrir el Navegador.

La variable **`<nodemodel>`** contiene la descripción del tipo de carpeta con las siguientes propiedades:

* **name**: nombre interno
* **label**: etiqueta utilizada en **[!UICONTROL Add new folder]** y como etiqueta predeterminada al insertar una carpeta.
* **img**: imagen predeterminada al insertar una carpeta.
* **hiddenCommands**: lista de comandos (separados por una coma) que se van a ocultar. Valores posibles: &quot;adbnew&quot;, &quot;adbsave&quot;, &quot;adbcancel&quot; y &quot;adbdup&quot;.
* **newFolderShortCuts**: lista de accesos directos en los modelos (**`<nodemodel>`** separada por una coma) en la creación de carpetas.
* **insertRight**, **editRight**, **deleteRight**: derechos para insertar, editar y eliminar carpetas.

La variable **`<view>`** debajo de **`<nodemodel>`** contiene la configuración de la lista asociada a la vista. El esquema de la lista se introduce en la variable **esquema** del **`<view>`** elemento.

Para editar los registros de la lista, se utiliza implícitamente el formulario de entrada con el mismo nombre que el esquema de lista. La variable **type** en la variable **`<view>`** afecta a la visualización del formulario. Los valores posibles son:

* **listdet**: muestra el formulario en la parte inferior de la lista.
* **list**: muestra la lista sola. El formulario se inicia haciendo doble clic o a través de la opción &quot;Abrir&quot; del menú al seleccionar la lista.
* **formulario**: muestra un formulario de solo lectura.
* **editForm**: muestra un formulario en modo de edición.

>[!NOTE]
>
>El nombre del formulario de entrada se puede sobrecargar introduciendo la variable **formulario** en la variable **`<view>`** elemento.

La configuración predeterminada de las columnas de la lista se introduce mediante la variable **`<columns>`** elemento. Se declara una columna en una **`<node>`** que contiene el **xpath** con el campo al que se hace referencia en su esquema como su valor.

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

El menú de inserción de la carpeta correspondiente:

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

Un comando de acceso directo permite iniciar una acción al seleccionar la lista. La acción puede ser un formulario de entrada o una llamada SOAP.

Se puede acceder a los comandos desde la **[!UICONTROL Action]** de la lista o el botón de menú asociado.

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

La descripción de un comando se introduce en la variable **`<command>`** con las siguientes propiedades:

* **name**: nombre interno del comando: el nombre debe introducirse y ser único.
* **label**: etiqueta del comando.
* **desc**: descripción visible desde la barra de estado de la pantalla principal.
* **formulario**: formulario que se va a iniciar: el valor que se va a introducir es la clave de identificación del formulario de entrada (p. ej. &quot;cus:recipient&quot;).
* **derechos**: lista de derechos asignados (separados por una coma) que permiten el acceso a este comando. Se puede acceder a la lista de derechos disponibles desde la **[!UICONTROL Administration > Access management > Named rights]** carpeta.
* **pointerLabel**: muestra un cuadro de confirmación antes de ejecutar el comando
* **monoSelection**: fuerza la selección mono (selección múltiple de forma predeterminada).
* **refreshView**: fuerza la recarga de la lista después de la ejecución del comando.
* **enabledIf**: activa el comando en función de la expresión introducida.
* **img**: introduce una imagen que permite acceder al comando desde la barra de herramientas de la lista.

A **`<command>`** el elemento puede contener **`<command>`** subelementos. En este caso, el elemento principal permite mostrar un submenú compuesto por estos elementos secundarios.

Los comandos se muestran en el mismo orden en que se declaran en el documento XML.

Un separador de comandos permite mostrar una barra de separación entre los comandos. Se identifica mediante la variable **&#39;-&#39;** valor contenido en la etiqueta de comando.

La presencia opcional del **`<soapcall>`** con sus parámetros de entrada define la llamada de un método SOAP que se va a ejecutar. Para obtener más información sobre las API de SOAP, consulte [Documentación de JSAPI de Campaign](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=es).

El contexto del formulario se puede actualizar en la inicialización a través del **`<enter>`** etiqueta. Para obtener más información sobre esta etiqueta, consulte la documentación del formulario de entrada.

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

1. La carpeta es una vista: la lista muestra todos los registros asociados al esquema, con la posibilidad de que el sistema filtre introducidos en las propiedades de la carpeta.
1. La carpeta está vinculada: los registros de la lista se filtran implícitamente en el vínculo de carpeta.

Para una carpeta vinculada, la variable **folderLink** en la variable **`<nodemodel>`** debe rellenarse. Este atributo contiene el nombre del vínculo en la carpeta configurada en el esquema de datos.

Ejemplo de declaración de una carpeta vinculada en el esquema de datos:

```
<element default="DefaultFolder('nmsFolder', [@_folder-id])" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="define" revLabel="Recipients" target="xtk:folder" type="link"/>
```

La configuración de la variable **`<nodemodel>`** en el vínculo de la carpeta denominada &quot;carpeta&quot; es el siguiente:

```
<nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
  img="nms:folder.png" insertRight="folderInsert" label="Recipients" name="nmsFolder">
...
</nodeModel>
```
