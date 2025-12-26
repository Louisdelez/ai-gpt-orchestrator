# Feature Specification: AI Orchestrated GPT Production System

**Feature Branch**: `001-gpt-orchestration-system`
**Created**: 2025-12-26
**Status**: Draft
**Input**: User description: "Systeme de production assiste par IA avec GPT personnalises incarnes, orchestres par un GPT central, operes via copier-coller strict"

## Clarifications

### Session 2025-12-26

- Q: Langue des prompts GPT generes? → A: Francais uniquement
- Q: Strategie de generation des 15 GPT? → A: Batch complet (tous les prompts en une seule operation)

## User Scenarios & Testing *(mandatory)*

### User Story 1 - Initiation d'un nouveau projet (Priority: P1)

L'Initiateur souhaite demarrer un nouveau projet complexe (SaaS, application, jeu ou media). Il envoie sa demande a l'Orchestrateur Esteban Durand, qui analyse la demande et fournit un bloc pret a copier-coller pour lancer le workflow Spec-Kit.

**Why this priority**: C'est le point d'entree fondamental du systeme. Sans cette capacite, aucun projet ne peut demarrer. L'Initiateur doit pouvoir exprimer une intention et recevoir des instructions claires et executables.

**Independent Test**: Peut etre teste en soumettant une intention de projet a l'Orchestrateur et en verifiant qu'un bloc copier-coller valide est retourne avec la commande Spec-Kit appropriee.

**Acceptance Scenarios**:

1. **Given** l'Initiateur a une idee de projet, **When** il envoie sa demande a l'Orchestrateur, **Then** l'Orchestrateur retourne un bloc `=== CLAUDE CODE ===` avec la commande `/speckit.specify` et le contenu du projet
2. **Given** l'Orchestrateur a analyse la demande, **When** il determine qu'une clarification est necessaire, **Then** il retourne un bloc `=== CLAUDE CODE ===` avec `/speckit.clarify` et les questions appropriees
3. **Given** l'Initiateur copie le bloc dans Claude Code, **When** il execute la commande, **Then** un document de specification est genere sans erreur

---

### User Story 2 - Delegation vers un GPT specialise (Priority: P2)

L'Initiateur a besoin d'une expertise specifique (design UX, architecture technique, securite, etc.). L'Orchestrateur analyse la demande et fournit un bloc de delegation vers le GPT specialise approprie avec un message pret a copier.

**Why this priority**: La delegation est le mecanisme central qui permet au systeme de produire des livrables specialises. Sans cette capacite, l'Orchestrateur serait limite a son propre domaine.

**Independent Test**: Peut etre teste en soumettant une demande technique a l'Orchestrateur et en verifiant qu'un bloc de delegation valide est genere vers le bon GPT specialise.

**Acceptance Scenarios**:

1. **Given** l'Initiateur demande un design UX, **When** il soumet la demande a l'Orchestrateur, **Then** il recoit un bloc `=== GPT DELEGATION ===` ciblant Clara Morel - UX/UI Designer
2. **Given** l'Initiateur demande une validation d'architecture, **When** il soumet la demande, **Then** il recoit un bloc de delegation ciblant Quentin Delacroix - Tech Lead / Architect
3. **Given** le GPT specialise recoit une demande hors perimetre, **When** il analyse la demande, **Then** il refuse et renvoie vers l'Orchestrateur

---

### User Story 3 - Generation de prompt GPT final (Priority: P3)

L'Initiateur souhaite creer un nouveau GPT personnalise pour son equipe. Claude Code genere le prompt systeme complet, pret a etre colle dans le GPT Builder de ChatGPT, incluant le nom, le prenom, le role, les regles de comportement et les limites.

**Why this priority**: C'est le livrable final du systeme - les prompts GPT directement utilisables. Cela permet de reproduire le systeme sur d'autres projets.

**Independent Test**: Peut etre teste en demandant la generation d'un prompt GPT et en verifiant qu'il est directement collable dans le GPT Builder sans modification.

**Acceptance Scenarios**:

1. **Given** l'Initiateur demande la creation du GPT "Product Lead", **When** Claude Code execute la generation, **Then** un prompt complet est genere avec le nom "Benjamin Caron", le role "Product Lead", et les regles de comportement
2. **Given** le prompt est genere, **When** l'Initiateur le colle dans le GPT Builder, **Then** le GPT est cree sans erreur et fonctionne selon les specifications
3. **Given** le GPT est cree, **When** l'Initiateur lui envoie une demande hors perimetre, **Then** le GPT refuse et redirige vers l'Orchestrateur

---

### User Story 4 - Integration IA externe (Priority: P4)

L'Initiateur a besoin d'un asset mediatique (image, audio, video, 3D). Le GPT specialise approprie genere un prompt exact pour l'IA externe avec des instructions claires sur ou l'utiliser.

**Why this priority**: Etend les capacites du systeme au-dela de ChatGPT pour la production de contenus multimedias.

**Independent Test**: Peut etre teste en demandant un logo et en verifiant qu'un prompt pour DALL-E ou Midjourney est genere avec les instructions d'utilisation.

**Acceptance Scenarios**:

1. **Given** l'Initiateur demande un logo, **When** Lucas Perrin (Visual Designer) analyse la demande, **Then** il genere un prompt exact pour DALL-E/Midjourney avec instructions
2. **Given** l'Initiateur demande une voix off, **When** Nassim Haddad (Audio Designer) analyse la demande, **Then** il genere un prompt pour ElevenLabs avec les parametres vocaux

---

### User Story 5 - Gestion des snapshots projet (Priority: P5)

L'Initiateur souhaite sauvegarder l'etat actuel du projet pour pouvoir le reprendre plus tard ou le partager. L'Orchestrateur genere un snapshot synthetise du contexte projet.

**Why this priority**: Permet la continuite des projets entre sessions et la reinjecton du contexte.

**Independent Test**: Peut etre teste en demandant un snapshot et en verifiant qu'il peut etre reinjecte pour reprendre le projet.

**Acceptance Scenarios**:

1. **Given** un projet en cours, **When** l'Initiateur demande un snapshot, **Then** l'Orchestrateur genere un bloc `=== PROJECT SNAPSHOT vX ===` avec le contexte synthetise
2. **Given** un snapshot existe, **When** l'Initiateur le reinjecte dans une nouvelle session, **Then** le contexte est restaure et le projet peut continuer

---

### Edge Cases

- Que se passe-t-il si l'Initiateur envoie une demande a un GPT specialise au lieu de l'Orchestrateur? Le GPT doit refuser et rediriger vers l'Orchestrateur.
- Que se passe-t-il si une demande ne correspond a aucun GPT specialise? L'Orchestrateur doit identifier le manque et proposer soit une solution de contournement, soit indiquer que la fonctionnalite n'est pas couverte.
- Que se passe-t-il si Claude Code retourne une erreur? L'Initiateur doit envoyer le rapport d'erreur a l'Orchestrateur qui analysera et fournira des instructions correctives.
- Que se passe-t-il si un prompt GPT est trop long pour le GPT Builder? Le systeme doit generer des prompts respectant les limites de caracteres.

## Requirements *(mandatory)*

### Functional Requirements

- **FR-001**: Le systeme DOIT avoir un Orchestrateur central (Esteban Durand) comme unique point d'entree pour toutes les demandes
- **FR-002**: L'Orchestrateur DOIT analyser toute demande et decider de la suite logique (delegation GPT, Claude Code, IA externe)
- **FR-003**: L'Orchestrateur DOIT produire uniquement des blocs prets a copier-coller dans les formats standardises
- **FR-004**: Chaque GPT personnalise DOIT avoir un nom, un prenom et un role fixes selon le mapping officiel
- **FR-005**: Chaque GPT personnalise DOIT refuser toute demande hors de son perimetre et renvoyer vers l'Orchestrateur
- **FR-006**: Claude Code DOIT generer des prompts GPT complets directement collables dans le GPT Builder
- **FR-007**: Les prompts generes DOIVENT inclure: nom complet, prompt systeme, regles de comportement, formats de sortie, limites strictes
- **FR-016**: Les prompts GPT DOIVENT etre rediges en francais uniquement
- **FR-017**: Claude Code DOIT generer les 15 prompts GPT en une seule operation batch
- **FR-008**: Le systeme DOIT utiliser les commandes Spec-Kit obligatoires: specify, clarify, plan, tasks, implement
- **FR-009**: Les GPT specialises media DOIVENT generer des prompts exacts pour les IA externes (image, audio, video, 3D)
- **FR-010**: L'Orchestrateur DOIT pouvoir generer des snapshots projet pour la sauvegarde et la reprise de contexte
- **FR-011**: Aucun GPT NE DOIT contacter un autre GPT directement - toute communication passe par l'Orchestrateur via l'Initiateur
- **FR-012**: Aucune decision NE DOIT etre prise implicitement - tout doit etre explicite, ecrit et copiable
- **FR-013**: Les rapports Claude Code DOIVENT utiliser le format `=== CLAUDE CODE REPORT ===`
- **FR-014**: Les tests manuels DOIVENT utiliser le format `=== MANUAL TEST REPORT ===`
- **FR-015**: Les 15 roles GPT du mapping officiel DOIVENT etre supportes (Orchestrateur + 14 specialistes)

### Key Entities

- **Initiateur**: L'humain operateur du systeme, initie les actions, execute les copier-coller, valide les resultats
- **Orchestrateur**: GPT central unique (Esteban Durand), point d'entree exclusif, analyse et redirige les demandes
- **GPT Specialise**: Agent incarne (nom + prenom + role), limite a son domaine, genere des livrables ou prompts IA externe
- **Bloc Copier-Coller**: Unite d'instruction formatee prete a etre executee sans modification
- **Snapshot Projet**: Capture synthetisee du contexte projet pour sauvegarde et reprise
- **Prompt GPT Final**: Configuration complete d'un GPT personnalise, directement collable dans le GPT Builder

## Assumptions

- L'Initiateur a acces a ChatGPT avec la fonctionnalite GPT Builder pour creer des GPTs personnalises
- L'Initiateur a acces a Claude Code avec Spec-Kit installe et configure
- L'Initiateur maitrise le processus de copier-coller entre les differents outils
- Les limites de caracteres du GPT Builder sont respectees par les prompts generes (environ 8000 caracteres max pour les instructions systeme)
- Les IA externes mentionnees (DALL-E, Midjourney, ElevenLabs, etc.) sont accessibles a l'Initiateur

## Success Criteria *(mandatory)*

### Measurable Outcomes

- **SC-001**: L'Initiateur peut demarrer un nouveau projet en moins de 5 minutes en suivant uniquement les instructions de l'Orchestrateur
- **SC-002**: 100% des blocs generes sont executables tels quels sans modification humaine
- **SC-003**: L'Initiateur n'a jamais a se demander a qui parler - l'Orchestrateur decide toujours de la cible
- **SC-004**: Un projet complet (de l'idee au livrable) peut etre mene de bout en bout en utilisant uniquement le systeme
- **SC-005**: Les 15 GPT personnalises peuvent etre crees a partir des prompts generes sans echec
- **SC-006**: Le systeme est reproductible sur un nouveau projet sans configuration additionnelle
- **SC-007**: Un snapshot peut etre reinjecte pour reprendre un projet avec 100% du contexte preserve
- **SC-008**: Aucun GPT specialise n'accepte une tache hors de son perimetre (0% de debordement)
