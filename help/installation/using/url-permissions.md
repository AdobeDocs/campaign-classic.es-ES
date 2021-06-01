---
product: campaign
title: Configuración de permisos de URL
description: Obtenga información sobre cómo configurar los permisos de URL
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 67dda58f-97d1-4df5-9648-5f8a1453b814,6fe8da3b-57b9-4a69-8602-a03993630b27
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 34%

---

# Configuración de permisos de URL (locales){#url-permissions}

La lista predeterminada de direcciones URL a las que pueden llamar los códigos JavaScript (flujos de trabajo, etc.) a través de instancias de Campaign Classic es limitada. Son direcciones URL que permiten que las instancias funcionen correctamente.

De forma predeterminada, las instancias no pueden conectarse a direcciones URL externas. Sin embargo, es posible añadir algunas direcciones URL externas a la lista de direcciones URL autorizadas para que la instancia pueda conectarse a ellas. Esto le permite conectar las instancias de Campaign a sistemas externos como, por ejemplo, servidores SFTP o sitios web para habilitar la transferencia de datos o archivos.

>[!NOTE]
>
>Este procedimiento está restringido a **implementaciones locales**.
>
>Como cliente **alojado**, si puede acceder al [Panel de control de Campaign de campaña](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=es), puede utilizar la interfaz de autoservicio de permisos de URL. [Obtenga más información](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/url-permissions.html?lang=es)
>
>Otros clientes **híbridos/alojados** deben ponerse en contacto con el equipo de asistencia de Adobe para agregar IP a la lista de permitidos.


Para implementaciones **Hybrid** y **On-premise**, el administrador debe hacer referencia a un nuevo **urlPermission** en el archivo **serverConf.xml**.


Hay tres modos de protección de conexión disponibles:

* **Bloqueo**: todas las direcciones URL que no pertenecen a la lista de permitidos están bloqueadas, con un mensaje de error. Es el modo predeterminado después de una posactualización.
* **Permisivo**: se permiten todas las direcciones URL que no pertenecen a la lista de permitidos.
* **Advertencia**: se permiten todas las direcciones URL que no pertenecen a la lista de permitidos, pero el intérprete JS emite una advertencia para que el administrador pueda recopilarlas. Este modo añade mensajes de advertencia JST-310027.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!IMPORTANT]
>
>De forma predeterminada, las nuevas implementaciones utilizan el modo **Bloqueo**.
>
>Como cliente existente que proviene de una migración, puede utilizar temporalmente el modo **Warning**. Analice el tráfico saliente antes de permitir las direcciones URL. Una vez definida la lista de direcciones URL permitidas, puede añadir las direcciones URL a la lista de permitidos y activar el modo **Bloqueo**.

Para obtener más información, consulte estas secciones:

* [Documentación del Panel de control](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html)
* [Modelos de alojamiento](hosting-models.md)
* [Configuración del servidor de Campaign](configuring-campaign-server.md)
* [Parámetros del archivo de configuración del servidor de Campaign](the-server-configuration-file.md)
* [Lista de comprobación de seguridad y privacidad](get-started-security-privacy.md)
