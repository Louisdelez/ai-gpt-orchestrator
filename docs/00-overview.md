# Vue d'Ensemble

[← Index](./README.md) | [Architecture →](./01-architecture.md)

---

## Vision

Le **AI Orchestrated GPT Production System** est un systeme de production structure permettant de concevoir, orchestrer et exploiter plusieurs GPT personnalises specialises, pilotes par un Orchestrateur central unique.

## Problemes Resolus

### 1. La confusion "A qui parler ?"

**Avant** : Avec plusieurs GPT ou assistants IA, l'utilisateur doit constamment decider lequel utiliser pour quelle tache.

**Apres** : Un seul point d'entree (l'Orchestrateur) analyse chaque demande et redirige vers le bon specialiste.

### 2. L'incoherence des reponses

**Avant** : Chaque GPT a son propre style, ses propres formats, ses propres conventions.

**Apres** : Tous les GPT utilisent des formats de sortie standardises, definis dans la constitution du projet.

### 3. Les decisions implicites

**Avant** : Les IA prennent des decisions sans les expliciter, rendant le processus opaque.

**Apres** : Tout est explicite, ecrit et copiable. Aucun automatisme cache.

### 4. La perte de contexte

**Avant** : Les conversations longues perdent le fil, obligeant a tout re-expliquer.

**Apres** : Les snapshots projet permettent de sauvegarder et reinjecter le contexte a tout moment.

## Philosophie

### Copier-Coller Strict

Le systeme repose sur l'execution manuelle par l'Initiateur (l'humain) de toutes les instructions. Cela garantit :
- **Tracabilite** : Chaque action est visible et reproductible
- **Controle** : L'humain valide avant d'executer
- **Simplicite** : Pas de configuration complexe, pas d'API

### Specialisation Incarnee

Chaque GPT a une identite fixe (nom + prenom + role) et un perimetre strict. Il refuse toute tache hors de son domaine et renvoie vers l'Orchestrateur.

### Integration Spec-Kit

Le workflow est structure autour des commandes Spec-Kit :
1. `/speckit.specify` — Definir la fonctionnalite
2. `/speckit.clarify` — Clarifier les ambiguites
3. `/speckit.plan` — Planifier l'implementation
4. `/speckit.tasks` — Decouper en taches
5. `/speckit.implement` — Executer via Claude Code

## Acteurs du Systeme

| Acteur | Role |
|--------|------|
| **Initiateur** | L'humain qui opere le systeme, formule les demandes, execute les copier-coller |
| **Orchestrateur** | Esteban Durand — analyse, decide, redirige, ne produit jamais directement |
| **GPT Specialise** | Expert dans un domaine, refuse les taches hors perimetre |
| **Claude Code** | Execute les commandes Spec-Kit, genere le code et les prompts |
| **IA Externe** | DALL-E, Midjourney, ElevenLabs, etc. pour les medias |

## Criteres de Succes

Le systeme est valide si :
- Un projet complet peut etre mene de bout en bout
- L'Initiateur ne se demande jamais a qui parler
- Toutes les instructions sont executables telles quelles
- Le contexte peut etre reinjecte via snapshot
- Claude Code produit les GPT personnalises finaux

---

[← Index](./README.md) | [Architecture →](./01-architecture.md)
