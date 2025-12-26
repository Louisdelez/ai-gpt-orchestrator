# Data Model: AI Orchestrated GPT Production System

**Date**: 2025-12-26
**Feature**: 001-gpt-orchestration-system

## Entites Principales

### 1. GPT Personnalise

Represente un agent GPT incarne avec une identite et un perimetre fixes.

| Champ | Type | Description | Contraintes |
|-------|------|-------------|-------------|
| prenom | string | Prenom de l'agent | Requis, immuable |
| nom | string | Nom de famille | Requis, immuable |
| role | string | Titre du role | Requis, immuable |
| domaine | enum | Categorie fonctionnelle | orchestrateur, product, tech, quality, design, data |
| mission | string | Description de la mission | Max 500 chars |
| responsabilites | string[] | Liste des responsabilites | Min 3, max 10 |
| regles | string[] | Regles non negociables | Min 3 |
| formats_sortie | string[] | Formats de sortie autorises | Min 1 |
| limites | string[] | Ce que le GPT ne fait pas | Min 2 |
| prompt_complet | string | Prompt systeme genere | Max 6000 chars |

**Mapping des 15 GPT**:

| ID | Prenom | Nom | Role | Domaine |
|----|--------|-----|------|---------|
| 01 | Esteban | Durand | Orchestrateur | orchestrateur |
| 02 | Benjamin | Caron | Product Lead | product |
| 03 | Quentin | Delacroix | Tech Lead / Architect | tech |
| 04 | Thomas | Laurent | Frontend Lead | tech |
| 05 | Ulysse | Fabre | Backend Lead | tech |
| 06 | Yassine | El Amrani | DevOps / SRE | tech |
| 07 | Adrien | Roche | QA / Test Lead | quality |
| 08 | Rachid | Benyahia | Security / AppSec | quality |
| 09 | Sarah | Klein | Legal / RGPD | quality |
| 10 | Clara | Morel | UX/UI Designer | design |
| 11 | Lucas | Perrin | Visual Designer / Brand | design |
| 12 | Maya | Renaud | Motion / Video Designer | design |
| 13 | Nassim | Haddad | Audio / Voice & Sound Designer | design |
| 14 | Elodie | Martin | 3D / Asset Designer | design |
| 15 | Romain | Girard | Data Analyst | data |

### 2. Bloc Copier-Coller

Unite d'instruction formatee produite par l'Orchestrateur ou les GPT specialises.

| Champ | Type | Description | Contraintes |
|-------|------|-------------|-------------|
| type | enum | Type de bloc | claude_code, gpt_delegation, report, snapshot, ia_externe |
| cible | string | Destinataire (si delegation) | Optionnel |
| contenu | string | Corps du bloc | Requis |
| format | string | Format de sortie | Selon type |

**Types de blocs**:

```
claude_code:
  === CLAUDE CODE ===
  [commande + contenu]
  === END ===

gpt_delegation:
  === GPT DELEGATION ===
  Cible : [Prenom Nom] — [Role]
  Message a copier :
  [contenu]
  === END ===

report:
  === CLAUDE CODE REPORT ===
  [sortie brute]
  === END ===

test_report:
  === MANUAL TEST REPORT ===
  Fonctionnel :
  Casse :
  Notes :
  === END ===

snapshot:
  === PROJECT SNAPSHOT vX ===
  [contexte synthetise]
  === END ===

ia_externe:
  === IA EXTERNE ===
  Outil : [nom]
  Prompt a copier :
  [contenu]
  Instructions :
  [details]
  === END ===
```

### 3. Snapshot Projet

Capture synthetisee du contexte d'un projet pour sauvegarde et reprise.

| Champ | Type | Description | Contraintes |
|-------|------|-------------|-------------|
| version | integer | Numero de version | Auto-increment |
| resume | string | Resume du projet | Max 200 chars |
| etat | string | Phase actuelle | Max 100 chars |
| decisions | string[] | Decisions prises | Liste |
| prochaines_etapes | string[] | Actions a venir | Liste |
| fichiers_cles | string[] | Chemins importants | Liste |

**Contrainte globale**: Max 2000 caracteres total

### 4. Prompt IA Externe

Instructions pour delegation vers une IA externe (image, audio, video, 3D).

| Champ | Type | Description | Contraintes |
|-------|------|-------------|-------------|
| outil | enum | IA cible | dalle, midjourney, elevenlabs, suno, runway, blender |
| prompt | string | Prompt a copier | Requis |
| parametres | object | Parametres recommandes | Optionnel |
| instructions | string | Guide d'utilisation | Requis |

## Relations

```
Initiateur (humain)
    |
    v
Orchestrateur (Esteban Durand)
    |
    +---> GPT Specialise (1..14)
    |         |
    |         +---> Bloc Copier-Coller (livrable)
    |         +---> Prompt IA Externe (delegation)
    |
    +---> Claude Code
    |         |
    |         +---> Prompt GPT Final (generation)
    |
    +---> Snapshot Projet (sauvegarde)
```

## Regles de Validation

1. **Identite GPT**: Prenom + Nom + Role doivent correspondre exactement au mapping officiel
2. **Isolation**: Aucun GPT ne reference directement un autre GPT dans son prompt
3. **Formats**: Chaque bloc doit respecter strictement le format defini
4. **Taille prompt**: Maximum 6000 caracteres (marge sur limite GPT Builder de 8000)
5. **Taille snapshot**: Maximum 2000 caracteres pour reinjectabilite
6. **Langue**: Tous les contenus en francais uniquement
