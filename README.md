# TP1 - Maîtrise de Git

## Objectifs
- Se familiariser avec Git, un système de gestion de version décentralisé.
- Apprendre à gérer des projets, collaborer avec d'autres développeurs et utiliser les fonctionnalités avancées de Git.

## Partie 1 : Préparation de l'environnement Git

### 1. Création de clé SSH
Générez une clé SSH pour une connexion sécurisée aux dépôts distants.

bash
ssh-keygen -t rsa -b 4096 -C votreadresse@email.com
Ensuite, copiez la clé publique générée :

bash
cat ~/.ssh/id_rsa.pub
Ajoutez cette clé publique dans les paramètres SSH de votre compte GitHub ou GitLab.

2. Configuration de Git
Configurez votre nom d'utilisateur et votre adresse email pour identifier vos commits.

bash
git config --global user.name "Votre Nom"
git config --global user.email "votreadresse@email.com"
3. Tester la connexion SSH
Vérifiez votre connexion avec le dépôt distant.

bash
ssh -T git@github.com
ou

bash
ssh -T git@gitlab.com
4. Vérifier la configuration Git actuelle
Pour afficher les informations de configuration actuelles de Git, utilisez :

bash
git config --list
5. Modifier votre adresse email
Si vous avez mal configuré votre email, modifiez-le ainsi :

bash
git config --global user.email "nouveau@email.com"
Partie 2 : Création d'un nouveau projet
1. Création d'un nouveau dépôt sur GitHub/GitLab
Connectez-vous à GitHub ou GitLab et créez un nouveau dépôt. Copiez l'URL SSH du projet.

2. Cloner un dépôt
Clonez le dépôt sur votre machine locale.

bash
git clone git@github.com:votre-nom-utilisateur/mon-projet.git
Accédez ensuite au répertoire du projet :

bash
cd mon-projet
3. Ajouter un fichier README
Si vous avez oublié de créer un fichier README lors de l'initialisation, vous pouvez l'ajouter ainsi :

bash
touch README.md
echo "# Mon Projet" > README.md
git add README.md
git commit -m "Ajout du fichier README.md"
git push origin master
4. Définir un dépôt distant
Si un dépôt distant n'a pas été configuré, vous pouvez l'ajouter ainsi :

bash
git remote add origin git@github.com:votre-nom-utilisateur/mon-projet.git
Partie 3 : Concepts de base de Git
1. Travailler avec les fichiers
Créez un fichier index.html dans votre projet et ajoutez-y du contenu :

bash
touch index.html
echo "Contenu de votre fichier" > index.html
git add index.html
git commit -m "Premier commit : ajout de index.html"
2. Historique des commits
Pour afficher l'historique des commits :

bash

git log
3. Annuler les modifications locales
Pour annuler des modifications locales avant qu'elles ne soient ajoutées à l'index :

bash

git checkout -- <fichier>
4. Visualiser les fichiers en staging
Pour visualiser les fichiers prêts à être commités :

bash

git status
Partie 4 : Collaborer sur Git
1. Créer une branche
Créez une nouvelle branche pour développer une fonctionnalité spécifique :

bash

git branch ma-fonctionnalite
git checkout ma-fonctionnalite
2. Ajouter et pousser des modifications
Ajoutez vos modifications, puis poussez-les vers le dépôt distant :

bash

git add .
git commit -m "Modification de ma-fonctionnalite"
git push origin ma-fonctionnalite
3. Gestion des conflits
Simulez et résolvez un conflit lors de la fusion de deux branches :

bash

git merge ma-fonctionnalite
Partie 5 : Rebase d'une branche sur master
1. Rebaser une branche
Pour rebaser une branche sur master, suivez ces étapes :

bash

git checkout master
git pull origin master
git checkout ma-fonctionnalite
git rebase master
Si des conflits apparaissent, résolvez-les, puis continuez le rebase :

bash

git add <fichier_conflit>
git rebase --continue
Partie 6 : Utilisation de GitFlow
1. Initialiser GitFlow
Initialisez GitFlow dans votre dépôt :

bash

git flow init
2. Travailler sur une nouvelle fonctionnalité
Créez une nouvelle fonctionnalité :

bash

git flow feature start ma-fonctionnalite
Finalisez la fonctionnalité :

bash

git flow feature finish ma-fonctionnalite
git push origin --tags
3. Créer et finaliser un correctif
Pour un correctif, suivez :

bash

git flow hotfix start mon-correctif
git flow hotfix finish mon-correctif
git push origin --tags
