# Contribuer au projet

Ce guide explique comment on travaille à deux sans se marcher dessus. Pour chaque étape, il y a **trois façons de faire**, de la plus simple à la plus technique :

- 📊 **Dashboard** : https://taskf0rce.github.io/VeD_Opps/ (des boutons, rien à installer)
- 🖥️ **GitHub Desktop** : https://desktop.github.com (l'appli pour copier le code sur ton PC)
- 🧑‍💻 **VS Code** (ou le terminal, pour ceux qui aiment)

Prends celle que tu préfères. Le résultat est le même.

---

## Le principe en 30 secondes

```
  Issue          Branche              PR                 Review        Merge          Release
 (la tâche) → feature/ma-tache → (demande d'ajout) → (l'autre relit) → (dans main) → (v0.2.0)
```

1. **`main` est toujours stable** : c'est la version qui marche. On n'y pousse **jamais** directement.
2. **Une tâche = une issue = une branche** (`feature/...` pour une nouveauté, `fix/...` pour une correction).
3. Quand c'est prêt, on ouvre une **pull request (PR)** : « voici mes changements, je propose de les ajouter à `main` ».
4. **L'autre relit** et approuve. On review toujours le code de l'autre, jamais le sien.
5. Quand la CI est verte ✅ et la PR approuvée 👍, on **merge**.
6. De temps en temps, on publie une **release** : la version est calculée toute seule.

---

## 1. Créer la tâche

### 📊 Dashboard (recommandé)

Clique sur **＋ Nouvelle feature**, choisis le projet, le type (fonctionnalité ou correction) et un nom, par exemple « page de connexion ».

D'un seul clic, le dashboard crée :
- l'**issue** « page de connexion », qui t'est assignée,
- la **branche** `feature/page-de-connexion`,
- une **PR en brouillon** « feat: page de connexion », liée à l'issue,
- les cartes dans le **kanban**, colonne « En cours ».

### Sur github.com

1. Onglet **Issues** → **New issue** → formulaire « ✨ Feature » ou « 🐛 Bug ».
2. Dans l'issue, colonne de droite → **Development** → **Create a branch**. Nomme-la `feature/page-de-connexion`.

---

## 2. Récupérer la branche sur ton PC

> La première fois seulement, il faut **cloner** le projet (le copier sur ton PC).
> GitHub Desktop : **File → Clone repository** → onglet *GitHub.com* → choisis `TaskF0RCE/le-projet`.
> VS Code : **Ctrl+Maj+P** → `Git: Clone` → *Clone from GitHub*.

### 🖥️ GitHub Desktop
1. **Fetch origin**, le bouton en haut à droite.
2. **Current branch** → choisis `feature/page-de-connexion`.

### 🧑‍💻 VS Code
1. Clique sur le **nom de branche** en bas à gauche (souvent `main`).
2. Choisis `origin/feature/page-de-connexion`.

### Terminal
```bash
git fetch
git switch feature/page-de-connexion
```

✅ Vérifie que tu es bien sur **ta** branche avant de coder, pas sur `main`.

---

## 3. Coder et enregistrer (commit)

Un **commit**, c'est une sauvegarde de ton travail avec un petit message. Fais-en souvent : un commit par petite étape qui marche.

### 🖥️ GitHub Desktop
1. À gauche, coche les fichiers modifiés.
2. En bas à gauche, écris un résumé : `ajoute le formulaire de connexion`.
3. **Commit to feature/page-de-connexion**.

### 🧑‍💻 VS Code
1. Icône **Source Control** (la 3e à gauche, ou **Ctrl+Maj+G**).
2. **+** à côté des fichiers à inclure, écris le message, puis **✓ Commit**.

### Terminal
```bash
git add .
git commit -m "ajoute le formulaire de connexion"
```

> 💡 Les messages des commits intermédiaires sont libres. Seul le **titre de la PR** compte pour la version (voir [Conventional Commits](#conventional-commits-les-titres-de-pr)).

---

## 4. Envoyer sur GitHub (push)

Tant que tu n'as pas poussé, ton travail n'existe que sur ton PC.

- 🖥️ **GitHub Desktop** : bouton **Push origin** en haut.
- 🧑‍💻 **VS Code** : bouton **Sync Changes** (ou **⋯ → Push**).
- **Terminal** : `git push`

La **CI** se lance alors toute seule sur ta PR : elle vérifie que le code se construit et que les tests passent.

---

## 5. Demander la review

Quand ta tâche est finie et que la CI est verte :

- 📊 **Dashboard** : onglet **Pull requests** → ta PR → **Prête pour review**. L'autre est prévenu automatiquement et la carte passe dans « En review ».
- **github.com** : ouvre ta PR → **Ready for review**, puis colonne de droite → **Reviewers** → choisis l'autre.

Pense à remplir la description de la PR : ce que ça change et comment tester.

---

## 6. Reviewer le code de l'autre

L'onglet **Pull requests** du dashboard montre en haut ce que **tu** dois reviewer.

1. Ouvre la PR sur GitHub → onglet **Files changed** pour voir les modifications.
2. Clique sur le **+** à côté d'une ligne pour laisser un commentaire.
3. Termine avec **Review changes** :
   - **Approve** ✅ si c'est bon (ou le bouton **Approuver** du dashboard),
   - **Request changes** ✋ s'il faut corriger quelque chose,
   - **Comment** 💬 pour une simple question.

**Une bonne review :**
- reste gentille et précise : « ce cas plante si la liste est vide, non ? » plutôt que « c'est faux » ;
- pose des questions si tu ne comprends pas, ça compte aussi ;
- n'exige pas la perfection : est-ce que ça marche, et est-ce que c'est lisible ?

Si on te demande des modifications : corrige sur ta branche, commit, push. La PR se met à jour toute seule.

---

## 7. Merger

Quand la CI est verte ✅ **et** la PR approuvée 👍 :

- 📊 **Dashboard** : bouton **Merger**. Il reste grisé tant qu'il manque quelque chose, et le survoler indique quoi.
- **github.com** : bouton **Squash and merge** en bas de la PR.

Tous les commits de la branche deviennent **un seul commit** sur `main`, avec le titre de la PR. La branche est supprimée, l'issue est fermée et la carte du kanban passe dans « Fini ».

**Ensuite, reviens sur `main` et mets-la à jour** avant la tâche suivante :
- 🖥️ GitHub Desktop : **Current branch → main**, puis **Fetch origin → Pull origin**.
- 🧑‍💻 VS Code : nom de branche en bas à gauche → `main`, puis **Sync Changes**.
- Terminal : `git switch main && git pull`

---

## 8. Publier une version (release)

Quand plusieurs features sont mergées et que vous voulez « figer » une version :

1. 📊 Dashboard → **🏷 Nouvelle release** → choisis le projet.
2. Une minute plus tard, une PR **« chore(main): release 0.2.0 »** apparaît : elle contient la nouvelle version et le CHANGELOG.
3. Approuvez-la, puis **Merger**.
4. La release `v0.2.0` est publiée sur GitHub et visible dans l'onglet **Historique** du dashboard.

Sans dashboard : onglet **Actions** du repo → **Release** → **Run workflow**.

---

## Conventional Commits (les titres de PR)

Le titre de chaque PR commence par un **type**. C'est lui qui décide de la prochaine version :

| Titre de PR | Pour… | Effet sur la version |
| --- | --- | --- |
| `feat: ajoute la page profil` | une nouvelle fonctionnalité | 0.1.0 → **0.2.0** |
| `fix: corrige le crash au démarrage` | une correction de bug | 0.1.0 → **0.1.1** |
| `feat!: change le format des sauvegardes` | un changement qui casse l'existant | **1.0.0 → 2.0.0** (après la 1.0.0) |
| `docs: explique l'installation` | la documentation | pas de nouvelle version |
| `refactor: simplifie le calcul du score` | réorganiser du code sans changer le comportement | pas de nouvelle version |
| `test: ajoute les tests du panier` | les tests | pas de nouvelle version |
| `chore: met à jour les dépendances` | l'entretien | pas de nouvelle version |

On peut préciser une partie du projet entre parenthèses : `fix(api): …`, `feat(ui): …`.
Un titre mal formé met la CI au rouge, avec un exemple pour corriger. Modifie le titre de la PR et c'est reparti.

---

## Problèmes fréquents

<details>
<summary><b>La CI est rouge ❌</b></summary>

Dans la PR, clique sur **Details** à côté du check rouge pour lire l'erreur. Corrige sur ta branche, commit, push : la CI se relance toute seule.
Si c'est le check **« titre conventionnel »**, il suffit de modifier le titre de la PR (bouton **Edit** à côté du titre).
</details>

<details>
<summary><b>« This branch has conflicts » (conflit)</b></summary>

`main` a changé pendant que tu travaillais, et vous avez modifié les mêmes lignes.

- **github.com** : bouton **Resolve conflicts** dans la PR (pour les cas simples).
- 🖥️ **GitHub Desktop** : sur ta branche, **Branch → Update from main**, ouvre les fichiers en conflit, garde le bon code, puis commit et push.
- 🧑‍💻 **VS Code** : ouvre les fichiers marqués **!**, choisis *Accept Current / Incoming / Both*, puis commit et push.

Les marques `<<<<<<<`, `=======` et `>>>>>>>` délimitent les deux versions : il faut les supprimer.
</details>

<details>
<summary><b>J'ai codé sur <code>main</code> par erreur</b></summary>

Pas de panique, tant que tu n'as pas poussé :
- 🖥️ **GitHub Desktop** : **Current branch → New branch**. Desktop propose d'emmener tes changements (*Bring my changes*).
- **Terminal** : `git switch -c feature/mon-truc`. Tes modifications non commitées te suivent.

Si tu as déjà poussé sur `main`, préviens l'autre : le check « garde-fou main » sera rouge.
</details>

<details>
<summary><b>Le bouton « Merger » est grisé</b></summary>

Survole-le : le dashboard dit ce qui manque (CI pas verte, pas encore approuvée, encore en brouillon, conflit, titre non conforme…).
</details>

<details>
<summary><b>Mettre ma branche à jour avec main</b></summary>

- **github.com** : bouton **Update branch** dans la PR.
- 🖥️ GitHub Desktop : **Branch → Update from main**.
- Terminal : `git fetch && git merge origin/main`
</details>

---

## Lexique

| Mot | Ça veut dire |
| --- | --- |
| **Repo** | Le dossier du projet sur GitHub, avec tout son historique. |
| **Branche** | Une copie du code où l'on travaille sans toucher à `main`. |
| **Commit** | Une sauvegarde de modifications, avec un message. |
| **Push / Pull** | Envoyer ses commits sur GitHub / récupérer ceux des autres. |
| **PR (pull request)** | La demande pour ajouter une branche dans `main`. C'est là qu'on discute et qu'on review. |
| **Review** | La relecture du code de l'autre. |
| **Merge** | Ajouter les changements d'une PR dans `main`. |
| **CI** | Les vérifications automatiques (build, tests) lancées par GitHub Actions. |
| **Release** | Une version publiée (ex. `v0.2.0`), avec la liste des changements. |
| **SemVer** | La numérotation `MAJEUR.MINEUR.CORRECTIF` des versions. |
