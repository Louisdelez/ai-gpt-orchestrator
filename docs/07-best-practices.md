# Bonnes Pratiques

[← Snapshots](./06-snapshots.md) | [Index](./README.md) | [FAQ →](./08-faq.md)

---

## Les Regles d'Or

### 1. Toujours passer par l'Orchestrateur

```
✅ Correct
[A l'Orchestrateur]
J'ai besoin d'un logo pour mon app

❌ Incorrect
[Directement a Lucas Perrin]
Fais-moi un logo
```

### 2. Un seul sujet par message

```
✅ Correct
"Je veux ajouter l'authentification"

❌ Incorrect
"Je veux ajouter l'auth, un dashboard, des notifications et un systeme de paiement"
```

### 3. Toujours copier-coller les blocs complets

```
✅ Correct
Copier tout le bloc :
=== CLAUDE CODE ===
[contenu]
=== END ===

❌ Incorrect
Copier seulement une partie du bloc
```

### 4. Faire des snapshots reguliers

```
✅ Correct
Demander un snapshot toutes les 10-15 echanges

❌ Incorrect
Attendre que la conversation soit trop longue
```

### 5. Respecter les formats de retour

```
✅ Correct
=== CLAUDE CODE REPORT ===
[sortie complete]
=== END ===

❌ Incorrect
"Ca a marche" sans details
```

---

## Les Anti-Patterns

### Anti-Pattern 1 : Contacter un GPT directement

**Probleme** : Vous perdez la coherence du projet et le contexte global.

**Solution** : Toujours passer par l'Orchestrateur, meme si vous savez quel GPT peut repondre.

### Anti-Pattern 2 : Demander hors perimetre

**Probleme** : Demander a un GPT une tache qu'il ne peut pas faire.

**Exemple** :
```
[A Benjamin Caron - Product Lead]
Peux-tu coder l'API REST ?
```

**Solution** : Le GPT refusera et renverra vers l'Orchestrateur. C'est le comportement attendu.

### Anti-Pattern 3 : Ignorer les blocs de retour

**Probleme** : Ne pas renvoyer le resultat a l'Orchestrateur apres execution.

**Exemple** :
```
1. Orchestrateur donne un bloc CLAUDE CODE
2. Vous executez dans Claude Code
3. Vous ne renvoyez pas le CLAUDE CODE REPORT
4. L'Orchestrateur ne sait pas ou en est le projet
```

**Solution** : Toujours renvoyer le resultat avec le format REPORT.

### Anti-Pattern 4 : Messages trop longs

**Probleme** : Noyer le GPT dans trop d'informations.

**Solution** : Un sujet par message, structurer avec des sections claires.

### Anti-Pattern 5 : Oublier le contexte

**Probleme** : Reprendre un projet sans le contexte precedent.

**Solution** : Utiliser les snapshots pour maintenir la continuite.

---

## Performance et Chats Longs

### Symptomes d'un chat trop long

- Le GPT oublie des decisions prises au debut
- Les reponses deviennent moins precises
- Le GPT redemande des informations deja donnees

### Solutions

1. **Snapshot preventif** : Faire un snapshot avant que le chat ne devienne trop long
2. **Nouveau chat** : Demarrer une nouvelle conversation avec le snapshot
3. **Decoupage** : Traiter un sujet par session

### Regles de performance

| Nombre d'echanges | Action recommandee |
|-------------------|-------------------|
| 0-10 | Continuer normalement |
| 10-20 | Envisager un snapshot |
| 20-30 | Snapshot obligatoire |
| 30+ | Nouveau chat avec snapshot |

---

## Checklist Avant de Demander

- [ ] Ma demande est-elle claire et specifique ?
- [ ] Ai-je fourni le contexte necessaire ?
- [ ] Suis-je passe par l'Orchestrateur ?
- [ ] Mon dernier rapport a-t-il ete transmis ?
- [ ] Ai-je fait un snapshot recent ?

---

## Checklist Apres Execution

- [ ] Ai-je copie le bloc complet ?
- [ ] Ai-je renvoye le rapport a l'Orchestrateur ?
- [ ] Le resultat correspond-il a mes attentes ?
- [ ] Dois-je faire un snapshot maintenant ?

---

[← Snapshots](./06-snapshots.md) | [Index](./README.md) | [FAQ →](./08-faq.md)
