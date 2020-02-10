---
title: Configuración de la interfaz
seo-title: Configuración de la interfaz
description: Configuración de la interfaz
seo-description: null
page-status-flag: never-activated
uuid: 101ba02f-da43-4dcc-b9ff-6e5ca848fc5d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: 8fb9ff23-17a7-4425-9195-738d6fd914dc
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Configuración de la interfaz{#configuring-the-interface}

Para ver y dialogar con la nueva tabla de destinatarios en la interfaz de Adobe Campaign, siga los pasos siguientes:

* Cree un nuevo formulario para editar el contenido de la nueva tabla de destinatarios.
* Escriba un nuevo tipo en la carpeta del árbol del explorador.
* Cree una nueva aplicación web para acceder a la tabla personalizada a través de la página de inicio de Adobe Campaign.

Adobe Campaign utiliza una variable global &quot;Nms_DefaultRcpSchema&quot; para dialogar con la base de datos de destinatarios predeterminada (nms:Recipiente). Por lo tanto, es necesario modificar esta variable.

1. Vaya al **[!UICONTROL Administration>Platform>Options]** nodo del explorador.
1. Cambie el valor de la variable **Nms_DefaultRcpSchema** con el nombre del esquema que coincide con la tabla del destinatario externo (en este caso: cus:individual).
1. Guarde los cambios.

## Creating a new form {#creating-a-new-form-}

La creación de un nuevo formulario le permitirá ver y editar los datos de la tabla de destinatarios externos.

>[!CAUTION]
>
>El nombre del formulario debe ser idéntico al nombre del esquema al que se refiere.

1. Vaya al nodo **Administración > Configuración > Formularios** de entrada del explorador.
1. Cree un nuevo archivo de **formulario** xtk:form **** .
1. Describa todos los controles y campos que necesite en función de la plantilla de tabla.

   >[!NOTE]
   >
   >Para obtener más información sobre los archivos de tipo de **formulario** , consulte [esta página](../../configuration/using/identifying-a-form.md).

   En el ejemplo actual, el archivo de **formulario** debe basarse en el esquema **cus:individual** y, por tanto, tener la siguiente presentación:

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

1. Vaya al **[!UICONTROL Administration>Configuration>Navigation hierarchies]** nodo.
1. Cree un nuevo documento **xtk:navtree** de tipo **navtree** .
1. Describa todos los controles y campos que necesite en función de la plantilla de tabla.

   >[!NOTE]
   >
   >Para obtener más información sobre los archivos **navtree** , consulte [esta página](../../configuration/using/about-navigation-hierarchy.md).

   En el ejemplo actual, el archivo **navtree** debe basarse en el esquema **cus:individual** y, por lo tanto, tener el siguiente formato:

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

