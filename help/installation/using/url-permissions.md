---
product: campaign
title: Configuración de permisos de URL
description: Obtenga información sobre cómo configurar permisos de URL
feature: Installation, Instance Settings, Permissions
badge-v7-prem: label="On-premise/híbrido solo" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 6fe8da3b-57b9-4a69-8602-a03993630b27
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 31%

---

# Configuración de permisos de URL (local){#url-permissions}



La lista predeterminada de direcciones URL a las que pueden llamar los códigos JavaScript (flujos de trabajo, etc.) a través de instancias de Campaign Classic es limitada. Son direcciones URL que permiten que las instancias funcionen correctamente.

De forma predeterminada, las instancias no pueden conectarse a direcciones URL externas. Sin embargo, es posible añadir algunas direcciones URL externas a la lista de direcciones URL autorizadas para que la instancia pueda conectarse a ellas. Esto le permite conectar las instancias de Campaign a sistemas externos como, por ejemplo, servidores SFTP o sitios web para habilitar la transferencia de datos o archivos.

>[!NOTE]
>
>Este procedimiento está restringido a **implementaciones locales**.
>
>Como cliente de **hosted**, si puede acceder al [Panel de control de Campaign de Campaign](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=es), puede usar la interfaz de autoservicio de permisos de URL. [Más información](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/url-permissions.html?lang=es)
>
>Otros clientes de **híbrido/alojado** deben ponerse en contacto con el equipo de soporte de Adobe para agregar la IP a la lista de permitidos.
>

Para implementaciones **Hybrid** y **On-Premise**, el administrador debe hacer referencia a un nuevo **urlPermission** en el archivo **serverConf.xml**.


Hay tres modos de protección de conexión disponibles:

* **Bloqueo**: todas las direcciones URL que no pertenecen a la lista de permitidos están bloqueadas y muestran un mensaje de error. Es el modo predeterminado después de una posactualización.
* **Permisivo**: se permiten todas las direcciones URL que no pertenecen a la lista de permitidos.
* **Advertencia**: se permiten todas las direcciones URL que no pertenecen a la lista de permitidos, pero el intérprete JS emite una advertencia para que el administrador pueda recopilarlas. Este modo agrega mensajes de advertencia JST-310027.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!IMPORTANT]
>
>De manera predeterminada, las nuevas implementaciones utilizan el modo **Bloqueo**.
>
>Como cliente existente que proviene de una migración, puede usar temporalmente el modo **Advertencia**. Analice el tráfico saliente antes de permitir las direcciones URL. Una vez definida la lista de direcciones URL permitidas, puede agregarlas a la lista de permitidos y activar el modo **Bloqueo**.

Para obtener más información, consulte estas secciones:

* [Documentación del Panel de control](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=es)
* [Modelos de alojamiento](hosting-models.md)
* [Configuración del servidor de Campaign](configuring-campaign-server.md)
* [Parámetros del archivo de configuración del servidor Campaign](the-server-configuration-file.md)
* [Lista de comprobación de seguridad y privacidad](get-started-security-privacy.md)
