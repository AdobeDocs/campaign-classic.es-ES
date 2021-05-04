---
solution: Campaign Classic
product: campaign
title: Nota técnica
description: Nota técnica
hide: true
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 51773f48bac90febe44c6796b8cc08fce072bab3
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 7%

---

# Problema de firma de URL rastreadas {#tracked-urls}

Tras los cambios recientes, las direcciones URL rastreadas pueden fallar cuando la firma de URL está activa en Campaign. Algunos buzones pueden verse más afectados que otros, ya que algunas empresas cuentan con herramientas de seguridad específicas que pueden afectar a los vínculos y alterar el mecanismo de firma de la dirección URL.

Como consecuencia, Adobe recomienda desactivar el mecanismo de firma para el seguimiento de vínculos. Este procedimiento corrige los vínculos de seguimiento antiguos, excepto los recibidos con una doble omisión.

Tenga en cuenta que los vínculos de baja pueden fallar como cualquier otro vínculo, la frecuencia es variable de host a host pero es inferior al 1%.

**¿Estás afectado?**

Para mejorar la seguridad, el mecanismo de firma para el seguimiento de vínculos en correos electrónicos se ha introducido en [Campaign Gold Standard 8](../rn/using/gold-standard.md#gs8) - Abril de 2020 - y está habilitado de forma predeterminada para todos los clientes a partir de la versión 19.1.4 (9032@3a9dc9c) y Campaign 20.2.

Si su entorno se ejecuta en una de las versiones enumeradas a continuación, puede verse afectado:

* Gold Standard 8 a 11. [Obtenga más información](../rn/using/gold-standard.md#gs-8)
* Versiones de Campaign 21.1.1 (compilación 9277) a 21.1.2 (compilación 9282). [Obtenga más información](../rn/using/latest-release.md)
* Versiones de Campaign 20.3.1 (compilación 9228) a 20.3.3 (compilación 9234). [Obtenga más información](../rn/using/release--20-3.md)
* Versiones de Campaign 20.2.1 (versión 9178) a 20.2.4 (versión 9187). [Obtenga más información](../rn/using/release--20-2.md)
* Versiones de Campaign 20.1.1 (compilación 9122) a 21.1.3 (compilación 9124). [Obtenga más información](../rn/using/release--20-1.md)
* Versiones de Campaign 19.2.2 (compilación 9080) a 19.2.3 (compilación 9081). [Obtenga más información](../rn/using/release--19-2.md)
* Versiones de Campaign 19.1.5 (compilación 9033) a 19.1.7 (compilación 9036). [Obtenga más información](../rn/using/release--19-1.md)

Aprenda a comprobar su versión [en esta sección](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**¿Cómo se actualiza?**

Como **cliente alojado**, Adobe trabajará con usted para actualizar su configuración en breve.

Como **cliente local/híbrido**, debe actualizar su configuración.

Siga el paso siguiente:

1. En el [archivo de configuración del servidor](../installation/using/the-server-configuration-file.md) (serverConf.xml), cambie **signEmailLinks** a **false**.
1. Reinicie el servicio **nlserver**.
1. En el servidor de seguimiento, reinicie el servidor web (apache2 en Debian, httpd en CentOS/RedHat, IIS en Windows).

   ```
   nlserver restart web
   ```

>[!NOTE]
>
>El archivo **config-`<instance>`.xml** anula la configuración de **serverConf.xml**. Si el **signEmailLinks** está presente en el **config-`<instance>`.xml** (donde **instance** es el nombre de su instancia), también debe convertirse en **false**.


**¿Cuál es el impacto?**

El mantenimiento requiere un tiempo de inactividad máximo de 25 minutos y durante este periodo todas las entregas, los vínculos de seguimiento y las llamadas a la API no funcionarán.

Una vez completada la actualización, todos los vínculos funcionan según lo esperado.

>[!NOTE]
>
>Para cualquier pregunta acerca de estos cambios, póngase en contacto con el [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

