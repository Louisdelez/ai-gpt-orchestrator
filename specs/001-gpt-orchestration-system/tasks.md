# Tasks: AI Orchestrated GPT Production System

**Input**: Design documents from `/specs/001-gpt-orchestration-system/`
**Prerequisites**: plan.md (required), spec.md (required), data-model.md, contracts/gpt-prompt-schema.md

**Tests**: Non demandes dans la specification - validation manuelle via GPT Builder.

**Organization**: Taches organisees par user story pour permettre une implementation et des tests independants.

## Format: `[ID] [P?] [Story] Description`

- **[P]**: Peut s'executer en parallele (fichiers differents, pas de dependances)
- **[Story]**: User story concernee (US1, US2, US3, US4, US5)
- Chemins de fichiers exacts inclus dans les descriptions

## Path Conventions

- **Prompts GPT**: `prompts/[domaine]/[prenom-nom].md`
- **Documentation**: `specs/001-gpt-orchestration-system/`

---

## Phase 1: Setup (Infrastructure de base)

**Purpose**: Initialisation du projet et creation de la structure de repertoires

- [x] T001 Creer la structure de repertoires `prompts/` selon plan.md
- [x] T002 [P] Creer le repertoire `prompts/01-orchestrateur/`
- [x] T003 [P] Creer le repertoire `prompts/02-product/`
- [x] T004 [P] Creer le repertoire `prompts/03-tech/`
- [x] T005 [P] Creer le repertoire `prompts/04-quality/`
- [x] T006 [P] Creer le repertoire `prompts/05-design/`
- [x] T007 [P] Creer le repertoire `prompts/06-data/`

**Checkpoint**: Structure de repertoires prete pour la generation des prompts

---

## Phase 2: Foundational (Prerequisites bloquants)

**Purpose**: Verification des prerequis avant generation

**CRITICAL**: Aucune generation de prompt ne peut commencer avant cette phase

- [x] T008 Verifier la presence et validite de `.specify/memory/constitution.md` (5 principes, mapping, formats)
- [x] T009 Verifier la presence et validite de `specs/001-gpt-orchestration-system/spec.md` (US P1-P5, FR, SC)
- [x] T010 Charger le schema de prompt depuis `specs/001-gpt-orchestration-system/contracts/gpt-prompt-schema.md`
- [x] T011 Construire le mapping identitaire des 15 GPT en memoire depuis `specs/001-gpt-orchestration-system/data-model.md`

**Checkpoint**: Tous les prerequis valides - generation des prompts autorisee

---

## Phase 3: User Story 1 - Initiation de projet (Priority: P1)

**Goal**: L'Orchestrateur peut recevoir une demande de projet et retourner un bloc CLAUDE CODE ou GPT DELEGATION

**Independent Test**: Soumettre "Je veux creer une app de gestion de taches" a l'Orchestrateur et verifier qu'un bloc `=== CLAUDE CODE ===` avec `/speckit.specify` est retourne

### Implementation for User Story 1

- [x] T012 [US1] Generer le prompt GPT pour Esteban Durand (Orchestrateur) dans `prompts/01-orchestrateur/esteban-durand.md`

**Contenu requis pour T012**:
- Identite complete (Esteban Durand, Orchestrateur)
- Mission centrale (analyser, decider, rediriger)
- Responsabilites (6 items selon schema)
- Regles non negociables (5 items: pas d'implementation, pas de decision implicite, formats standard, redirection, analyse)
- Formats de sortie (CLAUDE CODE, GPT DELEGATION, PROJECT SNAPSHOT)
- Limites (5 items)
- Protocole de redirection special (point d'entree unique)

**Checkpoint**: L'Orchestrateur est fonctionnel et peut initier des projets

---

## Phase 4: User Story 2 - Delegation vers GPT specialise (Priority: P2)

**Goal**: L'Orchestrateur peut deleguer vers les 14 GPT specialises qui refusent les demandes hors perimetre

**Independent Test**: Demander un "design UX" a l'Orchestrateur et verifier qu'un bloc `=== GPT DELEGATION ===` ciblant Clara Morel est retourne

### Implementation for User Story 2

**Domaine Product**:
- [x] T013 [P] [US2] Generer le prompt GPT pour Benjamin Caron (Product Lead) dans `prompts/02-product/benjamin-caron.md`

**Domaine Tech**:
- [x] T014 [P] [US2] Generer le prompt GPT pour Quentin Delacroix (Tech Lead / Architect) dans `prompts/03-tech/quentin-delacroix.md`
- [x] T015 [P] [US2] Generer le prompt GPT pour Thomas Laurent (Frontend Lead) dans `prompts/03-tech/thomas-laurent.md`
- [x] T016 [P] [US2] Generer le prompt GPT pour Ulysse Fabre (Backend Lead) dans `prompts/03-tech/ulysse-fabre.md`
- [x] T017 [P] [US2] Generer le prompt GPT pour Yassine El Amrani (DevOps / SRE) dans `prompts/03-tech/yassine-el-amrani.md`

**Domaine Quality**:
- [x] T018 [P] [US2] Generer le prompt GPT pour Adrien Roche (QA / Test Lead) dans `prompts/04-quality/adrien-roche.md`
- [x] T019 [P] [US2] Generer le prompt GPT pour Rachid Benyahia (Security / AppSec) dans `prompts/04-quality/rachid-benyahia.md`
- [x] T020 [P] [US2] Generer le prompt GPT pour Sarah Klein (Legal / RGPD) dans `prompts/04-quality/sarah-klein.md`

**Domaine Data**:
- [x] T021 [P] [US2] Generer le prompt GPT pour Romain Girard (Data Analyst) dans `prompts/06-data/romain-girard.md`

**Checkpoint**: 9 GPT specialises (Product, Tech, Quality, Data) sont fonctionnels

---

## Phase 5: User Story 3 - Generation de prompt GPT final (Priority: P3)

**Goal**: Tous les 15 prompts sont generes et directement collables dans le GPT Builder

**Independent Test**: Copier le prompt de Benjamin Caron dans le GPT Builder et verifier que le GPT est cree sans erreur

**Note**: Cette phase est automatiquement completee par les phases precedentes car tous les prompts sont generes. La validation se fait en verifiant que chaque fichier respecte le schema.

### Implementation for User Story 3

- [x] T022 [US3] Valider que tous les prompts generes respectent le schema (7 sections, <6000 chars, francais)
- [x] T023 [US3] Verifier l'absence de references directes entre GPT dans les prompts

**Checkpoint**: Tous les prompts sont valides et prets pour le GPT Builder

---

## Phase 6: User Story 4 - Integration IA externe (Priority: P4)

**Goal**: Les GPT Design/Media peuvent generer des prompts pour DALL-E, Midjourney, ElevenLabs, etc.

**Independent Test**: Demander un "logo minimaliste" a Lucas Perrin et verifier qu'un bloc `=== IA EXTERNE ===` avec un prompt DALL-E/Midjourney est retourne

### Implementation for User Story 4

**Domaine Design/Media**:
- [x] T024 [P] [US4] Generer le prompt GPT pour Clara Morel (UX/UI Designer) dans `prompts/05-design/clara-morel.md`
- [x] T025 [P] [US4] Generer le prompt GPT pour Lucas Perrin (Visual Designer / Brand) dans `prompts/05-design/lucas-perrin.md`
- [x] T026 [P] [US4] Generer le prompt GPT pour Maya Renaud (Motion / Video Designer) dans `prompts/05-design/maya-renaud.md`
- [x] T027 [P] [US4] Generer le prompt GPT pour Nassim Haddad (Audio / Voice & Sound Designer) dans `prompts/05-design/nassim-haddad.md`
- [x] T028 [P] [US4] Generer le prompt GPT pour Elodie Martin (3D / Asset Designer) dans `prompts/05-design/elodie-martin.md`

**Contenu specifique pour T024-T028**:
- Inclure le format `=== IA EXTERNE ===` dans les formats de sortie
- Specifier les outils IA supportes par role (DALL-E, Midjourney, ElevenLabs, Suno, Runway, Blender)
- Inclure des exemples de prompts IA dans les responsabilites

**Checkpoint**: 5 GPT Design/Media sont fonctionnels avec delegation IA externe

---

## Phase 7: User Story 5 - Gestion des snapshots (Priority: P5)

**Goal**: L'Orchestrateur peut generer et recharger des snapshots projet

**Independent Test**: Demander un "snapshot du projet actuel" a l'Orchestrateur et verifier qu'un bloc `=== PROJECT SNAPSHOT v1 ===` est retourne avec le contexte synthetise

### Implementation for User Story 5

- [x] T029 [US5] Verifier que le prompt de l'Orchestrateur inclut la gestion des snapshots (format, structure, reinjectabilite)
- [x] T030 [US5] Documenter le processus de snapshot dans `specs/001-gpt-orchestration-system/quickstart.md`

**Checkpoint**: Les snapshots sont fonctionnels pour sauvegarde et reprise de contexte

---

## Phase 8: Polish & Validation Finale

**Purpose**: Verification globale et compilation des livrables

- [x] T031 [P] Verifier que les 15 fichiers de prompts existent et sont non-vides
- [x] T032 [P] Verifier que tous les prompts sont en francais (aucun texte anglais)
- [x] T033 [P] Verifier que chaque prompt inclut le protocole de redirection vers l'Orchestrateur
- [x] T034 Generer un rapport de fin listant les 15 GPT generes dans `specs/001-gpt-orchestration-system/validation-report.md`
- [x] T035 Valider le quickstart.md avec les chemins corrects des prompts

---

## Dependencies & Execution Order

### Phase Dependencies

- **Setup (Phase 1)**: Aucune dependance - peut demarrer immediatement
- **Foundational (Phase 2)**: Depend de Setup - BLOQUE toutes les user stories
- **User Story 1 (Phase 3)**: Depend de Foundational - Orchestrateur requis en premier
- **User Story 2 (Phase 4)**: Depend de US1 (l'Orchestrateur delegue vers ces GPT)
- **User Story 3 (Phase 5)**: Depend de US1 + US2 (validation de tous les prompts existants)
- **User Story 4 (Phase 6)**: Peut demarrer apres Foundational (independant de US2/US3)
- **User Story 5 (Phase 7)**: Depend de US1 (snapshot est une fonctionnalite de l'Orchestrateur)
- **Polish (Phase 8)**: Depend de toutes les user stories

### User Story Dependencies

- **User Story 1 (P1)**: Peut demarrer apres Foundational - Aucune dependance sur d'autres stories
- **User Story 2 (P2)**: Depend de US1 (l'Orchestrateur doit exister pour deleguer)
- **User Story 3 (P3)**: Depend de US1 + US2 (validation de prompts existants)
- **User Story 4 (P4)**: Peut demarrer apres Foundational - Independant de US2
- **User Story 5 (P5)**: Depend de US1 (fonctionnalite de l'Orchestrateur)

### Within Each User Story

- T012 (Orchestrateur) DOIT etre complete avant T013-T021 (GPT specialises utilisent le meme schema)
- Les taches [P] au sein d'une phase peuvent s'executer en parallele
- Validation apres chaque checkpoint avant de passer a la phase suivante

### Parallel Opportunities

- T002-T007 (creation des repertoires) peuvent s'executer en parallele
- T013-T021 (GPT Product, Tech, Quality, Data) peuvent s'executer en parallele
- T024-T028 (GPT Design/Media) peuvent s'executer en parallele
- T031-T033 (validations finales) peuvent s'executer en parallele

---

## Parallel Example: Phase 4 (User Story 2)

```bash
# Lancer tous les GPT specialises en parallele:
Task: "Generer prompt Benjamin Caron dans prompts/02-product/benjamin-caron.md"
Task: "Generer prompt Quentin Delacroix dans prompts/03-tech/quentin-delacroix.md"
Task: "Generer prompt Thomas Laurent dans prompts/03-tech/thomas-laurent.md"
Task: "Generer prompt Ulysse Fabre dans prompts/03-tech/ulysse-fabre.md"
Task: "Generer prompt Yassine El Amrani dans prompts/03-tech/yassine-el-amrani.md"
Task: "Generer prompt Adrien Roche dans prompts/04-quality/adrien-roche.md"
Task: "Generer prompt Rachid Benyahia dans prompts/04-quality/rachid-benyahia.md"
Task: "Generer prompt Sarah Klein dans prompts/04-quality/sarah-klein.md"
Task: "Generer prompt Romain Girard dans prompts/06-data/romain-girard.md"
```

---

## Implementation Strategy

### MVP First (User Story 1 Only)

1. Completer Phase 1: Setup
2. Completer Phase 2: Foundational (CRITICAL)
3. Completer Phase 3: User Story 1 (Orchestrateur)
4. **STOP et VALIDER**: Tester l'Orchestrateur dans le GPT Builder
5. Deployer/demo si pret

### Incremental Delivery

1. Setup + Foundational → Infrastructure prete
2. Ajouter US1 → Tester independamment → L'Orchestrateur fonctionne (MVP!)
3. Ajouter US2 → Tester independamment → Delegation fonctionne
4. Ajouter US4 → Tester independamment → IA externes fonctionnent
5. Ajouter US3 + US5 → Validation complete → Systeme operationnel

### Batch Execution (Recommande)

Etant donne que la strategie est "batch complet", executer:
1. Phase 1 + Phase 2 (prerequis)
2. Toutes les phases 3-7 en sequence rapide
3. Phase 8 (validation finale)

---

## Notes

- [P] tasks = fichiers differents, pas de dependances
- [Story] label mappe la tache a une user story specifique
- Chaque user story est independamment completable et testable
- Valider via GPT Builder apres chaque checkpoint
- Commit apres chaque tache ou groupe logique
- Limite de 6000 caracteres par prompt (marge sur 8000)
- Langue: francais uniquement
