---
source-git-commit: 65d223acd23f26bd9c6979d11815d23f02ae2382
workflow-type: tm+mt
source-wordcount: '948'
ht-degree: 24%

---
# 📊 v7: reorganización de la documentación: información general

**Generado**: 13-01-2026\
**Carpetas totales**: 21\
**Archivos totales**: ~1,500

&#x200B;---

## 📈 resumen ejecutivo

| Métrica | Recuento | Porcentaje |
|--------|-------|------------|
| 📄 **Archivos totales** | 1.500 | 100 % |
| ✅ **MANTENER (específico para la versión 7)** | 400 | 27 % |
| 🗑️ **DELETE (en la versión 8)** | 800 | 53 % |
| ➡️ **MOVER (a la versión 8)** | 200 | 13 % |
| 🔍 **REVISIÓN (poco clara)** | 100 | 7 % |

**🎯Reducción estimada**: 60-75% (1.500 → 400-600 archivos)

&#x200B;---

## 📁 análisis de carpeta por prioridad

### 🟢 Prioridad 1: 100% KEEP - Solo funciones v7

| Carpeta | Archivos | Motivo | Estado de v8 | Acción |
|--------|-------|--------|-----------|--------|
| 📂 `/installation/` | 75 | Configuración on-premise/híbrida | Solo en la nube en la versión 8 | ✅ MANTENER TODO + distintivo |
| 📂 `/mrm/` | 5 | Administración de recursos de marketing | NO en FDAC | ✅ MANTENER TODO + distintivo |
| 📂 `/surveys/` | 8 | Encuestas en línea | NO en FDAC | ✅ MANTENER TODO + distintivo |
| 📂 `/distributed/` | 7 | Marketing distribuido | NO en FDAC | ✅ MANTENER TODO + distintivo |
| 📂 `/response/` | 5 | Gestión de respuestas | Estado poco claro | 🔍 VERIFICAR y CONTINUAR |
| 📂 `/migration/` | 8 | Migración v6.1 → v7 | Específico de v7 | ✅ MANTENER TODO |
| **TOTAL** | **108** | **7%** | - | **Insignia como solo v7** |

&#x200B;---

### Prioridad 2 de 🔴: DELETE del 60 al 70 % (alta duplicación)

| Carpeta | Total | MANTENER | DELETE | MOVER | REVISAR | Notas |
|--------|-------|------|--------|------|--------|-------|
| 📂 `/delivery/` | 111 | 18 (16 %) | 67 (60 %) | 8 (7 %) | 18 (17 %) | Correo electrónico/SMS/push en la versión 8 |
| 📂 `/workflow/` | 121 | 24 (20 %) | 60 (50 %) | 12 (10 %) | 25 (20 %) | Actividades comunes en la versión 8 |
| 📂 `/reporting/` | 32 | 3 (10 %) | 22 (70 %) | 2 (6 %) | 5 (14 %) | Informes rediseñados en la versión 8 |
| 📂 `/platform/` | 61 | 12 (20 %) | 34 (55 %) | 5 (8 %) | 10 (17 %) | Funciones comunes de la versión 8 de |
| 📂 `/campaign/` | 11 | 2 (18 %) | 7 (64 %) | 1 (9 %) | 1 (9 %) | Administración de Campaign en la versión 8 |
| **TOTAL** | **336** | **59** | **190** | **28** | **59** | **Alto potencial de reducción** |

&#x200B;---

### 🟡 Prioridad 3: 30-50% MIXTA - Se Necesita Análisis Detallado

| Carpeta | Total | MANTENER % | DELETE % | Notas |
|--------|-------|--------|----------|-------|
| 📂 `/configuration/` | 69 | 65 % | 22 % | Configuraciones de esquema/base de datos (principalmente v7) |
| 📂 `/production/` | 43 | 65 % | 23 % | Administración de servidores (principalmente v7) |
| 📂 `/integrations/` | 37 | 40 % | 40 % | Compruebe la disponibilidad del conector |
| 📂 `/interaction/` | 39 | 51 % | 31 % | Motor de ofertas (verificar v8) |
| 📂 `/web/` | 26 | 92 % | 8 % | Aplicaciones web > Páginas de destino v8 |
| 📂 `/message-center/` | 16 | 60 % | 30 % | Mensajería transaccional |
| **TOTAL** | **230** | **~55%** | **~25%** | **Requiere revisión carpeta por carpeta** |

&#x200B;---

## 🎯 victorias rápidas: semana 1

### Eliminaciones de alta confianza (coincidencia de 95-100 % v8)

| Carpeta | Archivos para eliminar | Impacto | Esforzar |
|--------|----------------|--------|--------|
| 📂 `/delivery/` | 67 archivos | 🔥🔥🔥 alto | 2 días |
| 📂 `/workflow/` | 60 archivos | 🔥🔥🔥 alto | 2 días |
| 📂 `/reporting/` | 22 archivos | 🔥🔥 Medium | 1 día |
| 📂 `/platform/` | 34 archivos | 🔥🔥 Medium | 1 día |
| 📂 `/campaign/` | 7 archivos | 🔥 baja | 0,5 día |
| **TOTAL** | **190 archivos** | **Reducción del 53%** | **6,5 días** |

**Ejemplos**:
- ✅ `about-email-channel.md` → `campaign-web/v8/email`
- ✅ `sms-channel.md` → `campaign-web/v8/msg/send-sms`
- ✅ `query.md` (flujo de trabajo) → `campaign/v8/automation/workflow/query`
- ✅ `about-workflows.md` → `campaign/v8/automation/workflow`

&#x200B;---

## 📋 desglose detallado de carpetas

### 📂 Entrega (`/help/delivery/using/`) - 111 archivos

| Categoría | Archivos | MANTENER | DELETE | MOVER | REVISAR | Notas |
|----------|-------|------|--------|------|--------|-------|
| Introducción | 8 | 0 | 7 | 0 | 1 | Conceptos básicos en la versión 8 |
| Correo electrónico | 18 | 0 | 16 | 0 | 2 | Totalmente en la versión 8 |
| SMS | 7 | 1 | 5 | 0 | 1 | Mid-sourcing = KEEP |
| Push | 9 | 0 | 8 | 0 | 1 | Totalmente en la versión 8 |
| Correo directo | 4 | 0 | 4 | 0 | 0 | En la versión 8 |
| Personalización | 8 | 1 | 6 | 0 | 1 | Cupones = KEEP |
| Plantillas | 6 | 0 | 6 | 0 | 0 | En la versión 8 |
| Pruebas A/B | 11 | 0 | 10 | 0 | 1 | En la versión 8 |
| Monitorización | 14 | 0 | 12 | 1 | 1 | Principalmente en la versión 8 de |
| Solución de problemas | 9 | 2 | 4 | 2 | 1 | Mantener sugerencias locales |
| Entrega | 8 | 3 | 4 | 0 | 1 | SpamAssassin = KEEP |
| Avanzado | 9 | 11 | 5 | 5 | 8 | Mixto |
| **TOTAL** | **111** | **18** | **67** | **8** | **18** | **El 60% se puede eliminar** |

**Debe Conservar**:
- ✅ `personalized-coupons.md` - NO en FDAC v8
- ✅ `sms-set-up-mid.md` - Intermediario (local)
- ✅ `spamassassin.md` - Filtrado de correo no deseado local

**Ejemplos de eliminación rápida**:
- 🗑️ `about-email-channel.md` → 95% en `campaign-web/v8/email`
- 🗑️ `creating-an-email-delivery.md` → 95% en `campaign-web/v8/email/create-email`
- 🗑️ `sms-channel.md` → 90% en `campaign-web/v8/msg/send-sms`

&#x200B;---

### 📂 flujo de trabajo (`/help/workflow/using/`) - 121 archivos

| Categoría | Archivos | MANTENER | DELETE | MOVER | REVISAR | Notas |
|----------|-------|------|--------|------|--------|-------|
| Introducción | 12 | 2 | 9 | 0 | 1 | Conceptos básicos en la versión 8 |
| Direccionamiento | 18 | 3 | 12 | 1 | 2 | Consulta/División en la versión 8 |
| Control de flujo | 15 | 2 | 10 | 1 | 2 | Frecuentes en la versión 8 |
| Actividades de acción | 24 | 4 | 16 | 2 | 2 | Más en la versión 8 |
| Actividades de evento | 8 | 1 | 6 | 0 | 1 | En la versión 8 |
| Actividades de MRM | 5 | 5 | 0 | 0 | 0 | NO en FDAC |
| Técnico | 16 | 4 | 8 | 2 | 2 | Mixto |
| Avanzado | 12 | 3 | 4 | 3 | 2 | Patrones útiles |
| Casos de uso | 11 | 0 | 5 | 3 | 3 | Buenos ejemplos |
| **TOTAL** | **121** | **24** | **60** | **12** | **25** | **50% se puede eliminar** |

**Debe Conservar**:
- ✅ todas las actividades MRM (5 archivos): NO en el FDAC de la versión 8
- ✅ configuraciones locales
- ✅ flujos de trabajo técnicos avanzados

**Ejemplos de eliminación rápida**:
- 🗑️ `query.md` → 95% en `campaign/v8/automation/workflow/query`
- 🗑️ `split.md` → 95% en `campaign/v8/automation/workflow/split`
- 🗑️ `enrichment.md` → 95% en `campaign/v8/automation/workflow/enrichment`

&#x200B;---

### Instalación de 📂 (`/help/installation/using/`): 75 archivos

| Categoría | Archivos | Acción | Notas |
|----------|-------|--------|-------|
| Instalación del servidor | 18 | ✅ MANTENER | Solo On-Premise |
| Configuración de base de datos | 12 | ✅ MANTENER | Solo On-Premise |
| Configuración | 15 | ✅ MANTENER | nlserver, etc. |
| Red | 8 | ✅ MANTENER | Zonas de seguridad |
| Integración | 10 | ✅ MANTENER | LDAP, etc. |
| Solución de problemas | 8 | ✅ MANTENER | Problemas locales |
| Documentos genéricos | 4 | 🗑️ DELETE | En la guía de inicio de v8 |
| **TOTAL** | **75** | **71 MANTENER / 4 DELETE** | **95% de la versión 7** específica |

**Motivo**: la versión 8 es solo de nube, todos los documentos de configuración locales son específicos de la versión 7.

&#x200B;---

### 📂 web (`/help/web/using/`): 26 archivos

| Categoría | Archivos | MANTENER | DELETE | Notas |
|----------|-------|------|--------|-------|
| Aplicaciones web | 14 | 14 | 0 | Funciones avanzadas no incluidas en la versión 8 de |
| Formularios web | 8 | 8 | 0 | Más de páginas de aterrizaje de la versión 8 |
| Páginas de destino | 2 | 0 | 2 | Páginas básicas en la versión 8 |
| Editor de HTML | 2 | 2 | 0 | Distinto de la versión 8 |
| **TOTAL** | **26** | **24** | **2** | **92% de la versión 7** específica |

**Motivo**: la versión 7 tiene un marco de trabajo de aplicaciones web completo y la versión 8 ha simplificado las páginas de destino.

&#x200B;---

## ✅ plan de acción

### Semana 1: Eliminaciones de alto impacto- [ ] `/delivery/`: eliminar 67 archivos (correo electrónico, SMS, conceptos básicos de inserción)- [ ] `/workflow/`: eliminar 60 archivos (actividades comunes)- [ ] `/reporting/`: eliminar 22 archivos (informes estándar)- [ ] `/platform/`: eliminar 34 archivos (características comunes)- [ ] `/campaign/`: eliminar 7 archivos (administración de campañas)- **Total**: 190 archivos eliminados (reducción del 13%)

### Semana 2: Distintivos específicos de la versión 7- [ ] `/installation/`: distintivo 71 archivos como &quot;v7 solo local&quot;- [ ] `/mrm/`: insignia 5 archivos como &quot;No disponible en FDAC v8&quot;- [ ] `/surveys/`: distintivo 8 archivos como &quot;No disponible en FDAC v8&quot;- [ ] `/distributed/`: archivos de la insignia 7 como &quot;No disponible en FDAC de la versión 8&quot;- [ ] `/web/`: distintivo 24 archivos como &quot;aplicaciones web v7&quot;- **Total**: 115 archivos marcados

### Semana 3: Migración de contenido- [ ] Migrar sugerencias de solución de problemas de `/delivery/` a v8- [ ]: migrar las prácticas recomendadas del flujo de trabajo a la versión 8- [ ] Migrar patrones avanzados de `/platform/` a v8- **Total**: 40 archivos migrados y eliminados

### Semana 4: Revisión manual- [ ] revisar `/configuration/` contenido mixto- [ ] revisar la disponibilidad del conector `/integrations/`- [ ] revisar `/interaction/` cobertura de motor de ofertas- [ ] revisar el estado de la característica `/response/`- **Total**: 50 archivos revisados y decididos

&#x200B;---

## 📊 resultados esperados

| Fase | Archivos afectados | % acumulado |
|-------|----------------|--------------|
| Semana 1: Eliminaciones | 190 | 13 % |
| Semana 2: Distintivos | 115 | 20 % |
| Semana 3: Migración | 40 | 23 % |
| Semana 4: Revisión | 50 | 26 % |
| **TOTAL** | **395** | **26% procesado** |

**Restantes**: ~1,100 archivos para procesar en fases subsiguientes

**Objetivo final**: 1.500 → 400-600 archivos (reducción del 60-73%)

&#x200B;---

## 🎯 métricas de éxito

| Métrica | Destinatario | Estado |
|--------|--------|--------|
| Archivos eliminados | 800+ (53%) | ⏳ pendientes |
| Archivos con distintivo | 200+ (13%) | ⏳ pendientes |
| Archivos migrados | 200+ (13%) | ⏳ pendientes |
| Vínculos rotos | 0 | ⏳ pendientes |
| Aprobación de partes interesadas | ✅ | ⏳ pendientes |

&#x200B;---

**Última actualización**: 13-01-2026\
**Próxima revisión**: Después de la ejecución de la semana 1

