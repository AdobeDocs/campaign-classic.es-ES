---
product: campaign
title: Prueba del seguimiento de mensajes
description: Obtenga información sobre cómo probar el seguimiento de mensajes
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
feature: Monitoring
role: User
exl-id: 16ad36b7-c13e-4b77-86ca-41c9ef174172
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: ht
source-wordcount: '266'
ht-degree: 100%

---

# Prueba del seguimiento de mensajes{#testing-tracking}

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
