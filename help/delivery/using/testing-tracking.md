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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Seguimiento de pruebas{#testing-tracking}

Puede probar el seguimiento en páginas espejo, “logs” de correo electrónico y enlaces. Para ello:

1. Cree un nuevo envío de correo electrónico que se utiliza para realizar pruebas.
1. Especifique el usuario que debe recibir el correo electrónico. Dado que este usuario debe abrir el correo electrónico y hacer clic en los enlaces que contiene, asegúrese de seleccionar una dirección de destinatario de la prueba que usted controle.
1. Añada un bloque de personalización de páginas espejo (MirrorPage) en el contenido del correo electrónico.
1. Realice el envío que contiene un enlace a la página espejo.
1. Una vez que haya recibido el correo electrónico, ábralo y haga clic en el enlace de la página espejo.
1. After you are correctly redirected to the mirror page, access the **Administration > Technical workflows** folder and open the **Tracking** workflow.
1. Inicie el flujo de trabajo, haga clic con el botón derecho en la actividad **Programador** y seleccione **Ejecutar ahora tarea pendiente**.
1. Espere unos 30 segundos y, a continuación, seleccione la pestaña **Auditoría.** Asegúrese de que se encuentre al menos un “log” de seguimiento.

   Haga clic en **Actualizar** si no ve ningún “log” nuevo.

1. Vaya a la página de perfil del destinatario que utilizó para la prueba y seleccione la pestaña **Seguimiento.** Algunos registros deben aparecer con el valor **Página espejo** en la columna **Tipo**.

   >[!NOTE]
   >
   >The recipient&#39;s profile page is located in the **Profiles and Targets > Recipients** folder by default.

   To check the email log tracking, look for the values **Open** and **[!UICONTROL Email click]** in the **Type** column.

   If the open logs do not appear, go to the delivery and access its **Properties** to make sure that both **Activate tracking** and **[!UICONTROL Opens tracking]** options are checked.

