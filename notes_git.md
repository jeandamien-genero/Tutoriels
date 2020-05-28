# Git

## Config

  * Configuration globale à partir d'un username ou d'un email :
```Git

git config --global user.name "username"

git config --global user.email email
```

## Branches
  * Créer une branche : ```git branch [nom de la branche]```

  * Aller dans une branche : ```git chekout [nom de la branche]```

  * Vérifier la branche où l'on se trouve : ```git branch```

  * Mettre la branche en ligne : ```git push --set-upstream origin [nom de la branche]```

  * Fusionner deux branches (ici, fusionner ```dev``` dans ```master```) :
  ```Git
  git checkout master
  [git branch]
  git merge dev
  [git status]
  git push
```

  * Supprimer une ancienne branche en local (ici, ```dev```) :
  ```Git
  git branch -d dev
  [git status]
  ```

  * Supprimer une ancienne branche GitHub distante (ici, ```dev```) :
  ```Git
  git push origin --delete dev
  [git status]
  ```

## Déplacer des fichiers à l'intérieur d'un dépôt
```Git
git mv [chemin vers le fichier à déplacer] [chemin vers le nouveau dossier à l'intérieur du même dépôt]
git commit -m 'rename [ancien chemin/nom du fichier] >> [nouveau chemin/nom du fichier]'
[git status]
git push
```

## Commits

  * Ne pas déclarer de modification :
```Git
git commit -m --no-edit
```