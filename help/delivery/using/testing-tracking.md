---
title: Seguimiento de pruebas
seo-title: Seguimiento de pruebas
description: Seguimiento de pruebas
seo-description: null
page-status-flag: never-activated
uuid: 76d84ab4-b632-4498-96a1-ce9c773ec125
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: tracking-messages
discoiquuid: 4ed23249-4ecf-4e57-91b3-6fae1387bd6a
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 100%

---


# Seguimiento de pruebas{#testing-tracking}

Puede probar el seguimiento en páginas espejo, “logs” de correo electrónico y vínculos. Para ello:

1. Cree un nuevo envío de correo electrónico que se utiliza para realizar pruebas.
1. Especifique el usuario que debe recibir el correo electrónico. Dado que este usuario debe abrir el correo electrónico y hacer clic en los vínculos que contiene, asegúrese de seleccionar una dirección de destinatario de la prueba que usted controle.
1. Añada un bloque de personalización de páginas espejo (MirrorPage) en el contenido del correo electrónico.
1. Realice la entrega que contiene un vínculo a la página espejo.
1. Una vez que haya recibido el correo electrónico, ábralo y haga clic en el vínculo de la página espejo.
1. Una vez que se le haya redirigido correctamente a la página espejo, acceda a la carpeta **Administration > Technical workflows** y abra el flujo de trabajo **Tracking**.
1. Inicie el flujo de trabajo, haga clic con el botón derecho en la actividad **Programador** y seleccione **Ejecutar ahora tarea pendiente**.
1. Espere unos 30 segundos y, a continuación, seleccione la pestaña **Auditoría.** Asegúrese de que se encuentre al menos un “log” de seguimiento.

   Haga clic en **Actualizar** si no ve ningún “log” nuevo.

1. Vaya a la página de perfil del destinatario que utilizó para la prueba y seleccione la pestaña **Seguimiento.** Algunos registros deben aparecer con el valor **Página espejo** en la columna **Tipo**.

   >[!NOTE]
   >
   >La página de perfil del destinatario se encuentra en la carpeta **Profiles and Targets > Recipients** de forma predeterminada.

   Para comprobar el seguimiento del registro de correo electrónico, busque los valores **Open** y **[!UICONTROL Email click]** en la columna **Type**.

   Si no aparecen los registros de aperturas, vaya a la entrega y acceda a su **Properties** para asegurarse de que las opciones **Activate tracking** y **[!UICONTROL Opens tracking]** estén seleccionadas.

