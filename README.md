# POC - Spring Boot Project

## Gestion des Git Hooks

Ce projet utilise des **Git hooks partagés** pour assurer la qualité du code et l'exécution de vérifications automatiques avant les commits ou les pushes.

### Comment ça fonctionne ?

1. **Clone automatique des hooks partagés**

   - Maven utilise le plugin `exec-maven-plugin` pour cloner le dépôt des hooks partagés depuis GitHub dans le répertoire cible `target/shared-hooks`.
   - Le clone est effectué uniquement si le répertoire n’existe pas déjà.

2. **Configuration de Git pour utiliser ces hooks**

   - Le plugin `git-build-hook-maven-plugin` configure Git pour utiliser le répertoire cloné comme `core.hooksPath`.
   - Tous les hooks (pre-commit, pre-push, etc.) définis dans ce dépôt seront automatiquement utilisés par Git.

3. **Exécution automatique**

   - Tout est exécuté automatiquement lors de la phase `initialize` de Maven.

---

## How to set it up

Pour configurer les hooks sur votre machine, il suffit d’exécuter la commande suivante à la racine du projet :

```bash
mvn initialize
