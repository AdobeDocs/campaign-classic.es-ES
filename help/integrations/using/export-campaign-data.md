---
solution: Campaign Classic
product: campaign
title: Exportar datos de Campaign a Adobe Experience Platform
description: Obtenga información sobre cómo exportar datos de Campaign Classic a Adobe Experience Platform.
audience: integrations
content-type: reference
translation-type: tm+mt
source-git-commit: 1c07c3b10a6d38ca67c20746a51301d71aec0015
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---


# Exportar datos de Campaign a Adobe Experience Platform {#sources}

Para exportar datos de Campaign Classic a la plataforma de datos del cliente en tiempo real de Adobe (RTCDP), primero debe crear un flujo de trabajo en Campaign Classic para exportar a su ubicación de almacenamiento del blob de S3 o Azure los datos que desee compartir.

Una vez configurado el flujo de trabajo y enviado los datos a su ubicación de almacenamiento, debe conectar su ubicación de almacenamiento del blob S3 o Azure como **Source** en Adobe experience Platform.

>[!NOTE]
>
>Tenga en cuenta que se recomienda exportar solo los datos generados por Campaign (por ejemplo, envíos, aperturas, clics, etc.) a Adobe Experience Platform. Los datos que se incorporan desde un origen de terceros (como su CRM) deben importarse directamente en Adobe Experience Platform.

## Creación de un flujo de trabajo de exportación en el Campaign Classic

Para exportar datos de Campaign Classic a su ubicación de almacenamiento S3 o Azure Blob, debe crear un flujo de trabajo para dirigir los datos que desea exportar y enviarlos a su ubicación de almacenamiento.

Para ello, añada y configure:

* Una actividad **[!UICONTROL Data extraction (file)]** para extraer los datos de destino en un archivo CSV. Para obtener más información sobre cómo configurar esta actividad, consulte [esta sección](../../workflow/using/extraction--file-.md).

   ![](assets/rtcdp-extract-file.png)

* Una actividad **[!UICONTROL File transfer]** para transferir el archivo CSV a su ubicación de almacenamiento. Para obtener más información sobre cómo configurar esta actividad, consulte [esta sección](../../workflow/using/file-transfer.md).

   ![](assets/rtcdp-file-transfer.png)

Por ejemplo, el flujo de trabajo siguiente extrae registros de forma regular en un archivo CSV y, a continuación, transfiere el archivo a una ubicación de almacenamiento.

![](assets/aep-export.png)

## Conecte la ubicación de almacenamiento como origen

A continuación se enumeran los pasos principales para conectar su ubicación de almacenamiento del blob S3 o Azure como **Source** en Adobe experience Platform. Encontrará información detallada sobre cada uno de estos pasos en la [Documentación de conectores de origen](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html).

1. En el menú Adobe Experience Platform **[!UICONTROL Sources]**, cree una conexión con su ubicación de almacenamiento:

   * [Crear una conexión de origen de Amazon S3](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/cloud-storage/s3.html)
   * [Conector de Azure Blob](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/cloud-storage/blob.html)

   >[!NOTE]
   >
   >La ubicación de almacenamiento puede ser Amazon S3, SFTP con contraseña, SFTP con clave SSH o conexiones Azure Blob. El método preferido para enviar datos a Adobe Campaign es mediante Amazon S3 o Azure Blob:

   ![](assets/rtcdp-connector.png)

1. Configure un flujo de datos para una conexión por lotes de almacenamiento en la nube. Un flujo de datos es una tarea programada que recupera e incorpora datos de la ubicación de almacenamiento en un conjunto de datos de Adobe Experience Platform. Estos pasos le permiten configurar la ingesta de datos desde su ubicación de almacenamiento, incluida la selección de datos y la asignación de los campos CSV a un esquema XDM.

   Encontrará información detallada en [esta página](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/dataflow/cloud-storage.html).

   ![](assets/rtcdp-map-xdm.png)

1. Una vez configurado el origen, Adobe Experience Platform importará el archivo desde la ubicación de almacenamiento proporcionada.

   Esta operación se puede programar según sus necesidades. Se recomienda realizar la exportación hasta 6 veces al día, en función de la carga ya presente en la instancia.
