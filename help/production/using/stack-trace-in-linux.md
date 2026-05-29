---
product: campaign
title: Seguimiento de pila en Linux
description: Seguimiento de pila en Linux
feature: Monitoring
badge-v7-prem: label="On-premise/híbrido solo" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 91662d6d-2177-4440-b31f-7b031bd953cb
TQID: https://experienceleague.adobe.com/djAlzlskJf-rVq57J-fS5hG1HdeMSSvskl9jByDYS9I
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
feature_v2: []
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 149
ht-degree: 29%

---

# Seguimiento de pila en Linux{#stack-trace-in-linux}



Un seguimiento de pila **stack** representa un seguimiento contenido en un archivo de tipo **core**. Este archivo se genera en caso de error del equipo. Puede identificar el origen del error.

>[!NOTE]
>
>* Un archivo **core** se llama **core.`<num>`**.
>* **gdb: el depurador GNU** debe estar instalado en el equipo.
>

El soporte técnico de Adobe Campaign puede pedirle este **seguimiento de pila**. Para obtenerlo, introduzca los siguientes comandos en Linux:

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

El soporte técnico de Adobe Campaign podría pedirle que ejecute este comando con un ejecutable específico (que proporcionaremos nosotros).

En este caso, simplemente ejecute el siguiente comando reemplazando **nlserver** por el ejecutable proporcionado por Adobe Campaign:

```
gdb nlserver <coreFile>
```

Por ejemplo:

```
gdb nlserver.1823 <coreFile>
```
