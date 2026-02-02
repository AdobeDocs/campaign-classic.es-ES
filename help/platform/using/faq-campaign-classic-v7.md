---
product: campaign
title: Preguntas frecuentes sobre Campaign Classic
description: Preguntas específicas sobre la arquitectura, la implementación y las funciones de Adobe Campaign Classic v7
feature: Overview, Troubleshooting
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
source-git-commit: 8d9bb9d2ff4450646bbf218804b8c8b4459b5a91
workflow-type: tm+mt
source-wordcount: '1345'
ht-degree: 3%

---

# Preguntas frecuentes sobre Campaign Classic v7 {#campaign-classic-v7-faq}

>[!NOTE]
>
>Estas preguntas frecuentes responden a preguntas específicas sobre la arquitectura de Adobe Campaign Classic v7, los modelos de implementación y las funciones específicas de la versión 7.
>
>**Para obtener respuestas completas a las preguntas comunes sobre Campaign** (flujos de trabajo, envíos, audiencias, creación de informes, personalización, etc.), consulte [**Preguntas frecuentes completas sobre Campaign v8**](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/new/campaign-faq-comprehensive){target="_blank"}, que proporciona respuestas detalladas organizadas por temas.

## Arquitectura e implementación de Campaign Classic v7 {#v7-architecture}

Encuentre respuestas acerca de modelos de alojamiento, diferencias de implementación y rutas de migración para Campaign Classic v7. Estas preguntas se centran en las opciones de infraestructura y las responsabilidades relacionadas.

+++ ¿Cuáles son los modelos de alojamiento disponibles en Campaign Classic v7? {#what-are-the-hosting-models-available-in-campaign-classic-v7}

Adobe Campaign Classic v7 ofrece tres modelos de implementación:

* **Alojado (Managed Services)**: administrado completamente por Adobe en la infraestructura de Adobe
* **Local**: instalado y administrado en su propia infraestructura
* **Híbrido**: arquitectura intermediaria con mezcla de componentes locales y de nube

Cada modelo de implementación tiene diferentes capacidades y responsabilidades de administración. La disponibilidad de los módulos, las opciones y las configuraciones depende del tipo de implementación.

[Haga clic aquí para obtener más información](../../installation/using/hosting-models.md) acerca de los modelos de alojamiento y sus diferencias.

**Nota:** Campaign v8 está disponible exclusivamente como Cloud Services administrados. [Más información sobre la versión 8 de Campaign](https://experienceleague.adobe.com/docs/campaign/campaign-v8/new/whats-new.html){target="_blank"}.

+++

+++ ¿Cuáles son las diferencias entre trabajar On-Premise y en un entorno alojado?{#what-are-the-differences-when-working-on-premise-vs-in-a-hosted-environment}

Adobe Campaign Classic v7 incluye un conjunto de módulos y opciones. La disponibilidad de estos módulos y su configuración dependen del [tipo de implementación](../../installation/using/hosting-models.md) de la instalación: alojado (Managed Services), híbrido o local.

Diferencias clave:

* **On-Premise**: control total de la instalación, infraestructura y configuración. Requiere recursos de TI internos para mantenimiento, actualizaciones y seguridad.
* **Alojado/Managed Services**: infraestructura y mantenimiento administrados por Adobe. Actualizaciones automáticas y seguridad mejorada. Acceso directo limitado al servidor.
* **Híbrido**: combina las ventajas de ambos modelos. Instancia de marketing alojada por Adobe, ejecución/intermediario administrada por separado.

[Haga clic aquí para ver la matriz de capacidades completa](../../installation/using/capability-matrix.md).

+++

+++ ¿Cómo migre de local/híbrido a Adobe Managed Services? {#how-do-i-migrate-from-on-premise-hybrid-to-adobe-managed-services}

La migración a Adobe Managed Services ofrece una escalabilidad y seguridad mejoradas y reduce la sobrecarga de TI. A menudo es un paso importante antes de pasar a Campaign v8.

**Puntos clave:**

* No hay ninguna herramienta de migración automatizada disponible: se requiere planificación y ejecución manuales
* Se recomienda encarecidamente soporte de Adobe Professional Services
* Las ventajas incluyen infraestructura en la nube, parches de seguridad automáticos, asistencia técnica especializada y una ruta más sencilla hacia la versión 8 de
* La migración implica la diligencia debida, la auditoría del entorno, la limpieza de datos, la migración de etapas y la migración total de la producción

**Introducción:** Póngase en contacto con su representante de Adobe para evaluar su entorno y desarrollar un plan de migración detallado con Adobe Professional Services.

Más información sobre [migrar a Managed Services](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic-blogs/migrate-your-adobe-campaign-v7-onprem-hybrid-environment-to/ba-p/681605){target="_blank"}.

+++

+++ ¿Debería migrar de Campaign Classic v7 a Campaign v8? {#should-i-migrate-to-v8}

La versión 8 de Campaign es la plataforma estratégica de Adobe, ideal para organizaciones que necesitan campañas de gran volumen, una interfaz de usuario web moderna, beneficios nativos de la nube y asistencia a largo plazo. Campaign Classic v7 llegará al fin de la asistencia en los próximos años.

**Considere migrar a Campaign v8 si:**

* Gestionar grandes volúmenes de datos o problemas de rendimiento de experiencias
* Desea reducir la sobrecarga de TI y la administración de la infraestructura (la versión 8 solo es Cloud Services administrados)
* Necesita una interfaz de usuario moderna e integración con Adobe Experience Platform
* Desea una tecnología preparada para el futuro con actualizaciones automáticas
* Están actualmente en servicios alojados/administrados (ruta de migración más sencilla)

**Consideraciones importantes:**

* Campaign v8 solo está disponible como Cloud Services administrados (sin opciones locales/híbridas)
* Requiere planificación para la migración de personalizaciones e integraciones
* La arquitectura de FDAC ofrece rendimiento, pero requiere algunas adaptaciones de flujo de trabajo/API

**Pasos siguientes:** Póngase en contacto con su representante de Adobe para evaluar la preparación para la migración y acceder a las herramientas de migración.

Más información:

* [Información general de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/new/whats-new.html){target="_blank"}
* [Transición de Campaign Classic v7 a v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/v7-to-v8.html){target="_blank"}
* [Preguntas frecuentes completas sobre Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html?lang=es){target="_blank"}

**Para obtener respuestas detalladas a preguntas comunes de Campaign sobre flujos de trabajo, envíos, audiencias, creación de informes, personalización y mucho más**, visite [Preguntas frecuentes completas de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html?lang=es){target="_blank"}.

+++

## Actualizaciones de compilación (Campaign Classic v7) {#build-upgrades-v7}

Para obtener instrucciones sobre la actualización de compilaciones y preguntas más frecuentes relacionadas, consulte [Preguntas frecuentes sobre la actualización de compilaciones](faq-build-upgrade.md) y [Documentación sobre la actualización de compilaciones](../../production/using/build-upgrade.md).

## Configuración de Campaign Classic v7 {#v7-configuration}

Estas preguntas tratan sobre tareas y directivas de configuración comunes en Campaign Classic v7, desde la configuración de idioma hasta la seguridad. Utilícelos para validar las opciones de configuración y las prácticas operativas.

+++ ¿Puedo cambiar el idioma de la interfaz de Campaign Classic v7? {#can-i-change-language-v7}

El idioma de Campaign Classic v7 se selecciona al crear la instancia. **No puede cambiarlo posteriormente.**

La interfaz de usuario de Adobe Campaign v7 está disponible en 4 idiomas: inglés, francés, alemán y japonés. La consola de cliente y el servidor deben estar configurados en el mismo idioma. Cada instancia de Campaign Classic v7 solo se puede ejecutar en un idioma.

Para inglés, al instalar Campaign v7, puede seleccionar inglés de EE. UU. o inglés de Reino Unido: difieren en los formatos de fecha y hora.

[Obtenga más información en esta sección](../../installation/using/creating-an-instance-and-logging-on.md).

**Nota:** La interfaz de usuario web de Campaign v8 permite a los usuarios cambiar el idioma de la interfaz de forma independiente. [Más información](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/connect.html#language-pref){target="_blank"}.

+++

+++ ¿Cómo puedo configurar las zonas de seguridad en Campaign Classic v7? {#how-can-i-configure-security-zones-v7}

La interfaz de autoservicio de zonas de seguridad se puede utilizar para administrar entradas en la configuración de la zona de seguridad de una VPN de una implementación de Adobe Campaign Classic v7. Esto es principalmente relevante para implementaciones locales e híbridas.

Lea [esta sección](../../installation/using/security-zones.md) para obtener más información sobre las zonas de seguridad en Campaign v7.

[Haga clic aquí para obtener más información](https://helpx.adobe.com/es/campaign/kb/configuring-security-zones-self-service.html){target="_blank"} acerca de la interfaz de usuario de autoservicio de la zona de seguridad.

**Nota:** Los clientes alojados o de Managed Services deben ponerse en contacto con Adobe para configurar las zonas de seguridad.

+++

+++ ¿Se puede integrar Adobe Campaign Classic v7 con LDAP? {#can-campaign-classic-integrate-with-ldap}

Sí. Como **cliente on-premise/híbrido**, puede integrar Campaign Classic v7 con su directorio LDAP para la autenticación centralizada y la administración de usuarios.

Esta integración permite:

* Usuarios que se autentican en el directorio LDAP corporativo
* Administración centralizada de usuarios y derechos
* Sincronización automática de grupos de usuarios y permisos
* Funciones de inicio de sesión único

[Haga clic aquí para obtener información](../../installation/using/connecting-through-ldap.md) sobre cómo configurar la integración de LDAP en Campaign Classic v7.

**Nota:** La integración de LDAP está disponible para implementaciones locales e híbridas. Los clientes alojados utilizan Adobe IMS para la autenticación.

+++

+++ ¿Cuáles son las prácticas recomendadas de seguridad para implementaciones locales? {#security-best-practices-on-premise}

Las implementaciones on-premise e híbridas requieren una configuración de seguridad y una protección adicionales en comparación con los entornos alojados.

**Áreas de seguridad clave:**

* Seguridad de red y configuración del cortafuegos
* Acceso y seguridad a bases de datos
* Endurecimiento del sistema operativo
* Permisos de archivos y controles de acceso
* Configuración de zonas de seguridad
* Cifrado (datos en reposo y en tránsito)
* Administración de acceso de usuario
* Parches de seguridad regulares
* Registro y monitorización de auditorías

Lea la [lista de comprobación de la configuración de seguridad](https://helpx.adobe.com/es/campaign/kb/acc-security.html){target="_blank"} para descubrir elementos clave, comprobar la configuración de seguridad y reforzar las implementaciones locales.

+++

+++ ¿Cómo borro la caché de la consola del cliente? {#how-do-i-clear-console-cache}

Borrar la caché de la consola del cliente de Campaign resuelve muchos problemas comunes de visualización y funcionalidad. La caché almacena archivos de configuración local que a veces pueden dañarse o quedar obsoletos.

**Cuándo borrar la caché:**

* Los nuevos elementos de personalización de marca no se muestran correctamente
* Error inesperado en las funciones de exportación/importación
* Los elementos de la interfaz no se actualizan después de cambios de configuración
* Problemas de rendimiento o respuesta lenta de la consola
* Después de actualizar a una nueva versión de la consola del cliente

**Cómo borrar la caché:**

1. **Borrar caché de software (intente esto primero):**
   * Abra la consola del cliente de Campaign
   * Ir al menú **[!UICONTROL File]**
   * Seleccionar **[!UICONTROL Clear the local cache...]**
   * Confirme la acción cuando se le solicite
   * Reinicie la consola del cliente

2. **Borrado de caché de disco duro (si el borrado suave no resuelve el problema):**
   * Realice primero el borrado de caché de software
   * Cierre la sesión y la consola de cliente por completo
   * Vaya a:
      * Windows 7/10: `C:\Users\<Username>\AppData\Roaming\Neolane\NL_5\`
      * Windows XP: `C:\Documents and Settings\<Username>\Application Data\Neolane\NL_5\`
   * Eliminar todos los archivos XML llamados `nlclient-config-<alphanumerical value>.xml` y las carpetas asociadas
   * **Importante:** NO elimine el archivo `nlclient_cnx.xml`
   * Reiniciar la consola de cliente

Obtenga más información en [Documentación de la consola del cliente de Campaign](../../platform/using/launching-adobe-campaign.md).

+++

+++ ¿Dónde pueden administrar la configuración de las instancias los clientes alojados? {#where-to-manage-instance-settings}

El [Panel de control de Campaign](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=es){target="_blank"} ayuda a los administradores de productos de Adobe Campaign a administrar la configuración y a rastrear el uso de cada instancia. Su intuitiva interfaz le permite supervisar los recursos clave y realizar tareas de gestión, como actualizaciones de listas de permitidos IP, supervisión del almacenamiento SFTP, administración de claves, etc.

**Ventajas principales:**

* Cambie la configuración rápidamente sin ponerse en contacto con el Servicio de atención al cliente.
* Configure las opciones en función de las diferentes necesidades comerciales en distintos momentos.
* Mejore la seguridad controlando la configuración de acceso según sus necesidades.

+++

## Obtención de ayuda {#getting-help}

Encuentre documentación clave, preguntas frecuentes y canales de asistencia para Campaign Classic v7, incluidos vínculos a foros de la comunidad y asistencia de Adobe.

+++ ¿Dónde puedo encontrar la documentación de Campaign Classic v7? {#where-to-find-more-info-v7}

**Documentación y recursos:**

* [Documentación de Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/campaign-classic-home.html?lang=es){target="_blank"} - Documentación completa
* [Notas de la versión de Campaign Classic v7](../../rn/using/latest-release.md) - Información de la versión más reciente
* [Matriz de compatibilidad de Campaign Classic](../../rn/using/compatibility-matrix.md) - Sistemas y versiones compatibles
* [Tutoriales de Campaign Classic](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=es){target="_blank"}: tutoriales en vídeo

**Para preguntas comunes de Campaign:**

Consulte las [**Preguntas frecuentes completas sobre la versión 8 de Campaign**](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html?lang=es){target="_blank"}, que proporcionan respuestas detalladas sobre:

* Introducción a Campaign
* Perfiles y públicos
* Diseño y envío de mensajes
* Flujos de trabajo y automatización
* Creación de informes y análisis
* Configuración y configuración de Campaign
* Recursos para desarrolladores
* Privacidad y cumplimiento

+++

+++ ¿Cómo puedo obtener asistencia de la comunidad o de Adobe para Campaign Classic v7? {#where-to-get-support-v7}

**Comunidad y soporte técnico:**

* [Foros de la comunidad Campaign](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic/ct-p/adobe-campaign-classic-community){target="_blank"}
* [Soporte de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}

+++
