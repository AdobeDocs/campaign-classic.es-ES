---
solution: Campaign Classic
product: campaign
title: Uso de derechos asignados para configurar permisos
description: Obtenga información sobre cómo utilizar derechos asignados para configurar permisos
feature: Gestión de acceso
role: Business Practitioner, Administrator
level: Beginner
exl-id: 07470a91-d8d2-4c41-9555-05522c8068f0
translation-type: tm+mt
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 99%

---

# Uso de derechos asignados para configurar permisos{#named-rights}

De forma predeterminada, Adobe Campaign propone un conjunto de derechos asignados que permiten definir las autorizaciones asignadas a operadores y grupos de operadores. Estos derechos se pueden editar desde el nodo **[!UICONTROL Administration > Access management > Named rights]** del árbol.

![](assets/s_ncs_admin_named_rights.png)

Estos derechos son los siguientes:

* **[!UICONTROL ADMINISTRATION]**: Los operadores con el derecho de **[!UICONTROL ADMINISTRATION]** tienen acceso total a la instancia. Los usuarios administradores pueden ejecutar, crear, editar o eliminar cualquier objeto, como flujo de trabajo, envío, secuencias de comandos, etc.

* **[!UICONTROL APPROVAL ADMINISTRATION]**: Puede definir varios pasos de aprobación dentro de flujos de trabajo y envíos para asegurarse de que un operador o grupo asignado ha aprobado el estado actual. Los usuarios con el derecho de **[!UICONTROL APPROVAL ADMINISTRATION]** pueden definir los pasos de aprobación y también asignar un operador o grupo de operadores que deben aprobar dichos pasos.

* **[!UICONTROL CENTRAL]**: derecho para la administración central (Marketing distribuido).

* **[!UICONTROL DELETE FOLDER]**: derecho para eliminar carpetas. Con este derecho, los usuarios pueden eliminar carpetas de la vista del explorador.

* **[!UICONTROL EDIT FOLDERS]**: Derecho a modificar propiedades de carpeta como nombre interno, etiqueta, imagen asociada, orden de subcarpeta, etc.

* **[!UICONTROL EXPORT]**: Los usuarios pueden exportar datos de sus instancias de Adobe Campaign a un archivo del servidor o del equipo local mediante la actividad de flujo de trabajo **[!UICONTROL EXPORT]**.

* **[!UICONTROL FILES ACCESS]**: Derecho de lectura y escritura de archivos mediante una secuencia de comandos que se puede escribir en la actividad de flujo de trabajo **[!UICONTROL JavaScript]** para leer y escribir archivos en un servidor. 

* **[!UICONTROL IMPORT]**: derecho para importar datos genéricos. **[!UICONTROL IMPORT]** permite importar datos en cualquier otra tabla, mientras que el derecho de **[!UICONTROL RECIPIENT IMPORT]** permite importarlos únicamente en la tabla de destinatarios.

* **[!UICONTROL INSERT FOLDERS]**: derecho para insertar carpetas. Los usuarios con el derecho de **[!UICONTROL INSERT FOLDERS]** pueden crear nuevas carpetas en el árbol de carpetas en la vista del explorador.

* **[!UICONTROL LOCAL]**: derecho para la administración local (Distributed Marketing).

* **[!UICONTROL MERGE]**: Derecho para combinar los registros seleccionados en uno. Si los destinatarios existen como duplicados, el derecho de **[!UICONTROL MERGE]** permite al usuario seleccionar los duplicados y combinarlos en un destinatario principal.

* **[!UICONTROL PREPARE DELIVERIES]**: Derecho a crear, editar y guardar un envío. Los usuarios con el derecho de **[!UICONTROL PREPARE DELIVERIES]** también pueden iniciar el proceso de análisis de envíos.

* **[!UICONTROL PRIVACY DATA RIGHT]**: Derecho a recopilar y eliminar datos de privacidad. Para obtener más información, consulte [esta página](https://helpx.adobe.com/es/campaign/kb/acc-privacy.html).

* **[!UICONTROL PROGRAM EXECUTION]**: Derecho a ejecutar comandos en diversos lenguajes de programación.

* **[!UICONTROL RECIPIENT IMPORT]**: derecho para importar destinatarios. Los usuarios con el derecho de **[!UICONTROL RECIPIENT IMPORT]** pueden importar un archivo local a la tabla de destinatarios.

* **[!UICONTROL SQL SCRIPT EXECUTION]** Derecho a ejecutar cualquier comando SQL directamente en la base de datos.

* **[!UICONTROL START DELIVERIES]**: derecho a aprobar los envíos analizados previamente. Después del análisis de envío, el envío se detiene en varios pasos de aprobación y debe aprobarse para reanudarse. Los usuarios con derecho a **[!UICONTROL START DELIVERIES]** pueden aprobar envíos.

* **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY]**: derecho para escribir sus propias secuencias de comandos SQL con la actividad Administración de datos SQL para crear y rellenar tablas de trabajo (consulte [esta sección](../../workflow/using/sql-data-management.md)).

* **[!UICONTROL WORKFLOW]**: Derecho a ejecutar flujos de trabajo. Sin este derecho, los usuarios no pueden iniciar, detener ni reiniciar flujos de trabajo.

* **[!UICONTROL WEBAPP]**: derecho para utilizar aplicaciones web.

>[!NOTE]
>
>Esta lista puede variar según los complementos instalados en la plataforma.

## Matriz de derechos de acceso {#access-rights-matrix}

Los grupos predeterminados y los derechos asignados permiten a los operadores acceder a ciertas carpetas de la jerarquía de navegación y conceder permisos de lectura, escritura y eliminación.

La matriz de derechos de acceso a Adobe Campaign está disponible [aquí](/help/platform/using/assets/access-rights-matrix.pdf).

[![imagen](assets/do-not-localize/user_management.png)](https://experienceleague.adobe.com/docs/campaign-classic/assets/access-rights-matrix.pdf?lang=en)
