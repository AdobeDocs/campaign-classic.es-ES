---
title: Solución de problemas del conector ACS
seo-title: Solución de problemas del conector ACS
description: Solución de problemas del conector ACS
seo-description: null
page-status-flag: never-activated
uuid: aef85b74-0388-44f8-b864-21db136a692c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: acs-connector
discoiquuid: 538d3b48-ff39-463f-878d-ebe085057129
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Solución de problemas del conector ACS{#troubleshooting-the-acs-connector}

Según su implementación, puede enfrentarse a varios problemas comunes.

* **¿Cuáles son las diferencias entre las interfaces de Campaign Standard y Campaign v7?**

   Campaign Standard y Campaign v7 funcionan de manera muy similar. La mayoría de los conceptos son los mismos, pero en algunos casos el enfoque puede diferir un poco. A continuación, se indican algunos conceptos que pueden diferir en el contexto del conector ACS:

<table> 
 <thead> 
  <tr> 
   <th> Campaign v7<br /> </th> 
   <th> Campaign Standard<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> destinatarios (o cualquier otra dimensión de perfil)<br /> </td> 
   <td> perfiles<br /> </td> 
  </tr> 
  <tr> 
   <td> lista<br /> </td> 
   <td> destinatarios<br /> </td> 
  </tr> 
  <tr> 
   <td> flujos de trabajo de campaña, flujos de trabajo de objetivo<br /> </td> 
   <td> flujos de trabajo<br /> </td> 
  </tr> 
  <tr> 
   <td> operaciones<br /> </td> 
   <td> campañas<br /> </td> 
  </tr> 
  <tr> 
   <td> aplicaciones web<br /> </td> 
   <td> páginas de destino<br /> </td> 
  </tr> 
  <tr> 
   <td> extensión de esquema y tabla personalizada<br /> </td> 
   <td> recurso personalizado y extensión de recursos<br /> </td> 
  </tr> 
  <tr> 
   <td> miembros sembrados<br /> </td> 
   <td> perfiles de prueba<br /> </td> 
  </tr> 
 </tbody> 
</table>

* **Los destinatarios en mi instancia de Campaign v7 no están sincronizados ni son visibles para Campaign Standard.**

   Este caso puede ocurrir por diferentes motivos:

   * Los destinatarios se crearon o se actualizaron en Campaign v7. La sincronización se activa cada 15 minutos. Esto significa que los destinatarios actualizados o recién creados se pueden ver en Campaign Standard después de la próxima sincronización.
   * La implementación se puede haber configurado para sincronizar únicamente los destinatarios de carpetas específicas. Los destinatarios de otras carpetas no están sincronizados.
   * El destinatario puede sincronizarse, pero no es visible en Campaign Standard. Compruebe la asignación de derechos de carpeta.

* **No encuentro los campos de perfil que necesito para basar mi consulta en Campaign Standard.**

   De forma predeterminada, los 20 campos de la tabla nms:recipient se sincronizan con Campaign Standard. Consulte la lista detallada de campos sincronizados. El consultor debe asignar y configurar cualquier campo adicional que se necesite recuperar en Campaign Standard.

   To make sure the field you want to use is available, you can check the profile resource definition from **[!UICONTROL Administration > Development > Diagnosis > Data schemas]**.

   Además, todos los datos adjuntos a los destinatarios y almacenados en tablas relacionadas con nms:recipients no se sincronizan de manera predeterminada a Campaign Standard.

   To still be able to use related data, you can perform your targeting in Campaign v7 and add additional data as explained in the [Synchronizing audiences](../../integrations/using/synchronizing-audiences.md) section, or you can refer to your consultant to explore customization possibilities.

* **Estoy utilizando otra dimensión de perfil distinta de la nms:recipient predeterminada en Campaign v7, ¿cómo puedo sincronizarla con Campaign Standard?**

   Standard Campaign utiliza un recurso de objetivo único que se denomina **perfiles**. La implementación básica de la funcionalidad Campaign Standard Connect proporciona una asignación predeterminada entre los destinatarios de Campaign v7 y los perfiles de Campaign Standard.

   Si utiliza otra dimensión de perfil en Campaign v7 o utiliza varias, debe asignarlas todas con los perfiles de Campaign Standard. Póngase en contacto con el consultor para solucionar esta necesidad concreta.

* **Deseo compartir una lista de perfiles con Campaign Standard a través de un flujo de trabajo, pero no puedo encontrar mi audiencia en Campaign Standard**.

   Audiences can be found in the **[!UICONTROL Audiences]** menu in Campaign Standard. They have the label specified in the **[!UICONTROL List update]** activity in your Campaign v7 workflow. Están sujetos a la asignación de carpetas definida durante la implementación.

   Lo primero que debe comprobar es si el flujo de trabajo ha finalizado sin errores. If you notice an error on the **[!UICONTROL List update]** activity, it means that the synchronization with Campaign Standard may have failed. To be able to see more details about what went wrong, go to **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**. This folder contains synchronization workflows triggered by the **[!UICONTROL List update]** activity execution.

   Also, make sure that the **[!UICONTROL Share with ACS]** option is checked in the **[!UICONTROL List update]** activity and that the workflow was correctly executed.

   Tenga en cuenta que los perfiles de los destinatarios de la lista deben haberse sincronizado con Campaign Standard antes de la ejecución del flujo de trabajo. Una vez compartidos con Campaign Standard, los destinatarios de la lista se concilian con los perfiles de Campaign Standard, lo cual significa que deben existir allí. Se omiten los destinatarios de la lista que no se puedan conciliar con los perfiles en Campaign Standard.

   Si comparte una lista de perfiles y ninguno está sincronizado con Campaign Standard, se crea una audiencia de consulta vacía en Campaign Standard que no se puede utilizar.

* **He recibido una notificación que me dice que hay un flujo de trabajo de sincronización en estado de error. ¿Qué debo hacer?**

   Compruebe la configuración de la cuenta externa en Campaign Standard y Campaign v7 probando la conexión:

   * **[!UICONTROL acsDefaultRelayAccount]** en Campaign Standard.
   * **[!UICONTROL acsDefaultAccount]** en Campaign v7.

* **No hay ningún grupo de seguridad disponible al asignar carpetas entre Campaign v7 y Campaign Standard.**

   You need to first synchronize your security groups from **[!UICONTROL Administration > ACS Connector > Rights management > Security groups]**. Esta acción comprueba los grupos de seguridad disponibles en Campaign Standard. Una vez sincronizados, puede encontrar los grupos de seguridad al configurar la asignación de carpetas.

* **No puedo editar un perfil, una audiencia o una página de destino en Campaign Standard. ¿Qué significa?**

   Los recursos sincronizados desde Campaign v7 se encuentran en modo de solo lectura en Campaign Standard para garantizar la coherencia de los datos. Si necesita editar uno de estos elementos, puede hacerlo en Campaign v7 y luego duplicar el cambio en Campaign Standard.

