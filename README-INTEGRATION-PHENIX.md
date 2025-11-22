# 🔧 GUIDE D'INTÉGRATION - PHENIX/MaïJinn ↔ Min&Maï v13.0

## 📦 Contenu de ce dossier

Ce dossier contient **tout ce dont vous avez besoin** pour intégrer les fonctionnalités d'échange avec Min&Maï v13.0 dans PHENIX/MaïJinn.

### Fichiers fournis

| Fichier | Description |
|---------|-------------|
| `minmai_export.py` | Module d'export de profil psychométrique |
| `minmai_import.py` | Module d'import de rapport Min&Maï |
| `minmai_progression.py` | Module de suivi de progression |
| `requirements.txt` | Dépendances Python nécessaires |
| `tests/` | Tests unitaires pour valider l'intégration |
| `README-INTEGRATION-PHENIX.md` | Ce fichier |

---

## 🎯 Vue d'ensemble

### 3 nouvelles commandes à ajouter à MaïJinn

1. **`!export_profile_minmai`** → Génère le profil psychométrique au format Min&Maï
2. **`!import_rapport_minmai [JSON]`** → Importe et analyse le rapport psychologique de Min&Maï
3. **`!progression_minmai [période]`** → Génère une synthèse de progression (bonus)

---

## 📋 ÉTAPE 1 : Installation

### 1.1 Copier les fichiers dans PHENIX

Copiez le contenu de ce dossier dans votre projet PHENIX :

```bash
# Depuis votre projet PHENIX
mkdir -p minmai_integration/
cp /chemin/vers/integration-phenix/* minmai_integration/
```

### 1.2 Installer les dépendances

```bash
pip install -r minmai_integration/requirements.txt
```

---

## 📋 ÉTAPE 2 : Intégration dans l'architecture PHENIX

### 2.1 Architecture actuelle de PHENIX (à adapter)

Vous devez avoir une structure similaire à :

```
PHENIX/
├── phenix/           # Module PHENIX (Big Five)
│   ├── __init__.py
│   ├── evaluator.py
│   └── ...
├── arsenal/          # Module ARSENAL (Biais)
│   ├── __init__.py
│   ├── detector.py
│   └── ...
├── forge/            # Module FORGE MÉMORIELLE
│   ├── __init__.py
│   ├── memory.py
│   └── ...
└── maijinn.py        # Point d'entrée principal
```

### 2.2 Ajouter le module d'intégration Min&Maï

```
PHENIX/
├── phenix/
├── arsenal/
├── forge/
├── minmai_integration/  ⭐ NOUVEAU
│   ├── __init__.py
│   ├── minmai_export.py
│   ├── minmai_import.py
│   ├── minmai_progression.py
│   └── tests/
└── maijinn.py
```

---

## 📋 ÉTAPE 3 : Modifier le code PHENIX

### 3.1 Créer `minmai_integration/__init__.py`

```python
"""
Module d'intégration avec Min&Maï v13.0
"""

from .minmai_export import export_profile_minmai_command
from .minmai_import import import_rapport_minmai_command
from .minmai_progression import progression_minmai_command

__all__ = [
    'export_profile_minmai_command',
    'import_rapport_minmai_command',
    'progression_minmai_command'
]
```

### 3.2 Modifier `maijinn.py` (point d'entrée)

Ajoutez les imports et les commandes :

```python
# maijinn.py

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

        # Initialiser les modules
        self.phenix = PHENIX()
        self.arsenal = ARSENAL()
        self.forge = ForgeMemorielle()

    def process_command(self, command: str, args: str = ""):
        """
        Traite les commandes utilisateur

        Args:
            command: Nom de la commande (ex: "export_profile_minmai")
            args: Arguments de la commande
        """
        if command == "export_profile_minmai":
            return self._handle_export_profile()

        elif command == "import_rapport_minmai":
            return self._handle_import_rapport(args)

        elif command == "progression_minmai":
            periode = args if args else "30j"
            return self._handle_progression(periode)

        # ... autres commandes existantes ...

    def _handle_export_profile(self):
        """Gère la commande !export_profile_minmai"""
        profile = export_profile_minmai_command(
            phenix=self.phenix,
            arsenal=self.arsenal,
            forge=self.forge,
            user_id=self.user_id,
            prenom=self.prenom
        )
        return profile

    def _handle_import_rapport(self, rapport_json: str):
        """Gère la commande !import_rapport_minmai [JSON]"""
        success = import_rapport_minmai_command(
            phenix=self.phenix,
            arsenal=self.arsenal,
            forge=self.forge,
            user_id=self.user_id,
            rapport_json=rapport_json
        )
        return success

    def _handle_progression(self, periode: str):
        """Gère la commande !progression_minmai [période]"""
        metrics = progression_minmai_command(
            arsenal=self.arsenal,
            forge=self.forge,
            user_id=self.user_id,
            periode=periode
        )
        return metrics


# Point d'entrée
if __name__ == "__main__":
    user_id = "123"
    prenom = "Sophie"

    maijinn = MaiJinn(user_id, prenom)

    # Exemple d'utilisation
    maijinn.process_command("export_profile_minmai")
```

---

## 📋 ÉTAPE 4 : Implémenter les méthodes manquantes

Les modules fournis utilisent des méthodes qui **doivent être implémentées** dans vos modules PHENIX, ARSENAL et FORGE MÉMORIELLE.

### 4.1 Méthodes à implémenter dans PHENIX

```python
# phenix/evaluator.py

class PHENIX:
    def get_big_five_scores(self, user_id: str) -> Dict[str, int]:
        """
        Retourne les scores Big Five (0-100)

        Returns:
            {
                "Openness": 65,
                "Conscientiousness": 45,
                "Extraversion": 70,
                "Agreeableness": 82,
                "Neuroticism": 73
            }
        """
        # TODO: Implémenter la logique de récupération
        pass

    def get_motivation_levers(self, user_id: str) -> List[str]:
        """
        Retourne les leviers de motivation

        Returns:
            ["Impact social", "Reconnaissance", "Autonomie"]
        """
        # TODO: Implémenter
        pass

    def adjust_neuroticism(self, user_id: str, adjustment: int) -> None:
        """
        Ajuste le score Neuroticism (ex: +5 si stress élevé)

        Args:
            adjustment: Valeur à ajouter (peut être négative)
        """
        # TODO: Implémenter
        pass

    def update_evaluation_date(self, user_id: str, date: str) -> None:
        """
        Met à jour la date d'évaluation du profil

        Args:
            date: Date au format "YYYY-MM-DD"
        """
        # TODO: Implémenter
        pass
```

### 4.2 Méthodes à implémenter dans ARSENAL

```python
# arsenal/detector.py

class ARSENAL:
    def get_top_biases(self, user_id: str, limit: int = 5) -> List[str]:
        """
        Retourne les N biais les plus fréquents

        Returns:
            ["Biais de confirmation", "Aversion à la perte", ...]
        """
        # TODO: Implémenter
        pass

    def analyze_decision_mode(self, user_id: str) -> str:
        """
        Analyse le mode de décision de l'utilisateur

        Returns:
            "Intuitif sous pression" / "Analytique équilibré" / etc.
        """
        # TODO: Implémenter
        pass

    def log_biais_occurrence(self, user_id: str, biais_name: str,
                            contexte: str, impact: str, date: str) -> None:
        """
        Enregistre une occurrence de biais détectée par Min&Maï

        Args:
            biais_name: Nom du biais (ex: "Aversion à la perte")
            contexte: Contexte de manifestation
            impact: Impact observé
            date: Date de l'observation
        """
        # TODO: Implémenter
        pass

    def count_biais_occurrences(self, user_id: str, biais_name: str,
                                days: int = 30) -> int:
        """
        Compte le nombre d'occurrences d'un biais sur une période

        Returns:
            Nombre d'occurrences
        """
        # TODO: Implémenter
        pass

    def mark_as_priority_pattern(self, user_id: str, biais_name: str) -> None:
        """
        Marque un biais comme pattern récurrent à traiter en priorité
        """
        # TODO: Implémenter
        pass

    def get_declining_biases(self, user_id: str, days: int) -> Dict:
        """
        Retourne les biais en régression

        Returns:
            {
                "Biais de confirmation": {
                    "reduction": 60,
                    "count_before": 8,
                    "count_after": 3
                }
            }
        """
        # TODO: Implémenter
        pass

    def get_persistent_biases(self, user_id: str, days: int) -> Dict:
        """
        Retourne les biais persistants

        Returns:
            {
                "Aversion à la perte": {
                    "status": "Stable",
                    "count": 5
                }
            }
        """
        # TODO: Implémenter
        pass
```

### 4.3 Méthodes à implémenter dans FORGE MÉMORIELLE

```python
# forge/memory.py

class ForgeMemorielle:
    def get_stress_triggers(self, user_id: str) -> List[str]:
        """
        Retourne les déclencheurs de stress identifiés

        Returns:
            ["Deadlines serrées", "Conflits d'équipe", ...]
        """
        # TODO: Implémenter
        pass

    def get_behavioral_patterns(self, user_id: str, days: int = 30) -> List[str]:
        """
        Retourne les patterns comportementaux récurrents

        Returns:
            ["Analysis paralysis", "Évitement des conflits", ...]
        """
        # TODO: Implémenter
        pass

    def log_friction_node(self, user_id: str, titre: str, type: str,
                         hypothese: str, verbatim: str, date: str) -> None:
        """
        Enregistre un nœud de friction détecté par Min&Maï

        Args:
            titre: Titre du nœud
            type: Type (Analysis paralysis / Déni / Évitement)
            hypothese: Hypothèse psychologique
            verbatim: Citation clé de l'utilisateur
            date: Date de détection
        """
        # TODO: Implémenter
        pass

    def log_success_moment(self, user_id: str, titre: str,
                          contexte: str, levier: str, date: str) -> None:
        """
        Enregistre un moment de succès / victoire psychologique

        Args:
            titre: Titre de la victoire
            contexte: Contexte
            levier: Ce qui a aidé
            date: Date
        """
        # TODO: Implémenter
        pass

    def get_minmai_reports(self, user_id: str, days: int) -> List[Dict]:
        """
        Retourne tous les rapports Min&Maï importés sur une période

        Returns:
            Liste de rapports triés par date
        """
        # TODO: Implémenter
        # Note: Vous devez stocker les rapports importés pour cette méthode
        pass
```

---

## 📋 ÉTAPE 5 : Tester l'intégration

### 5.1 Tests unitaires

```bash
# Lancer les tests
pytest minmai_integration/tests/
```

### 5.2 Test manuel du flux complet

```python
# test_integration_complete.py

from maijinn import MaiJinn
import json

# 1. Créer une instance MaiJinn
maijinn = MaiJinn(user_id="TEST_001", prenom="Sophie")

# 2. Exporter le profil
print("=== TEST 1: Export profil ===")
profile = maijinn.process_command("export_profile_minmai")
profile_json = json.dumps(profile, indent=2)
print(profile_json)

# 3. Simuler une session Min&Maï (normalement fait par l'utilisateur)
# ... utilisateur utilise Min&Maï avec ce profil ...

# 4. Importer un rapport Min&Maï
print("\n=== TEST 2: Import rapport ===")
rapport_exemple = {
    "session_id": "SESSION_TEST",
    "profile_id": "USER_TEST_001",
    "session_date": "2025-11-21",
    "session_duration_minutes": 45,
    "stress_level": 7,
    "biais_observes": [
        {
            "nom": "Aversion à la perte",
            "contexte": "Refus de licencier",
            "impact": "Bloque restructuration",
            "receptivite": "Moyenne"
        }
    ],
    "noeuds_friction": [],
    "victoires_psychologiques": [],
    "points_a_travailler": []
}

success = maijinn.process_command(
    "import_rapport_minmai",
    json.dumps(rapport_exemple)
)

print(f"Import réussi : {success}")

# 5. Voir la progression
print("\n=== TEST 3: Progression ===")
metrics = maijinn.process_command("progression_minmai", "30j")
```

---

## 📋 ÉTAPE 6 : Déploiement

### 6.1 Checklist avant déploiement

- [ ] Tous les modules sont installés
- [ ] Toutes les méthodes PHENIX/ARSENAL/FORGE sont implémentées
- [ ] Les tests unitaires passent
- [ ] Le test d'intégration complète fonctionne
- [ ] La documentation utilisateur est à jour

### 6.2 Mise à jour de la documentation utilisateur

Ajoutez dans votre documentation MaïJinn :

```markdown
## Nouvelles commandes v2.0 - Intégration Min&Maï

### !export_profile_minmai
Génère votre profil psychométrique au format Min&Maï v13.0

**Usage :**
!export_profile_minmai

**Résultat :**
Un JSON à copier-coller dans Min&Maï avec la commande :
!import_profile [JSON]

---

### !import_rapport_minmai [JSON]
Importe un rapport psychologique généré par Min&Maï

**Usage :**
!import_rapport_minmai {"session_id": "...", ...}

**Résultat :**
Analyse automatique + Exercices recommandés + Plan d'action

---

### !progression_minmai [période]
Affiche votre progression sur une période

**Usage :**
!progression_minmai 30j
!progression_minmai 3m

**Résultat :**
Synthèse avec score de progression et prochaines étapes
```

---

## 🔄 Flux d'utilisation complet

```
[Jour 1] Utilisateur dans MaïJinn
  → !export_profile_minmai
  → Copie le JSON

[Jour 1] Utilisateur dans Min&Maï v13.0
  → !import_profile [JSON]
  → Min&Maï s'adapte au profil
  → Session de travail stratégique (45 min)
  → !rapport_psycho
  → Copie le JSON rapport

[Jour 2] Utilisateur dans MaïJinn
  → !import_rapport_minmai [JSON rapport]
  → Analyse automatique
  → Exercices proposés
  → Session de travail sur biais

[Semaine suivante] Utilisateur dans MaïJinn
  → !progression_minmai 7j
  → Voit sa progression
  → !export_profile_minmai (profil mis à jour)
  → Retour dans Min&Maï avec nouveau profil

[Boucle continue...]
```

---

## 🐛 Dépannage

### Problème : "AttributeError: 'PHENIX' object has no attribute 'get_big_five_scores'"

**Solution :** La méthode n'est pas implémentée dans PHENIX. Voir ÉTAPE 4.1

---

### Problème : "JSON decode error"

**Solution :** Vérifiez que le JSON copié-collé est complet et valide.
Utilisez `json.loads()` pour valider :

```python
import json
try:
    data = json.loads(votre_json)
    print("JSON valide !")
except json.JSONDecodeError as e:
    print(f"Erreur : {e}")
```

---

### Problème : "Aucun rapport trouvé"

**Solution :** Assurez-vous que `forge.get_minmai_reports()` stocke bien les rapports importés.

---

## 📞 Support

Pour toute question :
1. Consultez `GUIDE-MISE-A-JOUR-MAIJINN.md` (dans Min&Maï)
2. Consultez `MAIJINN-INTEGRATION-GUIDE.md` (spécifications techniques)
3. Examinez les tests unitaires dans `tests/`

---

## 🎯 Prochaines étapes après intégration

Une fois l'intégration terminée :

1. **Testez avec des utilisateurs réels**
2. **Collectez les feedbacks**
3. **Optimisez les algorithmes** (détection de patterns, recommandations)
4. **Phase 2 (Q1 2026)** : API automatique (sans copier-coller)
5. **Phase 3 (Q2 2026)** : Intelligence prédictive

---

**Version :** 1.0
**Date :** Novembre 2025
**Compatibilité :** Min&Maï v13.0

---

*L'union de Min&Maï (stratégie) et MaïJinn (psychologie) crée un écosystème complet de croissance pour les dirigeants.*
