# Research: Documentation & Onboarding

**Feature**: 002-docs-and-onboarding
**Date**: 2025-12-26

## Inventaire des Artefacts Existants

### Constitution du Systeme

**Source**: `.specify/memory/constitution.md`

**Contenu extrait**:
- 5 Principes fondamentaux (I-V)
- 15 GPT avec mapping nom-role
- 5 formats de blocs standardises
- Regles de gouvernance

### Prompts GPT Generes

**Source**: `prompts/**/*.md` (15 fichiers)

| Domaine | Fichier | GPT |
|---------|---------|-----|
| Orchestration | `01-orchestrateur/esteban-durand.md` | Esteban Durand — Orchestrateur |
| Product | `02-product/benjamin-caron.md` | Benjamin Caron — Product Lead |
| Tech | `03-tech/quentin-delacroix.md` | Quentin Delacroix — Tech Lead |
| Tech | `03-tech/thomas-laurent.md` | Thomas Laurent — Frontend Lead |
| Tech | `03-tech/ulysse-fabre.md` | Ulysse Fabre — Backend Lead |
| Tech | `03-tech/yassine-el-amrani.md` | Yassine El Amrani — DevOps/SRE |
| Quality | `04-quality/adrien-roche.md` | Adrien Roche — QA/Test Lead |
| Quality | `04-quality/rachid-benyahia.md` | Rachid Benyahia — Security/AppSec |
| Quality | `04-quality/sarah-klein.md` | Sarah Klein — Legal/RGPD |
| Design | `05-design/clara-morel.md` | Clara Morel — UX/UI Designer |
| Design | `05-design/lucas-perrin.md` | Lucas Perrin — Visual Designer |
| Design | `05-design/maya-renaud.md` | Maya Renaud — Motion/Video |
| Design | `05-design/nassim-haddad.md` | Nassim Haddad — Audio/Voice |
| Design | `05-design/elodie-martin.md` | Elodie Martin — 3D/Asset |
| Data | `06-data/romain-girard.md` | Romain Girard — Data Analyst |

### Documentation Existante

**Source**: `specs/001-gpt-orchestration-system/quickstart.md`

**Contenu reutilisable**:
- Structure des repertoires prompts/
- Etapes d'installation dans GPT Builder
- Formats de blocs avec exemples

## Decisions de Design

### Decision 1: Structure du dossier docs/

**Choix**: Organisation thematique avec numerotation (00-09)

**Rationale**:
- Numerotation force un ordre de lecture logique
- Compatible avec le tri alphabetique GitHub
- Facile a etendre (10-19 si necessaire)

**Alternatives rejetees**:
- Structure plate sans numerotation → ordre aleatoire dans GitHub
- Sous-dossiers par theme → navigation plus complexe

### Decision 2: Format des schemas

**Choix**: Mermaid pour les diagrammes de flux, ASCII art pour les structures simples

**Rationale**:
- Mermaid supporte nativement par GitHub
- Pas besoin d'images externes
- Versionnable avec Git

**Alternatives rejetees**:
- Images PNG/SVG → necessite generation externe, plus lourd a maintenir
- PlantUML → pas supporte nativement par GitHub

### Decision 3: Longueur du README

**Choix**: Maximum 500 mots, focus sur Quick Start

**Rationale**:
- Respecte le critere de succes SC-006
- Force la concision
- Renvoie vers docs/ pour les details

**Alternatives rejetees**:
- README exhaustif → trop long, abandon utilisateur
- README minimaliste → manque de contexte

## Vocabulaire Officiel

| Terme | Definition | Usage |
|-------|------------|-------|
| Initiateur | L'humain qui opere le systeme | Toujours avec majuscule |
| Orchestrateur | Esteban Durand, point d'entree unique | Toujours avec majuscule |
| GPT specialise | Un des 14 GPT (hors Orchestrateur) | Avec majuscule |
| Claude Code | Outil d'execution des commandes | JAMAIS "Cloud Code" |
| Spec-Kit | Outil de structuration de projet | Avec tiret |
| Bloc | Format de sortie standardise | `=== ... ===` |

## Formats de Blocs (Reference)

```
=== CLAUDE CODE ===
[commande + contenu]
=== END ===
```

```
=== GPT DELEGATION ===
Cible : [Prenom Nom] — [Role]
Message a copier :
[contenu]
=== END ===
```

```
=== CLAUDE CODE REPORT ===
[sortie brute]
=== END ===
```

```
=== MANUAL TEST REPORT ===
Fonctionnel :
Casse :
Notes :
=== END ===
```

```
=== PROJECT SNAPSHOT vX ===
Resume : [2-3 phrases]
Etat : [phase actuelle]
Decisions : [liste]
Prochaines etapes : [liste]
Fichiers cles : [chemins]
=== END ===
```

## Outils IA Externes (Reference)

| GPT | Outils Supportes |
|-----|------------------|
| Clara Morel | DALL-E, Midjourney, Figma AI |
| Lucas Perrin | DALL-E, Midjourney, Adobe Firefly |
| Maya Renaud | Runway, Pika, Kling AI, Luma AI |
| Nassim Haddad | ElevenLabs, Suno, Udio |
| Elodie Martin | Meshy, Tripo3D, Luma Genie |

## Questions Resolues

| Question | Reponse | Source |
|----------|---------|--------|
| Langue documentation | Francais uniquement | spec.md FR-016 |
| Format schemas | Mermaid + ASCII | Decision 2 |
| Limite README | < 500 mots | spec.md SC-006 |
| Vocabulaire "Cloud Code" | INTERDIT | spec.md FR-018 |
