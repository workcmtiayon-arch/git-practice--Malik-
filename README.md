### PARTIE 1 : Depot local : Comprendre le suivi de versions
# Git Practice - version A et version B :
(Message genere par la commande : echo "# Git Practice" > README.md qui a efface le contenu de ce que j'avais deja ecris... heureusement qu'il y a CTRL + Z)

## Etape 1.1 : Initialiser un depot Local

# Q : Que fait git init ?
R : La commande git init initialise un depot Git local dans le repertoire courant

# Que se passe-t-il dans le dossier apres cette commande ?
R : Lorsqu'on execute la commade git init, Git cree un sous dossier cache nomme .git a la racine du projet.... Ce dossier est le coeur des gestions de version. 

# Commande pour voir les fichier caches :
tiayon@tiayon-Latitude-5420:~/git-practice-malik$ ls -a

# Resultat :
.  ..  .git  README.md

# Commande pour voir le contenu du fichier cache .git :
ls -F

# Resultat :
branches/  config  description  HEAD  hooks/  info/  objects/  refs/

Concretement :
- Il contient l'historique
- Il gere la configuration
- Il structure le projet
- Il stocke le contenu




## ETape 1.2 : Creer un fichier et observer le statut

# Q : Pourquoi README.md est un fichier "Non suivi" (untracked) ?

R : A notre stade present, (QUnd la commande git init viens juste de creer le depot vide) bien que le fichier bien que le fichier existe dans le dossier de travail, il reste inajoute a l'index de Git tant qu'on execute pas la commande git add.

Git le traite comme un element qu'il n'enregistre pas dans son historique de versions



## Etape 1.3 : Zone de Stanging (add) puis commit

# Q : QUelle est la difference entre git add et git commit ?
R : git add prepare le modifications et ajouts alors que git commit les enregistre definitivement

# Q : Pourquoi Git separe-til ces deux etapes (add puis commit) au lieu de tout enregistrer directement ?
R : 
- Le staging (git add) sert de salle de preparation... Il perment de selectionner les fichiers et lignes de codes qui doivent etre inclus dans la prochaine version
- Le commit valide cette selection et cree une photo de l'etat du code dans l'historique

# ==> Cette separation ermet donc e faire des commits propres, thematiques et organises


## Etape 1.4 : Historique et differences

# Q : A quoi sert Git log ?
R : A afficher la liste de tous les commits valides dans le depot, avec leur identifiant unique, l'auteur, la date et le message associe

# Q : Que montre git diff  avant un commit ?
R : Il afiiche les modifications exactes lignes par ligne (ajouts en vert et supp en rouge) qui on ete faites dans les fichiers mais qui n'ont pas encore ete ajoutes a la zone de staging (git add)

### PARTIE 2 : Depot distant : Comprendre local vs Distant

## Etape 2.1 : Gree le depot sur GitHUb et le relier

# Q : Quelle est la difference entre un depot local et un depot distant (remote) ?
R : 
- Le Depot local reside uniquement sur le disque de la machine a laquelle seule l'utilisateur proprietaire a acces
- Le depot distant est heberge sur un serveur en ligne (Comme Github) et sert de sauvegarde centrale et permet de collaborer avec d'autres developpeurs.

# Q : QUe fait concretement git push ?
R : Il transfere les commits locaux et l'historique des branches depuis la machine vers le serveur dstant (GitHub)

# Q : Que se passerait-il si vous perdiez votre ordinateur avant d'avoir fait ce push ?
R : Tout le travail et historique de versions seraient definitivement perdus. Le push sert de sauvegarde de securite externe.


## Etape 2.2 : Ignorer certains fichiers

# Q : Pourquoi ne faut-il jamais versionner un fichier .env ou un dossier node_modules ?
R : 
- Le fichier .env contient des donnees sensibles et secretes (cles d'API, mdp de bd). S'il est pousse sur GitHub, n'importe qui pourra voler les acces.
- Le dossier node_modules est extremement lourd, contient des milliers de dependances et peut etre retelecharge instantanement avec la commande "pnpm install" ou "npm install"

# Q : Que se passe-t-il si on les commit quand meme ?
R : Le dossier devient unitilement lour et il y a aussi le risque d'exposer publiquement les clefs secretes aux robots malveillants.
<<<<<<< HEAD
=======


### Partie 3 : Branches : Comprendre le travail isole

## Etape 3.1 : Creer une branche de travail

# Q : Pourquoi ne travaille-t-on pas directment sur main ?
R : Pour eviter de casser le code stable qui fonctionne deja en production et permettre a plusieurs developpeurs de travailler en meme temps sans se bloquer

# Q : Que represente une branche par rapport au depot princial ? 
R : Elle represente une ligne de developpement parallele isolee. C'est une copie virtuelle de l'etat du code a un instant T pour faire des tests en securite

## Etape 3.2 : Modifier, commiter et pousser la branche

# Q : Que remarquez-vous sur GitHub ares ce push (dans la liste de branches) ?
R : Une nouvelle branhe nommee feature/about-page apparaitb dans le menu deroulant des branches. GitHUb affiche une baniere jaune proposant de creer un Pull Request pour cette branche.

# Q : La branche main a-t-elle changee ?
R : Non la branche main reste identique et n'integre pas encore les modifications du fichier about.html


#### Partie 4 – Pull Request : comprendre la revue de code

## Étape 4.1 : Ouvrir une Pull Request

# Q : À quoi sert une Pull Request si on peut techniquement pousser directement sur main ?
R : Elle permet de soumettre les modifications aux autres membres pour relecture et discussion avant de fusionner... C'est un espace essentiel pour s'assurer de la qualite du code (revue du code)

# Q : Dans une equipe qui devrait valider une PR avant de fusionner ?
R : La validation par au moins un autre developpeur de l'equique

## Étape 4.2 : Fusionner la Pull Request

# Q : Pourquoi faut-il faire un git pull sur main ares avoir merge la PR sur GitHub, alors que le merge a deja eu lieu sur GitHub ?
R : La fusion a eu lieu uniquement sur les serveurs distants de GitHub....  Le depot local sur la machine n'est pas au courant de cette modification... De ce fait la commande "git pull"est indispensable pour recuperer l'historique mis a jour et synchroniser le  dossier de travail local

#### Partie 5 : Conflit de fusion (merge conflict)

## Étape 5.1 : Créer un conflit volontairement

## Étape 5.2 : Résoudre le conflit en local

# Q : Pourquoi ce conflit s'est-il produit ?

R : Le conflit s'est produit parce que les branches branch-a et branch-b ont modifié différemment la même ligne du fichier README.md. Lors de la fusion, Git n'a pas pu déterminer automatiquement quelle version conserver. Il a donc interrompu la fusion et demandé une intervention manuelle.

# Q : Que représentent exactement <<<<<<<, ======= et >>>>>>> ?

R : Ce sont des marqueurs de conflit ajoutés temporairement par Git.

- <<<<<<< HEAD marque le début du conflit et indique le contenu de la branche actuelle (HEAD).
- ======= sépare les deux versions en conflit.
- >>>>>>> branch-a marque la fin du conflit et indique que la seconde version provient de la branche branch-a.

Ces marqueurs doivent être supprimes apres avoir choisi ou combine le contenu souhaite.

# Q : Comment aurait-on pu éviter ce conflit en amont ?

R : On peut réduire les risques de conflit en synchronisant régulièrement sa branche avec main, en communiquant avec les autres développeurs pour éviter de modifier les mêmes parties d'un fichier en même temps, et en réalisant des fusions fréquentes plutôt que d'attendre longtemps avant de fusionner


#### Partie 6 – Collaboration : Fork et contribution externe

## Étape 6.1 : Fork et clone

# Q : Quelle est la différence entre un Fork et un Clone ?
R :

# Q : Pourquoi ce fork est-il nécessaire quand on n'a pas les droits d'écriture sur le dépôt d'origine ?
R :

## Étape 6.2 : Contribuer via Pull Request

# Q : Dans ce modèle de contribution par Fork + Pull Request, qui garde le contrôle final sur le dépôt d'origine ?
R :

# Q : Pourquoi ne pas donner directement les droits d'écriture à tout le monde ?
R :


#### Partie 7 – Issues : suivre les tâches et les problèmes

## Étape 7.1 : Créer une Issue

# Q : À quoi sert une Issue par rapport à un simple message Git ?
R :

## Étape 7.2 : Lier une Pull Request à l'Issue

# Q : À quoi sert une Issue par rapport à un Pull Request ?
R :

# Q : En automatisant la fermeture d'une Issue avec une Pull Request, qu'est-ce que cela apporte ?
R :


#### Partie 8 (bonus) – Versionner et annuler

## Étape 8.1 : Créer un tag de version

# Q : À quoi sert un tag Git ?
R :

# Q : Pourquoi utiliser une version numérotée (v1.0.0) plutôt qu'un simple commit ?
R :

## Étape 8.2 : Comprendre revert vs reset

# Q : Quelle est la différence fondamentale entre git revert et git reset --hard ?
R :

# Q : Lequel est préférable lorsqu'une branche est déjà partagée avec l'équipe et pourquoi ?
R :
>>>>>>> branch-a
