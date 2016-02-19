# POURQUOI ? #

Legrand possède plusieurs gammes de produit compatibles "InOne By Legrand" (IOBL) qui proposent des fonctionnalités de domotique, celles-ci permettent une interaction entre les interrupteurs, les ouvrants, le chauffage, etc.
Legrand a également fabriquer une passerelle permettant un accès entre leurs produits IOBL et un port USB informatique (Référence Legrand : 88213). Le protocole employé est un dérivé de l'OPENWEBNET mais il ne se comporte pas exactement de la même façon ce qui ferme les portes à un grand nombre d'applications récentes compatible MyHome basé intégralement sur la nome OPENWEBNET. La norme employé par Legrand a été renommé IOBL et reste actuellement peu utilisée car considérée comme obsolète et en fin de vie.
Le projet propose donc une suite d'outil permettant d'interagir avec le protocole IOBL, il est donc nécessaire de posséder au préalable :
  * un circuit électrique en 220V/110V
  * des produits estampillés « InOne By Legrand » (Céliane, Plexo, Sagane, Mosaic, etc.)
  * une interface Legrand 88213
  * Une Carte Raspberry Pi pour une installation autonome et sans pré-configuration

# LE SERVEUR #

## Introduction ##

Le serveur permet la récupération, l'interprétation et l'archivage des commandes provenant de l'interface 88213 en OPENWEBNET IOBL.

## Principe de fonctionnement ##

  1. Une commande est envoyée sur le réseau CPL
  1. L'interface Legrand 88213 la retranscrit sur le port USB en OPENWEBNET
  1. Un convertisseur SERIAL->TCP créé un socket en TCP pour transmettre la commande
  1. Le script server.php ouvre un socket vers le port SERIAL(USB) pour récupérer la commande
  1. Le script server.php interprète et analyse la commande puis met à jour la base de données MYSQL
  1. Le SERVEUR peut également faire le processus inverse pour l'envoie de commande, DB->SERVEUR->TCP->SERIAL(USB)->88213->CPL

## Prérequis ##

Le SERVEUR :
  * fonctionne sur une carte Raspberry Pi OS LINUX (tout est pré-configuré)
  * il contient un daemon pour le lancer automatiquement ou le redémarrer
  * peut également fonctionner dans n'importe qu'elle environnement Windows ou Unix, dans ce cas :
    * doit être utilisé avec le couple PHP/MYSQL (avec les extensions necessaires)
    * peut être lancé sur IIS ou Apache
    * doit être lancé en mode client et non graphique
    * ne fonctionne qu'avec un convertisseur SERIAL/TCP du type : SER2NET, SERPROXY, etc.

## Fichiers utilisés ##

Le daemon de démarrage (Uniquement sous Unix dans la version Raspberry Pi pré-configuré)
Le fichier server.php + fichiers connexes de configuration

# LA DB #

## Introduction ##

La DB est la base de donnée MYSQL elle est interrogée UNIQUEMENT au travers du SERVER.

## Principe de fonctionnement ##

> Elle contient :
  1. Les trames OPENWEBNET brutes qui circulent sur le CPL
  1. Les trames décryptées sous un format lisible
  1. Les références et définitions des équipements Legrand qui sont gérés
  1. Les références des équipements que l'utilisateur possède
  1. L'état des équipements enregistrés
  1. Les scénarios enregistrés

## Prérequis ##

Elle doit impérativement :
  * Fonctionner sous MYSQL
  * Contenir ses procédures stockées
  * Contenir ses vues
  * Contenir les définitions des équipements Legrand

# LE CLIENT #

## Introduction ##

Il permet de s'interfacer entre le SERVEUR et la DB.

## Prérequis ##

Ils sont identiques au SERVEUR sauf :
  * Il est appelé en HTTP depuis n'importe qu'elle navigateur/logiciel d’intégration avec des paramètres en GET
  * Certaines fonctionnalites necessittes des droits utilisateurs particuliers (UNIX)
  * Certaines fonctionnalites ne fonctionne pas sous Windows (Redemmarage serveur, etc.)

## Principe de fonctionnement ##

Le CLIENT est normalement le seul lien entre le SERVEUR et la DB toutes les opérations transitent par des demandes en HTTP avec des paramètres en GET qui retourne de l'XML, par exemple :
  1. Appel de http://ip_serveur/HTPC/legrand/client.php?get_last_trames=20
  1. Le CLIENT récupère en DB les 20 dernières trames qui ont circulées
  1. Le CLIENT retourne en XML le résultat
Autre exemple d'envoi de commande :
  1. Appel de http://ip_serveur/HTPC/legrand/client.php?send_trame=YZ1000Y8620320Y51ZZ
  1. Le CLIENT converti YZ1000Y8620320Y51ZZ en **#1000\*8620320\*51##
  1. Le CLIENT envoie dans la DB temporaire la trame convertie
  1. Le SERVEUR récupère la trame en DB et la transmet en TCP
  1. Le convertisseur TCP->SERIAL la renvoie à l'interface 88213 sur le CPL**

## Fichiers utilisés ##

Le fichier client.php + fichiers connexes de configuration

# L'INTERFACE WEB #

## Introduction ##

L'interface web permet d'envoyer et de récupérer des commandes du CLIENT, elle est codée en PHP/HTML/JAVASCRIPT basé sur le framwork ExtJs.
Elle est amenée à évoluer sans cesse pour ajouter les nouvelles fonctionnalités du CLIENT et du SERVEUR. A terme elle devrait être compatible avec tous les navigateurs et supportés également les Tablettes et Smartphones.

# L'API IVIEWER #

## Introduction ##

Cette API codée en JAVASCRIPT permet d'intégrer directement à Iviewer de Command Fusion les fonctionnalités du CLIENT. Le résultat obtenu est une interface personnalisable compatible IPAD/IPHONE et ANDROID.
Pour plus de renseignement sur Iviewer : [commandfusion.com](http://www.commandfusion.com/)