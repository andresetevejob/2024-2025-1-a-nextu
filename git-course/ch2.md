# GIT

## Histoire
![Torvalds](/git-course/images/torvalds.png "Le titre de mon image")

Git a été crée par Linux Torvalds en 2005, c’est un programmeur finlandais et aussi le créateur du noyau linux.
La naissance de cette solution est partie d’un désaccord entre Linus Torvalds et la société BitKeeper qui à l’origine fournissait le système de contrôle de version utilisé pour le noyau Linux.

Les objectifs de Git :
* Vitesse
* Conception simple
* Distribué
* Capacité à gérer de grands projets
* Support pour les développements non linéaires (possibilité de créer plusieurs branches)


## Installation de git
https://git-scm.com/

## Configuration
Gestion de l'identité
```
 git config --global user.name "André Kouamé"
 git config --global user.email monadressetest@gmail.com
```
Voir la liste de ses paramètres
```
 git config --list
```
Voir un paramètre spécifique
```
git config user.name
```


## Mon premier Commit

Nous allons démarrer un projet de gestion des tâches.Pour ce faire créer sur votre disque (de préférence dans votre dossier de projet si vous en avez un) un dossier appélé todo-list.

NB :  Toutefois qu'on serez amener à saisir une commande ce sera par défaut dans le repertoire
todo-list via le terminal à défaut d'une indication contraire.

### Initialisation du dépôt git

* Rendez vous au sein du dossier précédemment crée via l'invite de commande et saisissez la commande ci-dessous 
```
git init
```
Cette commande permettra à git de créer un dossier .git dans dossier de projet, ce dossier est aussi appélé un dépôt git et contiendra l'historique de vos fichiers que vous souhaitez versionner.


### Indexation

Créer un nouveau fichier todo.txt et rajouter la liste de tâches ci-dessous :

* Faire les achats au supermarché
* Planifier un resto avec ses potes
* Deposer ses lettres à la poste

Ensuite faite la commande ci-dessous
```
git status
```
Que constatez-vous ?
Git rend votre fichier candidat à l'indexation

Créer un dossier config au sein de votre projet todo-list
 
puis refaite la commande : git status

Que constatez vous ?
Votre dossier nouvellement crée n'apparaît pas dans la liste des candidats à l'indexation. Git indexe les fichiers et non les repertoires

Indexer le fichier todo

Faites les commandes ci-dessous
```
git add todo.txt
git status 
```
Que constatez vous ? 
Git a indexé votre fichier, ce dernier est candidat pour un prochain commit

Désindexer un fichier

IL se peut que vous ayez indexé un fichier par erreur. Pas de panique faites la commande ci-dessous

```
git restore --staged fichier_indesirable
```
où fichier_indesirable est le nom du fichier à desindexer

Indexation multipe
Pour indexer plusieurs fichiers vous pouvez faire les commandes suivantes :
```
git add . ou git add *
```
La difference entre ces deux commandes est que la première indexe tous les fichiers contenu dans les sous repertoires y compris les fichiers cachés, ce qui n'est pas le cas pour la séconde qui n'enregistre qu'uniquement les fichiers non cachés.Aussi la séconde sert pour les indexations à partir de pattern

Exemple : je souhaite indexer tous les fichier .js
```
  git add *.js
```

### Commit

#### premier commit
Vous souhaitez sauvegarder le fichier précedemment indexé dans la base de données de git.
Vous devez faire la commande
```
git commit -m "Mon premier commit"
```
Git enregistre dans sa base votre fichier indexé cela s'appelle un commit

#### historique des commits
```
git log
```
Que constatez vous ?
Git vous afficher les informations relatifs à votre commit ainsi que son auteur, la date, etc ...

Afficher sur une seule ligne
```
git log --pretty=oneline
```

Formatter l'affichage 
```
git log --pretty=format:"%h - %an, %ar : %s"
```


Format d'affichage graph
```
git log --pretty=format:"%h %s" --graph
```

##### Modification d'un commit

Créer un nouveau fichier readme.md dans votre projet todo-list, ajouter le contenu suivant : # Mon projet todo. Indexer ce dernier et ensuite sauvegarder le au moyen d'un commit
```
git add readme.md
git commit -m "ajout de la documentation"
```

Créer un nouveau fichier contributing.md, ajoutez le contenu suivant : # Contribution .
Vous vous rendez compte que ce fichier récemment crée devait faire partir du même commit que le readme.
Pas de panique, faites les commandes ci-dessous:
```
git add contributing.md
git commit --amend
```
Que contastez vous ? Git donne la possibilité de rajouter le fichier nouvellement indexé au précédent commit

#### Mettre des fichiers en brouillons
Créer un nouveau fichier todo-stash.txt dans votre projet todo, rajouter y le contenu suivant : 
"Les tâches que souhaiteraient rajouter au fichier todo"
Vous voulez sauvegarder ce fichier comme un brouillon qui vous servira pour plus tard.
Faites les commandes suivantes
```
git stash -u -m "ma fiche brouillon"
git status
git stash list
```
Que constatez vous ?
Git a mis votre fichier todo-stash.txt dans une liste de fichier qui pourra être recuperer plus tard

#### Ignorez certains fichiers
Vous souhaitez que certains de vos fichiers ne soient pas indexables par git.Généralement ce sont des fichiers de configuration personnel de votre projet que vous ne souhaitez pas partagez avec l'équipe.

Pour ce faire, vous devez créer un fichier .gitignore dans votre repertoire de et lister les fichiers que vous souhaitez ne pas indexer

NB : si un fichier a déja été sauvergarder au moyen d'un commit, et que voulez le rajouter plus tard dans un .gitignore, il faudrait supprimer ce dernier de la base de git via la commande
git rm --cached nom_fichier et après le rajouter dans le .gitignore