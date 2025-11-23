# 🔗 ÉCOSYSTÈME OMA - ORCHESTRATION MIN&MAÏ ARCHITECTURE

## 📦 Vue d'ensemble

Bienvenue dans **OMA (Orchestration Min&Maï Architecture)**, l'écosystème complet qui unifie :

- **Min&Maï v13.0** : Sparring stratégique avec intelligence psychologique
- **MaïJinn v3.4.0** : Développement personnel (PHÉNIX + ARSENAL + FORGE)
- **JDIC** : Journal de Décisions Importantes Continues (cœur décisionnel)

**Résultat :** Une boucle d'amélioration continue entre stratégie, décisions et développement personnel.

### 🎯 Composants clés

| Composant | Rôle | Documentation |
|-----------|------|---------------|
| **📘 JDIC** | Cœur décisionnel - Traçabilité des décisions | `JDIC_v3.4.1_OMA.md` |
| **🧠 PHÉNIX** | Profilage psychométrique (Big Five) | `Prompt_PHENIX_v3.4.0_OMA.md` |
| **⚔️ L'ARSENAL** | Détection et travail sur les biais | `Prompt_ARSENAL_v3.4.0_OMA.md` |
| **🔨 FORGE** | Capitalisation patterns et apprentissages | `Forge_MEMORIELLE_v3.4.0_OMA.md` |

---

## 📘 LE JDIC : PIÈCE MAÎTRESSE DE OMA

### Qu'est-ce que le JDIC ?

**JDIC = Journal de Décisions Importantes Continues**

Le JDIC est le **cœur documentaire** de l'écosystème OMA. C'est le registre vivant qui :

- ✅ **Capture** toutes les décisions stratégiques avec contexte
- ✅ **Structure** les actions avec échéances et responsables
- ✅ **Trace** l'évolution décisionnelle dans le temps
- ✅ **Alimente** MaïJinn pour le développement personnel
- ✅ **Assure** la continuité entre les sessions

> *"Une décision non documentée est une décision qui n'existe pas."*

### Pourquoi JDIC est essentiel ?

Sans JDIC, vous perdez :
- ❌ La traçabilité de vos décisions
- ❌ La continuité entre les sessions
- ❌ La capacité à mesurer votre progression
- ❌ L'analyse de vos patterns décisionnels

Avec JDIC, vous gagnez :
- ✅ Un historique complet et structuré
- ✅ Des actions claires avec accountability
- ✅ Une boucle d'amélioration continue
- ✅ Une meilleure qualité décisionnelle

### Commandes JDIC

| Commande | Description | Sortie |
|----------|-------------|--------|
| `!rapport` ou `!jdic` | Génère le JDIC de la session | JDIC markdown |
| `!rapport_complet` | Génère JDIC + Rapport Psycho | JDIC + JSON pour MaïJinn |
| `!jdic_mois` | JDIC consolidé mensuel | JDIC consolidé |

**📖 Documentation complète :** Consultez `JDIC_v3.4.1_OMA.md`

---

## 📁 Contenu du package

```
integration-phenix/
├── README.md                           ⭐ Ce fichier
├── README-INTEGRATION-PHENIX.md        📘 Guide d'intégration détaillé
├── requirements.txt                    📦 Dépendances Python
├── minmai_export.py                    🔼 Module d'export de profil
├── minmai_import.py                    🔽 Module d'import de rapport
├── minmai_progression.py               📈 Module de suivi de progression
└── tests/                              🧪 Tests unitaires
    ├── __init__.py
    └── test_minmai_export.py
```

---

## 🚀 Démarrage rapide (3 étapes)

### Étape 1 : Copier les fichiers dans PHENIX

```bash
# Depuis votre projet PHENIX
mkdir -p minmai_integration/
cp -r /chemin/vers/integration-phenix/* minmai_integration/
```

### Étape 2 : Installer les dépendances

```bash
pip install -r minmai_integration/requirements.txt
```

### Étape 3 : Intégrer dans votre code

```python
# Dans votre fichier principal PHENIX/MaïJinn

from minmai_integration import (
    export_profile_minmai_command,
    import_rapport_minmai_command,
    progression_minmai_command
)

# Utilisation
profile = export_profile_minmai_command(phenix, arsenal, forge, user_id, prenom)
```

**Consulter le guide détaillé :** `README-INTEGRATION-PHENIX.md`

---

## 🎯 Les 3 nouvelles commandes

### 1. `!export_profile_minmai`

**Fichier :** `minmai_export.py`

**Ce qu'elle fait :**
- Compile les données de PHENIX, ARSENAL et FORGE MÉMORIELLE
- Génère un JSON au format Min&Maï v13.0
- L'utilisateur copie ce JSON et l'importe dans Min&Maï

**Utilisation :**
```python
profile = export_profile_minmai_command(
    phenix=phenix_instance,
    arsenal=arsenal_instance,
    forge=forge_instance,
    user_id="123",
    prenom="Sophie"
)
```

---

### 2. `!import_rapport_minmai [JSON]`

**Fichier :** `minmai_import.py`

**Ce qu'elle fait :**
- Parse le rapport psychologique de Min&Maï
- Enregistre les biais observés dans ARSENAL
- Enregistre les nœuds de friction dans FORGE MÉMORIELLE
- Propose des exercices ciblés
- Met à jour le profil si nécessaire

**Utilisation :**
```python
rapport_json = '{"session_id": "...", ...}'
success = import_rapport_minmai_command(
    phenix=phenix_instance,
    arsenal=arsenal_instance,
    forge=forge_instance,
    user_id="123",
    rapport_json=rapport_json
)
```

---

### 3. `!progression_minmai [période]`

**Fichier :** `minmai_progression.py`

**Ce qu'elle fait :**
- Analyse l'évolution sur plusieurs sessions
- Calcule les métriques de progression
- Identifie les biais en régression vs persistants
- Génère un score global de progression

**Utilisation :**
```python
metrics = progression_minmai_command(
    arsenal=arsenal_instance,
    forge=forge_instance,
    user_id="123",
    periode="30j"  # ou "7j", "3m", etc.
)
```

---

## 📋 Checklist d'intégration

### Phase 1 : Installation
- [ ] Copier les fichiers dans PHENIX
- [ ] Installer les dépendances (`pip install -r requirements.txt`)

### Phase 2 : Implémentation
- [ ] Implémenter les méthodes PHENIX (voir guide détaillé)
  - [ ] `get_big_five_scores()`
  - [ ] `get_motivation_levers()`
  - [ ] `adjust_neuroticism()`
  - [ ] `update_evaluation_date()`

- [ ] Implémenter les méthodes ARSENAL (voir guide détaillé)
  - [ ] `get_top_biases()`
  - [ ] `analyze_decision_mode()`
  - [ ] `log_biais_occurrence()`
  - [ ] `count_biais_occurrences()`
  - [ ] `get_declining_biases()`
  - [ ] `get_persistent_biases()`

- [ ] Implémenter les méthodes FORGE MÉMORIELLE (voir guide détaillé)
  - [ ] `get_stress_triggers()`
  - [ ] `get_behavioral_patterns()`
  - [ ] `log_friction_node()`
  - [ ] `log_success_moment()`
  - [ ] `get_minmai_reports()`

### Phase 3 : Tests
- [ ] Lancer les tests unitaires : `pytest tests/`
- [ ] Tester manuellement le flux complet
- [ ] Valider avec un utilisateur test

### Phase 4 : Déploiement
- [ ] Mettre à jour la documentation utilisateur
- [ ] Former les utilisateurs aux nouvelles commandes
- [ ] Déployer en production

---

## 🔄 Flux d'utilisation complet

```
[Jour 1] MaïJinn
  User : !export_profile_minmai
  → Génère profil JSON
  → Copie le JSON généré

[Jour 2] Min&Maï v13.0
  User : !import_profile [JSON]
  → Min&Maï s'adapte au profil psychologique
  → Session de travail stratégique (45 min)
  → !rapport_complet
     ├─► 📘 JDIC (pour l'utilisateur)
     │   • Décisions prises avec échéances
     │   • Actions à prendre avec responsables
     │   • Points en suspens
     │   → L'utilisateur utilise ce JDIC pour son suivi opérationnel
     │
     └─► 📊 Rapport Psycho JSON (pour MaïJinn)
         • Biais observés
         • Nœuds de friction
         • Victoires psychologiques
         → Utilisateur copie ce JSON pour import dans MaïJinn

[Jour 3] MaïJinn
  User : !import_rapport_minmai [JSON rapport]
  → Analyse automatique (biais, nœuds, victoires)
  → Exercices recommandés
  → Plan d'action
  → Session de développement personnel

[Semaine suivante] MaïJinn
  User : !progression_minmai 7j
  → Synthèse de progression
  → Score global
  → Biais en régression vs persistants
  → Prochaines étapes

[Pendant la semaine] Utilisateur
  → Consulte le JDIC régulièrement
  → Met à jour les statuts des actions
  → Prépare la prochaine session avec Min&Maï

[Boucle continue...]
  Profil → Session → JDIC → Rapport Psycho → Analyse → Progression → ...
```

---

## 🧪 Tests

### Lancer les tests unitaires

```bash
# Installer pytest si nécessaire
pip install pytest pytest-cov

# Lancer tous les tests
pytest integration-phenix/tests/ -v

# Avec couverture de code
pytest integration-phenix/tests/ --cov=integration-phenix --cov-report=html
```

### Tests fournis

- `test_minmai_export.py` : Tests du module d'export
  - Validation de la structure JSON
  - Validation des scores Big Five
  - Sérialisation JSON
  - Format des dates

**TODO :** Ajouter `test_minmai_import.py` et `test_minmai_progression.py`

---

## 📖 Documentation

| Document | Description |
|----------|-------------|
| `README.md` | ⭐ Ce fichier (vue d'ensemble OMA) |
| `JDIC_v3.4.1_OMA.md` | ⭐ Documentation complète du JDIC (pièce maîtresse) |
| `MAIJINN_v3.4.0_OMA_ARCHITECTURE.md` | Architecture globale de l'écosystème OMA |
| `README-INTEGRATION-PHENIX.md` | Guide technique d'intégration |
| `GUIDE-MISE-A-JOUR-MAIJINN.md` | Guide avec pseudocode complet |
| `MAIJINN-INTEGRATION-GUIDE.md` | Spécifications techniques |

---

## 🎓 Exemples de code

### Exemple complet d'intégration

```python
# maijinn_main.py

from phenix import PHENIX
from arsenal import ARSENAL
from forge import ForgeMemorielle
from minmai_integration import (
    export_profile_minmai_command,
    import_rapport_minmai_command,
    progression_minmai_command
)


class MaiJinn:
    def __init__(self, user_id, prenom):
        self.user_id = user_id
        self.prenom = prenom
        self.phenix = PHENIX()
        self.arsenal = ARSENAL()
        self.forge = ForgeMemorielle()

    def handle_command(self, command, args=""):
        """Gestionnaire de commandes"""

        if command == "export_profile_minmai":
            return export_profile_minmai_command(
                self.phenix, self.arsenal, self.forge,
                self.user_id, self.prenom
            )

        elif command == "import_rapport_minmai":
            return import_rapport_minmai_command(
                self.phenix, self.arsenal, self.forge,
                self.user_id, args
            )

        elif command == "progression_minmai":
            periode = args if args else "30j"
            return progression_minmai_command(
                self.arsenal, self.forge,
                self.user_id, periode
            )

        else:
            print(f"Commande inconnue : {command}")
            return None


# Utilisation
if __name__ == "__main__":
    maijinn = MaiJinn(user_id="123", prenom="Sophie")

    # Exporter le profil
    profile = maijinn.handle_command("export_profile_minmai")
    print("Profil exporté !")

    # Importer un rapport
    rapport = '{"session_id": "...", ...}'
    maijinn.handle_command("import_rapport_minmai", rapport)

    # Voir la progression
    maijinn.handle_command("progression_minmai", "30j")
```

---

## 🐛 Dépannage

### Problème : "Module not found: minmai_integration"

**Solution :**
```python
import sys
sys.path.insert(0, '/chemin/vers/minmai_integration')
from minmai_integration import ...
```

### Problème : "AttributeError: 'PHENIX' object has no attribute..."

**Solution :** Vous devez implémenter les méthodes manquantes dans vos modules PHENIX/ARSENAL/FORGE. Voir le guide détaillé section "Étape 4".

### Problème : Tests qui échouent

**Solution :**
```bash
# Vérifier les imports
python -c "from minmai_integration import export_profile_minmai_command"

# Lancer les tests en mode verbose
pytest tests/ -v -s
```

---

## 🔗 Liens utiles

### Dans Min&Maï (repository Min-et-Mai)
- `MIN&MAÏ ULTRA v13.0 - Psychological Intelligence.md` - Prompt complet
- `GUIDE D'UTILISATION MIN&MAÏ v13.0.md` - Guide utilisateur
- `MAIJINN-INTEGRATION-GUIDE.md` - Spécifications techniques
- `GUIDE-MISE-A-JOUR-MAIJINN.md` - Guide pseudocode
- `exemples-profils/` - 5 profils types pour tests

### Dans PHENIX (ce package)
- `README-INTEGRATION-PHENIX.md` - Guide d'intégration détaillé
- `minmai_export.py` - Code source export
- `minmai_import.py` - Code source import
- `minmai_progression.py` - Code source progression
- `tests/` - Tests unitaires

---

## 📊 Métriques de succès

Après intégration, vous devriez observer :

- ✅ **Min&Maï s'adapte** automatiquement au profil de chaque utilisateur
- ✅ **MaïJinn reçoit des insights** concrets depuis les sessions Min&Maï
- ✅ **Progression mesurable** via `!progression_minmai`
- ✅ **Boucle d'amélioration** fonctionnelle

### Indicateurs quantitatifs attendus

- +40% de rapidité de décision (utilisateurs Min&Maï)
- +30% de qualité décisionnelle
- -50% de stress décisionnel
- Score de progression > 7/10 après 3 mois

---

## 🚀 Prochaines étapes

### Version 1.0 (Actuelle)
✅ Échange manuel via copier-coller JSON
✅ 3 commandes principales
✅ Tests unitaires

### Version 2.0 (Q1 2026)
🔮 API automatique (pas de copier-coller)
🔮 Synchronisation en temps réel
🔮 Notifications push

### Version 3.0 (Q2 2026)
🔮 Intelligence prédictive
🔮 Anticipation des biais
🔮 Coaching adaptatif automatique

---

## 📞 Support

### Questions fréquentes

**Q : Dois-je modifier mes modules PHENIX/ARSENAL/FORGE existants ?**
R : Oui, vous devez ajouter les méthodes listées dans le guide détaillé. Mais le code existant n'est pas modifié.

**Q : Puis-je tester sans tout implémenter ?**
R : Oui ! Les modules utilisent des mocks si les méthodes n'existent pas encore.Vous verrez juste des warnings.

**Q : Est-ce compatible avec mon architecture actuelle ?**
R : Oui, les modules sont conçus pour s'adapter. Ils n'imposent aucune structure spécifique.

### Obtenir de l'aide

1. Consultez `README-INTEGRATION-PHENIX.md` (guide détaillé)
2. Consultez `GUIDE-MISE-A-JOUR-MAIJINN.md` (dans Min&Maï)
3. Examinez les tests : `tests/test_minmai_export.py`
4. Testez les exemples fournis

---

## 🎯 Résumé

| Élément | Statut |
|---------|--------|
| Module d'export (minmai_export.py) | ✅ Prêt |
| Module d'import (minmai_import.py) | ✅ Prêt |
| Module de progression (minmai_progression.py) | ✅ Prêt |
| Documentation complète | ✅ Prête |
| Tests unitaires | ✅ Basiques fournis |
| Exemples de code | ✅ Fournis |

**Vous avez tout ce qu'il faut pour intégrer l'Intelligence Psychologique dans PHENIX !** 🚀

---

**Version :** 1.0
**Date :** Novembre 2025
**Compatibilité :** Min&Maï v13.0
**Licence :** À définir par le propriétaire de PHENIX

---

*Package créé dans le cadre de l'intégration Min&Maï v13.0 - Psychological Intelligence*
