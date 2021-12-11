# Débuter sur Git et Github

## Commandes sur le terminal Git

apt = npm
apt install "nomlogiciel"
'pour forcer' => sudo apt install "nomdulogiciel"

cat  / interroge
cd "nomdossier" / permet de rentrer dans un dossier
cd . 
cd .. / permet de revenir au dossier au-dessus

ls  / liste les documents présents<br>
ls l -a / liste les fichiers cachés<br>
ls -la  / liste les fichiers cachés<br>
ls -lh  / voir la liste des dossiers sans fichiers cachés<br>
la  / voir tout

mkdir / creer un dossier "make directory"

rm -rf nomdossier  / efface le dossier

touch "nomfichier"  / cree un fichier
<br>

<b>S'employe avec "git" en début de commande :</b>

git add .  / ajoute tout ce qui est au niveau de la branche où on se trouve<br>
git add "nomdossier"  / ajoute le dossier sur la branche où on se trouve

git branch -a  / liste toutes les branches

git branch -M main  / transforme la branche de master en main

git branch en alias devient...<br>
$ git config --global alias.br = git br

git commit -a  / permet de valider<br>
git commit -m "commentaire"  / valide plus commentaire de la modification apportée<br>
/ exemple pour visualiser le dernier commit<br>
en plus simple<br>
$ git last

git init  / initialise

git pull  / importe ou met à jour<br>
git pull upstream main  / importe un dossier sur notre branche principale

git push  / pousse le dossier ou met à jour<br>
git push -u origin

git remote -v  / verbose  concerne notre dossier<br>
git rm "nomfichier"  / supprime un fichier du dossier

gs  / git status (alias)<br>
git status  / met à jour et permet de voir les dossiers modifiés

git visual / alias gitk<br>
/ exemple $ git config --global alias.visual "!g


-------------------------



## Création d'alias de commandes

Une fois acquis les commandes et compris les actions,
on peut commencer à créer des alias pour simplifier 
l'écriture.
Lire ce post :
[1] https://git-scm.com/book/fr/v2/Les-bases-de-Git-Les-alias-Git

Pour exemple :

ajouter : $ git config --global alias."motàaliaser"<br>
cela donnera le raccourci git "2lettres" = gs / git status

-------------------------



# Memo des actions

La routine Git sur notre terminal



## creer un dossier

mkdir nomdudossier<br>
cd nomdudossier<br>
git init

tu as un dossier vide


## supprimer un dossier

action à réaliser si on ne souhaite pas 
conserver tout le contenu d'un dossier
ou supprimer un dossier vide 

rmdir nomdudossier

sinon on peut supprimer un sous-dossier (dit enfant) 
dans le dossier principal (considéré comme "parent")

rmdir/nomdossierparent/nomdossieràsupprimer

autre solution : pour supprimer tous les chemins liés à un dossier

rm -v nomduchemin/nomduchemin


## creer un fichier

touch test.txt<br>
git add test.txt<br>
git commit -m test.txt

on a cree le document mais sans le mettre dans un dossier


## ajouter un document
en exemple un document nommé index.html

git add index.html<br>
git commit -m index.html<br>
git pull origin


## supprimer un fichier du dossier

git rm nomdufichier<br>
git commit -m "commentaire"<br>
git push


## verifier si le doc est bon
action à réaliser par exemple après un add .
ou avant un commit -m

git status


## créer une branche

### Deux lignes: créer et basculer sur la nouvelle branch

git branch nombranchnouvelle<br>
git checkout nombranchnouvelle

### Une seule ligne: créer et basculer

git checkout -b nombranchnouvelle


## effacer une branche

### Si la branch est local et n'est pas créée sur le repo distant

git branch -d nombranchlocale

### Si la branch est présente sur le repo distant

git push origin --delete nombranchdistante

-------------------------

## fusionner une branche

un article détaillé :
[2] https://www.pierre-giraud.com/git-github-apprendre-cours/fusion-rebasage-git/#:~:text=Pour%20fusionner%20nos%20deux%20branches%2C%20on%20va%20se,master%20au%20niveau%20du%20commit%20point%C3%A9%20par%20test.

### fusionner d'après une base

on se positionne sur la base de la branche que l'on souhaite fusionner<br>
on se positionne sur la branche "main aussi appelée master sur certaines versions" et on fusionne avec une branche dite test

git checkout<br>
git merge nombranchmain/nombranchtest

ensuite on efface la branche test

git branch -d

-------------------------

## fusionner deux branches avec un historique divergent

git merge

git crée un "instantané" avec les deux contenus en se basant sur le dernier commit
du dossier de base et du dernier commit des dossiers que l'on veut fusionner
et git émet ensuite un commit relatif aux 3 sources (donc plusieurs parents) : ce commit
a pour nom "commit de fusion"

si il y a conflit sur l'une des branches, il faudra le résoudre à part avant de retenter la fusion
pour identifier le problème faire : git status

une fois cela réalisé :

git add<br>
git commit

ce commit termine le commit dit de fusion

-------------------------

## changer de branche

git checkout nombranche

GIT --version 2.23
git switch nombranche

-------------------------


# Les actions git/github

## faire la daily

il faut upstream le document du formateur depuis son github
vers notre terminal : il faut créer un dossier en local pour 
déposer les fichiers importés

on récupére donc son lien en cliquant sur le haut du dossier 
sur un picto représentant deux carrés superposés

git remote add upstream https://github.com/Simplon-hdf/daily-objectives-devinte-lil3.git <br>
git remote -v

on l'importe sur notre local

git pull upstream main<br>
git add .<br>
git commit -m "commentaire"<br>
git push

-------------------------

## Récuperer un doc en local

pour une mise à jour (l'action de récupérer le dossier
ayant déjà été faite auparavant)

git clone https://leliendesondossier.git <br>
ls

on ouvre le dossier pour le dailyobjective
et va déposer sur notre dossier créé pour le daily

cd dailyobjective...lil3<br>
git init<br>
git remove -v<br>
remote remove origin<br>
remote add origin git@github.com:votrenomsurubuntu/nomdudossierlocal.git<br>
git remote -v

je depose en local

git branch -M main<br>
git push -u origin main<br>
code .


## envoyer un document vers un dossier sur github

cd nomdossier<br>
ls (si vous avez besoin de voir le nom exact du dossier)

git init<br>
cela permet de mettre le document ou dossier en .git

git add .<br>
si vous voulez pointer un document précis :<br>
git reset HEAD nomdossier

git commit -m nomdossier

creer le dossier sur github (il editera un .git)<br>
et recuperer le lien, en ssh c'est mieux

git remote add origin liendudossiergithub(en ssh)<br>
git remote -v<br>
git push origin main

____________
<br>
