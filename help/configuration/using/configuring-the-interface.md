---
solution: Campaign Classic
product: campaign
title: Configuración de la interfaz
description: Configuración de la interfaz
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 4%

---


# Configuración de la interfaz{#configuring-the-interface}

Para realizar vistas y diálogos con la nueva tabla de destinatario en la interfaz de Adobe Campaign, siga los pasos siguientes:

* Cree un nuevo formulario para editar el contenido de la nueva tabla de destinatario.
* Escriba un nuevo tipo en la carpeta del árbol del explorador.
* Cree una nueva aplicación web para acceder a la tabla personalizada mediante la página de inicio de Adobe Campaign.

Adobe Campaign utiliza una variable global &quot;Nms_DefaultRcpSchema&quot; para dialogar con la base de datos de destinatario predeterminada (nms:destinatario). Por lo tanto, es necesario modificar esta variable.

1. Vaya al nodo **[!UICONTROL Administration>Platform>Options]** del explorador.
1. Cambie el valor de la variable **Nms_DefaultRcpSchema** con el nombre del esquema que coincide con la tabla de destinatario externo (en este caso: cus:individual).
1. Guarde los cambios.

## Creación de un nuevo formulario {#creating-a-new-form-}

La creación de un nuevo formulario le permitirá realizar vistas y editar los datos de la tabla de destinatario externo.

>[!IMPORTANT]
>
>El nombre del formulario debe ser idéntico al nombre del esquema al que se refiere.

1. Vaya al nodo **Administración > Configuración > Formularios de entrada** del explorador.
1. Cree un nuevo archivo **xtk:form** tipo **form**.
1. Describa todos los controles y campos que necesite en función de la plantilla de tabla.

   >[!NOTE]
   >
   >Para obtener más información acerca de los archivos de tipo **formulario**, consulte [esta página](../../configuration/using/identifying-a-form.md).

   En nuestro ejemplo actual, el archivo **form** debe basarse en el esquema **cus:individual** y, por lo tanto, tener la siguiente presentación:

   ```
   <container colspan="2">
       <input xpath="@id"/>
       <static type="separator"/>
   </container>
   <container colcount="2">
       <input xpath="@lastName"/>
       <input xpath="@firstName"/>
       <input xpath="@email"/>
       <input xpath="@mobile"/>
   </container> 
   ```

1. Guarde la creación.

## Creación de un nuevo tipo de carpeta en la jerarquía de navegación {#creating-a-new-type-of-folder-in-the-navigation-hierarchy}

1. Vaya al nodo **[!UICONTROL Administration>Configuration>Navigation hierarchies]**.
1. Cree un nuevo documento **xtk:navtree** tipo **navtree**.
1. Describa todos los controles y campos que necesite en función de la plantilla de tabla.

   >[!NOTE]
   >
   >Para obtener más información sobre los archivos de tipo **navtree**, consulte [esta página](../../configuration/using/about-navigation-hierarchy.md).

   En el ejemplo actual, el archivo **navtree** debe basarse en el esquema **cus:individual** y, por lo tanto, tener la siguiente forma:

   ```
    <model name="root">
       <nodeModel img="nms:usergrp.png" label="My recipient table" name="cusindividual">
         <view name="listdet" schema="cus:individual" type="listdet">
           <columns>
             <node xpath="@id"/>
             <node xpath="@lastName"/>
             <node xpath="@firstName"/>
             <node xpath="@email"/>
             <node xpath="@mobile"/>
           </columns>
         </view>
       </nodeModel>
   </model>
   ```

1. Guarde la creación.

