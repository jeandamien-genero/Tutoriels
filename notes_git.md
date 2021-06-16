# Git

## Config

  * Configuration globale à partir d'un username ou d'un email :
```Git

git config --global user.name "username"

git config --global user.email email
```

## Branches
  * Créer une branche : ```git branch <nom de la branche]```

  * Aller dans une branche : ```git chekout <nom de la branche>```

  * Vérifier la branche où l'on se trouve : ```git branch```

  * Mettre la branche en ligne : ```git push --set-upstream origin <nom de la branche>```

  * Fusionner deux branches (ici, fusionner ```dev``` dans ```master```) :
  ```Git
  git checkout master
  git branch
  git merge dev
  git status
  git push
```

  * Rappatrier une branche en local :
  ```Git
  git fetch origin <nom de la branche>
  git checkout --track origin/<nom de la branche>
  ```

  * Supprimer une ancienne branche en local (ici, ```dev```) :
  ```Git
  git branch -d dev
  git status
  ```

  * Supprimer une ancienne branche GitHub distante (ici, ```dev```) :
  ```Git
  git push origin --delete dev
  git status
  ```

## Déplacer des fichiers à l'intérieur d'un dépôt
```Git
git mv <chemin vers le fichier à déplacer> <chemin vers le nouveau dossier à l'intérieur du même dépôt>
git commit -m 'rename <ancien chemin/nom du fichier]> >> <nouveau chemin/nom du fichier>'
[git status]
git push
```

## Commits

  * Annuler un `git add` :
```Git
git restore <fichier>
```

  * Ne pas déclarer de modification :
```Git
git commit -m --no-edit
```

  * Modifier le message de commit :
```Git
git commit --amend -m "<nouveau message>"
```
