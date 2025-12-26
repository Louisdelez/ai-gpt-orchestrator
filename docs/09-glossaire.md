# Glossaire

[← FAQ](./08-faq.md) | [Index](./README.md)

---

## Termes Officiels

Ce glossaire definit les termes officiels du systeme. Utilisez ces termes de maniere coherente dans toutes les communications.

---

### Acteurs

| Terme | Definition |
|-------|------------|
| **Initiateur** | L'humain qui opere le systeme. Il formule les demandes, valide les propositions, et execute les copier-coller. |
| **Orchestrateur** | Esteban Durand. Le GPT central qui analyse toutes les demandes et redirige vers les bons acteurs. Point d'entree unique. |
| **GPT Specialise** | Un des 14 GPT experts (hors Orchestrateur) ayant un perimetre strict et une identite fixe. |

---

### Outils

| Terme | Definition |
|-------|------------|
| **Claude Code** | Outil CLI d'Anthropic pour executer des commandes et generer du code. Execute les commandes Spec-Kit. ⚠️ Jamais "Cloud Code". |
| **Spec-Kit** | Framework de structuration de projets integre a Claude Code. Fournit les commandes /speckit.*. |
| **GPT Builder** | Interface ChatGPT pour creer des GPT personnalises. Necessite ChatGPT Plus. |
| **IA Externe** | Outil d'IA tiers (DALL-E, Midjourney, ElevenLabs, etc.) vers lequel les GPT Design delegent. |

---

### Concepts

| Terme | Definition |
|-------|------------|
| **Bloc** | Format de sortie standardise delimitee par `=== ... ===`. Types : CLAUDE CODE, GPT DELEGATION, REPORT, SNAPSHOT. |
| **Snapshot** | Capture synthetisee de l'etat d'un projet a un instant donne, reinjectables dans un nouveau chat. |
| **Perimetre** | Ensemble des responsabilites et limites d'un GPT specialise. |
| **Protocole de Redirection** | Mecanisme par lequel un GPT refuse une tache hors perimetre et renvoie vers l'Orchestrateur. |
| **Copier-Coller** | Methode d'execution du systeme. Toutes les instructions sont executees manuellement par l'Initiateur. |

---

### Commandes Spec-Kit

| Commande | Description |
|----------|-------------|
| `/speckit.specify` | Definit une nouvelle fonctionnalite. Cree une specification. |
| `/speckit.clarify` | Identifie et resout les ambiguites dans la specification. |
| `/speckit.plan` | Genere le plan technique d'implementation. |
| `/speckit.tasks` | Decoupe le plan en taches executables. |
| `/speckit.implement` | Execute les taches pour implementer la fonctionnalite. |
| `/speckit.constitution` | Affiche ou modifie la constitution du projet. |

---

### Formats de Blocs

| Format | Usage |
|--------|-------|
| `=== CLAUDE CODE ===` | Bloc a executer dans Claude Code |
| `=== GPT DELEGATION ===` | Bloc a copier vers un GPT specialise |
| `=== CLAUDE CODE REPORT ===` | Retour d'execution de Claude Code |
| `=== MANUAL TEST REPORT ===` | Resultat de test manuel |
| `=== PROJECT SNAPSHOT vX ===` | Etat synthetise du projet |
| `=== IA EXTERNE ===` | Prompt pour outil IA externe |

---

### Domaines GPT

| Domaine | GPT | Expertise |
|---------|-----|-----------|
| **Central** | Esteban Durand | Orchestration |
| **Product** | Benjamin Caron | Vision produit, roadmap |
| **Tech** | Quentin, Thomas, Ulysse, Yassine | Architecture, frontend, backend, DevOps |
| **Quality** | Adrien, Rachid, Sarah | Tests, securite, legal |
| **Design** | Clara, Lucas, Maya, Nassim, Elodie | UX/UI, visuel, motion, audio, 3D |
| **Data** | Romain Girard | Analyse de donnees |

---

### Acronymes

| Acronyme | Signification |
|----------|---------------|
| **GPT** | Generative Pre-trained Transformer |
| **CLI** | Command Line Interface |
| **API** | Application Programming Interface |
| **RGPD** | Reglement General sur la Protection des Donnees |
| **UX** | User Experience |
| **UI** | User Interface |
| **QA** | Quality Assurance |
| **SRE** | Site Reliability Engineering |
| **CI/CD** | Continuous Integration / Continuous Deployment |

---

### Termes a Eviter

| ❌ Eviter | ✅ Utiliser |
|-----------|-------------|
| Cloud Code | Claude Code |
| Le bot | L'Orchestrateur / Le GPT |
| L'utilisateur | L'Initiateur |
| Prompt | Instructions / Bloc (selon contexte) |
| Automatique | Copier-coller / Manuel |

---

[← FAQ](./08-faq.md) | [Index](./README.md)
