---
product: campaign
title: Último lanzamiento
description: Notas de la versión más reciente de Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
TQID: https://experienceleague.adobe.com/Xq9y8r6xU-hypq1Eeo9ijaiGng7qqkWVqiCXW5fYx2c
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
level_v2: id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: d095671a-1355-40aa-8b5f-06c33c68080bid: e0eb8757-182f-49f3-94a4-1587d16f5094
feature_v2: []
subfeature_v2: id: e5e477db-ebc7-4368-ab0f-4d8fc2aed405id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
source-git-commit: a9e48513ed4ceb2650d0eeff18563a010a148c80
workflow-type: tm+mt
source-wordcount: 498
ht-degree: 81%

---

# Último lanzamiento {#latest-release}

Esta página lista las nuevas funcionalidades, mejoras y correcciones que se proporcionan con la **última versión de Campaign Classic v7**. Cada nueva compilación viene con un estado que se materializa con un color. Obtenga más información sobre los estados de compilación de Campaign Classic v7 en [esta página](rn-overview.md).

## Versión 7.4.3 {#release-7-4-3}

### Compilación 9397 {#build-9397}

[!BADGE Disponibilidad general]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=es#rn-statuses" tooltip="Disponibilidad general"}

_30 de junio de 2026_

#### Mejoras de seguridad {#security-7-4-3-9397}

Esta compilación incluye correcciones de seguridad. Es la versión de General Availability recomendada y reemplaza a las versiones de Campaign Classic v7 anteriores.

#### Otros cambios {#changes-7-4-3-9397}

De forma predeterminada, webForm.jsp ahora ignora los parámetros `ctx` proporcionados por el cliente. Esto se controla mediante el parámetro `disableCtxInWebForm`, que está establecido en &quot;true&quot; de forma predeterminada.

Si las solicitudes de webForm pasan actualmente un parámetro `ctx` en, puede volver a habilitar temporalmente este comportamiento agregando lo siguiente a <web> elemento de su configuración<instance>archivo .xml. Planifique la eliminación gradual de este uso.

```
<web>
  ...
  <jsp disableCtxInWebForm="false" />
  ...
</web>
```

### Compilación 9396 {#build-9396}

[!BADGE Obsoleto]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=es#rn-statuses" tooltip="Obsoleto"}

_9 de junio de 2026_

Esta compilación incluye correcciones de seguridad.

### Compilación 9394 {#build-9394}

[!BADGE Obsoleto]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=es#rn-statuses" tooltip="Obsoleto"}

>[!CAUTION]
>
> La actualización de la consola de cliente es obligatoria.

_31 de marzo de 2026_

#### Mejoras de seguridad {#security-7-4-3}

* Para mantener una seguridad, estabilidad y conformidad óptimas, Debian se ha actualizado a la versión 13 y PostgreSQL a la versión 17. Consulte la [matriz de compatibilidades](compatibility-matrix.md).

#### Correcciones {#fixes-7-4-3}

>[!NOTE]
>
> Las correcciones enumeradas a continuación se han implementado progresivamente en sucesivas versiones 7.4.3. Vaya al [menú](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) **[!UICONTROL Help > About...]** para comprobar que dispone de la última versión de 9394@28aaec9. Póngase en contacto con su representante de Adobe para obtener más información.

* Se ha corregido un problema en el cual el componente de código de barras permitía un parámetro de altura sin límites, lo que podría provocar una vulnerabilidad de seguridad. (NEO-89984)
* Se ha corregido un problema en el cual a los campos de enumeración de las listas creadas mediante flujos de trabajo les faltaban atributos de nombre temporales, lo que provocaba que se mostraran etiquetas de enumeración incorrectas o en blanco en la interfaz. (NEO-91158)
* Se corrigió un problema en el cual la preparación del envío fallaba con errores de personalización al utilizar campos targetData en flujos de trabajo con actividades de anulación de duplicación. (NEO-87693)
* Se ha corregido un problema en el cual la concatenación de campos de cadena de un solo carácter con otras cadenas fallaba en PostgreSQL 15 debido a los requisitos de conversión de tipos. (NEO-88028)
* Se ha corregido un problema en el cual los registros de seguimiento de las campañas de colaboración en Distributed Marketing no se escribían en la base de datos debido a una discrepancia entre los ID de envío principales y secundarios. (NEO-86836)
* Se ha corregido un problema por el cual los registros de envío mostraban mensajes como cancelados aunque se hubieran enviado correctamente, lo que afectaba especialmente a los envíos con programación de olas. (NEO-78933)
* Se corrigió un problema en el cual el flujo de trabajo de limpieza de la base de datos no depuraba los datos de forma eficaz, lo que podría afectar al rendimiento. (NEO-76439)

<!-- BUILD 7.0.9394.28aaec9 -->

* Se ha corregido un problema por el cual las estadísticas de entrega no se volvían a calcular completamente para algunos envíos, lo que afectaba especialmente a los indicadores de éxito. (NEO-88106) <!-- moved from original 7.4.3 GA Fixes section -->
* Se ha corregido un problema en el cual la consola del cliente podía bloquearse al abrir ciertos flujos de trabajo que hacían referencia a un esquema de segmentación ascendente que faltaba. (NEO-28727)
* Se ha corregido un problema en el cual la versión de la consola del cliente no se podía identificar después de un inicio fallido, porque faltaba el archivo de versión en el paquete de instalación. (NEO-94798)

<!--
other fixes - ommitted from release notes

Internal/non-customer-facing:

* Fixed an internal DevOps build race condition when copying the `teradata_timezones.txt` file during build packaging. (NEO-66532) — internal only; the Jira description states "No impact for customers: either it builds (99.9% of the time) or it does not."
* Fixed an internal CI/CD issue where AWS CodeBuild jobs could fail randomly on EC2 Docker containers when copying files during build. (NEO-90823) — internal CI/CD infrastructure only

Customer-specific hotfixes:

* Fixed an issue where coupon assignment could fail during delivery message preparation due to a SQL syntax error when looking up coupon codes. (NEO-92857) — Verizon only
* Fixed an issue where the error count and status in the `nms:address` table were not consistently updated on the marketing server after recurring soft bounces, causing recipients to not be quarantined as expected even though they were correctly flagged on the mid-sourcing server. (NEO-94422) — Walgreens only
-->

