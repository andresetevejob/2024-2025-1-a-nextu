# SYSTEME DE CONTRÔLE DE VERSION

## Sommaire
[Avant les systèmes de contrôle de version](#i---avant-les-systèmes-de-contrôle-de-version)

## Système de contrôle de version

### I - Avant les systèmes de contrôle de version

* IL fallait enregistrer son projet avec un nom comportant la version du projet
* Le travail collaboratif était compliqué car, il fallait récupérer le travail de ses collègues par plusieurs moyens, par exemple via une clé usb, et faire l’intégration du code sur une machine
* IL était difficile de savoir qui avait effectué une modification et pourquoi

### II - Système de version de contrôle

C’est un outil de travail collaboratif sur un projet informatique, il permet :
* Suivre la modification apporter à un code source
* Afficher l’historique des modifications d’un fichier ainsi que les raisons et l’auteur (il peut avoir du credit ou être blâmé parfois :)
* Restaurer le code source à partir d’une version antérieur, si une erreur survient dans la version courante

#### A - Les différents types de systèmes de contrôle de version

##### 1 - Local

![Torvalds](/git-course/images/ordinateur-local.png "Le titre de mon image")
Ce sont des logiciels qui permettent de suivre l’evolution des modifications d’un fichier mais au niveau local.IL ne permettent pas un travail collaboratif.

##### 2 - Centralisé
![Torvalds](/git-course/images/centralized-cvs.png "Le titre de mon image")

Le type centralisé permet : 

* Un travail collaboratif
* Un administrateur peut attribuer des permissions sur le projet aux utilisateurs
* Un utilisateur peut voire les modifications apporter par un autre

Cependant en cas de panne du serveur principal et sans sauvegarde du disque de ce dernier tout l'historique du projet est perdu
IL ne restera que les copies stockées localement par chaque utilisateur qui ne reflètent pas tous l'historique du projet
Aussi lorsque la connexion avec le serveur est coupé, les utilisateurs ne pourront enregister que localement leurs fichiers et ces derniers ne seront pas versionnés

##### 3 - Distribué
![Torvalds](/git-course/images/distributed-cvs.png "Le titre de mon image")

Dans le type distribué, les clients ne possèdent pas une version du fichier mais l'historique complet du projet en cas de panne du serveur, une copie d'un projet client peut être restaurer sur le serveur