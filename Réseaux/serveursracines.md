---
layout: default
title: roots servers
parent: Réseaux
---


# Introduction :

Dès que l'on recherche un élément en ligne, que l'on communique avec un service en ligne, le serveur racine (du DNS) joue un rôle important dans la résolution de nom. Comment, sur base d'une adresse IP, il est possible d'arriver sur Google, Youtube ou encore Facebook?

## Histoire :

Avant le DNS, la résolution de nom  sur internet se faisant  grâce à un fichier texte que l'on recopiait sur les ordinateurs, par transfert de fichier.

Ce fichier portait le nom de: HOSTS.TXT.

En 1982, ce système montre ses premières limites, et plusieurs propositions de remplacement  voient le jour. Les premières idées ne sont pas gardées. Un certain Paul Mockapetris vu désigné responsable quant au développement d'un autre système de résolution de nom.
Il est responsable du DNS, une architecture qu'il proposera en 1983 dans les RFC 882 et RFC 883.

Ce dernier est également l'inventeur du premier serveur de courrier électronique basé sur le protocole SMTP.

## Explications des roots-servers

Afin de nous rendre sur nos sites web préférés, nous utilisons la résolution de noms DNS, qui passe par les serveurs racines (roots-servers).

Un serveur racine est un élément primordial pour la résolution de nom. Il répond aux requêtes ou demandes des clients dans la zone racine du DNS (Cette zone marque le niveau le plus élevé, au premier niveau de l'espace de nom DNS).
Ces derniers n'exécutent pas eux-mêmes la résolution de nom, mais informent à la place le client d'autres serveurs DNS à consulter plus précis afin d'obtenir une meilleure réponse.

Cependant, afin de pouvoir aller interroger  un serveur racine, il faut également posséder des informations à son propos. Quelle  est l'adresse IP du serveur racine responsable de la zone que je cherche à joindre?
Pour ce faire, il existe un fichier, appelé "fichier de zone racine", qui contient tous les noms et toutes les adresses IP des domaines de premier niveau.
Ce fichier est téléchargé lors de l'installation d'un client DNS, comme Bind9 par exemple. 
Ce dernier se trouve dans le répertoire  /etc/bind, sous le nom de db.root.

La gestion de base du serveur racine est à la responsabilité de l'ICANN (Internet Corporation for Assigned Names and Numbers).

Il n'y a plus, contrairement à la croyance populaire, uniquement 13 serveurs racine du DNS unique.
En effet, nous devons plutôt parler de 13 "identitées de serveur". Ces "identitées", ayant chacune une adresse IP, sont souvent considérées comme des serveurs racines.

![root servers](https://github.com/zCargan/Wiki-TI/assets/64102236/cb16cd64-90b5-428e-a9f3-024823016412)

Lors d'une tentative de résolution de nom, on va tout d'abord interroger un serveur racine, afin d'obtenir plus d'informations sur le domaine de premier niveau (TLD, Top level Domaine).

Par la suite, grâce à la réponse du TLD, nous allons interroger le SOA de la zone recherchée, afin d'obtenir l'IP recherché.

C'est de cette manière que nous parvenons à accéder aux contenus de certains sites. Sans le fichier db.root, toute la résolution de nom du DNS globale ne marcherait pas. Les serveurs DNS racines sont les piliers du DNS.

## Attaque sur les serveurs racines :

Il y a déjà eu, durant son histoire, de nombreuses attaques sur les serveurs racine. Etant la base de la résolution de nom, si le service tombe en panne, c'est tout internet qui tombe en panne.

### Attaque de 2002 :

Lors de cette attaque, 7 serveurs sur les 13 ont été touchés, et ont vu leurs performances dégradées à cause de cette dernière. Les auteurs de cette attaque l'ont effectué à l'aide d'un DDoS. Ils ont réussi à générer un volume de requêtes 40x supérieur à la normal.
Suite à cette attaque, le systeme anycast a été mis en place :

"Anycast est une technique d'adressage et de routage permettant de rediriger les données vers le serveur informatique le « plus proche » ou le « plus efficace » selon la politique de routage."
[source](https://fr.wikipedia.org/wiki/Anycast).

### Attaque de 2007 :

Les serveurs F, G, L et M ont été attqués pendant 24h.

Lors de cette attaque, l'impact sur M a été moindre grâce à anycast.

5000 machines, essentiellement baséesen corée du sud, ont généré du trafic en direction des Etats-Unis.

### Attaque de 2015 : 
5 millions de requêtes par seconde prenant la route vers les 13 serveurs racines. L'attaque était destinée à chaque serveur racine de chaque lettre. La durée totale de cette attaque n'a pas dépassé 4 heures, mais les serveurs DNS racine ont été confrontés à environ 1 trillion de fausses requêtes.

## Conclusion :

Les roots-servers / serveurs racines sont un élément essentiel de la résolution de nom sur internet. Ils représentent le fondement du fonctionnement du service DNS. Sans eux, nous ne pourrions plus aller sur un site sur base de son URL. Ce service a, à de nombreuses fois, été attaqué en essayant de le faire tomber, mais ils n'y sont jamais arrivés.
Le service est super robuste, pas étonnant vu son importance dans la société à l'heure actuel.


## Bibliographie:


### source 1 :  

[URL](https://www.ionos.fr/digitalguide/serveur/know-how/quest-ce-quun-serveur-racine-definition-et-fonctionnement/) de l'article

Auteur : Know-how

Titre de l'article : Qu’est-ce qu’un serveur racine ? Définition et fonctionnement

Date de consultation : 25 mai 2023

### source 2 :  

[URL](https://www.ionos.fr/digitalguide/serveur/know-how/quest-ce-quun-serveur-racine-definition-et-fonctionnement/)
Auteur : ?

Titre de l'article : Chapitre 9. Monter un serveur DNS

Date de consultation : 25 mai 2023

### source 3 :  

[URL](https://news.sophos.com/fr-fr/2015/12/12/serveurs-dns-racine-attaque-ddos-massive/) de l'article

Auteur : Sophos France

Titre de l'article : Des serveurs DNS racine résistent à une attaque DDoS massive

Date de consultation : 25 mai 2023

### source 4 :  

[URL](https://fr.wikipedia.org/wiki/Serveur_racine_du_DNS) de l'article

Auteur : ?

Titre de l'article : Serveur racine du DNS

Date de consultation : 25 mai 2023

### source 5 :  

[URL](https://fr.wikipedia.org/wiki/Serveur_racine_du_DNS](https://www.techno-science.net/glossaire-definition/Domain-Name-System-page-2.html)) de l'article

Auteur : [liste ici](http://fr.wikipedia.org/w/index.php?title=Domain%20Name%20System&action=history)

Titre de l'article : Domain Name System

Date de consultation : 25 mai 2023

### source 6 :  

[URL](https://fr.wikipedia.org/wiki/Paul_Mockapetris) de l'article

Auteur : [ici]([http://fr.wikipedia.org/w/index.php?title=Domain%20Name%20System&action=history](https://fr.wikipedia.org/wiki/Utilisateur:Bot_de_pluie))

Titre de l'article : Paul Mockapetris

Date de consultation : 25 mai 2023



