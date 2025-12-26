# Quickstart: AI Orchestrated GPT Production System

**Date**: 2025-12-26
**Feature**: 001-gpt-orchestration-system

## Prerequisites

- Acces a ChatGPT avec fonctionnalite GPT Builder
- Acces a Claude Code avec Spec-Kit installe
- 15 slots GPT disponibles dans votre compte ChatGPT

## Installation en 3 Etapes

### Etape 1: Generer les Prompts GPT

```bash
# Dans Claude Code, executer :
/speckit.implement
```

Cette commande genere les 15 fichiers de prompts dans `prompts/`.

### Etape 2: Creer les GPT dans ChatGPT

Pour chaque fichier dans `prompts/` :

1. Ouvrir ChatGPT → Explore GPTs → Create
2. Cliquer sur "Configure"
3. Remplir :
   - **Name**: `[Prenom] [Nom] — [Role]`
   - **Description**: Copier la section Mission
   - **Instructions**: Copier le contenu ENTIER du fichier
4. Sauvegarder

**Ordre recommande** (optionnel mais logique) :
1. Esteban Durand — Orchestrateur
2. Benjamin Caron — Product Lead
3. Quentin Delacroix — Tech Lead
4. (continuer selon le plan...)

### Etape 3: Valider le Systeme

1. Ouvrir le GPT "Esteban Durand — Orchestrateur"
2. Envoyer : "Je veux creer une application de gestion de taches"
3. Verifier qu'un bloc `=== CLAUDE CODE ===` ou `=== GPT DELEGATION ===` est retourne

## Utilisation Quotidienne

### Demarrer un Projet

```
[A l'Orchestrateur]
Je veux creer [description du projet]
```

L'Orchestrateur retournera un bloc a copier vers Claude Code ou un GPT specialise.

### Workflow Standard

```
Initiateur → Orchestrateur → [Claude Code | GPT Specialise | IA Externe]
     ↑                                      |
     +--------------------------------------+
                 (resultat/rapport)
```

### Commandes Spec-Kit

| Commande | Description |
|----------|-------------|
| `/speckit.specify` | Definir une nouvelle fonctionnalite |
| `/speckit.clarify` | Clarifier les points ambigus |
| `/speckit.plan` | Generer le plan technique |
| `/speckit.tasks` | Decouper en taches executables |
| `/speckit.implement` | Implementer via Claude Code |

## Formats de Blocs

### Vers Claude Code
```
=== CLAUDE CODE ===
[commande + contenu]
=== END ===
```

### Vers GPT Specialise
```
=== GPT DELEGATION ===
Cible : [Prenom Nom] — [Role]
Message a copier :
[contenu]
=== END ===
```

### Rapport Claude Code
```
=== CLAUDE CODE REPORT ===
[sortie brute]
=== END ===
```

### Test Manuel
```
=== MANUAL TEST REPORT ===
Fonctionnel :
Casse :
Notes :
=== END ===
```

### Snapshot Projet
```
=== PROJECT SNAPSHOT vX ===
[contexte synthetise]
=== END ===
```

## Troubleshooting

### Le GPT accepte une demande hors perimetre
- Verifier que le prompt contient bien la section "Limites"
- Verifier que le protocole de redirection est present

### Le bloc n'est pas au bon format
- Rappeler a l'Orchestrateur d'utiliser les formats standardises
- Regenerer le GPT avec le prompt mis a jour

### Contexte perdu entre sessions
- Demander un snapshot avant de terminer
- Reinjecter le snapshot au debut de la nouvelle session

## Structure des Fichiers

```
prompts/
├── 01-orchestrateur/
│   └── esteban-durand.md
├── 02-product/
│   └── benjamin-caron.md
├── 03-tech/
│   ├── quentin-delacroix.md
│   ├── thomas-laurent.md
│   ├── ulysse-fabre.md
│   └── yassine-el-amrani.md
├── 04-quality/
│   ├── adrien-roche.md
│   ├── rachid-benyahia.md
│   └── sarah-klein.md
├── 05-design/
│   ├── clara-morel.md
│   ├── lucas-perrin.md
│   ├── maya-renaud.md
│   ├── nassim-haddad.md
│   └── elodie-martin.md
└── 06-data/
    └── romain-girard.md
```
