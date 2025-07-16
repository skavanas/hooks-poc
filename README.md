# Git Hooks PoC – Validation pre-commit et commit-msg

Ce projet est une preuve de concept (**PoC**) démontrant l’intégration de **hooks Git** personnalisés pour améliorer la qualité du code **avant et pendant les commits**.

---

## ✅ Objectifs

- Empêcher les commits avec du code non compilable ou mal formaté
- Forcer un format standard pour les messages de commit
- Détecter les erreurs courantes le plus tôt possible

---

## 🧩 Hooks utilisés

### `pre-commit`
Ce hook s'exécute **avant chaque commit** et utilise plusieurs outils :

| Outil Maven           | Rôle                                                                 |
|-----------------------|----------------------------------------------------------------------|
| `mvn compile`         | Vérifie que le code compile correctement                             |
| `mvn checkstyle:check`| Applique les règles de style de code définies (Checkstyle)           |
| `mvn formatter:format`| Formate automatiquement le code Java (Formatter Maven Plugin)        |
| `mvn test`            | Exécute les tests unitaires                                          |
| `mvn spotbugs:spotbugs`| Analyse statique pour détecter des bugs potentiels (SpotBugs)      |

### `commit-msg`
Ce hook s’assure que les **messages de commit** respectent un format prédéfini basé sur un **ID de ticket**.  
Exemple attendu :  


## 🔗 Configuration du sous-module Git

Les hooks sont gérés dans un **repository Git séparé** et liés via un **Git submodule**.

### Initialisation

Si vous clonez ce dépôt, exécutez :

```bash
git clone --recurse-submodules <url-du-repo>
```

Ou si vous avez déjà cloné sans les sous-modules :

```bash
git submodule update --init --recursive
```
Lien avec les hooks Git
Le projet utilise la configuration suivante pour pointer vers les hooks centralisés :
```bash
git config core.hooksPath .githooks
```

