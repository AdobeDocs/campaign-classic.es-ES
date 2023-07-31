---
product: campaign
title: Administración de perfiles
description: Administración de perfiles
feature: Profiles
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: profile-management
exl-id: e1d0556a-6f30-4863-9025-eb9c1b8b53d3
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: ht
source-wordcount: '236'
ht-degree: 100%

---

# Administración de perfiles{#managing-profiles}



## Árbol de destinatario {#recipient-tree}

Para acceder a las funcionalidades avanzadas de administración de destinatarios, debe editar el árbol de Adobe Campaign. Para ello, haga clic en el botón **[!UICONTROL Explorer]** de la barra de herramientas.

De forma predeterminada, los destinatarios se almacenan en el nodo **[!UICONTROL Profiles and targets]** del árbol de Adobe Campaign. En el mismo nodo, puede crear una o varias carpetas y subcarpetas para almacenar perfiles de destinatario.

Cada nodo coincide con una carpeta. Los datos de cada carpeta deben considerarse separados entre ellos. Esto significa que la administración de duplicación será más complicada para varias carpetas de destinatarios.

>[!NOTE]
>
>Para mostrar la lista de todos los destinatarios de la base de datos, debe crear una vista. Obtenga más información en [Carpetas y vistas](../../platform/using/access-management-folders.md).

## Movimiento de destinatarios {#moving-recipients}

Puede seleccionar uno o varios destinatarios, arrastrarlos de la lista de destinatarios y colocarlos en la carpeta deseada. Un mensaje de advertencia le pedirá que confirme esta acción.

## Copia de un destinatario {#copying-a-recipient}

Puede copiar un destinatario en la misma carpeta haciendo clic con el botón derecho en el destinatario deseado y seleccionando **[!UICONTROL Copy]**.

## Eliminación de destinatarios {#deleting-recipients}

Para eliminar destinatarios, muévalos a una carpeta específica y, a continuación, depure el contenido de esta carpeta. **Se recomienda no utilizar** la opción **[!UICONTROL Delete]** en este caso.

Para purgar una carpeta, utilice el menú **[!UICONTROL Actions > Purge folder]**, al que se accede haciendo clic con el botón derecho en la carpeta deseada.

![](assets/s_ncs_user_purge_folder.png)

Haga clic en **[!UICONTROL Start]** para iniciar la operación. La sección central de la ventana muestra el estado de progreso, como se muestra a continuación:

![](assets/s_ncs_user_purge_folder_start.png)
