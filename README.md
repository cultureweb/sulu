<br/>
<p align="center">
    <a href="https://sulu.io/" target="_blank">
        <img width="50%" src="https://sulu.io/website/images/sulu.svg" alt="Sulu logo">
    </a>
</p>

<br/>
<p align="center">
    <a href="LICENSE" target="_blank">
        <img src="https://img.shields.io/github/license/sulu/skeleton.svg" alt="GitHub license">
    </a>
    <a href="https://github.com/sulu/skeleton/releases" target="_blank">
        <img src="https://img.shields.io/github/tag/sulu/skeleton.svg" alt="GitHub tag (latest SemVer)">
    </a>
    <a href="https://github.com/sulu/skeleton/actions" target="_blank">
        <img src="https://img.shields.io/github/workflow/status/sulu/skeleton/Test%20application.svg?label=test-workflow" alt="Test workflow status">
    </a>
</p>
<br/>

[Sulu](https://sulu.io/) is a highly extensible open-source **PHP content management system based** on the [Symfony](https://symfony.com/) framework. Sulu is developed to deliver robust **multi-lingual and multi-portal websites** while providing an **intuitive and extensible administration interface** to manage the full content lifecycle. 

Have a look at the official [Sulu website](https://sulu.io/) for a comprehensive list of Sulus features, core values and use cases. 

<br/>
<p align="center">
    <img width="80%" src="https://sulu.io/uploads/media/800x@2x/07/167-ezgif.gif?v=2" alt="Sulu Slideshow">
</p>
<br/>

# Environnement de développement du projet

## Prérequis

Avoir docker 😉 qui tourne sur sa machine (vm ou wsl).
```
docker -v
Docker version 19.03.12, build 48a66213fe
```

- Docker : https://www.docker.com/get-started
- Docker-compose: https://docs.docker.com/compose/install/


#### Commandes à exécuter pour démarrer :

- `docker-compose up -d` pour lancer tous les containers
- `docker-compose exec apache bash` pour entrer en BASH dans le container
- `chmod -R 777 *` depuis le container peux être necessaire
- `composer install`
