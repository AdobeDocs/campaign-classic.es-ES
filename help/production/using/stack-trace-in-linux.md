---
product: campaign
title: Seguimiento de pila en Linux
description: Seguimiento de pila en Linux
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 91662d6d-2177-4440-b31f-7b031bd953cb
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 11%

---

# Seguimiento de pila en Linux{#stack-trace-in-linux}

Una **traza de pila** representa una traza contenida en un archivo de tipo **core**. Este archivo se genera en caso de error del equipo. Puede identificar el origen del error.

>[!NOTE]
>
>* Un archivo **core** se denomina **core.`<num>`**.
>* **gdb - El GNU** Debuggerer debe estar instalado en la máquina.

>



El soporte técnico de Adobe Campaign puede solicitarle este **seguimiento de pila**. Para obtenerlo, introduzca los siguientes comandos en Linux:

```
su - neolane
gdb nlserver <coreFile>
//You get lots of output but the stack trace (or Back trace) can be obtained with : 
(gdb) bt
// and forward all the output : 
#0 0x0836c189 in ObjectValue::SetPropertyTarget ()
#1 0x082623b3 in CXtkScriptProperty::VDeclareProperties ()
#2 0x0826a835 in CXtkScriptContext::OnGetProperty ()
#3 0x08370b3d in JavaScriptGetProperty ()
#4 0x557b8aa7 in js_Interpret () from /usr/local/neolane/nl6/lib/libmozjs.so
#5 0x557afb97 in js_Execute () from /usr/local/neolane/nl6/lib/libmozjs.so
#6 0x5578921f in JS_ExecuteScript () from /usr/local/neolane/nl6/lib/libmozjs.so
#7 0x08370468 in JavaScriptSource::Evaluate ()
#8 0x0848fa03 in JSTDeliveryContext::ProcessScript ()
#9 0x0848fcb6 in JSTDeliveryContext::ProcessTemplate ()
#10 0x08460d2b in CDeliveryToolbox::CreateMailMessage ()
#11 0x080d51fe in CMtaQueue::PrepareMessages ()
#12 0x080d2b07 in CMtaQueue::Prepare ()
#13 0x080dca38 in CMtaChild::OnRun ()
#14 0x0814792c in ThreadStartRoutine ()
#15 0x55575b63 in start_thread () from /lib/tls/libpthread.so.0
#16 0x5565918a in clone () from /lib/tls/libc.so.6
```

El servicio de asistencia técnica de Adobe Campaign puede solicitarle que ejecute este comando utilizando un ejecutable específico (que nosotros proporcionaremos).

En este caso, simplemente ejecute el siguiente comando reemplazando **nlserver** por el ejecutable proporcionado por Adobe Campaign:

```
gdb nlserver <coreFile>
```

Por ejemplo:

```
gdb nlserver.1823 <coreFile>
```
