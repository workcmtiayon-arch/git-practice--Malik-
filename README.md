### PARTIE 1 : Depot local : Comprendre le suivi de versions
# Git Practice :
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