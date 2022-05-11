---
product: campaign
title: Nota técnica - Adobe Campaign - Actualización de seguridad de la versión Apache
description: 'Adobe Campaign: actualización de seguridad de la versión de Apache'
hide: true
hidefromtoc: true
exl-id: 3d2f5d1d-4b31-4cc6-b6fb-13589856e00c
source-git-commit: 854278e3e2013293888ea194c12ec1a75e70d981
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 3%

---

# Adobe Campaign: actualización de seguridad de la versión de Apache {#apache-update}

>[!NOTE]
>Este artículo se aplica a:
> * Campaign Classic v7 clientes de Managed Services
> * Clientes de Campaign v8
> * clientes Campaign Standards



Adobe Campaign funciona con herramientas de terceros, y la compatibilidad se actualiza de forma regular para implementar únicamente versiones compatibles y beneficiarse de las últimas correcciones y mejoras.

Adobe Campaign incluye Apache Tomcat que actúa como punto de entrada en el servidor de aplicaciones a través de HTTP y está integrado con el servidor web Apache. La Apache Software Foundation ha lanzado Apache HTTP Server 2.4.53. Esta versión aborda vulnerabilidades que pueden permitir que un atacante remoto tome el control de un sistema afectado. Obtenga más información en [Anuncio de Apache 2.4.53](https://downloads.apache.org/httpd/Announcement2.4.html){target=&quot;_blank&quot;}.

El equipo de Adobe Campaign dirigirá la actividad de actualización de seguridad de la versión de Apache de **31 de mayo de 2022** para mitigar esta vulnerabilidad de Apache y hacer que su entorno de instancia sea más seguro. Esta actualización se aplica a todos los clientes de Managed Services de Campaign Classic v7, Campaign v8 y Campaign Standards que ejecutan una versión vulnerable de Apache HTTP Server. Si se ve afectado, Adobe ya se ha puesto en contacto con usted para informarle sobre esta actualización.

Se espera que esta actualización se ejecute automáticamente fuera del horario laboral normal para que pueda seguir utilizando el servicio de Campaign sin interrupciones.

Nuestros equipos actualizarán primero las instancias que no sean de producción antes de actualizar las instancias de producción. Como este es un proceso de actualización automática propiedad de Adobe, no es necesario que realice ninguna acción por su parte. Sin embargo, si experimenta algún problema, póngase en contacto con [Servicio de atención al cliente de Adobe](https://experienceleague.adobe.com/?support-solution=Campaign#support).


>[!NOTE]
>Esta actualización requiere reiniciar el servidor web Apache. El tiempo de inactividad no excederá los 10 minutos dentro del intervalo de tiempo mencionado a continuación.

## Preguntas frecuentes {#apache-faq}

* **¿Por qué se trata de una actualización obligatoria?**

   La versión actual de Apache es vulnerable y puede suponer una amenaza para la seguridad. Es importante que las instancias de Campaign se actualicen a la última versión aplicable de Apache para abordar el riesgo de seguridad.


* **¿A qué clientes se dirigen las actualizaciones de seguridad?**

   Todos los clientes que utilizan entornos de Campaign implementados en versiones anteriores de Apache se actualizan a la última versión aplicable de Apache.

* **¿Cuál es el tiempo de inactividad esperado?**

   El tiempo de inactividad esperado es inferior a 10 minutos.

* **¿Hay alguna acción que el cliente necesite para esta actualización de seguridad?**

   No se requiere ninguna acción, ya que la actualización de seguridad se ejecutará automáticamente.

* **¿Qué validaciones deben ejecutar los clientes?**

   No es necesario realizar pruebas específicas para esta actualización de seguridad. En caso de que se observe algún problema, póngase en contacto con [Servicio de atención al cliente de Adobe](https://experienceleague.adobe.com/?support-solution=Campaign#support)


* **¿Puedo solicitar un cambio en la fecha y la hora en la ranura de actualización de seguridad programada?**

   Como se trata de una solución de seguridad, le recomendamos encarecidamente que se adapte a la programación existente.


Para cualquier otra pregunta, puede contactar con el [Servicio de atención al cliente de Adobe](https://experienceleague.adobe.com/?support-solution=Campaign#support).
