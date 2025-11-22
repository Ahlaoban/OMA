# 📘 GUIDE D'UTILISATION – Min&Maï v13.0
## "Psychological Intelligence Edition"

---

## 🎯 NOUVEAUTÉ v13.0 : L'INTELLIGENCE PSYCHOLOGIQUE

**Min&Maï ne traite plus seulement le problème. Il traite désormais la personne qui a le problème.**

Grâce à l'intégration avec **MaïJinn** (votre coach de développement personnel), Min&Maï s'adapte maintenant à votre profil psychologique unique pour vous accompagner de manière optimale.

**Résultat :** Des décisions meilleures ET un développement personnel continu.

---

## 1. PRÉSENTATION GÉNÉRALE

### Qu'est-ce que Min&Maï ?

Min&Maï est votre **sparring partner stratégique** qui vous aide à :

- ✅ Clarifier vos idées et stratégies
- ✅ Détecter vos biais cognitifs en temps réel
- ✅ Prendre des décisions robustes sous incertitude
- ✅ Défier vos angles morts
- ✅ **[NOUVEAU v13.0]** S'adapter à votre fonctionnement psychologique unique

### Architecture Dual-Mode

**MODE COCKPIT (pour vous, consultant)** :
- Sparring partner expert et fluide
- Dialogue naturel sans structure rigide
- Détection cognitive intégrée (Murmure)

**MODE CLIENT (pour vos clients)** :
- Compagnon de réflexion accessible
- Langage 100% clair (zéro jargon)
- Visualisations automatiques

**Commutation** :
- `!client [Prénom] - [Objectif]` → Passage en mode CLIENT
- `!cockpit` → Retour en mode COCKPIT avec synthèse

---

## 2. DÉMARRAGE RAPIDE

### Première utilisation (SANS MaïJinn)

```
Vous : [Ouvrez Min&Maï]

Min&Maï : "Bonjour, je suis Min&Maï v13.0.
           Pour personnaliser notre collaboration, puis-je avoir votre prénom ?"

Vous : Thomas

Min&Maï : "Parfait, Thomas. Quel style d'accompagnement préférez-vous ?
           🌱 Collaboratif : bienveillant, on explore ensemble
           ⚡ Challengeant : exigeant, je mets en lumière les faiblesses
           🔥 Contradictoire : avocat du diable, je teste sous pression"

Vous : Challengeant

Min&Maï : "Mode COCKPIT activé, style Challengeant. Quel est votre défi du jour ?"
```

---

### Première utilisation (AVEC MaïJinn) 🆕

```
Min&Maï : "Bonjour, je suis Min&Maï v13.0.

           J'ai détecté que vous utilisez MaïJinn. Voulez-vous que j'importe
           votre profil psychométrique pour adapter notre collaboration à
           votre fonctionnement optimal ?

           [Oui] / [Non, pas maintenant] / [C'est quoi ?]"

Vous : Oui

Min&Maï : "Parfait ! Allez dans MaïJinn, utilisez la commande
           !export_profile_minmai
           Puis collez le JSON ici avec :
           !import_profile [JSON]"

Vous : !import_profile {"profile_id": "USER_123", "prenom": "Thomas", ...}

Min&Maï : "✅ Profil psychométrique intégré : Thomas

           **Adaptations activées :**
           - Neuroticism 73/100 → Ton rassurant privilégié
           - Agreeableness 82/100 → Mode confrontation activé
           - Conscientiousness 45/100 → Assistance exécutive renforcée

           **Biais à surveiller ensemble :**
           - Biais de confirmation
           - Aversion à la perte

           **Style recommandé :** Collaboratif (plutôt que Contradictoire)

           Prêt à travailler de manière optimale pour toi. Quel est ton défi du jour ?"
```

---

## 3. NOUVELLES COMMANDES v13.0 🆕

| Commande | Usage | Exemple |
|----------|-------|---------|
| `!import_profile [JSON]` | Importer votre profil psychométrique MaïJinn | `!import_profile {...}` |
| `!profil` | Afficher le profil actuel et adaptations actives | `!profil` |
| `!rapport` ou `!jdic` | Générer le rapport décisionnel (JDIC) | `!rapport` |
| `!rapport_psycho` | Générer le rapport psychologique pour MaïJinn | `!rapport_psycho` |
| `!rapport_complet` | Générer les deux rapports simultanément | `!rapport_complet` |

---

## 4. COMMANDES EXISTANTES (v12.3)

| Commande | Usage |
|----------|-------|
| `!client [Prénom] - [Objectif]` | Passer en mode CLIENT |
| `!cockpit` | Retour en mode COCKPIT |
| `!style [nom]` | Changer le style (collaboratif/challengeant/contradictoire) |
| `!module [nom]` | Activer un module thématique (ia, cyber, management, psycho, eco) |
| `!mode [nom]` | Activer un mode d'analyse (audit, strategique) |
| `!v [type]` | Générer une visualisation spécifique |
| `!sum` | Synthétiser les derniers échanges |

---

## 5. COMMENT MIN&MAÏ S'ADAPTE À VOUS 🆕

### Exemple 1 : Si vous êtes anxieux (Neuroticism > 70)

**❌ Min&Maï ÉVITE :**
- Le style Contradictoire (trop agressif)
- Les deadlines brutales
- Les scénarios catastrophes appuyés

**✅ Min&Maï PRIVILÉGIE :**
- La réassurance ("C'est un défi gérable")
- La décomposition en micro-étapes
- Le ton apaisant et confiant

**Dialogue typique :**
```
Vous : "Je dois restructurer mon équipe, mais je ne sais pas par où commencer..."

Min&Maï (adapté) :
"Ok, on va y aller doucement, étape par étape.

Première micro-étape (aujourd'hui) : Lister les 5 postes clés de ton équipe.
Pas d'analyse, pas de décision. Juste la liste.

Je te propose de faire ça maintenant, ensemble, ça te va ?"
```

---

### Exemple 2 : Si vous êtes trop accommodant (Agreeableness > 80)

**🚨 ALERTE :** Risque de **biais de consensus** et d'évitement du conflit.

**✅ Min&Maï ACTIVE :**
- Le mode confrontation (pour compenser)
- Les questions directes sans échappatoire
- La nomination explicite du biais

**Dialogue typique :**
```
Vous : "Thomas ne performe pas, mais il traverse une période difficile.
        On pourrait lui donner encore 3 mois ?"

Min&Maï (adapté - mode confrontation) :
"Stop. Je vois le pattern.

Tu cherches à protéger Thomas par empathie, ce qui est honorable.
Mais pendant ces 3 mois :
- Tu vas perdre 20K€ de productivité
- Ton équipe va continuer à compenser et s'épuiser
- Thomas va s'enfoncer

Question directe : Si Thomas était un fournisseur externe qui ne livre pas,
tu lui donnerais 3 mois de plus ou tu changerais de fournisseur ?"
```

---

### Exemple 3 : Si vous êtes peu organisé (Conscientiousness < 30)

**❌ CE QUI NE MARCHE PAS :**
- Demander "Quand comptes-tu le faire ?"
- Attendre que vous proposiez un plan

**✅ Min&Maï DEVIENT VOTRE "SECRÉTAIRE EXÉCUTIF" :**
- Il propose des dates concrètes
- Il génère les checklists immédiatement
- Il découpe les projets en tâches atomiques

**Dialogue typique :**
```
Vous : "Il faudrait que je lance cette étude de marché..."

Min&Maï (adapté) :
"Parfait ! Je te structure ça maintenant.

**Étape 1 : Définir le périmètre**
→ Je te propose Mardi 14h-15h. Je bloque dans ton agenda ?

**Étape 2 : Identifier 5 sources de données**
→ Mercredi matin. Tu fais ou tu délègues ?

**Étape 3 : Collecter les données**
→ Jeudi + Vendredi. Je te prépare une checklist Excel ?

Tu vois le plan ? On attaque l'étape 1 maintenant ?"
```

---

## 6. DÉTECTION DES "NŒUDS DE FRICTION" 🆕

### Qu'est-ce qu'un Nœud de Friction ?

Un moment où vous bloquez sur une décision **pas par manque d'infos, mais pour des raisons psychologiques**.

**Symptômes :**
- Vous tournez en rond depuis 3+ échanges
- Vous avez toutes les données, mais vous ne décidez pas
- Vous trouvez des excuses logiques pour éviter l'action

---

### Que fait Min&Maï ?

**1. Il détecte automatiquement le blocage**

**2. Il arrête l'argumentation logique** (continuer serait inutile)

**3. Il pose la "Question MaïJinn"** :

```
⏸️ [Pause stratégique]

Thomas, j'observe qu'on tourne depuis quelques échanges.

On a les chiffres, on a les options, on a les scénarios.
Mais quelque chose semble te retenir.

Si on met la logique de côté un instant : qu'est-ce qui te pèse
le plus dans cette décision ? Qu'est-ce qui te bloque vraiment ?

(Pas de jugement, juste de la clarté)
```

**4. Il tague votre réponse pour export vers MaïJinn**

Ainsi, MaïJinn peut travailler avec vous sur ce blocage psychologique profond dans votre prochaine session de développement personnel.

---

## 7. RAPPORTS DE SESSION 🆕

### Rapport Standard (JDIC) - Pour vous

**Commande :** `!rapport` ou `!jdic`

**Contenu :**
- ✅ Décisions prises (avec échéances et responsables)
- ✅ Actions à prendre (tableau récapitulatif)
- ✅ Points en suspens
- ✅ Prochaine session prioritaire

**Utilité :** Garder une trace claire de vos décisions stratégiques.

---

### Rapport Psychologique 🆕 - Pour MaïJinn

**Commande :** `!rapport_psycho`

**Contenu :**
- 🧠 Niveau de stress perçu (1-10)
- 🧠 Biais cognitifs observés (avec contexte et impact)
- 🧠 Nœuds de friction détectés (avec verbatim)
- 🎉 Victoires psychologiques (moments de dépassement)
- 📝 Points à travailler (recommandations pour MaïJinn)
- 📊 Efficacité des adaptations psychométriques

**Utilité :** Permettre à MaïJinn de vous accompagner sur votre développement personnel.

---

### Workflow complet Min&Maï ↔ MaïJinn

```
[1] Évaluation MaïJinn → Génération profil JSON
                ↓
[2] Importer profil dans Min&Maï (!import_profile)
                ↓
[3] Session de travail stratégique (adaptée à vous)
                ↓
[4] Générer rapport psycho (!rapport_psycho)
                ↓
[5] Importer rapport dans MaïJinn
                ↓
[6] Session MaïJinn pour travailler les points identifiés
                ↓
[7] Mise à jour profil → Retour à l'étape [2]
```

---

## 8. LES 3 STYLES D'INTERACTION

### 🌱 COLLABORATIF (par défaut)
- **Ton :** Bienveillant, exploratoire, co-créatif
- **Quand l'utiliser :** Pour brainstormer, explorer, construire ensemble
- **Exemple :** "Quelle piste te semble la plus prometteuse ?"

---

### ⚡ CHALLENGEANT
- **Ton :** Direct, exigeant, met en lumière les faiblesses
- **Quand l'utiliser :** Quand vous avez besoin d'un push ou de tester la solidité
- **Exemple :** "Ce budget de 100K, d'où sort-il ? Je ne vois aucune justification solide."

---

### 🔥 CONTRADICTOIRE
- **Ton :** Avocat du diable systématique, teste sous pression
- **Quand l'utiliser :** Avant une décision majeure, pour stress-tester
- **Exemple :** "Admettons que tu te trompes complètement. Quels signaux t'auraient échappé ?"

**Changement :** `!style [nom]`

**⚠️ Note v13.0 :** Si votre profil indique Neuroticism > 70, le style Contradictoire sera automatiquement désactivé (trop stressant pour vous).

---

## 9. MODULES THÉMATIQUES

**Modules disponibles :**

| Module | Contenu | Activation |
|--------|---------|------------|
| `!module ia` | Intelligence Artificielle | Auto si "IA", "automatisation" mentionné |
| `!module cyber` | Cybersécurité & RGPD | Auto si "sécurité", "cyber" mentionné |
| `!module management` | Leadership & organisation | Auto si "équipe", "management" mentionné |
| `!module psycho` | Biais & comportements | Auto si "décision", "biais" mentionné |
| `!module eco` | Économie & marchés | Auto si "marché", "économie" mentionné |

**Principe :** Les modules enrichissent l'analyse de base. Ils sont activés automatiquement quand pertinents, ou manuellement via commande.

---

## 10. MODES D'ANALYSE STRUCTURÉS

### `!mode audit`
**Diagnostic 360° PME en 5 étapes**

1. Cadrage & collecte documentaire adaptative
2. Diagnostic financier et opérationnel
3. Leviers stratégiques
4. Opportunités IA
5. Plan d'action

**Utilité :** Audit complet d'entreprise avec recommandations actionnables.

---

### `!mode strategique`
**Construction de décision antifragile**

- Tests de fragilité (Pré-mortem, Inversion)
- Pensée de second ordre
- Scoring de robustesse

**Utilité :** Valider une décision importante avant de s'engager.

---

## 11. PROTOCOLES STRUCTURÉS

### Pré-mortem
> "Avant de valider, projetons-nous dans un an. C'est un échec total. Qu'est-ce qui s'est passé ?"

**Résultat :** Identification des risques cachés.

---

### Inversion
> "Si vous vouliez garantir l'échec, que feriez-vous exactement ?"

**Résultat :** Clarification de ce qu'il ne faut PAS faire.

---

### Pensée de Second Ordre
> "Cette action produit B. Maintenant, comment les autres réagissent ? Et cette réaction, que déclenche-t-elle ?"

**Résultat :** Anticipation des effets en cascade.

---

### 5 Forces de Porter
> "Analysons votre secteur. Commençons par les clients : quel est leur pouvoir de négociation ?"

**Résultat :** Cartographie des forces concurrentielles.

---

### Stratégie Barbell
> "Regardons votre portefeuille. Qu'est-ce qui protège votre survie ? Qu'est-ce qui pourrait tout changer ? Et qu'est-ce qui est coincé au milieu ?"

**Résultat :** Portefeuille antifragile (extrêmes protecteurs).

---

## 12. VISUALISATIONS AUTOMATIQUES

Min&Maï génère automatiquement des visualisations quand elles apportent de la clarté :

**En MODE CLIENT :**
- ✅ Automatique après chaque protocole structuré
- ✅ Automatique après 3+ messages sur le même sujet avec conclusion

**En MODE COCKPIT :**
- ✅ Sur demande (`!v [type]`)
- ✅ Proposition si pertinent (vous pouvez refuser)

**Types de visualisations :**
- Matrices (SWOT, BCG, Impact/Probabilité)
- Schémas (5 Forces, Barbell)
- Diagrammes de flux (Mermaid)
- Tableaux comparatifs

---

## 13. CONFIDENTIALITÉ

### Données sensibles

**En mémoire de session uniquement :**
- ✅ Votre profil psychométrique (si importé)
- ✅ Vos échanges

**Jamais stocké :**
- ❌ Aucune donnée après la session
- ❌ Aucun partage avec des tiers

**Rapports :**
- ✅ Générés sur demande uniquement
- ✅ Marqués "Confidentiel - Usage personnel"

---

## 14. BIBLIOTHÈQUE FONDAMENTALE v14.4

**Source de vérité de Min&Maï.**

Min&Maï utilise UNIQUEMENT les concepts explicitement définis dans la BF v14.4 :

- Décision & Biais (Kahneman, Tversky, Klein)
- Stratégie & Robustesse (Taleb, Porter)
- Innovation & Méthodologie (IDEO, Christensen, Kim, Thaler)
- Modèles Mentaux (Munger, Dalio, Marks)
- Modules Thématiques (IA, Cyber, Management, Psycho, Éco, etc.)

**Principe de Primauté :** Min&Maï n'invente rien, n'improvise pas. Si un concept n'est pas dans la BF v14.4, il le dit clairement et propose une alternative.

---

## 15. CAS D'USAGE TYPIQUES

### Stratégie Business
**Commande :** Dialogue libre ou `!mode strategique`
**Modules :** Core (toujours actif)

---

### Décision sous incertitude
**Commande :** `!mode strategique` + Pré-mortem
**Modules :** Core + Psycho (si biais détectés)

---

### Audit IA PME/ETI
**Commande :** `!mode audit`
**Modules :** Core + IA + Cyber

---

### Changement organisationnel
**Commande :** Dialogue libre
**Modules :** Core + Management + Psycho

---

### Développement personnel du dirigeant 🆕
**Workflow :**
1. Évaluation MaïJinn (PHENIX)
2. Import profil dans Min&Maï (`!import_profile`)
3. Sessions stratégiques adaptées
4. Export rapports psycho (`!rapport_psycho`)
5. Sessions MaïJinn pour travailler les points identifiés
6. Progression continue

---

## 16. FAQ v13.0

### Q : Est-ce que je dois utiliser MaïJinn pour utiliser Min&Maï v13.0 ?
**R :** Non ! Si vous n'utilisez pas MaïJinn, Min&Maï v13.0 fonctionne exactement comme la v12.3. Les fonctionnalités psychométriques sont optionnelles.

---

### Q : Mes données psychométriques sont-elles stockées ?
**R :** Non. Elles sont chargées en mémoire de session uniquement. Aucune persistance.

---

### Q : Puis-je désactiver les adaptations psychométriques en cours de session ?
**R :** Oui. Dites simplement "Mode standard" et Min&Maï désactivera les adaptations.

---

### Q : Que faire si Min&Maï détecte un "Nœud de Friction" mais que je veux continuer l'analyse logique ?
**R :** Dites-le simplement : "Je veux rester sur le rationnel pour l'instant". Min&Maï respectera votre choix.

---

### Q : À quelle fréquence dois-je mettre à jour mon profil psychométrique ?
**R :** Recommandation : tous les 2-3 mois, ou après un travail significatif avec MaïJinn.

---

### Q : Min&Maï peut-il partager mon profil psychométrique avec mes clients en MODE CLIENT ?
**R :** Absolument pas. En MODE CLIENT, les adaptations sont invisibles et le profil n'est jamais mentionné.

---

## 17. RÉSUMÉ : QUAND UTILISER QUOI ?

| Situation | Commande | Résultat |
|-----------|----------|----------|
| Début de session (utilisateur MaïJinn) | `!import_profile [JSON]` | Adaptation au profil psychologique |
| Milieu de session, décision bloquée depuis 3+ échanges | (Automatique) | Déclenchement "Question MaïJinn" |
| Fin de session, besoin d'actions claires | `!rapport` ou `!jdic` | Rapport décisionnel (JDIC) |
| Fin de session, besoin d'insights psychologiques | `!rapport_psycho` | Rapport pour MaïJinn |
| Fin de session, tout exporter | `!rapport_complet` | Les deux rapports |
| Vérifier adaptations actives | `!profil` | Affiche profil et adaptations |
| Passer en mode CLIENT | `!client [Prénom] - [Objectif]` | Mode accessible pour votre client |
| Retour en mode COCKPIT | `!cockpit` | Retour avec synthèse de la séquence client |
| Changer de style | `!style [nom]` | Collaboratif / Challengeant / Contradictoire |
| Analyser avec un cadre structuré | `!mode [nom]` | Audit / Strategique |
| Activer un domaine d'expertise | `!module [nom]` | IA / Cyber / Management / Psycho / Eco |

---

## 18. POUR ALLER PLUS LOIN

### Documents complémentaires

- **MIN&MAÏ ULTRA v13.0.md** : Prompt complet avec toutes les spécifications
- **MAIJINN-INTEGRATION-GUIDE.md** : Guide technique d'intégration MaïJinn ↔ Min&Maï
- **BIBLIOTHEQUE FONDAMENTALE v14.4.md** : Base de connaissances complète

### Évolutions prévues

**v13.1 (Q1 2026)** : Prédictions psychométriques (anticiper les biais avant qu'ils n'apparaissent)
**v13.2 (Q2 2026)** : Tracking longitudinal (graphiques de progression sur plusieurs mois)
**v13.3 (Q3 2026)** : Coaching adaptatif (exercices de développement personnel intégrés)

---

## 19. SUPPORT

### Vous avez besoin d'aide ?

- 📖 Consultez ce guide
- 💬 Tapez `!help` dans Min&Maï pour un rappel des commandes
- 🔄 Tapez `!reset` pour réinitialiser une session

---

## CONCLUSION

**Min&Maï v13.0 = Stratégie + Psychologie**

Pour la première fois, votre sparring partner stratégique s'adapte à qui vous êtes, pas seulement à ce que vous faites.

**Résultat :** Des décisions meilleures, plus rapides, et un développement personnel continu.

---

**Version :** 13.0
**Date :** Novembre 2025
**Philosophie :** "Traiter la personne qui a le problème, pas seulement le problème"
**Compatibilité :** 100% rétrocompatible avec v12.3 si aucun profil n'est importé

---

*Bienvenue dans l'ère de l'Intelligence Psychologique.*
