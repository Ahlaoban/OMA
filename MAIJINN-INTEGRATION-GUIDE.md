# GUIDE D'INTÉGRATION MAÏJINN ↔ MIN&MAÏ v13.0

**Objectif :** Permettre une communication bidirectionnelle entre MaïJinn (coach psychologique) et Min&Maï (sparring partner stratégique).

---

## 1. ARCHITECTURE DE L'INTÉGRATION

```
┌─────────────────────────────────────────────────────────────┐
│                    ÉCOSYSTÈME COMPLET                       │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  ┌──────────────┐         ┌──────────────┐                │
│  │   MAÏJINN    │◄────────┤  MIN&MAÏ     │                │
│  │              │         │              │                │
│  │ PHENIX       │  JSON   │ Stratégie    │                │
│  │ ARSENAL      │  Profil │ Décisions    │                │
│  │ FORGE MEM.   │────────►│ Sparring     │                │
│  └──────────────┘         └──────────────┘                │
│         │                         │                         │
│         │                         │                         │
│         ▼                         ▼                         │
│  Développement            Insights Psycho                  │
│  Personnel                (Nœuds de friction)              │
│  (Biais, Patterns)        (Biais observés)                 │
│                           (Victoires)                       │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

**Flux de données :**

1. **MaïJinn → Min&Maï** : Profil psychométrique (JSON)
2. **Min&Maï → MaïJinn** : Rapport psychologique de session (JSON + Texte)
3. **MaïJinn → MaïJinn** : Mise à jour du profil basée sur les insights Min&Maï

---

## 2. MODIFICATIONS REQUISES DANS MAÏJINN

### 2.1 Nouvelle fonctionnalité : Génération de Profil pour Min&Maï

**Commande MaïJinn :** `!export_profile_minmai`

**Logique :**

MaïJinn doit compiler les données de PHENIX, ARSENAL et FORGE MÉMORIELLE en un JSON standardisé que Min&Maï peut lire.

**Format JSON de sortie :**

```json
{
  "profile_id": "USER_[ID_UNIQUE]",
  "prenom": "[Prénom de l'utilisateur]",
  "date_evaluation": "[Date au format YYYY-MM-DD]",
  "big_five": {
    "Openness": 65,
    "Conscientiousness": 45,
    "Extraversion": 70,
    "Agreeableness": 82,
    "Neuroticism": 73
  },
  "biais_dominants": [
    "Biais de confirmation",
    "Aversion à la perte",
    "Ancrage"
  ],
  "mode_decision": "Intuitif sous pression",
  "stress_triggers": [
    "Deadlines serrées",
    "Conflits d'équipe",
    "Incertitude financière"
  ],
  "leviers_motivation": [
    "Impact social",
    "Reconnaissance",
    "Autonomie"
  ],
  "patterns_comportementaux": [
    "Évitement des conflits",
    "Micro-gestion sous stress",
    "Procrastination sur décisions difficiles"
  ],
  "dernier_update": "[Timestamp]"
}
```

**Sources de données MaïJinn :**

| Champ JSON | Source MaïJinn | Méthode d'extraction |
|------------|----------------|----------------------|
| `profile_id` | FORGE MÉMORIELLE | ID utilisateur unique |
| `prenom` | PHENIX | Données utilisateur |
| `big_five.*` | PHENIX | Scores psychométriques Big Five |
| `biais_dominants` | ARSENAL | Top 3-5 biais détectés par fréquence |
| `mode_decision` | ARSENAL | Analyse des patterns de décision |
| `stress_triggers` | FORGE MÉMORIELLE | Événements corrélés avec stress élevé |
| `leviers_motivation` | PHENIX + ARSENAL | Analyse des réussites et engagements |
| `patterns_comportementaux` | FORGE MÉMORIELLE | Récurrence de comportements sur 30 jours |

---

### 2.2 Nouvelle fonctionnalité : Import de Rapport Min&Maï

**Commande MaïJinn :** `!import_rapport_minmai [JSON]`

**Format JSON reçu de Min&Maï :**

```json
{
  "session_id": "SESSION_[ID]",
  "profile_id": "USER_123",
  "session_date": "2025-11-21",
  "session_duration_minutes": 45,

  "stress_level": 7,

  "biais_observes": [
    {
      "nom": "Aversion à la perte",
      "contexte": "Refus de licencier un employé non performant",
      "impact": "Bloque restructuration nécessaire",
      "receptivite": "Moyenne"
    },
    {
      "nom": "Biais de confirmation",
      "contexte": "Cherche uniquement des arguments pro Option A",
      "impact": "Risque de décision sous-optimale",
      "receptivite": "Haute"
    }
  ],

  "noeuds_friction": [
    {
      "titre": "Licenciement de Thomas",
      "type": "Déni rationalisé",
      "duree_echanges": 4,
      "verbatim_cle": "Je sais qu'il faut le faire, mais c'est une période difficile pour lui...",
      "hypothese_psychologique": "Culpabilité + Évitement du conflit",
      "resolution": "Partielle - Décision reportée à J+7"
    }
  ],

  "victoires_psychologiques": [
    {
      "titre": "A tranché sur le pivot stratégique malgré l'incertitude",
      "contexte": "Décision de changer de marché cible sans données complètes",
      "difficulte": "Aversion au risque + Besoin de certitude",
      "levier_utilise": "Pré-mortem + Pensée de Second Ordre",
      "progression": "Première décision majeure sans 'analyse paralysis'"
    }
  ],

  "points_a_travailler": [
    {
      "titre": "Tendance à la micro-gestion sous stress",
      "observation": "Quand stress_level > 6, veut contrôler chaque détail",
      "pattern": "Récurrent (3ème occurrence)",
      "impact_potentiel": "Épuisement + Désengagement de l'équipe",
      "piste_travail": "Exercices de délégation + Travail sur confiance"
    }
  ],

  "efficacite_adaptations": {
    "neuroticism_adaptation": "Haute",
    "agreeableness_adaptation": "Moyenne",
    "conscientiousness_adaptation": "Haute",
    "openness_adaptation": "Non applicable cette session",
    "extraversion_adaptation": "Non applicable cette session"
  },

  "verbatims_cles": [
    "Je sais qu'il faut le faire, mais c'est une période difficile pour lui...",
    "J'ai peur de me tromper et de devoir tout recommencer",
    "Pour une fois, j'ai décidé sans avoir toutes les réponses, et ça fait du bien"
  ]
}
```

---

### 2.3 Logique de Traitement MaïJinn

**Quand MaïJinn reçoit un rapport Min&Maï :**

#### Étape 1 : Validation et parsing
```
- Vérifier que profile_id correspond à l'utilisateur actif
- Parser le JSON
- Stocker dans FORGE MÉMORIELLE
```

#### Étape 2 : Analyse des biais
```
POUR CHAQUE biais observé :
  - Croiser avec historique ARSENAL
  - Si récurrent (3+ occurrences) → Marquer comme "pattern à traiter prioritairement"
  - Si nouveau → Ajouter à la liste de surveillance
  - Si réceptivité "Haute" → Opportunité d'apprentissage
```

#### Étape 3 : Traitement des nœuds de friction
```
POUR CHAQUE nœud de friction :
  - Identifier le mécanisme psychologique sous-jacent
  - Chercher patterns similaires dans FORGE MÉMORIELLE
  - Proposer exercices ciblés :
    * Si "Évitement du conflit" → Exercices d'assertivité
    * Si "Analysis paralysis" → Exercices de décision sous incertitude
    * Si "Aversion à la perte" → Recadrage cognitif (gains vs pertes)
```

#### Étape 4 : Célébration des victoires
```
POUR CHAQUE victoire psychologique :
  - Enregistrer dans FORGE MÉMORIELLE comme "moment de succès"
  - Analyser le levier qui a fonctionné
  - Utiliser ce levier comme référence future ("Tu te souviens quand...")
  - Mettre à jour les scores de progression
```

#### Étape 5 : Plan d'action
```
POUR CHAQUE point à travailler :
  - Générer un objectif de développement spécifique
  - Proposer un protocole d'entraînement
  - Planifier une réévaluation dans 2-4 semaines
```

#### Étape 6 : Mise à jour du profil
```
- Ajuster les scores Big Five si changement significatif observé
- Mettre à jour la liste des biais_dominants (fréquence récente)
- Actualiser les stress_triggers si nouveaux identifiés
- Mettre à jour date_evaluation
```

---

### 2.4 Nouvelle commande MaïJinn : Synthèse de Progression

**Commande :** `!progression_minmai [période]`

**Exemples :**
- `!progression_minmai 30j` → Derniers 30 jours
- `!progression_minmai 3m` → Derniers 3 mois

**Sortie attendue :**

```markdown
# SYNTHÈSE DE PROGRESSION - [Prénom]
## Période : [Date début] → [Date fin]

---

## 📈 ÉVOLUTION DES COMPÉTENCES DÉCISIONNELLES

### Vitesse de décision
- Début période : Moyenne de 5.2 échanges avant décision
- Fin période : Moyenne de 3.1 échanges avant décision
- **Progression : +40% de rapidité**

### Tolérance à l'incertitude
- Début période : Besoin de 85% de certitude pour trancher
- Fin période : Capable de décider à 65% de certitude
- **Progression : +20 points de confort**

---

## 🎯 BIAIS EN RÉGRESSION (Bravo !)

1. **Biais de confirmation** : -60% de manifestations
   - Octobre : 8 occurrences / 10 sessions
   - Novembre : 3 occurrences / 10 sessions

2. **Analysis paralysis** : -50% de manifestations
   - Octobre : 6 nœuds de friction
   - Novembre : 3 nœuds de friction

---

## ⚠️ BIAIS PERSISTANTS (À travailler)

1. **Aversion à la perte** : Stable (pas de régression)
   - Toujours actif dans décisions RH difficiles
   - Recommandation : Exercices ARSENAL #12 (Reframing gains/pertes)

2. **Évitement du conflit** : En légère hausse (+10%)
   - Contexte : Période de tensions d'équipe
   - Recommandation : Travail sur assertivité

---

## 🏆 VICTOIRES MARQUANTES

1. **[Date] - Pivot stratégique sans données complètes**
   - Contexte : [...]
   - Levier : Pré-mortem
   - Impact : Décision qui a rapporté +30% de CA

2. **[Date] - Licenciement assumé malgré culpabilité**
   - Contexte : [...]
   - Levier : Confrontation Min&Maï
   - Impact : Équipe apaisée, performance +15%

---

## 🎓 PROCHAINES ÉTAPES

**Objectif 1 : Maîtriser l'aversion à la perte**
- Protocole ARSENAL #12 + #18
- 2 sessions MaïJinn dédiées
- Réévaluation dans 3 semaines

**Objectif 2 : Renforcer l'assertivité**
- Exercices pratiques de communication difficile
- Simulation avec Min&Maï (mode contradictoire)
- Réévaluation dans 4 semaines

---

**Score de progression global : 7.2/10** (Excellent, continue !)
```

---

## 3. DIALOGUE MAÏJINN ↔ MIN&MAÏ

### Scénario 1 : Début de parcours utilisateur

**Jour 1 - Utilisateur découvre MaïJinn**
```
User → MaïJinn
MaïJinn : "Bonjour ! Je suis MaïJinn, ton coach de développement personnel
           spécialisé en psychologie décisionnelle.

           Je vais d'abord t'évaluer avec PHENIX (Big Five), puis on travaillera
           ensemble sur tes biais avec ARSENAL.

           À la fin, je te génèrerai un profil que tu pourras utiliser avec
           Min&Maï, ton sparring partner stratégique.

           Min&Maï va s'adapter à ton fonctionnement unique pour t'accompagner
           au mieux dans tes décisions business. Cool, non ?"

[Session d'évaluation PHENIX]

MaïJinn : "✅ Évaluation terminée !

           Voici ton profil psychologique :
           [Affichage des scores Big Five]

           Je vais maintenant générer ton profil pour Min&Maï.

           !export_profile_minmai

           ✅ Profil généré ! Copie ce JSON et utilise la commande
           !import_profile dans Min&Maï pour qu'il s'adapte à toi :

           [JSON affiché]

           Tu peux maintenant aller travailler avec Min&Maï, et il sera
           parfaitement calibré pour toi !"
```

---

### Scénario 2 : Après une session Min&Maï

**Jour 7 - Retour à MaïJinn avec rapport**

```
User → MaïJinn : "Salut, j'ai fait une session avec Min&Maï"

MaïJinn : "Génial ! Tu as le rapport psychologique de la session ?

           Utilise la commande !rapport_psycho dans Min&Maï, copie le
           JSON, et utilise ici : !import_rapport_minmai [JSON]"

User : "!import_rapport_minmai [...]"

MaïJinn : "✅ Rapport analysé !

           Voici ce que j'observe :

           **🎉 Victoires :**
           - Tu as tranché sur le pivot stratégique sans avoir 100% des données !
             C'est une ÉNORME progression pour toi. Félicitations !

           **⚠️ Points de vigilance :**
           - L'aversion à la perte est réapparue sur la décision RH.
             Min&Maï a détecté que tu tournais en rond pendant 4 échanges.

           **📝 Plan d'action :**
           Je te propose une session de travail sur l'aversion à la perte.
           On va faire l'exercice ARSENAL #12 (Reframing gains/pertes).

           Ça te dit de travailler là-dessus maintenant ou tu préfères
           qu'on programme ça ?"
```

---

### Scénario 3 : Boucle d'amélioration continue

**Jour 30 - Utilisateur revient à Min&Maï après plusieurs sessions MaïJinn**

```
User → Min&Maï

Min&Maï : "Salut [Prénom] ! Ça fait 3 semaines qu'on ne s'est pas vus.

           J'ai vu que tu as travaillé avec MaïJinn entre-temps.
           Tu veux que je recharge ton profil à jour ?

           !import_profile [récupération auto du profil MaïJinn v2]

           ✅ Profil mis à jour !

           **Changements détectés depuis la dernière fois :**
           - Ton Neuroticism a baissé de 73 → 65 (super progression !)
           - Ton biais d'aversion à la perte est en régression (-40%)

           **Nouvelles adaptations :**
           - Je peux être un peu plus challengeant maintenant (tu gères mieux le stress)
           - Je vais moins hésiter à te pousser sur les décisions RH difficiles

           Prêt pour la suite ? Quel est ton défi du jour ?"
```

---

## 4. SPÉCIFICATIONS TECHNIQUES D'INTÉGRATION

### 4.1 Format d'échange de données

**Standard :** JSON avec validation de schéma

**Schéma de validation du Profil (MaïJinn → Min&Maï) :**

```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "title": "MaïJinn Psychological Profile",
  "type": "object",
  "required": ["profile_id", "prenom", "date_evaluation", "big_five"],
  "properties": {
    "profile_id": {
      "type": "string",
      "pattern": "^USER_[A-Z0-9]+$"
    },
    "prenom": {
      "type": "string",
      "minLength": 1
    },
    "date_evaluation": {
      "type": "string",
      "format": "date"
    },
    "big_five": {
      "type": "object",
      "required": ["Openness", "Conscientiousness", "Extraversion", "Agreeableness", "Neuroticism"],
      "properties": {
        "Openness": {"type": "integer", "minimum": 0, "maximum": 100},
        "Conscientiousness": {"type": "integer", "minimum": 0, "maximum": 100},
        "Extraversion": {"type": "integer", "minimum": 0, "maximum": 100},
        "Agreeableness": {"type": "integer", "minimum": 0, "maximum": 100},
        "Neuroticism": {"type": "integer", "minimum": 0, "maximum": 100}
      }
    },
    "biais_dominants": {
      "type": "array",
      "items": {"type": "string"}
    },
    "mode_decision": {"type": "string"},
    "stress_triggers": {
      "type": "array",
      "items": {"type": "string"}
    },
    "leviers_motivation": {
      "type": "array",
      "items": {"type": "string"}
    }
  }
}
```

---

### 4.2 Stockage et Sécurité

**MaïJinn (côté stockage long terme) :**
- Profils stockés dans FORGE MÉMORIELLE
- Historique des rapports Min&Maï conservé
- Analyse longitudinale possible

**Min&Maï (côté session) :**
- Profil chargé en mémoire de session uniquement
- Pas de stockage permanent (confidentialité)
- Génération de rapport à la demande

**Sécurité :**
- Transmission via JSON copier-coller (pas d'API externe pour éviter fuites)
- Chiffrement optionnel si implémentation future en API
- Consentement utilisateur explicite avant partage de données

---

### 4.3 Gestion des versions

**Versioning des profils :**

```json
{
  "profile_version": "1.0",
  "profile_id": "USER_123",
  "date_evaluation": "2025-11-21",
  "previous_versions": [
    {"date": "2025-10-15", "version": "0.9"},
    {"date": "2025-09-10", "version": "0.8"}
  ],
  ...
}
```

**Rétrocompatibilité :**
- Min&Maï v13.0 doit accepter les profils v1.0
- Si champs manquants → Utiliser des valeurs par défaut
- Avertir l'utilisateur si profil obsolète (> 90 jours)

---

## 5. PROTOCOLES DE COLLABORATION MAÏJINN ↔ MIN&MAÏ

### Protocole 1 : Détection de crise

**Déclencheur Min&Maï :** Stress_level ≥ 8 dans rapport

**Action automatique :**
```
Min&Maï → [En fin de session]
"⚠️ J'ai détecté un niveau de stress élevé aujourd'hui (8/10).

Je recommande vivement une session MaïJinn pour décompresser
et analyser ce qui se passe sous la surface.

Veux-tu que je génère un rapport prioritaire pour MaïJinn ?"

[Si Oui]
→ Génération d'un rapport marqué "PRIORITÉ HAUTE"
→ JSON contient un champ "crisis_mode": true
```

**Réaction MaïJinn :** Quand `crisis_mode: true`
```
MaïJinn : "⚠️ Min&Maï m'a signalé que tu as vécu une session stressante.

Avant de parler stratégie, on va prendre soin de toi.

Protocole de décompression immédiate activé.

Raconte-moi ce qui s'est passé, sans filtre."

[Session de débriefing émotionnel]
```

---

### Protocole 2 : Célébration des victoires

**Déclencheur Min&Maï :** Victoire psychologique majeure détectée

**Action automatique :**
```
Min&Maï → [Fin de session]
"🎉 Félicitations ! Aujourd'hui tu as réussi à [victoire].

C'est un vrai tournant. Tu devrais partager ça avec MaïJinn
pour ancrer cette réussite."

[Génération rapport avec champ "celebrate": true]
```

**Réaction MaïJinn :** Quand `celebrate: true`
```
MaïJinn : "🎉🎉🎉 BRAVO !

Min&Maï m'a dit que tu as [victoire] !

C'est ÉNORME pour toi, parce que [rappel du contexte historique].

On va ancrer ça. Dis-moi :
- Comment tu te sens ?
- Qu'est-ce qui a fait la différence cette fois ?
- Comment tu peux reproduire ça ?"

[Enregistrement dans FORGE MÉMORIELLE comme référence positive]
```

---

### Protocole 3 : Alerte pattern récurrent

**Déclencheur MaïJinn :** Même biais détecté 3+ fois par Min&Maï en 30 jours

**Action proactive MaïJinn :**
```
MaïJinn → [Au démarrage de session]
"Hey [Prénom],

J'ai analysé tes dernières sessions avec Min&Maï.

J'observe que [Biais X] revient systématiquement dans [Contexte Y].

C'est devenu un pattern. On doit travailler dessus.

Je te propose un plan de 3 sessions pour casser ce mécanisme.
Tu es partant ?"
```

---

## 6. ROADMAP D'INTÉGRATION

### Phase 1 : Intégration Manuelle (Q4 2025)
- ✅ Définition des formats JSON
- ✅ Commandes manuelles (`!export_profile_minmai`, `!import_rapport_minmai`)
- ✅ Copier-coller entre MaïJinn et Min&Maï

### Phase 2 : Automatisation Partielle (Q1 2026)
- 🔄 API interne simple (si même plateforme)
- 🔄 Synchronisation automatique des profils
- 🔄 Notifications push (MaïJinn → Min&Maï et vice-versa)

### Phase 3 : Intelligence Prédictive (Q2 2026)
- 🔮 MaïJinn prédit les blocages probables avant session Min&Maï
- 🔮 Min&Maï adapte proactivement le style selon évolution récente
- 🔮 Feedback loop complet et automatisé

---

## 7. CHECKLIST DE MISE EN ŒUVRE

### Pour développer MaïJinn :

- [ ] Implémenter l'évaluation Big Five (PHENIX)
- [ ] Créer la commande `!export_profile_minmai`
- [ ] Créer la commande `!import_rapport_minmai`
- [ ] Développer l'analyse des rapports Min&Maï (Étapes 1-6)
- [ ] Créer la commande `!progression_minmai`
- [ ] Implémenter les protocoles de collaboration (Crise, Célébration, Alerte)
- [ ] Tester l'intégration avec Min&Maï v13.0

### Pour utiliser l'intégration :

- [ ] Faire l'évaluation initiale avec MaïJinn
- [ ] Générer le profil JSON (`!export_profile_minmai`)
- [ ] Importer le profil dans Min&Maï (`!import_profile [JSON]`)
- [ ] Faire une session de travail avec Min&Maï
- [ ] Générer le rapport psycho (`!rapport_psycho`)
- [ ] Importer le rapport dans MaïJinn (`!import_rapport_minmai [JSON]`)
- [ ] Travailler les points identifiés avec MaïJinn
- [ ] Mettre à jour le profil et répéter

---

**Version :** 1.0
**Date :** Novembre 2025
**Compatibilité :** Min&Maï v13.0 + MaïJinn (PHENIX+ARSENAL+FORGE MÉMORIELLE)

---

*L'union de l'analyse stratégique (Min&Maï) et du développement personnel (MaïJinn) crée un écosystème complet de croissance pour les dirigeants.*
