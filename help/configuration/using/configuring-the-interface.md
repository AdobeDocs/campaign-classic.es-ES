---
product: campaign
title: Configuración de la interfaz
description: Configuración de la interfaz
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 9f50f258-845e-4895-b1ef-b73744dea326
source-git-commit: fb4b4c42b907e86813ea570f912312fccf893bfe
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 4%

---

# Configuración de la interfaz{#configuring-the-interface}

![](../../assets/common.svg)

Para ver la nueva tabla de destinatarios y dialogar con ella en la interfaz de Adobe Campaign, siga los siguientes pasos:

* Cree un nuevo formulario para editar el contenido de la nueva tabla de destinatarios.
* Introduzca un nuevo tipo en la carpeta del árbol del explorador.
* Cree una nueva aplicación web para acceder a la tabla personalizada a través de la página principal de Adobe Campaign.

Adobe Campaign utiliza una variable global &quot;Nms_DefaultRcpSchema&quot; para dialogar con la base de datos de destinatarios predeterminada (nms:recipient). Por lo tanto, esta variable debe modificarse.

1. Vaya a la **[!UICONTROL Administration>Platform>Options]** del explorador.
1. Cambiar el valor de la variable **Nms_DefaultRcpSchema** con el nombre del esquema que coincide con la tabla de destinatarios externa (en este caso: cus:individual).
1. Guarde los cambios.

## Creación de un nuevo formulario {#creating-a-new-form-}

La creación de un nuevo formulario permite ver y editar los datos de la tabla de destinatarios externa.

>[!IMPORTANT]
>
>El nombre del formulario debe ser idéntico al nombre del esquema al que hace referencia.

1. Vaya a la **Administración > Configuración > Formularios de entrada** del explorador.
1. Cree una nueva **xtk:form** type **formulario** archivo.
1. Describa todos los campos de monitorización y que necesite según la plantilla de tabla.

   >[!NOTE]
   >
   >Para obtener más información sobre **formulario** archivos de tipo , consulte [esta página](../../configuration/using/identifying-a-form.md).

   En nuestro ejemplo actual, la variable **formulario** debe basarse en la variable **cus:individual** y, por lo tanto, tienen la siguiente presentación:

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
1. Cree una nueva **xtk:navtree** type **navtree** documento.
1. Describa todos los campos de monitorización y que necesite según la plantilla de tabla.

   >[!NOTE]
   >
   >Para obtener más información, **navtree** archivos de tipo , consulte [esta página](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy).

   En el ejemplo actual, la variable **navtree** debe basarse en la variable **cus:individual** y, por lo tanto, tienen el siguiente formulario:

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
