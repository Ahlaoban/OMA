# CHANGELOG - MaïJinn v3.4.1-OMA

**Date :** 22 novembre 2025
**Type :** Patch - Amélioration Architecture Dual-Agent

---

## 🎯 Changements v3.4.0 → v3.4.1

### ✨ NOUVEAUTÉ MAJEURE : Instructions Unifiées avec Système de Modes

**Problème résolu :**
- v3.4.0 ne gérait pas clairement la **dualité PHÉNIX/ARSENAL**
- Absence de protocoles de transition explicites entre les deux agents
- Pas de bannières de mode pour identifier l'agent actif
- Mémoire du PUC non explicite lors des transitions

**Solution implémentée :**
- ✅ Nouveau fichier `INSTRUCTIONS_MAIJINN_UNIFIE_v3.4.1_OMA.md`
- ✅ Système de **modes actifs** avec détection automatique
- ✅ **Bannières visuelles** pour identifier le mode (PHÉNIX ou ARSENAL)
- ✅ **Protocoles de transition** explicites et bidirectionnels
- ✅ **Gestion de la mémoire du PUC** entre les modes

---

## 📋 Détails des Changements

### 1. Système de Modes Actifs

**Avant (v3.4.0) :**
```
Instructions séparées pour PHÉNIX et ARSENAL
→ Pas de coordination explicite
→ Pas de détection du mode approprié
→ Transitions floues
```

**Après (v3.4.1) :**
```
Instructions unifiées avec 2 modes distincts
→ Détection automatique du mode au démarrage
→ Bannières visuelles claires (PHÉNIX vs ARSENAL)
→ Protocoles de transition explicites
```

### 2. Bannières de Mode

**Bannière PHÉNIX :**
```
╔══════════════════════════════════════════════════════╗
║ 🧠 MODE PHÉNIX - Stratège Conversationnel           ║
║ Mission : Construction de votre PUC                  ║
╚══════════════════════════════════════════════════════╝
```

**Bannière ARSENAL :**
```
╔══════════════════════════════════════════════════════╗
║ ⚔️  MODE ARSENAL - Tacticien d'Exécution             ║
║ PUC actif : [Prénom] - [Archétype]                  ║
╚══════════════════════════════════════════════════════╝
```

### 3. Protocoles de Transition

#### PHÉNIX → ARSENAL
- **Déclencheur :** PUC validé (Sections A-E + validation explicite)
- **Protocole :** Passation formelle avec récapitulatif
- **Affichage :** Bannière de transition + options (Min&Maï ou Arsenal)

#### ARSENAL → PHÉNIX
- **Déclencheur :** Modification stratégique détectée
- **Protocole :** Retour obligatoire vers PHÉNIX
- **Affichage :** Bannière de détection + explication

### 4. Gestion de la Mémoire

**Nouveau système :**
```
PUC.validated == true
  → Autoriser mode ARSENAL
  → Conserver PUC en mémoire
  → Afficher archétype dans bannière

PUC.validated == false
  → Forcer mode PHÉNIX
  → Continuer construction
```

### 5. Référencement des Sources

**Clarification hiérarchique :**
```
INSTRUCTIONS_MAIJINN_UNIFIE_v3.4.1_OMA.md (gouvernance)
├─► Prompt_PHENIX_v3.4.0_OMA.md (détails PHÉNIX)
├─► Prompt_ARSENAL_v3.4.0_OMA.md (détails ARSENAL)
└─► Forge_MEMORIELLE_v3.4.0_OMA.md (base de connaissances)
```

---

## 📊 Impact Utilisateur

### Avant v3.4.1
- ❌ Confusion sur "qui parle" (PHÉNIX ou ARSENAL ?)
- ❌ Transitions floues entre agents
- ❌ Pas de visibilité sur l'avancement
- ❌ Risque de perte du PUC lors des transitions

### Après v3.4.1
- ✅ Identification claire du mode actif (bannières)
- ✅ Transitions formelles et explicites
- ✅ Visibilité constante de l'avancement
- ✅ Mémoire du PUC garantie

---

## 🔄 Compatibilité

### Rétrocompatibilité
- ✅ Toutes les commandes existantes conservées
- ✅ Format PUC inchangé (Sections A-F)
- ✅ Commandes OMA inchangées (`!export`, `!import`, `!progression`)
- ✅ Compatibilité Min&Maï v13.0 maintenue

### Fichiers Affectés
| Fichier | Statut |
|---------|--------|
| `INSTRUCTIONS_MAIJINN_UNIFIE_v3.4.1_OMA.md` | ✨ NOUVEAU |
| `Prompt_PHENIX_v3.4.0_OMA.md` | ✅ Inchangé (référencé) |
| `Prompt_ARSENAL_v3.4.0_OMA.md` | ✅ Inchangé (référencé) |
| `Forge_MEMORIELLE_v3.4.0_OMA.md` | ✅ Inchangé |
| `MAIJINN_v3.4.0_OMA_ARCHITECTURE.md` | ✅ Inchangé |
| `INSTRUCTIONS_PROJET_OMA.md` | ⚠️ Obsolète (remplacé par v3.4.1) |

---

## 🎯 Prochaines Étapes Recommandées

### Immédiat
- [x] Créer `INSTRUCTIONS_MAIJINN_UNIFIE_v3.4.1_OMA.md`
- [ ] Tester les transitions PHÉNIX ↔ ARSENAL
- [ ] Vérifier affichage des bannières
- [ ] Tester conservation du PUC

### Court terme (Q4 2025)
- [ ] Documenter cas d'usage typiques
- [ ] Créer guide de démarrage rapide
- [ ] Ajouter exemples de dialogues de transition

### Moyen terme (Q1 2026)
- [ ] Optimiser la détection automatique du mode
- [ ] Ajouter métriques de qualité des transitions
- [ ] Feedback utilisateur sur clarté du système

---

## 📝 Notes Techniques

### Architecture
Le système v3.4.1 utilise une approche **modes conditionnels** :
- Instructions unifiées chargées dès le début
- Activation conditionnelle selon état du PUC
- Bannières comme indicateurs visuels d'état
- Protocoles de transition comme machine à états

### Avantages vs Méta-Orchestrateur
✅ Plus simple à implémenter (pas de "chargement" de prompts)
✅ Mémoire cohérente entre modes
✅ Transitions fluides et explicites
✅ Moins de risque de perte de contexte

---

## 🌟 Citation

> "L'architecture OMA v3.4.1 honore enfin pleinement la dualité PHÉNIX/ARSENAL avec des transitions explicites, une mémoire cohérente, et une visibilité constante pour l'utilisateur."

---

**Version :** 3.4.1-OMA
**Date :** 22 novembre 2025
**Contributeurs :** Architecture OMA Team

---

**FIN CHANGELOG v3.4.1**
