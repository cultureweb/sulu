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

# Project development environment

## Prerequisites

Having docker 😉 that runs (vm ou wsl).
```
docker -v
Docker version 19.03.12, build 48a66213fe
```

- Docker : https://www.docker.com/get-started
- Docker-compose: https://docs.docker.com/compose/install/


#### Commandes à exécuter pour démarrer :

- `docker-compose up -d` to launch all containers
- `docker-compose exec apache bash` to get into the container
- `chmod -R 777 *` from inside the container
- `composer install`


#### Webspaces

The content management part of Sulu is built upon webspaces. Each of these webspaces configures a content tree. Each content tree may contain translations for different locales.

The default webspace configuration is located in ```config/webspaces/example.xml.``` Rename this file so that it matches the name of your project.

To get started, change the```<name>``` and the ```<key>``` of the webspace to the name of your project. The name is a human-readable label that is shown in the administration interface. The key is the unique identifier of the webspace:
```
<?xml version="1.0" encoding="utf-8"?>
<webspace xmlns="http://schemas.sulu.io/webspace/webspace"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="http://schemas.sulu.io/webspace/webspace http://schemas.sulu.io/webspace/webspace-1.1.xsd">

    <name>My Project</name>
    <key>my-project</key>

    <!-- ... -->
</webspace>
```

```
Caution

Changing the <key> of a webspace later on causes complications. We recommend to decide what key to use before you build the database in the next step.
```
#### Create the database

- Duplicate .env.dist to .env
- `php bin/console doctrine:database:create`
  

- `php bin/adminconsole sulu:build dev`

#### Configuring webspace localizations
The default webspace configuration is located in `config/webspaces/zehero.xml`. Rename this file so that it matches the name of your project. 

 ```
       <localizations>
        <!-- See: http://docs.sulu.io/en/latest/book/localization.html how to add new localizations -->
        <localization language="en" default="true"/>
        <localization language="fr"/>
    </localizations>
  ```
**After adding localizations in the webspace, note that you need to run**
- `php bin/adminconsole sulu:document:initialize`

### Using Webpack Encore for your website assets

Webpack Encore is a tool to manage your javascript and css assets. It seamlessly integrates webpack into your symfony application.

Installation
First add the WebpackEncoreBundle as a dependency to your `composer.json` file.

- `composer require symfony/webpack-encore-bundle`
To enable it, add the following line to the `config/bundles.php` file, if that has not been done already for you by Symfony Flex:
 ```
return [
...
Symfony\WebpackEncoreBundle\WebpackEncoreBundle::class => ['all' => true],
];
 ```
