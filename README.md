# Nom du projet

> Une phrase pour dire ce que fait le projet.

## Démarrer

```bash
# Comment installer et lancer le projet (à compléter)
```

## Contribuer

Tout est expliqué dans [CONTRIBUTING.md](CONTRIBUTING.md) : issue → branche → PR → review → merge → release.
Le plus simple est de passer par le [dashboard VeD Opps](https://taskf0rce.github.io/VeD_Opps/).

## Versions

Les versions suivent [SemVer](https://semver.org/lang/fr/) et sont publiées automatiquement :
voir les [releases](../../releases) et le [CHANGELOG](CHANGELOG.md) (créé à la première release).

---

<details>
<summary>📦 Ce que contient ce template (à lire une fois, puis tu peux supprimer cette section)</summary>

| Fichier | Rôle |
| --- | --- |
| `.github/workflows/ci.yml` | Lint, tests et build à chaque PR. Détecte tout seul Node, Python, Maven ou Gradle. |
| `.github/workflows/pr-title.yml` | Vérifie que le titre de la PR suit les Conventional Commits. |
| `.github/workflows/release.yml` | Release automatique avec release-please (bouton « Nouvelle release » du dashboard). |
| `.github/ISSUE_TEMPLATE/` | Formulaires « Bug » et « Feature ». |
| `.github/PULL_REQUEST_TEMPLATE.md` | Ce qu'on remplit en ouvrant une PR. |
| `.github/CODEOWNERS` | Chacun review le code de l'autre. |
| `release-please-config.json` | Sections du CHANGELOG et règles de version. |
| `CONTRIBUTING.md` | Le guide pas à pas. |

**À adapter selon le projet :**

- **Code dans un sous-dossier** : décommente `working-directory` dans `.github/workflows/ci.yml`.
- **Projet Node** : dans `release-please-config.json`, remplace `"release-type": "simple"` par `"node"` pour que la version de `package.json` soit mise à jour aussi. (`"python"` pour un `pyproject.toml`, `"maven"` pour un `pom.xml`.)
- **Commandes de CI** : la CI lance `npm run lint`, `npm test` et `npm run build` s'ils existent (Python : `ruff` et `pytest` ; Java : `mvn verify` ou `gradle build`). Ajoute ces scripts dans ton projet et ils seront vérifiés.

</details>
