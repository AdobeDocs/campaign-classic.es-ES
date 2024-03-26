---
product: campaign
title: Nota técnica - Adobe Campaign - Actualización de seguridad de la versión de Apache
description: 'Adobe Campaign: Actualización de seguridad de la versión de Apache'
feature: Technote, Upgrade
hide: true
hidefromtoc: true
exl-id: 3d2f5d1d-4b31-4cc6-b6fb-13589856e00c
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 2%

---

# Adobe Campaign: Actualización de seguridad de la versión de Apache {#apache-update}

>[!CAUTION]
>Este artículo se aplica a: **Campaign Classic v7 Managed Services** clientes, **Campaign v8** clientes y **Campaign Standard** clientes.

Adobe Campaign funciona con herramientas de terceros y la compatibilidad se actualiza de forma regular para implementar únicamente versiones compatibles y beneficiarse de las últimas correcciones y mejoras.

Adobe Campaign incluye Apache Tomcat, que actúa como punto de entrada en el servidor de aplicaciones a través de HTTP y está integrado con el servidor web Apache. Apache Software Foundation ha lanzado Apache HTTP Server 2.4.53. Esta versión aborda las vulnerabilidades que pueden permitir a un atacante remoto tomar el control de un sistema afectado. Obtenga más información en [Anuncio de Apache 2.4.53](https://downloads.apache.org/httpd/Announcement2.4.html){target="_blank"}.

El equipo de Adobe Campaign llevará a cabo la actividad de actualización de seguridad de la versión de Apache mediante **15 de junio de 2022** para mitigar esta vulnerabilidad de Apache y hacer que su entorno de instancia sea más seguro. Esta actualización se aplica a todos los clientes de Campaign Classic v7 Managed Services, Campaign v8 y los clientes de Campaign Standard que se ejecutan en una versión vulnerable de Apache HTTP Server. Si se ve afectado, Adobe ya se ha puesto en contacto con usted para informarle sobre esta actualización.

Se espera que esta actualización se ejecute automáticamente fuera del horario laboral normal para que pueda seguir utilizando el servicio de Campaign sin interrupciones.

Las instancias que no son de producción se actualizarán primero mediante Adobe y luego las instancias de producción se actualizarán. Dado que se trata de un proceso de actualización automática propiedad de Adobe, no se requiere ninguna acción por su parte. Sin embargo, si tiene algún problema, póngase en contacto con [Adobe del Servicio de atención al cliente](https://experienceleague.adobe.com/?support-solution=Campaign#support).


>[!NOTE]
>Esta actualización requiere reiniciar el servidor web Apache. El tiempo de inactividad no excederá los 10 minutos dentro del lapso de tiempo mencionado a continuación.
> 

## Preguntas frecuentes {#apache-faq}

* **¿Por qué es una actualización obligatoria?**

  La versión actual de Apache es vulnerable y tiene una amenaza de seguridad potencial. Es importante que las instancias de Campaign se actualicen a la última versión de Apache aplicable para hacer frente al riesgo de seguridad.

* **¿Qué clientes son el objetivo de las actualizaciones de seguridad?**

  Todos los clientes que utilizan entornos de Campaign implementados en versiones de Apache anteriores se actualizan a la última versión de Apache aplicable.

* **¿Cuál es el tiempo de inactividad esperado?**

  El tiempo de inactividad esperado es inferior a 10 minutos.

* **¿El cliente necesita llevar a cabo alguna acción para esta actualización de seguridad?**

  No se requiere ninguna acción, ya que la actualización de seguridad se ejecutará automáticamente.

* **¿Cuál es el impacto en la ejecución de campañas/flujos de trabajo durante la ventana de mantenimiento?**

  Durante la ventana de mantenimiento, el flujo de trabajo y los servicios de correo se detendrán y las actividades programadas no se ejecutarán. Cualquier actividad en curso o proceso en ejecución se detendrá durante el tiempo de inactividad hasta que se reinicie el servidor. Una vez completada la actividad y reiniciado el servidor, se reanudarán todos los servicios.

* **¿Qué validaciones deben ejecutar los clientes?**

  No se necesitan pruebas específicas para esta actualización de seguridad. Si se observa algún problema, póngase en contacto con [Adobe del Servicio de atención al cliente](https://experienceleague.adobe.com/?support-solution=Campaign#support).


* **¿Puedo solicitar un cambio de fecha y hora en el intervalo de actualización de seguridad programado?**

  Como se trata de una corrección de seguridad, le recomendamos encarecidamente que se adapte a la programación existente.


Para cualquier otra pregunta, puede contactar con el [Servicio de atención al cliente de Adobe](https://experienceleague.adobe.com/?support-solution=Campaign#support).
