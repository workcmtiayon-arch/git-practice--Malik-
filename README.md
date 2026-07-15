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
