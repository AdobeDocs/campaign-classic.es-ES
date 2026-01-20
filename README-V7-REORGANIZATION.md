---
source-git-commit: 65d223acd23f26bd9c6979d11815d23f02ae2382
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---
# 📚 v7: kit de reorganización de documentación

**2 mensajes para analizar y reorganizar la documentación v7 → v8**

---

## 📁 archivos

### 🔍 indicadores (instrucciones)

| Fichier | Descripción | Output |
|---------|-------------|--------|
| `PROMPT-1-OVERVIEW-ALL-FOLDERS.md` | Vue d&#39;ensemble de TOUS les folders v7 | `v7-reorganization-overview.md` |
| `PROMPT-2-DETAILED-FOLDER.md` | Analizar detalles de la carpeta UN avec % match | `[folder]-detailed-analysis.md` |

---

## Utilización de 🚀

### 1️⃣ Vue d&#39;Ensemble (tous les folders)

```bash
# 1. Ouvrir le prompt
open PROMPT-1-OVERVIEW-ALL-FOLDERS.md

# 2. Copier tout le contenu du bloc "COPIER CE PROMPT"
# 3. Coller dans Cursor/ChatGPT
# 4. Obtenir : v7-reorganization-overview.md
```

**Génère** :
- 📊 Resumen ejecutivo (estadísticas globales)
- 📁 analizar des 21 carpetas
- 🎯 asignación de prioridad
- ✅ elementos de acción
- ⚠️ risques
- 📈 Métricas

**Cola**: ~50-60 páginas de Markdown

---

### 2️⃣ Analizar carpeta de documentos

```bash
# 1. Ouvrir le prompt
open PROMPT-2-DETAILED-FOLDER.md

# 2. Modifier la ligne :
📁 **Analyze**: /Users/.../help/delivery/using/

# 3. Remplacer par le folder souhaité :
# - /help/delivery/using/
# - /help/workflow/using/
# - /help/web/using/
# - etc.

# 4. Copier tout le contenu du bloc "COPIER CE PROMPT"
# 5. Coller dans Cursor/ChatGPT
# 6. Obtenir : [folder]-detailed-analysis.md
```

**Génère** :
- 📊 estadísticas de la carpeta
- 📋 Tableau détaillé organization comme Experience League
- 🔗 vínculos escalables (v7 + Experience League)
- 📈 Jusqu&#39;à 3 coincide con v8 par fichier avec %
- 📄 archivo de recapitulación por archivo
- 🎯 plan de reorganización
- ✅ casillas de verificación para seguimiento

**Cola**: ~30-40 páginas Markdown

---

## 📊 Ejemplo de salida

### Mensaje 1 (descripción general)

```markdown
# 📊 v7 Documentation Reorganization Overview

**Total Files**: 1,500
**KEEP**: 400 (27%)
**DELETE**: 800 (53%)
**MOVE**: 200 (13%)
**REVIEW**: 100 (7%)

## 📁 Folder Analysis

### 🟢 100% KEEP - v7-Only Content
| Folder | Files | Reason |
|--------|-------|--------|
| /installation/ | 75 | On-premise setup |
| /mrm/ | 5 | Not in v8 FFDA |
...
```

### Preguntar 2 (carpeta detallada)

```markdown
# 📊 v7 Folder Analysis: Delivery

**Total Files**: 111

| # | v7 File | v8 Match 1 | % | v8 Match 2 | % | Notes | Action |
|---|---------|------------|---|------------|---|-------|--------|
| 1 | about-email-channel.md | campaign-web/v8/email | 95% | - | - | Fully in v8 | 🗑️ DELETE |
| 9 | sms-set-up-mid.md | NONE | 0% | - | - | Mid-sourcing (on-prem) | ✅ KEEP |
...
```

---

## 🎯 flujo de trabajo recomendado

### Semaine 1 : Vue d&#39;ensemble
1. Ejecutor **Mensaje 1** → Obtenedor `v7-reorganization-overview.md`
2. Identifier les folders priority
3. Colaborador con partes interesadas

### Semaine 2-4 : Analizar detalles
1. Vierta la carpeta chaque priority :
   - Ejecutor **Mensaje 2**
   - Obtenedor `[folder]-detailed-analysis.md`
   - Valider les décisions
   - Comenzar menos acciones

### Semaine 5+ : Ejecución
1. Supprimer les fichiers identifiés (DELETE)
2. Badger les fichiers v7-only (KEEP)
3. Migrer le contu manquant (MOVE)
4. Revisor menos ambigüedades (REVIEW)

---

## 💡 sugerencias

### Vierta menos indicaciones
- ✅ Copier/coller l&#39;intégralité du prompt
- ✅ Nuevo formato de modificador pas
- ✅ adaptador de búsqueda le chemin du folder (indicador 2)

### Vierta menos salidas
- 📝 salida en Markdown (pasa a HTML)
- 🔗 automaticas de ligas cliquables
- ✅ casillas de verificación para seguimiento
- 📊 estadísticas y porcentajes
- 🎨 Emojis e iconos

### Verter l&#39;analyze
- 🎯 carpeta de inicio por les gros (envío, flujo de trabajo)
- ⚡ ganadores menos rápidos (coincidencia del 95 al 100%)
- 🔍 Manuales del revisor menos ambigüedades de mayúsculas y minúsculas (&lt;70% de coincidencia)
- ✅ Validador avec SME avant suppression masivo

---

## ⚠️ importante

### Avant de supprimer
1. ✅ Verificador l&#39;équivalent v8
2. ✅ modificador qu&#39;il n&#39;y a pas de contenu v7 específico
3. ✅ métrica en el día `redirects.csv`
4. ✅ Valider avec un expert (para los premiers)

### Verter los archivos solo v7
1. ✅ Ajouter un badge au début du fichier
2. ✅ Expliquer pourquoi c&#39;est v7-only
3. ✅ Lien vers menos limitaciones v8

---

## Compatibilidad con 🆘

**Preguntas**?
- Prompt ne fonctionne pas → Vérifier les chemins des repos
- Salida trop larga → Demander un currículum
- Besoin d&#39;aide → Ping l&#39;équipe doc

---

**Dernière mise à jour**: 13-01-2026

