# Quickstart: Documentation & Onboarding

**Feature**: 002-docs-and-onboarding
**Date**: 2025-12-26

## Objectif

Generer la documentation complete du AI Orchestrated GPT Production System pour publication GitHub.

## Prerequis

- Repository `ai-gpt-orchestrator` clone
- Branche `002-docs-and-onboarding` active
- Constitution existante (`.specify/memory/constitution.md`)
- Prompts GPT generes (`prompts/**/*.md`)

## Etapes d'Implementation

### Etape 1: Creer la structure docs/

```bash
mkdir -p docs
```

### Etape 2: Generer les fichiers

Executer `/speckit.tasks` puis `/speckit.implement` pour generer :

1. `README.md` (racine)
2. `docs/README.md` (index)
3. `docs/00-overview.md`
4. `docs/01-architecture.md`
5. `docs/02-installation.md`
6. `docs/03-deploiement-gpt.md`
7. `docs/04-workflows.md`
8. `docs/05-media-ia-externe.md`
9. `docs/06-snapshots.md`
10. `docs/07-best-practices.md`
11. `docs/08-faq.md`
12. `docs/09-glossaire.md`

### Etape 3: Valider

Checklist de validation :

- [ ] README < 500 mots : `wc -w README.md`
- [ ] Pas de "Cloud Code" : `grep -ri "cloud code" README.md docs/`
- [ ] Liens fonctionnels : Tester chaque lien dans GitHub
- [ ] 15 GPT documentes : Verifier 01-architecture.md
- [ ] 10+ FAQ : Verifier 08-faq.md
- [ ] Vocabulaire stable : Relire 09-glossaire.md

## Verification Rapide

```bash
# Compter les mots du README
wc -w README.md

# Verifier absence de "Cloud Code"
grep -ri "cloud code" README.md docs/ || echo "OK: Aucune mention de Cloud Code"

# Lister les fichiers generes
ls -la docs/
```

## Resultat Attendu

```text
README.md                    # < 500 mots
docs/
├── README.md                # Index avec 10 liens
├── 00-overview.md           # Vision du projet
├── 01-architecture.md       # 15 GPT documentes
├── 02-installation.md       # Guide pas a pas
├── 03-deploiement-gpt.md    # GPT Builder
├── 04-workflows.md          # 3+ workflows
├── 05-media-ia-externe.md   # 5 types IA
├── 06-snapshots.md          # Modele snapshot
├── 07-best-practices.md     # Do/Don't
├── 08-faq.md                # 10+ questions
└── 09-glossaire.md          # Termes officiels
```

## Test d'Acceptance

Un nouvel utilisateur doit pouvoir :

1. Lire le README et comprendre le projet en < 5 min
2. Suivre l'installation et avoir un systeme fonctionnel en < 30 min
3. Deployer 1 GPT dans ChatGPT
4. Executer un workflow complet (specify → implement)
5. Creer et reinjecter un snapshot
