---
product: campaign
title: Configuración de permisos de URL
description: Obtenga información sobre cómo configurar permisos de URL
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 6fe8da3b-57b9-4a69-8602-a03993630b27
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 34%

---

# Configuración de permisos de URL (local){#url-permissions}



La lista predeterminada de direcciones URL a las que pueden llamar los códigos JavaScript (flujos de trabajo, etc.) a través de instancias de Campaign Classic es limitada. Son direcciones URL que permiten que las instancias funcionen correctamente.

De forma predeterminada, las instancias no pueden conectarse a direcciones URL externas. Sin embargo, es posible añadir algunas direcciones URL externas a la lista de direcciones URL autorizadas para que la instancia pueda conectarse a ellas. Esto le permite conectar las instancias de Campaign a sistemas externos como, por ejemplo, servidores SFTP o sitios web para habilitar la transferencia de datos o archivos.

>[!NOTE]
>
>Este procedimiento está restringido a **on-premise** implementaciones.
>
>As a **alojado** cliente, si puede acceder a [Panel de control de Campaign de campaña](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=es), puede utilizar la interfaz de autoservicio de permisos de URL. [Más información](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/url-permissions.html?lang=es)
>
>Otros **híbrido/alojado** Los clientes de deberán ponerse en contacto con el equipo de asistencia del Adobe de para añadir la IP a la lista de permitidos.

Para **Híbrido** y **On-Premise** implementaciones, el administrador debe hacer referencia a un nuevo **urlPermission** en el **serverConf.xml** archivo.


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
>De forma predeterminada, las nuevas implementaciones utilizan el **Bloqueo** modo.
>
>Como cliente existente que proviene de una migración, puede utilizar temporalmente el **Advertencia** modo. Analice el tráfico saliente antes de permitir las direcciones URL. Una vez definida la lista de direcciones URL permitidas, puede añadir las direcciones URL a la lista de permitidos y activar el **Bloqueo** modo.

Para obtener más información, consulte estas secciones:

* [Documentación del Panel de control](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=es)
* [Modelos de alojamiento](hosting-models.md)
* [Configuración del servidor de Campaign](configuring-campaign-server.md)
* [Parámetros del archivo de configuración del servidor Campaign](the-server-configuration-file.md)
* [Lista de comprobación de seguridad y privacidad](get-started-security-privacy.md)
