# Implementation Plan: Documentation & Onboarding

**Branch**: `002-docs-and-onboarding` | **Date**: 2025-12-26 | **Spec**: [spec.md](./spec.md)
**Input**: Feature specification from `/specs/002-docs-and-onboarding/spec.md`

## Summary

Produire une documentation complete et exploitable pour le AI Orchestrated GPT Production System, comprenant un README.md GitHub comme point d'entree synthetique et un dossier `docs/` avec 10 pages couvrant l'installation, l'architecture, les workflows quotidiens, et les bonnes pratiques. La documentation doit permettre a un nouvel utilisateur d'etre autonome en moins de 30 minutes.

## Technical Context

**Language/Version**: Markdown (GitHub Flavored Markdown)
**Primary Dependencies**: Mermaid (diagrammes), ASCII art (schemas simples)
**Storage**: Fichiers Markdown dans le repository Git
**Testing**: Validation manuelle (lecture, execution des exemples)
**Target Platform**: GitHub (rendu Markdown natif, support Mermaid)
**Project Type**: Documentation only (pas de code applicatif)
**Performance Goals**: README lisible en < 5 minutes
**Constraints**: 100% francais, pas de "Cloud Code", < 500 mots pour README
**Scale/Scope**: 12 fichiers Markdown (1 README + 11 docs)

## Constitution Check

*GATE: Must pass before Phase 0 research. Re-check after Phase 1 design.*

| Principe | Conformite | Notes |
|----------|------------|-------|
| I. Orchestrateur Central | ✅ PASS | Documentation explique le role d'Esteban Durand |
| II. Systeme Copier-Coller | ✅ PASS | Tous les exemples sont copiables |
| III. Isolation GPT | ✅ PASS | Documentation des 15 GPT avec perimetres |
| IV. Integration Spec-Kit | ✅ PASS | Workflows Spec-Kit documentes |
| V. Delegation IA Externes | ✅ PASS | Section dediee aux IA externes |

**Formats Obligatoires**: Tous documentes (CLAUDE CODE, GPT DELEGATION, CLAUDE CODE REPORT, MANUAL TEST REPORT, PROJECT SNAPSHOT)

**Vocabulaire Officiel**:
- Outil d'execution = **Claude Code**
- Outil de structuration = **Spec-Kit**
- Point d'entree unique = **Esteban Durand — Orchestrateur**
- Humain = **Initiateur**

## Project Structure

### Documentation (this feature)

```text
specs/002-docs-and-onboarding/
├── plan.md              # This file
├── research.md          # Phase 0 output
├── data-model.md        # Phase 1 output (structure docs)
├── quickstart.md        # Phase 1 output
└── tasks.md             # Phase 2 output (/speckit.tasks)
```

### Source Code (repository root)

```text
README.md                    # Point d'entree GitHub (< 500 mots)

docs/
├── README.md                # Index de la documentation
├── 00-overview.md           # Vision, problemes resolus, philosophie
├── 01-architecture.md       # Orchestrateur, GPT specialises, flux, regles
├── 02-installation.md       # Prerequis, Spec-Kit, Claude Code
├── 03-deploiement-gpt.md    # Comment creer les GPT dans ChatGPT
├── 04-workflows.md          # Workflows: projet, feature, bugfix
├── 05-media-ia-externe.md   # Image/Audio/Video/3D delegation
├── 06-snapshots.md          # Conservation et reinjection du contexte
├── 07-best-practices.md     # Regles d'or, anti-patterns
├── 08-faq.md                # Questions frequentes, erreurs courantes
└── 09-glossaire.md          # Termes officiels du systeme
```

**Structure Decision**: Documentation-only project. Tous les fichiers sont des Markdown GitHub-compatible avec schemas Mermaid integres.

## Complexity Tracking

Aucune violation de la constitution. Le projet est strictement documentaire et ne necessite pas de justification de complexite.

## Implementation Phases

### Phase 0 — Cadrage & Inventaire

**Objectif**: Lister et valider les inputs existants

**Artefacts existants a documenter**:
- `.specify/memory/constitution.md` — Regles du systeme
- `specs/001-gpt-orchestration-system/spec.md` — Specification initiale
- `specs/001-gpt-orchestration-system/quickstart.md` — Guide existant
- `prompts/01-orchestrateur/esteban-durand.md` — Orchestrateur
- `prompts/02-product/benjamin-caron.md` — Product Lead
- `prompts/03-tech/*.md` — 4 GPT Tech
- `prompts/04-quality/*.md` — 3 GPT Quality
- `prompts/05-design/*.md` — 5 GPT Design
- `prompts/06-data/romain-girard.md` — Data Analyst

**Invariants a extraire**:
1. Regles non negociables (5 principes)
2. Formats de blocs standardises (5 formats)
3. Mapping nom-role des 15 GPT
4. Workflow Initiateur → Orchestrateur → Execution

### Phase 1 — Architecture de la Documentation

**Objectif**: Creer la structure `docs/` et le README

**Contenu par fichier**:

| Fichier | Contenu Principal |
|---------|-------------------|
| README.md | Pitch, Quick Start (3 etapes), liens docs |
| docs/README.md | Table des matieres, navigation |
| 00-overview.md | Pourquoi ce systeme, problemes resolus |
| 01-architecture.md | Schema flux, 15 GPT, regles communication |
| 02-installation.md | Prerequis, installation pas a pas |
| 03-deploiement-gpt.md | GPT Builder, copier-coller prompts |
| 04-workflows.md | Projet, feature, bug, avec exemples |
| 05-media-ia-externe.md | DALL-E, Midjourney, ElevenLabs, etc. |
| 06-snapshots.md | Quand, comment, modele standard |
| 07-best-practices.md | Do/Don't, anti-patterns |
| 08-faq.md | 10+ questions avec solutions |
| 09-glossaire.md | Initiateur, Orchestrateur, Spec-Kit, etc. |

### Phase 2 — Redaction Complete

**Contraintes de redaction**:
- 100% francais
- Oriente "copier-coller" (exemples executables)
- Aucune mention de "Cloud Code"
- Chaque section mene a une action concrete

**Contenu obligatoire par theme**:

1. **Concept** (00-overview):
   - Pourquoi un Orchestrateur central
   - Problemes resolus (confusion, incoherence)

2. **Regles** (01-architecture):
   - Tout passe par l'Orchestrateur
   - Aucun GPT ne contacte un autre GPT
   - Copier-coller strict
   - Formats standardises

3. **Workflows** (04-workflows):
   - Demarrer un projet (specify → implement)
   - Ajouter une feature
   - Corriger un bug

4. **Deploiement GPT** (03-deploiement-gpt):
   - Ou coller le prompt systeme
   - Nom du GPT = "Prenom Nom — Role"
   - Test rapide de chaque GPT

5. **IA externes** (05-media-ia-externe):
   - GPT Design fournit prompt + outil
   - Exemples par type (image, audio, video, 3D)

6. **Snapshots** (06-snapshots):
   - Quand en faire
   - Modele standard
   - Reinjection dans nouveau chat

### Phase 3 — Validation

**Checklist qualite**:
- [ ] README lisible en < 5 minutes
- [ ] Documentation couvre 100% du flux
- [ ] Exemples prets a copier
- [ ] Aucune mention "Cloud Code"
- [ ] Vocabulaire stable (Initiateur/Orchestrateur/Claude Code)
- [ ] Formats de blocs conformes a la constitution

**Test "nouvel utilisateur"**:
1. Peut installer Spec-Kit
2. Comprend le role d'Esteban
3. Deploie 1 GPT via GPT Builder
4. Execute un workflow complet
5. Utilise un snapshot

### Phase 4 — Packaging GitHub

**Finalisation**:
- Table des matieres dans README
- Index dans docs/README.md
- Sections optionnelles (Contributing, License si publication)

## Dependencies

### Inputs Requis

| Source | Utilisation |
|--------|-------------|
| constitution.md | Regles, formats, vocabulaire |
| prompts/**/*.md | Liste des 15 GPT avec details |
| quickstart.md existant | Base pour docs/02-installation.md |

### Outputs Generes

| Fichier | Description |
|---------|-------------|
| README.md | Point d'entree GitHub |
| docs/*.md | 11 fichiers de documentation |

## Risks & Mitigations

| Risque | Impact | Mitigation |
|--------|--------|------------|
| Documentation trop longue | Abandon utilisateur | Limite stricte de mots, exemples concis |
| Incoherence vocabulaire | Confusion | Glossaire obligatoire, relecture |
| Exemples non executables | Frustration | Test manuel de chaque exemple |
| Oubli d'un GPT | Documentation incomplete | Checklist des 15 GPT |
