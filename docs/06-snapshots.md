# Snapshots Projet

[← IA Externes](./05-media-ia-externe.md) | [Index](./README.md) | [Bonnes Pratiques →](./07-best-practices.md)

---

## Introduction

Les snapshots permettent de sauvegarder l'etat d'un projet a un instant donne, puis de le reinjecter dans une nouvelle conversation pour reprendre le travail.

## Pourquoi Utiliser les Snapshots ?

### Probleme

Les conversations ChatGPT ont une limite de contexte. Apres un certain nombre d'echanges, le GPT "oublie" le debut de la conversation.

### Solution

Le snapshot synthetise l'etat du projet en quelques lignes, permettant de :
- Reprendre dans un nouveau chat sans tout re-expliquer
- Partager le contexte avec d'autres personnes
- Archiver l'etat du projet a une date cle

## Quand Faire un Snapshot ?

| Situation | Action |
|-----------|--------|
| Fin de session de travail | Demander un snapshot |
| Avant un changement majeur | Archiver l'etat actuel |
| Conversation longue (> 20 echanges) | Creer un snapshot de secours |
| Changement de personne | Transmettre le contexte |
| Jalon projet atteint | Documenter l'etat |

## Format Standard de Snapshot

```
=== PROJECT SNAPSHOT v1 ===
Resume : Application de gestion de taches avec auth JWT.
         Phase d'implementation en cours.

Etat : Phase 4 - Implementation des endpoints API

Decisions :
- Stack : Node.js + Express + PostgreSQL
- Auth : JWT avec refresh tokens
- Front : React avec TailwindCSS

Prochaines etapes :
1. Finir les endpoints CRUD pour les taches
2. Ajouter la validation des donnees
3. Implementer les tests d'integration

Fichiers cles :
- specs/001-task-manager/spec.md
- specs/001-task-manager/plan.md
- src/routes/tasks.js (en cours)
=== END ===
```

## Comment Demander un Snapshot

```
[A l'Orchestrateur]
Genere un snapshot du projet actuel
```

L'Orchestrateur retourne un bloc `=== PROJECT SNAPSHOT vX ===` avec le contexte synthetise.

## Comment Reinjecter un Snapshot

### Etape 1 : Demarrer une nouvelle conversation

Ouvrir un nouveau chat avec l'Orchestrateur.

### Etape 2 : Coller le snapshot

```
[A l'Orchestrateur]
Voici le contexte de mon projet :

=== PROJECT SNAPSHOT v3 ===
Resume : Application de gestion de taches...
[reste du snapshot]
=== END ===

Je voudrais continuer avec [votre demande]
```

### Etape 3 : L'Orchestrateur reprend le contexte

L'Orchestrateur analyse le snapshot et reprend la ou le projet en etait.

## Bonnes Pratiques

### Frequence

- **Minimum** : Un snapshot par session de travail
- **Recommande** : Un snapshot tous les 10-15 echanges significatifs
- **Obligatoire** : Avant de fermer un chat important

### Versioning

Incrementer le numero de version a chaque nouveau snapshot :
- `v1` : Premier snapshot
- `v2` : Apres changements majeurs
- `v3` : etc.

### Archivage

Conserver les snapshots dans un fichier local :

```bash
# Creer un fichier de snapshots
echo "[SNAPSHOT v1 - 2025-01-15]" >> project-snapshots.md
# Coller le contenu du snapshot
```

## Exemple Complet

### Situation

Vous avez travaille 2 heures sur un projet. La conversation devient longue.

### Action

```
[A l'Orchestrateur]
Je vais faire une pause. Genere un snapshot complet du projet.
```

### Resultat

```
=== PROJECT SNAPSHOT v2 ===
Resume : E-commerce avec panier et paiement Stripe.
         Frontend React termine, backend en cours.

Etat : Phase 3 - Implementation API paiement

Decisions :
- Stripe pour les paiements (decision T015)
- PostgreSQL pour la persistance
- Redis pour les sessions panier

Prochaines etapes :
1. Webhook Stripe pour confirmer les paiements
2. Emails de confirmation avec SendGrid
3. Tests E2E du parcours achat

Fichiers cles :
- specs/002-ecommerce/spec.md
- src/services/payment.js (en cours)
- src/routes/checkout.js (a creer)
=== END ===
```

### Reprise

Le lendemain, nouveau chat :

```
[A l'Orchestrateur]
Reprise du projet e-commerce :

=== PROJECT SNAPSHOT v2 ===
[coller le snapshot]
=== END ===

Je voudrais implementer le webhook Stripe.
```

---

[← IA Externes](./05-media-ia-externe.md) | [Index](./README.md) | [Bonnes Pratiques →](./07-best-practices.md)
