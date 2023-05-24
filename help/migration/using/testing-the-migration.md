---
product: campaign
title: Prueba de la migración
description: Prueba de la migración
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: migration
content-type: reference
topic-tags: migration-procedure
hide: true
hidefromtoc: true
exl-id: 228ee9e4-46a0-4d82-b8ba-b019bc0e7cac
source-git-commit: 4b13e310fcee9ba24e83b697fca57bc494505642
workflow-type: tm+mt
source-wordcount: '706'
ht-degree: 4%

---

# Pruebas de migración{#testing-the-migration}



## Procedimiento general {#general-procedure}

Según la configuración, hay varias formas de realizar pruebas de migración.

Debe tener un entorno de prueba/desarrollo para realizar pruebas de migración. Los entornos de Adobe Campaign están sujetos a licencia: compruebe el contrato de licencia o póngase en contacto con el representante del Adobe.

1. Detenga todos los desarrollos en curso y transfiéralos al entorno de producción.
1. Realice una copia de seguridad de la base de datos del entorno de desarrollo.
1. Detenga todos los procesos de Adobe Campaign en la instancia de desarrollo.
1. Realice una copia de seguridad de la base de datos del entorno de producción y restáurela como un entorno de desarrollo.
1. Antes de iniciar los servicios de Adobe Campaign, ejecute el **congelaciónInstance.js** script de cauterización que permite borrar la base de datos de cualquier objeto que se estaba ejecutando cuando se inició la copia de seguridad.

   ```
   nlserver javascript nms:freezeInstance.js -instance:<instance> -arg:<run|dry>
   ```

   >[!NOTE]
   >
   >El comando se inicia de forma predeterminada en **seco** y enumera todas las solicitudes ejecutadas por ese comando sin iniciarlas. Para ejecutar solicitudes de cauterización, utilice **correr** en el comando.

1. Asegúrese de que las copias de seguridad sean correctas al intentar restaurarlas. Asegúrese de que puede acceder a la base de datos, a las tablas, a los datos, etc.
1. Pruebe el procedimiento de migración en el entorno de desarrollo.
1. Si la migración del entorno de desarrollo se realiza correctamente, puede migrar el entorno de producción.

>[!CAUTION]
>
>Debido a los cambios realizados en la estructura de datos, no es posible importar y exportar paquetes de datos entre las plataformas v5 y v7.


## Herramientas de migración {#migration-tools}

Varias opciones permiten medir el impacto de una migración e identificar los posibles problemas. Estas opciones se van a ejecutar:

* en el **config** comando:

   ```
   nlserver.exe config <option> -instance:<instance-name>
   ```

* o en la posactualización:

   ```
   nlserver.exe config -postupgrade <option> -instance:<instance-name>
   ```

>[!NOTE]
>
>* Debe utilizar el **-instancia:`<instanceame>`** opción. No se recomienda el uso de **-todas las instancias** opción.
>* El comando Adobe Campaign update (**posterior a la actualización**) permite sincronizar recursos y actualizar esquemas y la base de datos. Esta operación solo se puede realizar una vez y solo en el servidor de aplicaciones. Después de sincronizar los recursos, la variable **posterior a la actualización** El comando permite detectar si la sincronización genera errores o advertencias.


### Objetos no estándar o faltantes

* El **-showCustomEntities** Esta opción muestra la lista de todos los objetos no estándar:

   ```
   nlserver.exe config -showCustomEntities -instance:<instance-name>
   ```

   Ejemplo de mensaje enviado:

   ```
   xtk_migration:opsecurity2 xtk:entity
   ```

* El **-showDeletedEntities** Esta opción muestra la lista de todos los objetos estándar que faltan en la base de datos o en el sistema de archivos. Para cada objeto que falta, se especifica la ruta.

   ```
   nlserver.exe config -showDeletedEntities -instance:<instance-name>
   ```

   Ejemplo de mensaje enviado:

   ```
   Out of the box object 'nms:deliveryCustomizationMdl' belonging to the 'xtk:srcSchema' schema has not been found in the file system.
   ```

### Proceso de verificación {#verification-process}

Integrado como estándar en el comando postupgrade, este proceso permite mostrar advertencias y errores que podrían provocar errores en la migración. **Si se muestran errores, no se ha ejecutado la migración.** Si esto sucede, corrija todos los errores y vuelva a iniciar la posactualización.

Puede iniciar el proceso de verificación por su cuenta (sin migración) mediante el comando:

```
nlserver.exe config -postupgrade -check -instance:<instance-name>
```

>[!NOTE]
>
>Puede ignorar todas las advertencias y errores con el código JST-310040.

Se buscan las siguientes expresiones (con distinción de mayúsculas y minúsculas):

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
   <td> Advertencia<br /> </td> 
   <td> Este tipo de sintaxis ya no se admite en la personalización de envíos. <br /> </td> 
  </tr> 
  <tr> 
   <td> common.js<br /> </td> 
   <td> PU-0002<br /> </td> 
   <td> Advertencia<br /> </td> 
   <td> Esta biblioteca no debe utilizarse.<br /> </td> 
  </tr> 
  <tr> 
   <td> logon(<br /> </td> 
   <td> PU-0003<br /> </td> 
   <td> Advertencia<br /> </td> 
   <td> Este método de conexión ya no debe usarse.<br /> </td> 
  </tr> 
  <tr> 
   <td> new SoapMethodCall()<br /> </td> 
   <td> PU-0004<br /> </td> 
   <td> Advertencia<br /> </td> 
   <td> Esta función solo se admite cuando se utiliza en código JavaScript ejecutado desde una zona de seguridad en <strong>sessionTokenOnly</strong> modo.<br /> </td> 
  </tr> 
  <tr> 
   <td> sql=<br /> </td> 
   <td> PU-0005<br /> </td> 
   <td> Error<br /> </td> 
   <td> Este tipo de error provoca un error de migración.<br /> </td> 
  </tr> 
  <tr> 
   <td> crmDeploymentType="onpremise"<br /> </td> 
   <td> PU-0007<br /> </td> 
   <td> Error<br /> </td> 
   <td> Ya no se admite este tipo de implementación. El tipo de implementación de Office 365 y el conector CRM On-premise de Microsoft ya no se utiliza. 
   </br>Si utiliza uno de estos tipos de implementación obsoletos en una cuenta externa, esta cuenta externa debe eliminarse y luego debe ejecutar el <b>posterior a la actualización</b> comando. 
   </br>Para cambiar a la implementación de API web, consulte <a href="../../platform/using/crm-ms-dynamics.md#configure-acc-for-microsoft" target="_blank">Aplicaciones web</a>.<br /> </td>
  </tr> 
  <tr> 
   <td> CRM v1(mscrmWorkflow/sfdcWorkflow)<br /> </td> 
   <td> PU-0008<br /> </td> 
   <td> Error<br /> </td> 
   <td> Las actividades de acción Microsoft CRM, Salesforce y Oracle CRM bajo demanda ya no están disponibles. Para configurar la sincronización de datos entre Adobe Campaign y un sistema CRM, debe utilizar el <a href="../../workflow/using/crm-connector.md" target="_blank">Conector CRM</a> actividad de segmentación.<br /> </td>
  </tr> 
 </tbody> 
</table>

También se realiza una comprobación de coherencia de la base de datos y el esquema.

### Opción de restauración {#restoration-option}

Esta opción permite restaurar objetos listos para usar si se han modificado. Para cada objeto restaurado, se almacena una copia de seguridad de los cambios en la carpeta seleccionada:

```
nlserver.exe config -postupgrade -restoreFactory:<backupfolder> -instance:<instance-name>
```

>[!NOTE]
>
>Se recomienda encarecidamente utilizar rutas de carpeta absolutas y mantener la estructura del árbol de carpetas. Por ejemplo: backupFolder\nms\srcSchema\billing.xml.

### Reanudación de la migración {#resuming-migration}

Si reinicia la posactualización después de un error de migración, se reanudará desde el mismo lugar en el que se detuvo.
