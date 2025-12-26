# Installation

[← Architecture](./01-architecture.md) | [Index](./README.md) | [Deploiement GPT →](./03-deploiement-gpt.md)

---

## Prerequis

### Obligatoires

| Outil | Version | Pourquoi |
|-------|---------|----------|
| **ChatGPT Plus** | Abonnement actif | Acces au GPT Builder pour creer les 15 GPT |
| **Claude Code** | Derniere version | Execution des commandes Spec-Kit |
| **Terminal** | Bash/Zsh/PowerShell | Execution des commandes |
| **Editeur de texte** | VS Code recommande | Edition des fichiers Markdown |

### Optionnels

| Outil | Usage |
|-------|-------|
| Git | Versioning du projet |
| Node.js | Si projets JavaScript/TypeScript |
| Python 3.x | Si projets Python |

## Etape 1 : Installer Claude Code

### macOS / Linux

```bash
# Via npm (recommande)
npm install -g @anthropic-ai/claude-code

# Verification
claude --version
```

### Windows

```powershell
# Via npm
npm install -g @anthropic-ai/claude-code

# Verification
claude --version
```

### Configuration

```bash
# Configurer la cle API Anthropic
claude config set api_key YOUR_API_KEY
```

## Etape 2 : Installer Spec-Kit

Spec-Kit est integre a Claude Code. Verifiez qu'il est disponible :

```bash
# Tester une commande Spec-Kit
claude "/speckit.constitution"
```

Si la commande repond, Spec-Kit est operationnel.

## Etape 3 : Cloner le Repository

```bash
# Cloner le projet
git clone https://github.com/YOUR_USERNAME/ai-gpt-orchestrator.git

# Entrer dans le dossier
cd ai-gpt-orchestrator

# Verifier la structure
ls prompts/
```

Vous devez voir :
```
01-orchestrateur/
02-product/
03-tech/
04-quality/
05-design/
06-data/
```

## Etape 4 : Verifier les Prompts GPT

```bash
# Compter les fichiers de prompts
find prompts -name "*.md" | wc -l
# Resultat attendu : 15
```

## Checklist Post-Installation

- [ ] Claude Code installe et configure
- [ ] Commande `/speckit.constitution` repond
- [ ] Repository clone
- [ ] 15 fichiers de prompts presents
- [ ] Acces a ChatGPT Plus confirme

## Prochaine Etape

Une fois l'installation validee, passez au [Deploiement des GPT](./03-deploiement-gpt.md) pour creer les 15 GPT dans ChatGPT.

## Depannage

### Claude Code ne s'installe pas

```bash
# Verifier Node.js
node --version  # Doit etre >= 18.x

# Reinstaller avec sudo si necessaire (Linux/macOS)
sudo npm install -g @anthropic-ai/claude-code
```

### Spec-Kit ne repond pas

```bash
# Verifier la configuration Claude Code
claude config list

# Reinitialiser si necessaire
claude config reset
```

### Prompts manquants

```bash
# Regenerer les prompts si necessaire
claude "/speckit.implement"
```

---

[← Architecture](./01-architecture.md) | [Index](./README.md) | [Deploiement GPT →](./03-deploiement-gpt.md)
