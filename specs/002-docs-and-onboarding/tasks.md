# Tasks: Documentation & Onboarding

**Input**: Design documents from `/specs/002-docs-and-onboarding/`
**Prerequisites**: plan.md (required), spec.md (required), research.md, data-model.md, quickstart.md

**Tests**: Non demandes - validation manuelle de la documentation.

**Organization**: Taches organisees par user story pour permettre une livraison incrementale de la documentation.

## Format: `[ID] [P?] [Story] Description`

- **[P]**: Peut s'executer en parallele (fichiers differents, pas de dependances)
- **[Story]**: User story concernee (US1, US2, US3, US4, US5)
- Chemins de fichiers exacts inclus dans les descriptions

## Path Conventions

- **Documentation racine**: `README.md`
- **Documentation complete**: `docs/*.md`

---

## Phase 1: Setup (Infrastructure Documentation)

**Purpose**: Creation de la structure de base pour la documentation

- [x] T001 Creer le dossier `docs/` a la racine du repository
- [x] T002 Extraire les invariants de `.specify/memory/constitution.md` (regles, formats, vocabulaire)
- [x] T003 Lister les 15 GPT depuis `prompts/**/*.md` avec leurs chemins et roles

**Checkpoint**: Structure prete, inventaire des sources complete

---

## Phase 2: Foundational (Index et Navigation)

**Purpose**: Creation de l'index de documentation - BLOQUE les autres phases

**CRITICAL**: L'index doit exister avant de creer les pages individuelles

- [x] T004 Creer `docs/README.md` avec table des matieres et liens vers toutes les pages
- [x] T005 Definir la navigation inter-pages (liens Precedent/Suivant)

**Checkpoint**: Index fonctionnel, navigation definie

---

## Phase 3: User Story 1 - Decouverte du Projet (Priority: P1)

**Goal**: Un nouvel utilisateur comprend le projet en moins de 5 minutes via le README

**Independent Test**: Faire lire le README a une personne externe et verifier qu'elle peut expliquer le concept

### Implementation for User Story 1

- [x] T006 [US1] Creer `README.md` avec pitch du projet (< 500 mots) a la racine
- [x] T007 [US1] Ajouter schema Mermaid du workflow principal dans `README.md`
- [x] T008 [US1] Ajouter section "Quick Start" (3 etapes max) dans `README.md`
- [x] T009 [US1] Ajouter liste des prerequis techniques dans `README.md`
- [x] T010 [US1] Ajouter liens vers `docs/` dans `README.md`
- [x] T011 [P] [US1] Creer `docs/00-overview.md` avec vision et philosophie du systeme
- [x] T012 [US1] Documenter les problemes resolus par le systeme dans `docs/00-overview.md`

**Checkpoint**: README complet et lisible en < 5 minutes

---

## Phase 4: User Story 2 - Installation du Systeme (Priority: P1)

**Goal**: Un utilisateur peut installer et configurer le systeme en < 30 minutes

**Independent Test**: Suivre le guide depuis zero et verifier que le systeme fonctionne

### Implementation for User Story 2

- [x] T013 [P] [US2] Creer `docs/02-installation.md` avec prerequis detailles
- [x] T014 [US2] Documenter l'installation de Claude Code dans `docs/02-installation.md`
- [x] T015 [US2] Documenter l'installation de Spec-Kit dans `docs/02-installation.md`
- [x] T016 [US2] Ajouter checklist de verification post-installation dans `docs/02-installation.md`
- [x] T017 [P] [US2] Creer `docs/03-deploiement-gpt.md` pour le deploiement GPT Builder
- [x] T018 [US2] Documenter le processus de creation d'un GPT dans ChatGPT
- [x] T019 [US2] Documenter le nommage des GPT ("Prenom Nom — Role")
- [x] T020 [US2] Ajouter guide de test rapide d'un GPT deploye

**Checkpoint**: Un utilisateur peut installer le systeme sans assistance

---

## Phase 5: User Story 3 - Comprehension de l'Architecture (Priority: P2)

**Goal**: L'utilisateur comprend les roles, regles et interactions du systeme

**Independent Test**: L'utilisateur peut dessiner le flux de travail apres lecture

### Implementation for User Story 3

- [x] T021 [P] [US3] Creer `docs/01-architecture.md` avec vue d'ensemble
- [x] T022 [US3] Documenter le role de l'Orchestrateur (Esteban Durand) dans `docs/01-architecture.md`
- [x] T023 [US3] Ajouter tableau des 15 GPT avec nom, role et perimetre dans `docs/01-architecture.md`
- [x] T024 [US3] Documenter les regles de communication (pas de GPT-to-GPT) dans `docs/01-architecture.md`
- [x] T025 [US3] Ajouter schema Mermaid du flux Initiateur → Orchestrateur → GPT/Claude Code
- [x] T026 [US3] Documenter les 5 formats de blocs standardises dans `docs/01-architecture.md`

**Checkpoint**: Architecture complete et comprehensible

---

## Phase 6: User Story 4 - Utilisation Quotidienne (Priority: P2)

**Goal**: L'utilisateur maitrise les workflows : projet, feature, bug, medias, snapshots

**Independent Test**: Suivre un workflow et obtenir un resultat conforme

### Implementation for User Story 4

**Workflows Spec-Kit**:
- [x] T027 [P] [US4] Creer `docs/04-workflows.md` avec introduction aux workflows
- [x] T028 [US4] Documenter workflow "Nouveau projet" (specify → implement) dans `docs/04-workflows.md`
- [x] T029 [US4] Documenter workflow "Nouvelle feature" dans `docs/04-workflows.md`
- [x] T030 [US4] Documenter workflow "Correction de bug" dans `docs/04-workflows.md`
- [x] T031 [US4] Ajouter exemples concrets copiables pour chaque workflow

**IA Externes**:
- [x] T032 [P] [US4] Creer `docs/05-media-ia-externe.md` avec introduction
- [x] T033 [US4] Documenter generation d'images (DALL-E, Midjourney) dans `docs/05-media-ia-externe.md`
- [x] T034 [US4] Documenter generation audio (ElevenLabs, Suno) dans `docs/05-media-ia-externe.md`
- [x] T035 [US4] Documenter generation video (Runway, Pika) dans `docs/05-media-ia-externe.md`
- [x] T036 [US4] Documenter generation 3D (Meshy, Tripo) dans `docs/05-media-ia-externe.md`

**Snapshots**:
- [x] T037 [P] [US4] Creer `docs/06-snapshots.md` avec introduction
- [x] T038 [US4] Definir le modele standard de snapshot dans `docs/06-snapshots.md`
- [x] T039 [US4] Expliquer quand et pourquoi faire un snapshot
- [x] T040 [US4] Documenter la reinjection du snapshot dans un nouveau chat

**Checkpoint**: Tous les workflows documentes avec exemples

---

## Phase 7: User Story 5 - Eviter les Erreurs Courantes (Priority: P3)

**Goal**: L'utilisateur connait les bonnes pratiques et peut resoudre les problemes courants

**Independent Test**: Chaque erreur listee a une solution claire

### Implementation for User Story 5

**Bonnes pratiques**:
- [x] T041 [P] [US5] Creer `docs/07-best-practices.md` avec introduction
- [x] T042 [US5] Lister les "Do" (bonnes pratiques) dans `docs/07-best-practices.md`
- [x] T043 [US5] Lister les "Don't" (anti-patterns) dans `docs/07-best-practices.md`
- [x] T044 [US5] Documenter la gestion des chats longs et performance

**FAQ**:
- [x] T045 [P] [US5] Creer `docs/08-faq.md` avec structure Q&A
- [x] T046 [US5] Ajouter 10+ questions frequentes avec reponses dans `docs/08-faq.md`
- [x] T047 [US5] Documenter les erreurs courantes et leurs solutions

**Glossaire**:
- [x] T048 [P] [US5] Creer `docs/09-glossaire.md` avec termes officiels
- [x] T049 [US5] Definir tous les termes cles (Initiateur, Orchestrateur, Claude Code, Spec-Kit, etc.)

**Checkpoint**: Documentation de support complete

---

## Phase 8: Polish & Validation Finale

**Purpose**: Verification globale et preparation pour publication GitHub

- [x] T050 [P] Verifier coherence globale de toute la documentation
- [x] T051 [P] Verifier conformite avec la constitution (vocabulaire, formats)
- [x] T052 Verifier absence totale de "Cloud Code" : `grep -ri "cloud code" README.md docs/`
- [x] T053 [P] Verifier rendu Markdown GitHub (liens, tableaux, Mermaid)
- [x] T054 Verifier que le README fait < 500 mots : `wc -w README.md`
- [x] T055 Ajouter navigation inter-pages dans chaque fichier docs/
- [x] T056 Mettre a jour `docs/README.md` avec liens finaux
- [x] T057 Generer rapport de validation dans `specs/002-docs-and-onboarding/validation-report.md`

---

## Dependencies & Execution Order

### Phase Dependencies

- **Setup (Phase 1)**: Aucune dependance - peut demarrer immediatement
- **Foundational (Phase 2)**: Depend de Setup - BLOQUE les user stories
- **User Story 1 (Phase 3)**: Depend de Foundational - README prioritaire
- **User Story 2 (Phase 4)**: Depend de Foundational - Peut demarrer avec US1
- **User Story 3 (Phase 5)**: Depend de Foundational - Architecture
- **User Story 4 (Phase 6)**: Depend de US3 (architecture comprise d'abord)
- **User Story 5 (Phase 7)**: Depend de US4 (workflows documentes d'abord)
- **Polish (Phase 8)**: Depend de toutes les user stories

### User Story Dependencies

- **User Story 1 (P1)**: Peut demarrer apres Foundational - README independant
- **User Story 2 (P1)**: Peut demarrer apres Foundational - Installation independante
- **User Story 3 (P2)**: Peut demarrer apres Foundational - Architecture independante
- **User Story 4 (P2)**: Recommande apres US3 (comprehension architecture)
- **User Story 5 (P3)**: Recommande apres US4 (erreurs liees aux workflows)

### Within Each User Story

- Fichiers marques [P] peuvent s'executer en parallele
- Creation du fichier principal avant ses sous-sections
- Exemples concrets obligatoires pour chaque workflow

### Parallel Opportunities

- T011 (overview) et T013 (installation) peuvent s'executer en parallele
- T021 (architecture), T027 (workflows), T032 (media), T037 (snapshots) en parallele
- T041, T045, T048 (best practices, FAQ, glossaire) en parallele
- T050, T051, T053 (validations) en parallele

---

## Parallel Example: Phase 6 (User Story 4)

```bash
# Lancer la creation des fichiers de base en parallele:
Task: "Creer docs/04-workflows.md"
Task: "Creer docs/05-media-ia-externe.md"
Task: "Creer docs/06-snapshots.md"

# Puis remplir sequentiellement chaque fichier
```

---

## Implementation Strategy

### MVP First (User Stories 1 + 2)

1. Completer Phase 1: Setup
2. Completer Phase 2: Foundational (index)
3. Completer Phase 3: User Story 1 (README)
4. Completer Phase 4: User Story 2 (Installation)
5. **STOP et VALIDER**: Le systeme peut etre utilise avec juste README + Installation
6. Publier si pret (MVP documentation)

### Incremental Delivery

1. Setup + Foundational → Structure prete
2. Ajouter US1 (README) → Point d'entree fonctionnel
3. Ajouter US2 (Installation) → Utilisateurs peuvent demarrer
4. Ajouter US3 (Architecture) → Comprehension approfondie
5. Ajouter US4 (Workflows) → Usage quotidien
6. Ajouter US5 (FAQ) → Support autonome

### Batch Execution (Recommande)

Etant donne que toute la documentation doit etre coherente:
1. Phase 1 + Phase 2 (setup et index)
2. Phases 3-7 en sequence rapide (toutes les user stories)
3. Phase 8 (validation finale)

---

## Notes

- [P] tasks = fichiers differents, pas de dependances
- [Story] label mappe la tache a une user story specifique
- Chaque fichier docs/ doit inclure navigation vers precedent/suivant
- Tous les exemples doivent etre copiables directement
- Limite de 500 mots pour le README
- Aucune mention de "Cloud Code" autorisee
- Langue: francais uniquement

---

## Phase 9: Correction Contrat de Sortie (Post-Implementation)

**Purpose**: Garantir que les outputs GPT activent le bouton "Copier le code" dans ChatGPT

**Contexte**: Les blocs `=== GPT DELEGATION ===` n'activaient pas le bouton "Copier" car ils n'etaient pas dans des fenced code blocks Markdown.

- [x] T058 Ajouter section "Contrat de Sortie Obligatoire" dans les 15 prompts
- [x] T059 Encapsuler tous les delimiteurs `=== ... ===` dans des blocs ```text
- [x] T060 Standardiser la cloture en `=== END ===`
- [x] T061 Valider: 0 occurrence de blocs hors fenced code blocks
- [x] T062 Mettre a jour `validation-report.md` avec section correction

**Checkpoint**: Tous les outputs GPT sont copiables en un clic

**Fichiers modifies**: 15 prompts dans `prompts/**/*.md`
