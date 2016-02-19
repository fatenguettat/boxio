## INTRODUCTION ##

Le fonctionnement du protocole peut paraitre simple lorsqu'il est programmé par un "Utilisateur" à l'aide des boutons sur les équipements, mais dès que l'on souhaite interroger sur le BUS les équipements, la réalité est différente et on se perd vite avec les questions :

  * Qui parle à qui ?
  * Qui écoute qui ?
  * Dans quel sens vont les informations ?
  * Qui contient la programmation du scénario ?
  * Etc...

## LES LIAISONS PHYSIQUES ##

Il en existe trois différentes :
  * Le CPL (Courant Porteur en Ligne) les informations transitent sur l'installation électrique. Conditions obligatoires :
    1. que l'équipement soit relié à l'aide de la phase et du neutre
    1. que la portée soit inférieur à 50 mètres, au-delà les transmissions peuvent devenir hasardeuse. Ce qui signifie qu'un interrupteur qui est à 25 m de câble du tableau peut rencontrer des difficultés pour envoyer un ordre à un interrupteur situé également à 25 m (25m + 25m = 50m), etc.
  * Le RF (Radio Fréquence) les informations sont envoyées en Radio mais elles peuvent être transmises sur le CPL grâce à l'interface référence 3600
  * L'IR (Infra-Rouge) destiné aux télécommandes, les informations sont interprétées par les équipements qui possèdent une cellule Infrarouge mais elles peuvent également être retransmises sur le CPL par certains équipements

## LE SENS DE COMMUNICATION ##

Les équipements sont divisés en trois catégories :
  1. Les Emetteurs, ils envoient des ordres sur le BUS
  1. Les Récepteurs, ils écoutent les messages qui circulent sur le BUS
  1. Les Emetteurs/Récepteurs, ils envoient et écoutent les messages sur le BUS

## LES UNITES ET MODULES ##

Les équipements peuvent être équipés de un ou plusieurs modules selon leur nature. Par exemple un interrupteur double possède deux modules.
Chaque module d'un équipement est composé d'une ou plusieurs unités. Les unités sont des références sur des fonctions de l'équipement.
  * Dans le cas d'un interrupteur simple émetteur il n'y a qu'un module d'une seul unité
  * Dans le cas d'un interrupteur simple émetteur/récepteur il n'y a qu'un module mais il est composé de deux unités. La première unité est principalement utilisée pour émettre les ordres, la seconde unité permet d'enregistrée les équipements associés.
Exemples :
  * Inter Simple RF : 1 unité
  * Inter Simple émetteur/récepteur CPL : 2 unités
  * Inter Double émetteur/récepteur CPL : 4 unités
  * Télécommande Interscenario 8 actions RF : 8 unités

## L'ENVOI ET LA RECEPTION D'ORDES ##

L'IOBL fonctionne sur un procédé de « Broadcast » il n'y a pas de d'échange établie entre deux équipements. Chaque équipement envoi une commande « à qui veux l'entendre », chaque commande qui circule sur le BUS est lu par tous les équipements et si un équipement est « concerné » par la commande il réagira en fonction de celle-ci.
C'est pour cette raison qu'il arrive que des ordres se perdent, lorsque deux interrupteur sont associés il n'y a pas de vérification si la commande est bien reçu.
Une action est se déroule ainsi, lorsqu'un interrupteur est associé à un autre :
  1. Interrupteur 1, appui sur la touche ON
  1. Interrupteur 1, envoie sur le BUS « INTER1 ON »
  1. Interrupteur 2, lecture sur le BUS « INTER1 ON »
  1. Interrupteur 2, si programmé pour « INTER1 ON » alors changement de l'état à ON

## LA PROGRAMATION DES EQUIPEMENTS ##

Pour rappel les équipements ne s'adresse pas directement entre eux mais indique une action, ils sont alors émetteurs.
La programmation se fait donc uniquement sur les récepteurs, par exemple un interscenario ne contient pas la programmation des équipements qui réagissent à ces actions car il est émetteur d'ordre. Ce sont les équipements récepteurs qui ont enregistrés en mémoire qu'il devait réagir à l'interscenario.

  * Les plus :
    * Alléger considérablement le BUS, une seule commande pour réaliser plusieurs d'action
    * Le nombres d'action peut être infinie
    * Si un équipement est supprimé de l'installation il n'y a pas de reprogrammation à réaliser

  * Les moins :
    * Impossible de savoir à qui s'adresse une action sans connaitre la programmation de tous les récepteurs associés
    * Si un émetteurs est supprimé de l'installation, les récepteurs ne peuvent plus le déprogrammé (sauf programmation directement sur le BUS ou reset des récepteurs)

La programmation se fait donc sur les récepteur, un unit est réservé à la programmation de chaque module. Chaque unit de programmation contient 16 ou 32 blocs de mémoires en fonction de l'équipement, c'est pourquoi un récepteur ne participer à plus de 16 ou 32 scénarios.