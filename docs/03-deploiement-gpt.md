# Deploiement des GPT

[← Installation](./02-installation.md) | [Index](./README.md) | [Workflows →](./04-workflows.md)

---

## Objectif

Creer les 15 GPT personnalises dans le GPT Builder de ChatGPT en copiant les prompts generes.

## Prerequis

- Compte ChatGPT Plus actif
- Prompts GPT generes dans `prompts/`

## Processus de Creation

### Etape 1 : Ouvrir le GPT Builder

1. Aller sur [chat.openai.com](https://chat.openai.com)
2. Cliquer sur **Explore GPTs** (menu gauche)
3. Cliquer sur **Create** (bouton en haut a droite)
4. Choisir **Configure** (onglet)

### Etape 2 : Configurer le GPT

Pour chaque GPT, remplir :

| Champ | Valeur |
|-------|--------|
| **Name** | `Prenom Nom — Role` (ex: "Esteban Durand — Orchestrateur") |
| **Description** | Copier la section "Mission" du fichier prompt |
| **Instructions** | Copier le contenu ENTIER du fichier `.md` |
| **Conversation starters** | Optionnel |

### Etape 3 : Sauvegarder

1. Cliquer sur **Save**
2. Choisir **Only me** (pour usage personnel) ou **Anyone with a link**
3. Confirmer

## Ordre de Deploiement Recommande

Deployer dans cet ordre pour tester incrementalement :

### 1. Orchestrateur (Priorite absolue)

| Fichier | Nom GPT |
|---------|---------|
| `prompts/01-orchestrateur/esteban-durand.md` | Esteban Durand — Orchestrateur |

**Test** : Envoyer "Je veux creer une application" et verifier qu'un bloc `=== CLAUDE CODE ===` est retourne.

### 2. GPT Product

| Fichier | Nom GPT |
|---------|---------|
| `prompts/02-product/benjamin-caron.md` | Benjamin Caron — Product Lead |

### 3. GPT Tech

| Fichier | Nom GPT |
|---------|---------|
| `prompts/03-tech/quentin-delacroix.md` | Quentin Delacroix — Tech Lead |
| `prompts/03-tech/thomas-laurent.md` | Thomas Laurent — Frontend Lead |
| `prompts/03-tech/ulysse-fabre.md` | Ulysse Fabre — Backend Lead |
| `prompts/03-tech/yassine-el-amrani.md` | Yassine El Amrani — DevOps/SRE |

### 4. GPT Quality

| Fichier | Nom GPT |
|---------|---------|
| `prompts/04-quality/adrien-roche.md` | Adrien Roche — QA/Test Lead |
| `prompts/04-quality/rachid-benyahia.md` | Rachid Benyahia — Security/AppSec |
| `prompts/04-quality/sarah-klein.md` | Sarah Klein — Legal/RGPD |

### 5. GPT Design

| Fichier | Nom GPT |
|---------|---------|
| `prompts/05-design/clara-morel.md` | Clara Morel — UX/UI Designer |
| `prompts/05-design/lucas-perrin.md` | Lucas Perrin — Visual Designer |
| `prompts/05-design/maya-renaud.md` | Maya Renaud — Motion/Video |
| `prompts/05-design/nassim-haddad.md` | Nassim Haddad — Audio/Voice |
| `prompts/05-design/elodie-martin.md` | Elodie Martin — 3D/Asset |

### 6. GPT Data

| Fichier | Nom GPT |
|---------|---------|
| `prompts/06-data/romain-girard.md` | Romain Girard — Data Analyst |

## Test Rapide d'un GPT

Pour chaque GPT deploye, effectuer ce test :

### Test 1 : Demande dans le perimetre

```
[Au GPT]
Quelle est ta mission ?
```

**Attendu** : Le GPT repond en decrivant son role specifique.

### Test 2 : Demande hors perimetre

```
[Au GPT]
Peux-tu coder une API REST ?
```

**Attendu** (pour un GPT non-tech) : Le GPT refuse et renvoie vers l'Orchestrateur.

## Nommage Officiel

Le nom de chaque GPT DOIT suivre ce format :

```
[Prenom] [Nom] — [Role]
```

Exemples :
- ✅ `Esteban Durand — Orchestrateur`
- ✅ `Clara Morel — UX/UI Designer`
- ❌ `Orchestrateur` (manque le nom)
- ❌ `Esteban` (incomplet)

## Checklist de Deploiement

- [ ] Orchestrateur deploye et teste
- [ ] 14 GPT specialises deployes
- [ ] Tous les GPT nommes correctement
- [ ] Test dans/hors perimetre effectue pour chaque GPT

## Depannage

### Le GPT accepte une demande hors perimetre

1. Verifier que le prompt contient la section "Limites"
2. Verifier que le protocole de redirection est present
3. Regenerer le GPT avec le prompt mis a jour

### Le GPT ne repond pas au format attendu

1. Verifier que la section "Formats de Sortie" est presente
2. Rappeler le format dans la conversation

---

[← Installation](./02-installation.md) | [Index](./README.md) | [Workflows →](./04-workflows.md)
