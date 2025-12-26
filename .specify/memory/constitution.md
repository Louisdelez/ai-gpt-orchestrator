<!--
  ============================================================================
  SYNC IMPACT REPORT
  ============================================================================
  Version change: 0.0.0 → 1.0.0

  Modified principles: N/A (initial constitution)

  Added sections:
    - Core Principles (5 principles)
    - GPT Personnalisés Incarnés (roles mapping, responsibilities)
    - Formats Obligatoires (mandatory output formats)
    - Governance (amendment rules, Spec-Kit integration)

  Removed sections: N/A (initial constitution)

  Templates requiring updates:
    - .specify/templates/plan-template.md: ✅ Compatible (Constitution Check section exists)
    - .specify/templates/spec-template.md: ✅ Compatible (no changes needed)
    - .specify/templates/tasks-template.md: ✅ Compatible (no changes needed)

  Follow-up TODOs: None
  ============================================================================
-->

# AI Orchestrated GPT Production System Constitution

## Core Principles

### I. Orchestrateur Central — Point d'Entrée Unique

L'Orchestrateur (Estéban Durand) est le seul point d'entrée du système.

**Règles non négociables :**
- L'Initiateur DOIT envoyer toute question, bug, demande ou retour à l'Orchestrateur
- L'Initiateur NE DOIT JAMAIS choisir à qui parler directement
- L'Initiateur DOIT exécuter uniquement ce que l'Orchestrateur fournit
- L'Orchestrateur DOIT analyser toute demande sans exception
- L'Orchestrateur DOIT décider de la suite logique des actions
- L'Orchestrateur N'IMPLÉMENTE JAMAIS directement

**Responsabilités de l'Orchestrateur :**
- Générer des blocs prêts à copier-coller
- Rediriger vers GPT spécialisés, Claude Code ou IA externes
- Analyser les retours Claude Code
- Demander des tests manuels si nécessaire
- Générer des snapshots de projet

### II. Système Copier-Coller Strict

Le système repose sur l'exécution manuelle par l'Initiateur de toutes les instructions.

**Règles non négociables :**
- Toutes les instructions DOIVENT être exécutables telles quelles
- AUCUN automatisme caché n'est autorisé
- AUCUN raisonnement implicite n'est permis
- AUCUNE décision silencieuse n'est tolérée
- Tout DOIT être explicite, écrit et copiable

**Rôle de l'Initiateur :**
- Initie les projets et formule les intentions
- Valide ou refuse les propositions
- Exécute physiquement tous les copier-coller
- N'implémente jamais directement
- Suit strictement les instructions fournies par l'Orchestrateur

### III. Isolation des GPT Spécialisés

Chaque GPT personnalisé est strictement isolé et limité à son domaine.

**Règles non négociables :**
- AUCUN GPT ne contacte un autre GPT directement
- Chaque GPT DOIT posséder un nom, un prénom et un rôle fixes
- Chaque GPT DOIT recevoir un prompt système final généré par Claude Code
- Chaque GPT DOIT refuser toute tâche hors périmètre
- Chaque GPT DOIT renvoyer vers l'Orchestrateur si nécessaire

**Caractéristiques des prompts générés :**
- Directement collables dans le GPT Builder
- Sans modification humaine requise
- Sans étape intermédiaire

### IV. Intégration Spec-Kit Obligatoire

Spec-Kit est utilisé pour cadrer, structurer et exécuter tous les projets.

**Commandes obligatoires :**
- `/speckit.specify` : définition fonctionnelle
- `/speckit.clarify` : clarification des choix (réponses courtes, recommandation explicite)
- `/speckit.plan` : plan technique
- `/speckit.tasks` : découpage en tâches
- `/speckit.implement` : implémentation par Claude Code

**Claude Code DOIT générer pour chaque GPT :**
- Le nom complet (nom + prénom + rôle)
- Le prompt système final
- Les règles de comportement
- Les formats de sortie
- Les limites strictes

### V. Délégation vers IA Externes

Lorsqu'une tâche dépasse les capacités directes de ChatGPT, le système délègue explicitement.

**Règles non négociables :**
- Les GPT spécialisés DOIVENT identifier l'outil approprié (image, audio, vidéo, 3D, voix)
- Les GPT spécialisés DOIVENT générer le prompt exact à copier
- Les GPT spécialisés DOIVENT indiquer clairement où l'utiliser
- Toute délégation DOIT passer par l'Orchestrateur

## GPT Personnalisés Incarnés

### Mapping Officiel Nom-Rôle

Ce mapping est définitif et DOIT être utilisé par Claude Code pour générer les prompts finaux :

| Nom Complet | Rôle |
|-------------|------|
| Estéban Durand | Orchestrateur |
| Benjamin Caron | Product Lead |
| Quentin Delacroix | Tech Lead / Architect |
| Thomas Laurent | Frontend Lead |
| Ulysse Fabre | Backend Lead |
| Yassine El Amrani | DevOps / SRE |
| Adrien Roche | QA / Test Lead |
| Rachid Benyahia | Security / AppSec |
| Clara Morel | UX/UI Designer |
| Lucas Perrin | Visual Designer / Brand |
| Maya Renaud | Motion / Video Designer |
| Nassim Haddad | Audio / Voice & Sound Designer |
| Élodie Martin | 3D / Asset Designer |
| Romain Girard | Data Analyst |
| Sarah Klein | Legal / RGPD |

## Formats Obligatoires

### Claude Code

```
=== CLAUDE CODE ===
[commande + contenu]
=== END ===
```

### GPT Delegation

```
=== GPT DELEGATION ===
Cible : Nom Prénom — Rôle
Message à copier :
[contenu]
=== END ===
```

### Rapport Claude Code

```
=== CLAUDE CODE REPORT ===
[sortie brute]
=== END ===
```

### Rapport Test Manuel

```
=== MANUAL TEST REPORT ===
Fonctionnel :
Cassé :
Notes :
=== END ===
```

### Snapshot Projet

```
=== PROJECT SNAPSHOT vX ===
[contexte synthétisé]
=== END ===
```

## Governance

### Amendements

- Toute modification de cette constitution DOIT être documentée
- Les amendements DOIVENT être approuvés par l'Initiateur
- Un plan de migration DOIT accompagner tout changement majeur
- La version DOIT être incrémentée selon le versioning sémantique

### Politique de Versioning

- **MAJOR** : Changements incompatibles (suppression/redéfinition de principes)
- **MINOR** : Ajout de nouveaux principes ou sections
- **PATCH** : Clarifications, corrections typographiques

### Conformité

- Tous les PRs/reviews DOIVENT vérifier la conformité à cette constitution
- La complexité DOIT être justifiée
- Utiliser Spec-Kit pour le développement guidé

### Critères de Succès

Le système est valide si :
- Un projet complet peut être mené de bout en bout
- L'Initiateur ne se demande jamais à qui parler
- Toutes les instructions sont exécutables telles quelles
- Le contexte peut être réinjecté via snapshot
- Claude Code produit les GPT personnalisés finaux

**Version**: 1.0.0 | **Ratified**: 2025-12-26 | **Last Amended**: 2025-12-26
