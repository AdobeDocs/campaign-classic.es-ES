---
product: campaign
title: Configuración de la interfaz
description: Obtenga información sobre cómo configurar la interfaz de Campaign
feature: Application Settings
role: Data Engineer, Developer
badge-v8: label="También se aplica a la versión 8" type="Positive" tooltip="También se aplica a Campaign v8"
exl-id: 9f50f258-845e-4895-b1ef-b73744dea326
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 3%

---

# Configuración de la interfaz{#configuring-the-interface}

Para ver y dialogar con la nueva tabla de destinatarios en la interfaz de Adobe Campaign, aplique los siguientes pasos:

* Cree un nuevo formulario para editar el contenido de la nueva tabla de destinatarios.
* Introduzca un nuevo tipo en la carpeta del árbol del explorador.
* Cree una nueva aplicación web para acceder a la tabla personalizada a través de la página principal de Adobe Campaign.

Adobe Campaign utiliza una variable global &quot;Nms_DefaultRcpSchema&quot; para dialogar con la base de datos de destinatario predeterminada (nms:recipient). Por lo tanto, esta variable debe modificarse.

1. Vaya a la **[!UICONTROL Administration>Platform>Options]** del explorador.
1. Cambie el valor del **Nms_DefaultRcpSchema** variable con el nombre del esquema que coincide con la tabla de destinatarios externa (en este caso: cus:individual).
1. Guarde los cambios.

## Creación de un nuevo formulario {#creating-a-new-form-}

La creación de un nuevo formulario permite ver y editar los datos de la tabla de destinatarios externa.

>[!IMPORTANT]
>
>El nombre del formulario debe ser idéntico al nombre del esquema al que hace referencia.

1. Vaya a la **Administration > Configuration > Input forms** del explorador.
1. Crear un nuevo **xtk:formulario** type **formulario** archivo.
1. Describa todos los campos y la monitorización que necesite en función de la plantilla de tabla.

   >[!NOTE]
   >
   >Para obtener más información sobre **formulario** escriba archivos, consulte [esta página](../../configuration/using/identifying-a-form.md).

   En el ejemplo actual, la variable **formulario** el archivo debe basarse en el **cus:individual** y, por lo tanto, tienen el siguiente diseño:

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
1. Crear un nuevo **xtk:navtree** type **navtree** documento.
1. Describa todos los campos y la monitorización que necesite en función de la plantilla de tabla.

   >[!NOTE]
   >
   >Para obtener más información sobre **navtree** escriba archivos, consulte [esta página](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy).

   En el ejemplo actual, la variable **navtree** el archivo debe basarse en el **cus:individual** y, por lo tanto, tienen la siguiente forma:

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
