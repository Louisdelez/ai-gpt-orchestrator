# FAQ — Questions Frequentes

[← Bonnes Pratiques](./07-best-practices.md) | [Index](./README.md) | [Glossaire →](./09-glossaire.md)

---

## Installation

### Q1 : J'ai besoin de ChatGPT Plus ?

**Oui, obligatoire.** Le GPT Builder n'est accessible qu'avec un abonnement ChatGPT Plus (ou Team/Enterprise).

### Q2 : Claude Code ne s'installe pas, que faire ?

Verifiez :
1. Node.js >= 18.x installe : `node --version`
2. npm a jour : `npm --version`
3. Droits d'administration si necessaire

```bash
# Reinstaller
sudo npm install -g @anthropic-ai/claude-code
```

### Q3 : Ou trouver ma cle API Anthropic ?

1. Aller sur [console.anthropic.com](https://console.anthropic.com)
2. Section "API Keys"
3. Creer une nouvelle cle
4. Configurer : `claude config set api_key YOUR_KEY`

---

## Usage

### Q4 : Pourquoi toujours passer par l'Orchestrateur ?

L'Orchestrateur :
- Maintient la coherence du projet
- Connait le contexte global
- Sait quel GPT peut repondre a quelle demande
- Genere les blocs au bon format

Contacter un GPT directement = perdre ces avantages.

### Q5 : Un GPT refuse ma demande, c'est normal ?

**Oui, c'est le comportement attendu.** Chaque GPT a un perimetre strict. S'il refuse, il vous redirige vers l'Orchestrateur qui assignera le bon GPT.

### Q6 : Comment savoir quel GPT fait quoi ?

Voir le [tableau des 15 GPT](./01-architecture.md#les-15-gpt-specialises) dans la documentation Architecture.

### Q7 : Puis-je modifier les prompts des GPT ?

Oui, mais :
- Respectez la structure (7 sections)
- Ne supprimez pas le protocole de redirection
- Testez apres modification

---

## Workflows

### Q8 : Dans quel ordre utiliser les commandes Spec-Kit ?

```
1. /speckit.specify  → Definir
2. /speckit.clarify  → Clarifier
3. /speckit.plan     → Planifier
4. /speckit.tasks    → Decouper
5. /speckit.implement → Executer
```

Cet ordre est recommande mais pas obligatoire. Vous pouvez sauter `clarify` si la spec est claire.

### Q9 : Je peux utiliser Spec-Kit sans l'Orchestrateur ?

Techniquement oui, mais vous perdez :
- L'analyse de votre demande
- La redirection intelligente
- Les formats standardises
- La gestion du contexte projet

### Q10 : Comment corriger un bug avec ce systeme ?

1. Decrire le bug a l'Orchestrateur
2. Il redirige vers le GPT technique approprie
3. Le GPT analyse et propose une solution
4. Vous executez via Claude Code
5. Vous testez et confirmez

---

## Snapshots

### Q11 : A quelle frequence faire des snapshots ?

- **Minimum** : 1 par session de travail
- **Recommande** : Tous les 10-15 echanges
- **Obligatoire** : Avant de fermer un chat important

### Q12 : Mon snapshot est trop long, que faire ?

Le snapshot doit etre synthetique. Si trop long :
1. Gardez seulement les decisions cles
2. Resumez l'etat en 2-3 phrases
3. Listez uniquement les fichiers actifs

### Q13 : Comment reprendre un projet abandonne depuis longtemps ?

1. Retrouvez le dernier snapshot
2. Demarrez un nouveau chat avec l'Orchestrateur
3. Collez le snapshot
4. Demandez un rappel de l'etat

---

## Erreurs Courantes

### E1 : "Cloud Code" au lieu de "Claude Code"

**Probleme** : Vous avez ecrit "Cloud Code" quelque part.

**Solution** : C'est **Claude Code**, pas "Cloud Code". Verifiez votre documentation.

### E2 : Le GPT accepte une demande hors perimetre

**Probleme** : Le prompt du GPT est incomplet.

**Solution** :
1. Verifiez que la section "Limites" existe
2. Verifiez le protocole de redirection
3. Regenerez le GPT si necessaire

### E3 : Les blocs ne sont pas au bon format

**Probleme** : L'Orchestrateur ne genere pas les bons delimiteurs.

**Solution** : Rappelez le format dans votre message :
```
Genere un bloc au format :
=== CLAUDE CODE ===
[contenu]
=== END ===
```

### E4 : Contexte perdu en cours de projet

**Probleme** : Le GPT oublie les decisions precedentes.

**Solution** :
1. La conversation est trop longue
2. Faites un snapshot
3. Demarrez un nouveau chat
4. Reinjectez le snapshot

### E5 : Claude Code ne reconnait pas les commandes Spec-Kit

**Probleme** : Spec-Kit n'est pas configure.

**Solution** :
```bash
# Verifier la configuration
claude config list

# Tester
claude "/speckit.constitution"
```

---

## Support

### Ou poser des questions ?

1. Consultez d'abord cette FAQ
2. Verifiez la [documentation complete](./README.md)
3. Ouvrez une issue sur le repository GitHub

### Comment contribuer ?

1. Fork le repository
2. Creez une branche pour votre modification
3. Soumettez une Pull Request

---

[← Bonnes Pratiques](./07-best-practices.md) | [Index](./README.md) | [Glossaire →](./09-glossaire.md)
