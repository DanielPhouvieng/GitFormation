# GIT : Comment l'utiliser?

## <span style="color:royalblue">**Qu'est-ce git?**</span>

Git est un système de contrôle de version. 

C'est un outil de développement qui aide une équipe de développeurs ou autre à gérer les changements apportés au code source/documents autres au fil du temps.

## <span style="color:royalblue">**A quoi sert github ou gitlab?**</span>

Ce sont des logiciels/site web libre de forge basé sur le logiciel git proposant :
- des fonctionnalités de wiki,
- un système de suivi des bugs,
- intégration,
- livraison continue.

## <span style="color:royalblue">**Commandes git / Methodes de travail**</span>
![plot](./git_schema)

### <span style="color:deepskyblue">*Commandes d'initialisation*</span>

- <span style="color:cornflowerblue">*git init*</span> :                                                 initialise le dossier en question en dépôt Git
- <span style="color:cornflowerblue">*git clone* <url_repo>l*</span> :                                   clone le repo distant dans un repo local (là où est lancé la commande git)
- <span style="color:cornflowerblue">*git switch -c "nom de la branche"*</span> :                        permet de créer une nouvelle branche à partir de la branche où est lancé la commande
- <span style="color:cornflowerblue">*git switch "nom de la branche"*</span> :                           permet de changer vers la branche "nom de la branche"

### <span style="color:deepskyblue">*Commandes utilitaire*</span>

- <span style="color:cornflowerblue">*git status*</span> :                                               permet d'avoir le statut du dépôt Git dans laquelle on est
- <span style="color:cornflowerblue">*git log*</span> :                                                  permet d'afficher les logs du projet git => liste des commit, et diffs sur les diverses branches
  
     petite commande git qui affiche un historique assez sympathique : git log --graph --date=relative --pretty=tformat:'%Cred%h%Creset -%C(auto)%d%Creset %s %Cgreen(%an %ad)%Creset' --all
- <span style="color:cornflowerblue">*git branch -a*</span> :                                            permet d'afficher la liste des branches locales et en remote
- <span style="color:cornflowerblue">*git branch -l*</span> :                                            permet d'afficher la liste des branches locales 
- <span style="color:cornflowerblue">*git branch -r*</span> :                                            permet d'afficher la liste des branches remotes
- <span style="color:cornflowerblue">*git branch -vva*</span> :                                          permet d'afhicer les branch avec des détails tels que des commits id

### <span style="color:deepskyblue">*Commandes de modifications du dépôt:*</span>

- <span style="color:cornflowerblue">*git pull*</span> :                                                 rapatrie les modifications distantes dans la branche actuelle (git pull --rebase fait un gir rebase au lieu d'un merge)
- <span style="color:cornflowerblue">*git fetch*</span> :                                                permet de récupérer l'historique du dépôt sans modifier la branche locale
- <span style="color:cornflowerblue">*git push*</span> :                                                 permet de mettre à jour les modifications locales dans la distante
- <span style="color:cornflowerblue">*git rebase<branch to rebase with> <branch to be rebased>*</span> : mets des commits au top d'une autre base id
![plot](./git_rebase.png)
- <span style="color:cornflowerblue">*git cherry-pick*</span> :                                          applique des changement introduits dans des commits déjà existants

### <span style="color:deepskyblue">*Commandes pour mettre les modifications de code sur le distant:*</span>

- <span style="color:cornflowerblue">*git add <fichier>*</span> :                                       ajoute le contenu de fichiers à l'index en cours
- <span style="color:cornflowerblue">*git commit -m <message du commit>*</span> :                       enregistre les modifications dans le dépôt local
- <span style="color:cornflowerblue">*git checkout <nom du fichier>*</span> :                           enlever les commits et modifications du fichier en question


## <span style="color:royalblue">**Process Git + commandes:**</span>

> Un projet de base est obligatoirement constitué de 2 branches de références:
1. *master* : branche de références pour les livraisons + tag, branche de départ pour les hotfix sur des livraisons ou mise en prod
2. *main* : branche de référence de travail pour le projet

> En cas de modification de code, il faut partir d'une branche de référence et créer une nouvelle branche afin de pouvoir y travailler dessus.
1. Se placer sur la branche de référence : <span style="color:cornflowerblue">*git checkout -b main*</span>
2. faire un git fetch pour mettre à jour l'historique du dépôt de la branche de référence et faire un git pull si nécessaire
3. Créer une nouvelle branche : <span style="color:cornflowerblue">*git checkout -b <nom de la nouvelle branche>*</span>
4. Faire les modifications de code ou de documents
5. Tester votre code, voir s'il n'y a pas eu de régression.
5.  : ajoute le fichier modifié à commit, possible de faire plusieurs ajouts avant un commit
6. <span style="color:cornflowerblue">*Git commit -m <message du commit>*</span> : enregistre les modifications du fichier dans le dépôt local
7. <span style="color:cornflowerblue">*Git push *</span>: mettre à jour le local avec le distant

> Si vous voulez merge votre code dans la branche de référence.
1. Aller sur la branche de référence : <span style="color:cornflowerblue">*git checkout main*</span>
2. Mettre à jour la branche: <span style="color:cornflowerblue">*git fetch*</span>  <span style="color:cornflowerblue">*git pull*</span>
3. Aller sur la branche de travail et faire un rebase : <span style="color:cornflowerblue">*git rebase main*</span>
4. Corriger les conflits si nécessaire.
5. Tester la branche rebasée et voir s'il n'y a pas eu de régression
6. Aller sur la branche de référence, et merger : <span style="color:cornflowerblue">*git merge <branche de travail>*</span> 

## <span style="color:royalblue">**Process GitLab Github:**</span>

> Tagguer chaque livraisons ou version logicielles importantes 

> Créer des tickets ou tickets chapeau pour chaque tâche de développement

Un ticket chapeau est une macro tâche pouvant être divisées en plusieurs plus petites tâches.
Chaque ticket doit comporter :
- le statut d'avancement de la tâche
- la description de la tâche
- le moyen pour réaliser la tâches
- la description du résultat de la tâche
> Nommer les commit et/ou les branches en fonction des numéro ou titre de tickets créés

> Ne jamais travailler sur une même branche à plusieurs hormis les branches de références : le process ci-dessus permet de limiter les problèmes
