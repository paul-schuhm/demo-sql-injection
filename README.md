# Démo injection SQL

![](assets/exploits_of_a_mom.png)

> Source : [Exploits of a Mom](https://xkcd.com/327/)

- [Démo injection SQL](#démo-injection-sql)
  - [Contenu de la démo](#contenu-de-la-démo)
  - [Lancer la démo](#lancer-la-démo)
    - [Prérequis](#prérequis)
    - [Instructions](#instructions)
  - [Utiliser la démo](#utiliser-la-démo)
  - [Qu'est ce qu'une injection SQL ?](#quest-ce-quune-injection-sql-)
  - [Commentaires](#commentaires)
  - [Références](#références)


## Contenu de la démo

Cette démonstration contient un système complet divisé en trois modules :

- Une application cliente web écrite en PHP. C'est elle qui exposera les failles de sécurité permettant l'injection SQL
- Une base de données relationnelle MySQL, hébergée sur un conteneur Docker
- Un client graphique [Adminer](https://www.adminer.org/), pour inspecter la base de données avec une interface graphique (optionnel)

Le système sera compromis via l'exploitation de faille de sécurité présente dans l'application cliente.

## Lancer la démo

### Prérequis

Les programmes suivants doivent être installés sur la machine hôte :

- git
- PHP8+
- [Docker](https://www.docker.com/get-started/) et [(Docker)Compose](https://docs.docker.com/compose/)

### Instructions

1. Cloner le dépôt.
2. Créer un fichier .env à partir du fichier .env.dist
~~~bash
cp .env.dist .env
~~~
3. Lancer le conteneur qui héberge la base de données MySQL (et le conteneur Adminer)
~~~bash
docker-compose up -d
~~~

## Utiliser la démo


## Qu'est ce qu'une injection SQL ?

> Applications that access MySQL **should not trust any data entered by users**, who can try to trick your code by *entering special or* *escaped character sequences* in Web forms, URLs, or whatever application you have built. Be sure that your application remains secure if a user tries to perform SQL injection by entering something like `; DROP DATABASE mysql;` into a form. This is an extreme example, but **large security leaks and data loss might occur as a result of hackers using similar techniques**, if you do not prepare for them. 
>   
> Source : [Handle External Data Properly](https://dev.mysql.com/doc/refman/5.7/en/secure-client-programming.html), de la documentation officielle de MySQL

Une *injection SQL* désigne un ensemble de méthodes d'**exploitation de faille de sécurité d'une application** interagissant avec une base de données relationnelle. Elle consiste à *injecter* des instructions SQL non prévues initialement par l'application cliente permettant de compromettre sa sécurité (cohérence, disponibilité, confidentialité, intégrité). Il existe [tout un ensemble de méthodes](https://fr.wikipedia.org/wiki/Injection_SQL) pour y parvenir.

Comment fonctionne l'injection ? En insérant des caractères spéciaux permettant de briser la logique de la requête SQL initiale. En effet, une requête SQL est une séquence de caractères alphanumériques interprétée par le serveur de base de données. Il est donc possible de transformer une requête *dynamiquement* en y insérant les bons caractères au bon endroit.

Une injection SQL **est donc une attaque qui vise les clients** d'un serveur de base de données. C'est au niveau du client de la base de données, le plus souvent une application web, que la faille est exploitée s'il y'en a. Si l'application cliente ne prend pas des précautions pour se prémunir de telles attaques, elle met en péril le système tout entier, car la base de données est le coeur du système d'information attaqué.


## Commentaires


## Références

- [Exploits of a Mom](https://xkcd.com/327/), comic strip d'xkcd sur l'injection SQL
- [Running an SQL Injection Attack - Computerphile ](https://www.youtube.com/watch?v=ciNHn38EyRc), un bon exposé de ce qu'est une injection SQL accompagné d'une démonstration, dont la démo présente s'inspire fortement
- [Client Programming Security Guidelines MySQL, documentation officielle](https://dev.mysql.com/doc/refman/5.7/en/secure-client-programming.html), un ensemble de règles/conseils de sécurité à suivre pour les clients MySQL (vrai pour d'autres SBGDR)
- [MySQL Docker Image, quick reference](https://hub.docker.com/_/mysql/)