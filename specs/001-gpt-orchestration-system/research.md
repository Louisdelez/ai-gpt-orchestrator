# Research: AI Orchestrated GPT Production System

**Date**: 2025-12-26
**Feature**: 001-gpt-orchestration-system

## Recherches Effectuees

### 1. Structure Optimale des Prompts GPT

**Decision**: Utiliser une structure en 7 sections standardisees

**Rationale**: Les prompts GPT efficaces suivent un pattern etabli qui maximise la coherence et la previsibilite des reponses. La structure choisie couvre tous les aspects necessaires pour un GPT specialise dans un systeme orchestra.

**Structure retenue**:
1. Identite (nom, prenom, role)
2. Mission principale
3. Responsabilites specifiques
4. Regles de comportement non negociables
5. Formats de sortie obligatoires
6. Limites et restrictions
7. Protocole de redirection

**Alternatives considerees**:
- Structure libre : rejetee car manque de coherence entre GPT
- Structure minimale (3 sections) : rejetee car insuffisante pour le controle des perimetres

### 2. Limite de Caracteres GPT Builder

**Decision**: Limiter chaque prompt a 6000 caracteres (marge de securite)

**Rationale**: Le GPT Builder accepte environ 8000 caracteres pour les instructions systeme. Une marge de 2000 caracteres permet des ajustements futurs sans restructuration.

**Alternatives considerees**:
- Utiliser 8000 caracteres max : risque de depassement lors d'evolutions
- Limiter a 4000 caracteres : trop restrictif pour les roles complexes

### 3. Gestion des Refus Hors Perimetre

**Decision**: Message de refus standardise avec redirection explicite

**Rationale**: Chaque GPT doit refuser de maniere coherente et guider l'Initiateur vers l'Orchestrateur. Un message type garantit une experience uniforme.

**Format de refus**:
```
Cette demande sort de mon perimetre en tant que [Role].
Veuillez soumettre cette demande a l'Orchestrateur (Esteban Durand) qui la redirigera vers le bon specialiste.
```

**Alternatives considerees**:
- Refus sans explication : rejetee car frustrant pour l'utilisateur
- Tentative partielle : rejetee car viole le principe d'isolation

### 4. Formats de Sortie par Type de GPT

**Decision**: Adapter les formats obligatoires selon le domaine

**Rationale**: Chaque type de GPT produit des livrables differents. Les formats doivent etre specifiques au domaine tout en restant coherents avec les formats globaux de la constitution.

| Type GPT | Formats Specifiques |
|----------|---------------------|
| Orchestrateur | CLAUDE CODE, GPT DELEGATION, PROJECT SNAPSHOT |
| Product | Specifications fonctionnelles, User Stories |
| Tech | Architecture, Schemas techniques, Code snippets |
| Design | Briefs visuels, Prompts IA externe |
| QA | Plans de test, Rapports de validation |
| Security | Analyses de risques, Recommandations |
| Legal | Avis juridiques, Checklists conformite |
| Data | Rapports d'analyse, Metriques |

### 5. Delegation vers IA Externes

**Decision**: Utiliser un format de prompt structure avec metadata

**Rationale**: Les GPT media doivent generer des prompts prets a l'emploi pour les IA externes. Un format standardise facilite le copier-coller.

**Format de prompt IA externe**:
```
=== IA EXTERNE ===
Outil : [DALL-E / Midjourney / ElevenLabs / Suno / etc.]
Prompt a copier :
[contenu du prompt]
Instructions :
[ou coller, parametres recommandes]
=== END ===
```

### 6. Contenu des Snapshots Projet

**Decision**: Snapshot structure en 5 sections

**Rationale**: Un snapshot doit etre suffisamment complet pour reprendre un projet mais assez concis pour tenir dans une fenetre de contexte.

**Structure snapshot**:
1. Resume du projet (2-3 phrases)
2. Etat actuel (phase, derniere action)
3. Decisions prises (liste)
4. Prochaines etapes (liste)
5. Fichiers cles (chemins)

**Limite**: Maximum 2000 caracteres pour garantir la reinjectabilite

## Synthese

Toutes les decisions de recherche sont alignees avec:
- La constitution v1.0.0
- Les clarifications (francais, batch complet)
- Les exigences fonctionnelles de la spec

Aucun "NEEDS CLARIFICATION" restant.
