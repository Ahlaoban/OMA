# CHANGELOG - MaïJinn v3.4.0-OMA

**Date de release :** 22 novembre 2025  
**Version précédente :** v3.3.1 Big Five

---

## 🎉 Résumé de la version

**v3.4.0-OMA** introduit l'**Architecture OMA** (Orchestration Min&Maï) qui permet une intégration bidirectionnelle entre MaïJinn et Min&Maï v13.0.

Cette version transforme MaïJinn d'un outil isolé de développement de carrière en un composant d'un écosystème complet combinant **stratégie business** (Min&Maï) et **développement personnel** (MaïJinn).

---

## 🆕 Nouvelles fonctionnalités

### 1. Commande `!export_profile_minmai`

**Description :** Génère un profil psychométrique JSON compatible Min&Maï v13.0

**Fonctionnalités :**
- Compilation automatique des données PHÉNIX, ARSENAL, FORGE
- Conversion des évaluations qualitatives Big Five en scores numériques (0-100)
- Format JSON standardisé pour import Min&Maï
- Instructions d'utilisation intégrées

**Données exportées :**
- Scores Big Five (5 dimensions)
- Biais dominants
- Mode de décision
- Stress triggers
- Leviers de motivation
- Patterns comportementaux

---

### 2. Commande `!import_rapport_minmai [JSON]`

**Description :** Importe et analyse les rapports psychologiques générés par Min&Maï v13.0

**Fonctionnalités :**
- Parsing et validation du JSON
- Analyse des biais observés avec détection de patterns récurrents
- Analyse des nœuds de friction avec exercices recommandés
- Célébration des victoires psychologiques
- Création automatique de plan d'action
- Mise à jour du profil si nécessaire

**Types de données importées :**
- Session metadata (durée, stress level)
- Biais observés (nom, contexte, impact, réceptivité)
- Nœuds de friction (type, durée, hypothèse)
- Victoires psychologiques (contexte, levier, progression)
- Points à travailler (observation, pattern, piste)

---

### 3. Commande `!progression_minmai [période]`

**Description :** Génère une synthèse de progression sur une période donnée

**Périodes supportées :**
- `7j` - 7 jours
- `30j` - 30 jours (défaut)
- `3m` - 3 mois
- `6m` - 6 mois
- `1a` - 1 an

**Métriques calculées :**
- Vitesse de décision (échanges/décision)
- Tolérance à l'incertitude (% certitude requise)
- Biais en régression (amélioration)
- Biais persistants (à travailler)
- Évolution du stress
- Top 3 victoires marquantes
- Score global de progression (0-10)

---

### 4. Strate 8 - Intégration OMA

**Description :** Nouvelle section de la Forge Mémorielle dédiée à l'intégration Min&Maï

**Contenu :**
- Vue d'ensemble de l'architecture OMA
- Protocoles détaillés pour chaque commande
- Formats JSON standardisés
- Nœuds de friction : définition, types, exercices
- Victoires psychologiques : scoring, importance
- Adaptations Min&Maï selon Big Five
- Flux d'utilisation recommandé
- Sécurité et confidentialité

---

### 5. Règle R7 - Commandes OMA

**Description :** Nouvelle règle de gouvernance pour les commandes OMA

**Contenu :**
- Les deux agents (PHÉNIX et Arsenal) peuvent traiter les commandes OMA
- Export profil requiert PUC complet
- Import rapport valide le profile_id avant traitement
- Progression requiert au moins 2 rapports importés

---

## 🔄 Modifications

### Prompt PHÉNIX

**Ajouts :**
- Section "Commandes OMA" avec protocoles détaillés
- Pilier "CONNECTER" ajouté (gestion échanges Min&Maï)
- Mention OMA dans le message d'accueil
- Proposition d'export après validation PUC
- Cas particuliers OMA (export sans PUC, import sans JSON, explication Min&Maï)
- Table de conversion Big Five qualitatif → numérique

**Modifications :**
- Accès à la Strate 8 ajouté
- Version mise à jour (v3.4.0-OMA)

---

### Prompt L'ARSENAL

**Ajouts :**
- Section "Commandes OMA (Support)"
- Commandes OMA dans le message d'initialisation
- Intégration des insights Min&Maï dans les livrables
- Adaptation des livrables basée sur les rapports importés
- Checklist qualité : alignment OMA
- Mention OMA dans le script de fin de mission

**Modifications :**
- Accès à la Strate 8 ajouté
- Version mise à jour (v3.4.0-OMA)

---

### Forge Mémorielle

**Ajouts :**
- Strate 8 complète (Intégration OMA)
- Sommaire mis à jour avec Strate 8
- Référence à Min&Maï v13.0 dans Strate 7.1 (Versioning)

**Modifications :**
- Version mise à jour (v3.4.0-OMA)
- Date mise à jour (22 novembre 2025)

---

### Instructions Projet

**Ajouts :**
- Section "Nouveautés v3.4.0-OMA"
- Règle R7 (Commandes OMA)
- Workflow OMA
- Protocoles OMA détaillés
- Checklist session OMA
- Sécurité OMA
- Métriques de succès OMA
- Tableau comparatif v3.3.1 → v3.4.0-OMA

**Modifications :**
- Version mise à jour (v3.4.0-OMA)
- Table des fichiers & références enrichie

---

## 📁 Nouveaux fichiers

| Fichier | Description |
|---------|-------------|
| `MAIJINN_v3.4.0_OMA_ARCHITECTURE.md` | Document d'architecture principal |
| `Forge_MEMORIELLE_v3.4.0_OMA.md` | Forge mise à jour avec Strate 8 |
| `Prompt_PHENIX_v3.4.0_OMA.md` | Prompt PHÉNIX mis à jour |
| `Prompt_ARSENAL_v3.4.0_OMA.md` | Prompt Arsenal mis à jour |
| `Instructions_Projet_v3.4.0_OMA.md` | Nouvelles instructions projet |
| `CHANGELOG_v3.4.0_OMA.md` | Ce fichier |

---

## 🔗 Compatibilité

### Min&Maï v13.0
- ✅ 100% compatible
- ✅ Format JSON standardisé
- ✅ Adaptations psychométriques supportées

### MaïJinn v3.3.1 (rétrocompatibilité)
- ✅ Toutes les fonctionnalités existantes préservées
- ✅ Commandes `/cv`, `/linkedin`, etc. inchangées
- ✅ Big Five et DISC toujours supportés
- ✅ PUC structure identique

### Sans Min&Maï
- ✅ MaïJinn fonctionne normalement sans Min&Maï
- ⚠️ Commandes OMA retournent des messages explicatifs
- ⚠️ Pas de boucle d'amélioration

---

## 🛠️ Notes de migration

### Depuis v3.3.1

**Aucune migration nécessaire** pour les fonctionnalités existantes.

Pour activer les fonctionnalités OMA :

1. **Mettre à jour les fichiers du projet Claude :**
   - Remplacer `Forge_MEMORIELLE_v3.3.1.md` par `Forge_MEMORIELLE_v3.4.0_OMA.md`
   - Remplacer `Prompt_PHENIX_v3.3.1.md` par `Prompt_PHENIX_v3.4.0_OMA.md`
   - Remplacer `Prompt_ARSENAL_v3.3.1.md` par `Prompt_ARSENAL_v3.4.0_OMA.md`
   - Remplacer les instructions projet

2. **Tester les nouvelles commandes :**
   - `!export_profile_minmai` (requiert PUC complet)
   - `!import_rapport_minmai [JSON test]`
   - `!progression_minmai 30j`

3. **Optionnel - Intégrer Min&Maï v13.0 :**
   - Utiliser le prompt Min&Maï v13.0 séparément
   - Suivre le flux OMA documenté

---

## 🐛 Corrections

*Aucune correction de bug dans cette version (nouvelle fonctionnalité uniquement)*

---

## ⚠️ Problèmes connus

### Limitation : Stockage des rapports

Les rapports Min&Maï importés ne sont pas persistés entre sessions Claude. L'utilisateur doit ré-importer si nécessaire.

**Contournement :** Utiliser la mémoire Claude ou un stockage externe.

### Limitation : Validation profile_id

La validation du profile_id dans `!import_rapport_minmai` est basique (comparaison string). Des profile_id légèrement différents seront rejetés.

**Contournement :** S'assurer que le profile_id dans le rapport correspond exactement à celui généré par `!export_profile_minmai`.

---

## 🔮 Roadmap

### v3.4.1 (Q1 2026)
- Prédictions psychométriques
- Alertes proactives
- Amélioration détection patterns

### v3.5.0 (Q2 2026)
- API bidirectionnelle automatique
- Pas de copier-coller
- Synchronisation temps réel

### v4.0.0 (Q3 2026)
- Intelligence prédictive
- Plateforme web unifiée
- Analytics avancés

---

## 📞 Support

### Questions fréquentes

**Q : Puis-je utiliser MaïJinn sans Min&Maï ?**  
R : Oui, toutes les fonctionnalités existantes fonctionnent. OMA est optionnel.

**Q : Le JSON est-il sensible ?**  
R : Oui, il contient des données psychométriques. Ne pas partager publiquement.

**Q : Quelle fréquence pour la boucle OMA ?**  
R : Idéalement 2-4 sessions Min&Maï par mois, avec import dans MaïJinn.

**Q : Comment mettre à jour depuis v3.3.1 ?**  
R : Remplacer les fichiers du projet. Aucune migration de données nécessaire.

---

## 📝 Crédits

Cette version a été développée pour intégrer :
- **Min&Maï v13.0 - Psychological Intelligence** 
- **Architecture OMA** pour créer un écosystème complet de développement des dirigeants

---

**Version :** 3.4.0-OMA  
**Date :** 22 novembre 2025  
**Statut :** Production Ready
