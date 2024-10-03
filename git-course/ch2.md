# GIT

## Histoire
![Architecture](/git-course/images/torvalds.png "Le titre de mon image")

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
