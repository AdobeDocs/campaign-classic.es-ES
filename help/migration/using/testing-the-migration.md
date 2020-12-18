---
solution: Campaign Classic
product: campaign
title: Prueba de la migración
description: Prueba de la migración
audience: migration
content-type: reference
topic-tags: migration-procedure
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '667'
ht-degree: 2%

---


# Prueba de la migración{#testing-the-migration}

## Procedimiento general {#general-procedure}

Según la configuración, existen varias formas de realizar pruebas de migración.

Debe tener un entorno de prueba/desarrollo para realizar pruebas de migración. Los entornos de desarrollo están sujetos a licencia: consulte su contrato de licencia o póngase en contacto con el servicio de ventas de Adobe Campaign.

1. Detener todos los acontecimientos en curso y llevarlos al entorno de producción.
1. Realice una copia de seguridad de la base de datos de entorno de desarrollo.
1. Detenga todos los procesos de Adobe Campaign en la instancia de desarrollo.
1. Realice una copia de seguridad de la base de datos de entorno de producción y restauítela como entorno de desarrollo.
1. Antes de iniciar los servicios de Adobe Campaign, ejecute la **secuencia de comandos de cauterización de &lt;a0/>congelarInstance.js**, la cual le permite borrar la base de datos de cualquier objeto que se estuviera ejecutando cuando se inició la copia de seguridad.

   ```
   nlserver javascript nms:freezeInstance.js -instance:<instance> -arg:<run|dry>
   ```

   >[!NOTE]
   >
   >El comando se inicia de forma predeterminada en el modo **dry** y lista todas las solicitudes ejecutadas por ese comando, sin iniciarlas. Para ejecutar solicitudes de cauterización, utilice **ejecutar** en el comando.

1. Asegúrese de que las copias de seguridad sean correctas, intentando restaurarlas. Asegúrese de tener acceso a la base de datos, las tablas, los datos, etc.
1. Pruebe el procedimiento de migración en el entorno de desarrollo.

   Los procedimientos completos se detallan en la sección [Requisitos previos para la migración a Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md).

1. Si la migración del entorno de desarrollo es correcta, puede migrar el entorno de producción.

>[!IMPORTANT]
>
>Debido a los cambios realizados en la estructura de datos, no es posible importar ni exportar paquetes de datos entre una plataforma v5 y una plataforma v7.

>[!NOTE]
>
>El comando de actualización de Adobe Campaign (**postupgrade**) le permite sincronizar recursos y actualizar esquemas y la base de datos. Esta operación solo se puede realizar una vez y solo en el servidor de aplicaciones. Después de sincronizar los recursos, el comando **postupgrade** permite detectar si la sincronización genera errores o advertencias.

## Herramientas de migración {#migration-tools}

Varias opciones permiten medir el impacto de una migración e identificar los problemas potenciales. Estas opciones se van a ejecutar:

* en el comando **config**:

   ```
   nlserver.exe config <option> -instance:<instanceName>
   ```

* o en el período posterior a la actualización:

   ```
   nlserver.exe config -postupgrade <option> -instance:<instanceName>
   ```

>[!NOTE]
>
>Debe utilizar la opción **-instance:`<instanceame>`**. No se recomienda utilizar la opción **-allinstance**.

### -showCustomEntities y las opciones -showDeletedEntities {#showcustomentities-and--showdeletedentities-options}

* La opción **-showCustomEntities** muestra la lista de todos los objetos no estándar:

   ```
   nlserver.exe config -showCustomEntities -instance:<instanceName>
   ```

   Ejemplo de un mensaje enviado:

   ```
   xtk_migration:opsecurity2 xtk:entity
   ```

* La opción **-showDeletedEntities** muestra la lista de todos los objetos estándar que faltan en la base de datos o en el sistema de archivos. Se especifica la ruta de acceso para cada objeto que falta.

   ```
   nlserver.exe config -showDeletedEntities -instance:<instanceName>
   ```

   Ejemplo de un mensaje enviado:

   ```
   Out of the box object 'nms:deliveryCustomizationMdl' belonging to the 'xtk:srcSchema' schema has not been found in the file system.
   ```

### Proceso de verificación {#verification-process}

Integrado como estándar en el comando post-upgrade, este proceso le permite mostrar advertencias y errores que podrían provocar errores en la migración. **Si se muestran errores, la migración no se ha ejecutado.** Si esto sucede, corrija todos los errores y vuelva a realizar el inicio posterior a la actualización.

Puede realizar el inicio del proceso de verificación por sí mismo (sin migración) mediante el comando:

```
nlserver.exe config -postupgrade -check -instance:<instanceName>
```

>[!NOTE]
>
>Ignore todas las advertencias y errores que tengan el código JST-310040.

Se buscan las siguientes expresiones (distinguen entre mayúsculas y minúsculas):

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
   <td> Este tipo de sintaxis ya no se admite en la personalización de envío. Consulte <a href="../../migration/using/general-configurations.md#javascript" target="_blank">JavaScript</a>. De lo contrario, compruebe que el tipo de valor es correcto.<br /> </td> 
  </tr> 
  <tr> 
   <td> common.js<br /> </td> 
   <td> PU-0002<br /> </td> 
   <td> Aviso<br /> </td> 
   <td> No se debe usar esta biblioteca.<br /> </td> 
  </tr> 
  <tr> 
   <td> login(<br /> </td> 
   <td> PU-0003<br /> </td> 
   <td> Aviso<br /> </td> 
   <td> Este método de conexión ya no debe usarse. Consulte <a href="../../migration/using/general-configurations.md#identified-web-applications" target="_blank">Aplicaciones Web identificadas</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> nuevo SoapMethodCall(<br /> </td> 
   <td> PU-0004<br /> </td> 
   <td> Aviso<br /> </td> 
   <td> Esta función solo se admite cuando se utiliza en código JavaScript ejecutado desde una zona de seguridad en modo <strong>sessionTokenOnly</strong>.<br /> </td> 
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
   <td> Este tipo de error provoca un error de migración. Consulte <a href="../../migration/using/general-configurations.md#sqldata" target="_blank">SQLData</a>. Si obtiene registros de errores de aplicación Web de tipo overview (migración desde v6.02), consulte <a href="../../migration/using/specific-configurations-in-v6-02.md#web-applications" target="_blank">Aplicaciones web</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

También se realiza una comprobación de la coherencia de la base de datos y el esquema.

### Opción de restauración {#restoration-option}

Esta opción le permite restaurar objetos listos para usar si se han modificado. Para cada objeto restaurado, se almacena una copia de seguridad de los cambios en la carpeta seleccionada:

```
nlserver.exe config -postupgrade -restoreFactory:<backupfolder> -instance:<instanceName>
```

>[!NOTE]
>
>Se recomienda encarecidamente utilizar rutas absolutas de carpeta y mantener la estructura del árbol de carpetas. Por ejemplo: backupFolder\nms\srcSchema\billing.xml.

### Reanudando la migración {#resuming-migration}

Si reinicia la posactualización después de un error de migración, se reanuda desde el mismo lugar donde se detuvo.
