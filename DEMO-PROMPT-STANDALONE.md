---
source-git-commit: 65d223acd23f26bd9c6979d11815d23f02ae2382
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---
# 🚀 INDICADOR DE DEMOSTRACIÓN - Análisis de la documentación de las versiones 7 a 8

**Copie y pegue todo este mensaje en Cursor/ChatGPT para analizar cualquier carpeta v7**

&#x200B;---

## 📋 EL SÍMBOLO DEL SISTEMA (COPIE DESDE AQUÍ) ⬇️

```markdown
# Campaign v7 Documentation Analysis

Analyze the v7 documentation folder and generate a detailed Markdown report with recommendations.

---

## CONTEXT

**v7 Repository**: `/Users/florentvignes/Documents/GitHub/campaign-classic.en/`  
**v8 Repositories**:
- `/Users/florentvignes/Documents/GitHub/campaign.en/` (Campaign v8)
- `/Users/florentvignes/Documents/GitHub/campaign-web.en/` (Campaign Web UI v8)

---

## TARGET FOLDER

**Analyze this folder**: `/Users/florentvignes/Documents/GitHub/campaign-classic.en/help/delivery/using/`

*(Replace with any folder: workflow, web, platform, reporting, etc.)*

---

## FEATURE PARITY CONTEXT

### v7-Specific Features (NOT in v8 FFDA)
- **Coupons** (personalized-coupons.md)
- **MRM** (Marketing Resource Management)
- **Surveys** (online surveys)
- **Distributed Marketing**
- **Mid-sourcing** (on-premise setup)
- **SpamAssassin** (on-premise spam filtering)
- **On-premise/Hybrid** configurations

### v8 Documentation Structure
- **Campaign Web UI**: `/campaign-web.en/help/v8/` - https://experienceleague.adobe.com/en/docs/campaign-web/v8/
- **Campaign v8**: `/campaign.en/help/v8/` - https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/

---

## OUTPUT FORMAT

Generate a complete Markdown report with this structure:

### 1. HEADER & SUMMARY
\`\`\`markdown
# 📊 v7 [Folder Name] Analysis

**Folder**: `/help/[folder]/using/`  
**Generated**: [Date]  
**Total Files**: [X]

## 📈 Summary

| Metric | Count | Percentage |
|--------|-------|------------|
| 📄 Total Files | X | 100% |
| ✅ KEEP | X | X% |
| 🗑️ DELETE | X | X% |
| ➡️ MOVE | X | X% |
| 🔍 REVIEW | X | X% |
\`\`\`

### 2. FILE-BY-FILE ANALYSIS TABLE
\`\`\`markdown
## 📋 Complete File Analysis

### [Category Name] (X files)

| # | v7 File | v8 Match | Match % | Notes | Action |
|---|---------|----------|---------|-------|--------|
| 1 | filename.md | [v8 link](https://...) | 95% | Fully in v8 | 🗑️ DELETE |
| 2 | **filename.md** | NONE | 0% | **v7-specific** | ✅ **KEEP** |
| 3 | filename.md | [v8 link](https://...) | 70% | Migrate tips | ➡️ MOVE |

[Repeat for each category: Get Started, Email, SMS, etc.]
\`\`\`

### 3. MUST KEEP SECTION
\`\`\`markdown
## ✅ Must Keep - v7-Specific Features

| File | Reason | Badge Text |
|------|--------|------------|
| filename.md | Feature not in v8 FFDA | "This feature is not available..." |
\`\`\`

### 4. QUICK WINS SECTION
\`\`\`markdown
## 🗑️ Quick Wins - Safe to Delete Now

**[Category]** (X files):
- ✅ filename.md → 95% in v8/path
- ✅ filename.md → 90% in v8/path
\`\`\`

### 5. MIGRATION SECTION
\`\`\`markdown
## ➡️ Content to Migrate First

| v7 File | v8 Destination | Content to Migrate | Effort |
|---------|----------------|-------------------|--------|
| filename.md | /v8/path.md | Sections X, Y, Z | 2 hours |
\`\`\`

### 6. EXECUTION PLAN
\`\`\`markdown
## 🎯 Execution Plan

### Week 1: Quick Deletions
- [ ] Delete [category] files (X)
- [ ] Delete [category] files (X)
**Total**: X files deleted

### Week 2: Badging
- [ ] Badge v7-specific files (X)

### Week 3: Review
- [ ] Review partial matches (X)
\`\`\`

---

## ANALYSIS RULES

### For Each File, Determine:

1. **Match Percentage**:
   - 95-100% = Fully covered in v8 → DELETE
   - 70-90% = Mostly covered, check gaps → DELETE or MOVE
   - 40-70% = Partial coverage → REVIEW
   - 0-40% = Not in v8 → KEEP or REVIEW

2. **v7-Specific Indicators** (→ KEEP):
   - Mentions "on-premise", "hybrid", "mid-sourcing"
   - Coupons, MRM, Surveys, Distributed Marketing
   - SpamAssassin, nlserver configuration
   - Client Console specific features
   - Database schema/structure docs

3. **DELETE Criteria**:
   - Basic features (email, SMS, push creation)
   - Standard workflow activities (query, split, enrichment)
   - Common reports
   - Channel basics fully documented in v8

4. **MOVE Criteria**:
   - Troubleshooting tips not in v8
   - Best practices missing in v8
   - Advanced patterns useful for v8
   - Good examples/use cases

5. **REVIEW Criteria**:
   - Partial v8 coverage (50-70%)
   - Unclear if feature exists in v8
   - Complex mixed content

---

## IMPORTANT

- **Organize by category** (Get Started, Email, SMS, Push, etc.)
- **Include Experience League URLs** for v8 matches
- **Bold v7-specific files** that must be kept
- **Estimate match percentage** for each file
- **Provide clear reasoning** for each decision
- **Include effort estimates** for migrations

---

Generate the complete Markdown report now.
```

&#x200B;---

## 🎯 INSTRUCCIONES DE DEMOSTRACIÓN

### Paso 1: Mostrar el indicador1. Abrir este archivo (`DEMO-PROMPT-STANDALONE.md`)2. Desplácese hasta la sección &quot;EL MENSAJE&quot;.3. Diga: *&quot;Este es nuestro mensaje de análisis automatizado&quot;*

### Paso 2: Copiar el indicador1. Seleccione todo, desde &quot;# Campaign v7 Documentation Analysis&quot; hasta el final2. Copiar al portapapeles3. Diga: *&quot;Acabo de copiar todo el mensaje...&quot;*

### Paso 3: Pegar y ejecutar1. Abrir cursor2. Pegar el mensaje3. Diga: *&quot;...y péguelo en el cursor&quot;*4. Pulse Intro

### Paso 4: Mostrar resultados1. Esperar generación (~30-60 segundos)2. Desplazarse por el informe generado3. Resaltar secciones clave:   - 📊 estadísticas de resumen   - 📋 tabla Archivo por archivo   - ✅ debe conservar la sección   - 🗑️ victorias rápidas   - 🎯 plan de ejecución

### Paso 5: Momento &quot;Wow&quot;1. Mostrar vista previa de markdown2. Señale lo siguiente:   - *&quot;111 archivos analizados automáticamente&quot;*   - *&quot;Se pueden eliminar 67 archivos (reducción del 60 %)&quot;*   - *&quot;18 archivos específicos de la versión 7 identificados&quot;*   - *&quot;Completar plan de ejecución con escalas de tiempo&quot;*

&#x200B;---

## 💡 SUGERENCIAS DE DEMOSTRACIÓN

### Convertir en interactivo&#x200B;**Preguntar a la audiencia**: *&quot;¿Qué carpeta debemos analizar?&quot;*- envío ✅ (111 archivos - impresionante)- flujo de trabajo ✅ (121 archivos, incluso más grande)- web ✅ (26 archivos: demostración rápida)- informar sobre ✅ (32 archivos - rápido)

### Personalización sobre la marcha&#x200B;**Mostrar flexibilidad**: cambie la ruta de la carpeta en el mensaje:

```
/help/workflow/using/  → Analyze workflows
/help/web/using/       → Analyze web apps
/help/platform/using/  → Analyze platform
```

### Resaltar características clave1. **Automatización**: *&quot;No se necesita trabajo manual&quot;*2. **Precisión**: *&quot;Utiliza la documentación de la versión 8 para la comparación&quot;*3. **Procesable**: *&quot;Plan listo para ejecutarse con casillas de verificación&quot;*4. **Inteligente**: *&quot;Identifica automáticamente las características específicas de la versión 7&quot;*

### Comparación de tiempo&#x200B;**Antes de**: *&quot;Análisis manual = 2-3 días por carpeta&quot;*\**Después**: *&quot;Análisis automatizado = 30 segundos por carpeta&quot;*

**ROI**: *&quot;21 carpetas × 2 días = 42 días → 15 minutos&quot;*

&#x200B;---

## 📊 PREVISUALIZACIÓN DE SALIDA ESPERADA

```markdown
# 📊 v7 Delivery Analysis

**Total Files**: 111

## 📈 Summary
| Metric | Count | Percentage |
|--------|-------|------------|
| ✅ KEEP | 18 | 16% |
| 🗑️ DELETE | 67 | 60% |
| ➡️ MOVE | 8 | 7% |
| 🔍 REVIEW | 18 | 17% |

## 📋 File Analysis

### 📧 Email (18 files)
| # | v7 File | v8 Match | % | Action |
|---|---------|----------|---|--------|
| 1 | about-email-channel.md | campaign-web/v8/email | 95% | 🗑️ DELETE |
| 2 | creating-an-email-delivery.md | campaign-web/v8/email/create | 95% | 🗑️ DELETE |

### 📱 SMS (7 files)
| # | v7 File | v8 Match | % | Action |
|---|---------|----------|---|--------|
| 1 | sms-channel.md | campaign-web/v8/msg/send-sms | 90% | 🗑️ DELETE |
| 2 | **sms-set-up-mid.md** | NONE | 0% | ✅ **KEEP** |

[... continues for all categories ...]

## ✅ Must Keep (18 files)
- **personalized-coupons.md** - Coupons not in v8 FFDA
- **sms-set-up-mid.md** - Mid-sourcing (on-prem)
- **spamassassin.md** - On-prem spam filtering

## 🗑️ Quick Wins (67 files)
Email basics, SMS, Push, Direct mail → All in v8

## 🎯 Execution Plan
Week 1: Delete 67 files (60%)
Week 2: Badge 18 files
Week 3: Review 18 files
```

&#x200B;---

## 🎬 SCRIPT DE DEMOSTRACIÓN

**Abriendo**:
> &quot;Hoy les mostraré cómo hemos automatizado la reorganización de la documentación de v7 mediante IA. Esto solía tomar semanas, ahora toma minutos&quot;.

**Problema**:
> &quot;Tenemos más de 1500 archivos de documentación v7. Muchos están duplicados en la versión 8. Necesitamos identificar qué conservar, eliminar o migrar&quot;.

**Solución**:
> &quot;Hemos creado un mensaje inteligente que analiza cualquier carpeta y genera recomendaciones procesables&quot;.

**Demostración**:
> &quot;Déjame mostrarte. Analizaré la carpeta &quot;delivery&quot; con 111 archivos...&quot;
> 
> [Copiar solicitud, pegar, ejecutar]
> 
> &quot;...y en 30 segundos, obtenemos un análisis completo.&quot;

**Resultados**:
> &quot;Mira esto:
> - 67 archivos para eliminar (reducción del 60 %)
> - 18 archivos específicos de la versión 7 identificados
> - 8 archivos para migrar
> - Plan de ejecución completo de tres semanas
> 
> Todo automatizado. Todo preciso&quot;.

**Cerrar**:
> &quot;Este mismo proceso funciona para las 21 carpetas. Lo que antes tomaba 6 semanas ahora toma 15 minutos&quot;.

&#x200B;---

## 🚀 LISTO PARA LA DEMOSTRACIÓN

**Sólo**:
1. Abrir este archivo
2. Copiar el mensaje
3. Pegar en el cursor
4. Mostrar la magia ✨

**Tiempo total de demostración**: de 3 a 5 minutos\
**Factor de avance**: 🔥🔥🔥

