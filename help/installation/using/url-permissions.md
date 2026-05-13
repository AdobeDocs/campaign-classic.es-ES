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
TQID: https://experienceleague.adobe.com/5F4SRt978KzXMI06t3rNt3YRnYI-EWwSkQIrAd0oDq8
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a7760dfc-5c44-4d77-bb68-c50b1e265c93
subfeature_v2:
  - id: ac9c0a9c-8a76-4419-bd64-9c34c5782666
  - id: fb2a841f-c522-491f-9901-a1b939d252df
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 380
ht-degree: 33%

---

# Configuración de permisos de URL (local){#url-permissions}



La lista predeterminada de direcciones URL a las que pueden llamar los códigos JavaScript (flujos de trabajo, etc.) por las instancias de Campaign Classic es limitada. Son direcciones URL que permiten que las instancias funcionen correctamente.

De forma predeterminada, las instancias no pueden conectarse a direcciones URL externas. Sin embargo, es posible añadir algunas direcciones URL externas a la lista de direcciones URL autorizadas para que la instancia pueda conectarse a ellas. Esto le permite conectar las instancias de Campaign a sistemas externos como, por ejemplo, servidores SFTP o sitios web para habilitar la transferencia de datos o archivos.

>[!NOTE]
>
>Este procedimiento está restringido a **implementaciones locales**.
>
>Como cliente de **hosted**, si puede acceder al [Panel de control de Campaign de Campaign](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=es), puede usar la interfaz de autoservicio de permisos de URL. [Más información](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/url-permissions.html?lang=es)
>
>Otros clientes **híbridos/alojados** deben ponerse en contacto con el equipo de soporte de Adobe para agregar la IP a la lista de permitidos.
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

* [documentación del Panel de control de Campaign](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=es)
* [Modelos de alojamiento](hosting-models.md)
* [Configuración del servidor de Campaign](configuring-campaign-server.md)
* [Parámetros del archivo de configuración del servidor Campaign](the-server-configuration-file.md)
* [Lista de comprobación de seguridad y privacidad](get-started-security-privacy.md)
