# Démo injection SQL

![](assets/exploits_of_a_mom.png)

> Source : [Exploits of a Mom](https://xkcd.com/327/)

- [Démo injection SQL](#démo-injection-sql)
  - [Installation](#installation)
  - [Lancer la démo](#lancer-la-démo)
  - [Commentaires](#commentaires)
  - [Références](#références)


## Installation

Prérequis :

- PHP8+
- MySQL ou Docker et Docker Compose

## Lancer la démo


## Commentaires

> Applications that access MySQL **should not trust any data entered by users**, who can try to trick your code by entering special or escaped character sequences in Web forms, URLs, or whatever application you have built. Be sure that your application remains secure if a user tries to perform SQL injection by entering something like ; DROP DATABASE mysql; into a form. This is an extreme example, but **large security leaks and data loss might occur as a result of hackers using similar techniques**, if you do not prepare for them. Source : 
[Handle External Data Properly](https://dev.mysql.com/doc/refman/5.7/en/secure-client-programming.html), de la documentation officielle de MySQL


## Références

- [Exploits of a Mom](https://xkcd.com/327/), comic strip d'xkcd sur l'injection SQL
- [Running an SQL Injection Attack - Computerphile ](https://www.youtube.com/watch?v=ciNHn38EyRc), un bon exposé de ce qu'est une injection SQL accompagné d'une démonstration, dont la démo présente s'inspire fortement
- [Client Programming Security Guidelines MySQL, documentation officielle](https://dev.mysql.com/doc/refman/5.7/en/secure-client-programming.html), un ensemble de règles/conseils de sécurité à suivre pour les clients MySQL (vrai pour d'autres SBGDR)