---
product: campaign
title: Prueba de la migración
description: Prueba de la migración
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: 228ee9e4-46a0-4d82-b8ba-b019bc0e7cac
source-git-commit: 9ba2199eabf91381e87661f30c9af8aa0ce4cc26
workflow-type: tm+mt
source-wordcount: '729'
ht-degree: 1%

---

# Prueba de la migración{#testing-the-migration}

![](../../assets/v7-only.svg)

## Procedimiento general {#general-procedure}

Según la configuración, hay varias formas de realizar pruebas de migración.

Debe tener un entorno de prueba/desarrollo para realizar pruebas de migración. Los entornos de desarrollo están sujetos a licencia: compruebe su contrato de licencia o póngase en contacto con el servicio de ventas de Adobe Campaign.

1. Detenga todos los avances en curso y transfiérselos al entorno de producción.
1. Haga una copia de seguridad de la base de datos del entorno de desarrollo.
1. Detenga todos los procesos de Adobe Campaign en la instancia de desarrollo.
1. Haga una copia de seguridad de la base de datos del entorno de producción y restablézcala como un entorno de desarrollo.
1. Antes de iniciar los servicios de Adobe Campaign, ejecute el **frozenInstance.js** secuencia de comandos de cauterización que permite borrar la base de datos de cualquier objeto que se estuviera ejecutando cuando se inició la copia de seguridad.

   ```
   nlserver javascript nms:freezeInstance.js -instance:<instance> -arg:<run|dry>
   ```

   >[!NOTE]
   >
   >El comando se inicia de forma predeterminada en **seca** y enumera todas las solicitudes ejecutadas por ese comando, sin iniciarlas. Para ejecutar solicitudes de cauterización, utilice **run** en el comando .

1. Asegúrese de que las copias de seguridad sean correctas al intentar restaurarlas. Asegúrese de tener acceso a la base de datos, las tablas, los datos, etc.
1. Pruebe el procedimiento de migración en el entorno de desarrollo.

   Los procedimientos completos se detallan en la [Requisitos previos para la migración a Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) para obtener más información.

1. Si la migración del entorno de desarrollo se realiza correctamente, puede migrar el entorno de producción.

>[!IMPORTANT]
>
>Debido a los cambios realizados en la estructura de datos, no es posible importar y exportar paquetes de datos entre una plataforma v5 y una plataforma v7.

>[!NOTE]
>
>El comando de actualización de Adobe Campaign (**postupgrade**) le permite sincronizar recursos y actualizar esquemas y la base de datos. Esta operación solo se puede realizar una vez y solo en el servidor de aplicaciones. Después de sincronizar los recursos, la variable **postupgrade** permite detectar si la sincronización genera errores o advertencias.

## Herramientas de migración {#migration-tools}

Varias opciones permiten medir el impacto de una migración e identificar los posibles problemas. Estas opciones se deben ejecutar:

* en el **config** comando:

   ```
   nlserver.exe config <option> -instance:<instanceName>
   ```

* o después de la actualización:

   ```
   nlserver.exe config -postupgrade <option> -instance:<instanceName>
   ```

>[!NOTE]
>
>Debe usar la variable **-instancia:`<instanceame>`** . No se recomienda usar la variable **-allinstances** .

### Opciones -showCustomEntities y -showDeletedEntities {#showcustomentities-and--showdeletedentities-options}

* La variable **-showCustomEntities** muestra la lista de todos los objetos no estándar:

   ```
   nlserver.exe config -showCustomEntities -instance:<instanceName>
   ```

   Ejemplo de mensaje enviado:

   ```
   xtk_migration:opsecurity2 xtk:entity
   ```

* La variable **-showDeletedEntities** muestra la lista de todos los objetos estándar que faltan en la base de datos o en el sistema de archivos. Para cada objeto que falta, se especifica la ruta.

   ```
   nlserver.exe config -showDeletedEntities -instance:<instanceName>
   ```

   Ejemplo de mensaje enviado:

   ```
   Out of the box object 'nms:deliveryCustomizationMdl' belonging to the 'xtk:srcSchema' schema has not been found in the file system.
   ```

### Proceso de verificación {#verification-process}

Este proceso, integrado como estándar en el comando posactualización, permite mostrar advertencias y errores que podrían provocar errores en la migración. **Si se muestran errores, la migración no se ha ejecutado.** Si esto sucede, corrija todos los errores y vuelva a iniciar la posactualización.

Puede iniciar el proceso de verificación por su cuenta (sin migración) mediante el comando :

```
nlserver.exe config -postupgrade -check -instance:<instanceName>
```

>[!NOTE]
>
>Ignore todas las advertencias y errores que tengan el código JST-310040.

Se buscan las expresiones siguientes (con distinción de mayúsculas y minúsculas):

<table> 
 <thead> 
  <tr> 
   <th> Expresión<br /> </th> 
   <th> Código de error<br /> </th> 
   <th> Tipo de registro<br /> </th> 
   <th> Comentarios<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> .@<br /> </td> 
   <td> PU-0001<br /> </td> 
   <td> Aviso<br /> </td> 
   <td> Este tipo de sintaxis ya no se admite en la personalización de envíos. Consulte <a href="../../migration/using/general-configurations.md#javascript" target="_blank">JavaScript</a>. De lo contrario, compruebe que el tipo de valor es correcto.<br /> </td> 
  </tr> 
  <tr> 
   <td> common.js<br /> </td> 
   <td> PU-0002<br /> </td> 
   <td> Aviso<br /> </td> 
   <td> Esta biblioteca no debe utilizarse.<br /> </td> 
  </tr> 
  <tr> 
   <td> logon(<br /> </td> 
   <td> PU-0003<br /> </td> 
   <td> Aviso<br /> </td> 
   <td> Este método de conexión ya no debe utilizarse. Consulte <a href="../../migration/using/general-configurations.md#identified-web-applications" target="_blank">Aplicaciones web identificadas</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> new SoapMethodCall(<br /> </td> 
   <td> PU-0004<br /> </td> 
   <td> Aviso<br /> </td> 
   <td> Esta función solo se admite cuando se utiliza en código JavaScript ejecutado desde una zona de seguridad incluida en <strong>sessionTokenOnly</strong> en el menú contextual.<br /> </td> 
  </tr> 
  <tr> 
   <td> sql=<br /> </td> 
   <td> PU-0005<br /> </td> 
   <td> Error<br /> </td> 
   <td> Este tipo de error provoca un error de migración. Consulte <a href="../../migration/using/general-configurations.md#sqldata" target="_blank">SQLData</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> SQLDATA<br /> </td> 
   <td> PU-0006<br /> </td> 
   <td> Error<br /> </td> 
   <td> Este tipo de error provoca un error de migración. Consulte <a href="../../migration/using/general-configurations.md#sqldata" target="_blank">SQLData</a>. Si obtiene registros de errores de aplicaciones web de tipo "descripción general" (migración de la versión 6.02), consulte <a href="../../migration/using/specific-configurations-in-v6-02.md#web-applications" target="_blank">Configuración de Campaign</a>.<br /> </td> 
  </tr>
  <tr> 
   <td> crmDeploymentType="onpremise"<br /> </td> 
   <td> PU-0007<br /> </td> 
   <td> Error<br /> </td> 
   <td> Este tipo de implementación ya no es compatible. El tipo de implementación del conector Microsoft CRM local y de Office 365 ya no se utiliza. 
   </br>Si está utilizando uno de estos tipos de implementación obsoletos en una cuenta externa, esta cuenta externa debe eliminarse y luego debe ejecutar el <b>postupgrade</b> comando. 
   </br>Para cambiar a la implementación de API web, consulte <a href="../../platform/using/crm-ms-dynamics.md#configure-acc-for-microsoft" target="_blank">Aplicaciones web</a>.<br /> </td>
  </tr> 
 </tbody> 
</table>

También se realiza una comprobación de la coherencia de la base de datos y el esquema.

### Opción Restauración {#restoration-option}

Esta opción permite restaurar objetos predeterminados si se han modificado. Para cada objeto restaurado, se almacena una copia de seguridad de los cambios en la carpeta seleccionada:

```
nlserver.exe config -postupgrade -restoreFactory:<backupfolder> -instance:<instanceName>
```

>[!NOTE]
>
>Se recomienda encarecidamente utilizar rutas de carpeta absolutas y mantener la estructura del árbol de carpetas. Por ejemplo: backupFolder\nms\srcSchema\billing.xml.

### Reanudar la migración {#resuming-migration}

Si reinicia la actualización después de un error de migración, se reanuda desde el mismo lugar en que se detuvo.
