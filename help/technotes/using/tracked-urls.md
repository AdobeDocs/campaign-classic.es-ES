---
product: campaign
title: Problema de firma de URL rastreadas
description: Problema de firma de URL rastreadas
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
hide: true
hidefromtoc: true
exl-id: e7d4331b-7149-4768-8e46-2e2911319074
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 37%

---

# Problema de firma de URL rastreadas {#tracked-urls}



Tras los cambios recientes, las direcciones URL rastreadas pueden fallar cuando la firma de URL está activa en Campaign. Algunos buzones pueden verse más afectados que otros, ya que algunas empresas cuentan con herramientas de seguridad específicas que pueden afectar a los vínculos y alterar el mecanismo de firma de las URL.

Como consecuencia, Adobe recomienda desactivar el mecanismo de firma para el seguimiento de vínculos. Este procedimiento corrige los vínculos de seguimiento antiguos, excepto los recibidos con una doble omisión.

Tenga en cuenta que los vínculos de baja pueden dar error como los demás. La frecuencia es variable en función del host, pero es inferior al 1 %.

**¿Se ha visto afectado?**

Para mejorar la seguridad, se ha introducido el mecanismo de firma para el seguimiento de vínculos en correos electrónicos en [Campaign Gold Standard 8](../../rn/using/gold-standard.md#gs8) - Abril de 2020 - y está habilitado de forma predeterminada para todos los clientes que comienzan la versión 19.1.4 (9032@3a9dc9c) y Campaign 20.2.

Si su entorno se ejecuta en una de las versiones enumeradas a continuación, puede verse afectado:

* Gold Standard 8 a 11. [Más información](../../rn/using/gold-standard.md#gs-8)
* Versiones de Campaign 21.1.1 (compilación 9277) a 21.1.2 (compilación 9282). [Más información](../../rn/using/latest-release.md)
* Versiones de Campaign 20.3.1 (compilación 9228) a 20.3.3 (compilación 9234). [Más información](../../rn/using/release--2020.md#release-20-3)
* Versiones de Campaign 20.2.1 (versión 9178) a 20.2.4 (versión 9187). [Más información](../../rn/using/release--2020.md#release-20-2)
* Versiones de Campaign 20.1.1 (compilación 9122) a 21.1.3 (compilación 9124). [Más información](../../rn/using/release--2020.md#release-20-1)
* Versiones de Campaign 19.2.2 (compilación 9080) a 19.2.3 (compilación 9081). [Más información](../../rn/using/release--2019.md#release-19-2)
* Versiones de Campaign 19.1.5 (compilación 9033) a 19.1.7 (compilación 9036). [Más información](../../rn/using/release--2019.md#release-19-1)


Descubra cómo comprobar su versión [en esta sección](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**¿Cómo realizar la actualización?**

Como **cliente alojado**, Adobe trabajará con usted para actualizar su configuración en breve.

Como **cliente local/híbrido**, debe actualizar la configuración.

Siga el paso siguiente:

1. En el [archivo de configuración del servidor](../../installation/using/the-server-configuration-file.md) (serverConf.xml), cambiar **signEmailLinks** a **false**.
1. Reinicie el servicio **nlserver**.
1. En el servidor de seguimiento, reinicie el servidor web (apache2 en Debian, httpd en CentOS/RedHat, IIS en Windows).

   ```
   nlserver restart web
   ```

>[!NOTE]
>
>La variable **config-`<instance>`.xml** anula los valores de **serverConf.xml** configuración. Si la variable **signEmailLinks** está presente en la variable  **config-`<instance>`.xml** (donde **instancia** es el nombre de su instancia), también debe convertirse en **false**.

**¿Cuáles son las consecuencias?**

Las tareas de mantenimiento requieren un tiempo de inactividad máximo de 25 minutos y, durante este periodo, todas las entregas, los vínculos de seguimiento y las llamadas a la API no funcionarán.

Una vez completada la actualización, todos los vínculos funcionarán según lo esperado.

>[!NOTE]
>
>En caso de que tenga preguntas acerca de estos cambios, póngase en contacto con el [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
