
Lorsque nous souhaitons utiliser un package composer que nous développons activement et que nous utilisons dans un projet, nous n'avons pas envie d'appliquer les changements du package en passant par les étapes de commit, de push et d'update du package. Cela introduit trop de commits intermédiaires et donc du bruit dans l'historique du projet. De plus, cela est chronophage est energivore pour rien.

Ce guide explique les étapes à suivre pour gérer les packages composer en développement dans un projet.

## Installation du package sur la machine

Tout d'abord, il faut installer le package en local, sur sa machine. Le mieux est de créer un dossier dédié aux packages `packages`, dans le dossier où vous installez tous vos projets.

Dans mon exemple, cela donne cela:

```
sites/
├─ packages/
│  ├─ package_1
│  ├─ package_2
├─ site_1/
│  ├─ favicon.ico
│  ├─ index.html
│  ├─ robots.txt
├─ site_2/
│  ├─ index.css
│  ├─ index.js
```

## Installation du package dans le projet
### Lien symbolique

Pour permettre à composer l'accès aux packages; à la fois à composer, qui est dans Lando, et à la fois à notre éditeur, pour l'autocomplétion; nous devons créer un lien symbolique entre le dossier contenant les packages en local et notre projet.

```bash
ln -sf /path/to/your/packages /path/to/your/project/packages
```

Ce lien symbolique doit être ignoré afin de ne pas apparaître dans le repo.
Ajoutez le dans le gitignore comme si c'était un fichier.


## Définition de l'emplacement du package dans le `composer.json`

Nous allons maintenant dire à composer où aller chercher notre package. Pour cela, ajoutez deux entrées dans votre `composer.json`  dans l'entrée `repositories`. La première correspond à la localisation du package en local. La seconde à la localisation du repository distant de votre package. En effet, composer recherche le package dans chaque emplacement, dans l'ordre déclaration dans le `composer.json`. Si il n'est pas présent dans le premier emplacement, il regarde dans le suivant. Cela évitera les erreurs lors du déploiement et évitera aux nouveaux développeur d'installer les packages en local pour commencer à travailler. [Plus d'infos disponibles dans la doc de composer.](https://getcomposer.org/doc/articles/repository-priorities.md) 
```json
"repositories": {  
    "packageLocal": {  
        "type": "path",  
        "url": "./packages/package_1",  
        "options": {  
            "symlink": true  
        }  
    },  
    "packageRepository": {  
        "type": "vcs",  
        "url": "git@github.com:akki-team/package_1"  
    },
},
```

### Final touch

Si vous aviez déjà installé le package depuis un repo distant, alors un coup de ```

```bash
composer update {nom-du-package}:@dev
```

fera le lien entre le projet et le package. Ainsi, à chaque changement dans le package, vous pourrez en profiter tout de suite dans votre projet.
Si vous n'avez pas déjà installé le package, alors la commande est
```bash
composer require {nom-du-package}:@dev
```

### Attention

Bien penser à faire des package avec des numéros de version une fois que vous voulez déployer le changement en prod. Autrement, vous risquez d'introduire des *breaking-changes* dans vos projets.