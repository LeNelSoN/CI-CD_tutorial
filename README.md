# CI/CD tutorial

![Black and White Chalkboard Brainstorm Presentation](https://github.com/user-attachments/assets/968f7c2c-7fb8-4ed1-9b70-b075931dcfb4)


## Introduction
Bonjour et bienvenue ! 

Ce tutoriel a été conçu pour vous guider pas à pas dans la mise en place d’un projet Symfony avec un pipeline CI/CD automatisé grâce à GitHub Actions.

À la fin de ce tutoriel, vous aurez une base pratique pour automatiser vos projets Symfony et améliorer votre workflow de développement.

Restez avec moi et suivez les étapes. Une petite vidéo d'introduction vous expliquera tout en détail.

[Video d'introduction](https://vimeo.com/1047858664/4e1ecda036?share=copy)

---

![Black and White Chalkboard Brainstorm Presentation (1)](https://github.com/user-attachments/assets/5564ec48-b4de-4ef6-af59-0526964aa717)

---

## Création du projet symfony

[Video de création du repository](https://vimeo.com/1047889713/6776a92079?share=copy)

1. Symfony dispose d’un outil CLI (Command Line Interface) pour créer et gérer facilement des projets. Je fais l'impasse sur l'intallation de Symfony mais vérifions tout de même qu'il soit présent.

```bash
symfony -v
```

2. Ensuite pour créer un projet symfony il suffit d'utiliser la commande

```bash
symfony new e-commerce
```

3. Installons les dépendances, grace au gestionnaire de dépendance composer

```bash
composer install
```

4. Et enfin lance l'application

```bash
symfony server:start
```

L’application sera disponible sur http://127.0.0.1:8000

## Préparons la CI/CD avec PHPUnit

[Lien de la video de préparation](https://vimeo.com/1047869030/892d772abe?share=copy)

1. D'abord nous allons installer PHPUnit qui est un framework de test pour php. Il permet d'écrire des tests unitaires pour vos méthodes de classe.

```bash
composer require --dev phpunit/phpunit
```
2. Nous allons ensuite créer un test simple

```bash
mkdir -p tests/Basic
touch tests/Basic/BasicTest.php
```

3. Ajoutons un test factice pour notre tuto

```php
<?php

namespace App\Tests\Basic;

use PHPUnit\Framework\TestCase;

class BasicTest extends TestCase
{
    public function testTrueIsTrue()
    {
        $this->assertTrue(true);
    }
}

```

4. Exécutons ensemble les tests localement.

```bash
vendor/bin/phpunit
```

>J'ai du remplacer le `phpunit.xml.dist` par celui-ci pour que cela fonctionne mais cela vient peut etre des versions de PHP, symfony et PHPUnit que j'utilise.
>```xml
><phpunit xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
>         xsi:noNamespaceSchemaLocation="https://schema.phpunit.de/11.0/phpunit.xsd"
>         bootstrap="vendor/autoload.php"
>         colors="true">
>  <php>
>    <env name="APP_ENV" value="test"/>
>  </php>
>  <testsuites>
>    <testsuite name="Application Test Suite">
>      <directory>tests</directory>
>    </testsuite>
>  </testsuites>
></phpunit>
>```

## Mise en place CI/CD avec GITHUB actions

### Initialisation
1. Initialiser Git en Local
**À la racine du projet Symfony**
```bash
git init
```

2. Ajouter tous les fichiers au suivi
**Cela inclut tous les fichiers essentiels**
```bash
git add .
```

3. Créer un premier commit
```bash
git commit -m "Initial commit"
```

### Création du Dépot

[Video D'explication](https://vimeo.com/1047889713/6776a92079?share=copy)

1. Se connecter à GitHub
   
Accède à [GITHUB](https://github.com).

2. Créer un nouveau dépôt
   
3. Connecter le dépôt local à GitHub
   
**Ajoute l'URL de ton dépôt distant**

```bash
git remote add origin https://github.com/nom-utilisateur/nom-projet.git
```

### Configuration de GitHub Actions

Tout est dans la vidéo :)

[Video de mise en place](https://vimeo.com/1048115026/f39150d767?share=copy)

### En Bonus les Github secrets

[Video des secrets](https://vimeo.com/1047925524/6d1d710024?share=copy)
