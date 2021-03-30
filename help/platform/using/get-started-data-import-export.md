---
solution: Campaign Classic
product: campaign
title: Introducción a la importación y exportación de datos
description: Obtenga más información sobre la importación y exportación de datos en Campaign Classic.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: b05b8daad449aeb1f5226fdd76744776c6553b63
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 96%

---


# Introducción a la importación y exportación de datos {#get-started-data-import-export}

Adobe Campaign Classic ofrece funciones de administración de datos que le permiten importar y exportar datos. Estas operaciones se pueden realizar utilizando flujos de trabajo o importaciones y exportaciones genéricas.

>[!IMPORTANT]
>
>Tenga en cuenta los límites de almacenamiento SFTP, almacenamiento de la base de datos y perfil activo según el contrato de Adobe Campaign al usar esta funcionalidad.

## Flujos de trabajo {#workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**Los flujos de trabajo** son una forma útil de automatizar los procesos de importación. Tanto si se importan datos desde un archivo local como desde un SFTP, le ayudan a estandarizar los procedimientos de administración de datos.

Con los flujos de trabajo se pueden repetir automáticamente las importaciones y exportaciones según una programación, por ejemplo, para automatizar el intercambio de datos entre varios sistemas de información.

Para obtener más información, consulte [esta sección](../../platform/using/import-export-workflows.md).

## Importación y exportación genéricas {#generic-import-export}

<img src="assets/do-not-localize/icon_templates.svg" width="60px">

Además, Campaign Classic proporciona **importaciones y exportaciones genéricas** que le permiten crear ocasionalmente trabajos de importación o exportación.

Las importaciones y exportaciones se configuran en plantillas dedicadas, que se pueden configurar y utilizar para lanzar y supervisar los trabajos de importación y exportación.

Para obtener más información sobre las importaciones y exportaciones genéricas, consulte [esta sección](../../platform/using/about-generic-imports-exports.md).

>[!IMPORTANT]
>Las importaciones y exportaciones genéricas deben utilizarse únicamente para operaciones ocasionales. Para garantizar la coherencia de los datos y mejorar la eficacia, se recomienda realizar las operaciones de importación y exportación mediante flujos de trabajo.

## Encriptación y compresión de datos {#data-encryption-compression}

<img src="assets/do-not-localize/icon_encrypt.svg" width="60px">

Campaign Classic le permite importar y exportar archivos comprimidos o cifrados.

Estas operaciones se realizan dentro de flujos de trabajo mediante la aplicación de etapas de preprocesamiento a los datos que desea aprovechar.

Para obtener más información, consulte estas secciones:

* [Descomprimir o desencriptar un archivo](../../platform/using/unzip-decrypt.md)
* [Comprimir o encriptar un archivo](../../platform/using/zip-encrypt.md)

## Prácticas recomendadas y solución de problemas {#best-practices-troubleshooting}

<img src="assets/do-not-localize/icon_bestpractices.svg" width="60px">

Se deben seguir varias [prácticas recomendadas](../../platform/using/import-export-best-practices.md) al realizar operaciones de importación y exportación para garantizar la coherencia de los datos dentro de la base de datos y evitar errores comunes durante la actualización o exportación.

Además, las recomendaciones y los problemas comunes relacionados con el uso de los servidores SFTP están disponibles en [esta sección](../../platform/using/sftp-server-usage.md).
