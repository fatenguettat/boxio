#summary Liste des futurs implémentations et corrections

# BETA 1.3 #

  1. Correction et Amélioration des exemples dans iViewer
  1. Afficher la dernière action (et trier par date) les équipements trouvés dans "Liste des équipements non trouvés"
  1. Ajout de la gestion des status pour les scenarios temporels (ACTION\_IN\_TIME et ACTION\_FOR\_TIME)
  1. Ajout du support des paramètres pour les commandes Lexic (inter, poussoir, tempo, etc.), pour détecter le bon status
  1. ~~Ajout des commandes d'arrêt pour interrompre les scripts en cours (stop\_command, stop\_favoris, stop\_macros et stop\_trame)~~
  1. Ajout de délais pour les commandes en cours (delay\_command, delay\_favoris, delay\_macros et delay\_trame)
  1. Ajout des déclencheurs

# BETA 1.2 #

  1. ~~Corriger la référence 84541 en attente de validation par Frederic~~ -> MYSQL Table references
  1. ~~Ajout de la référence 67255 en attente de validation par Aurélien~~ -> MYSQL Table references
  1. ~~Ajout de la programmation des scénarios des équipements sans les ouvrir et sans utiliser la procédure classique de Legrand, plus besoin de retirer les enjoliveurs :)~~ -> équipements.js
  1. ~~Bug dans "Liste des scénarios de l'équipement" certains Id/Unit Legrand n'était pas affichés~~ -> equipements.js

# BETA 1.1 #

  1. ~~Bug dans "ajout d'un équipement" si la liste des références n'a pas été dépliée les références sont inconnues~~ -> equipements.js
  1. ~~Bug dans "ajout d'un équipement" la liste des références n'affiche que les références listées dans "liste des références supportées par le serveur"~~ -> equipements.js
  1. ~~Bug dans la génération des trames lorsque le unit est supérieur à 9~~ -> own\_scripts.js
  1. ~~Bug lorsque le serveur ne contient aucun jalon, fichier de log boxio.err qui gonfle, merci Sylvain~~ -> server.php

# BETA 1.0 #

  1. ~~Problèmes d'accents dans "Ajout d'un équipement" lors de l'enregistrement (Bug UTF-8)~~ -> client.php
  1. ~~Automatiser le rafraichissement dans "Liste des équipements non trouvés"~~ -> equipements.js
  1. Afficher la dernière action (et trier par date) les équipements trouvés dans "Liste des équipements non trouvés"
  1. ~~Bug lors de la mise à jour d'un équipement pour changer la zone, 2 zones sont crées dans "Modification d'un équipement"~~ -> MYSQL Routine add\_equipement
  1. ~~Vérifier le retour lors de la programmation automatique d'un scenario et indique une erreur si nécessaire dans "liste des scenarios de l'équipement"~~ -> équipements.js
  1. ~~Décrypter les paramètres dans "Etat du Bus" pour faciliter la compréhension~~ -> trame.js
  1. ~~Bug dans "Modification d'un jalon" la mise à jour créée un nouveau jalon~~ -> cron.js
  1. ~~Bug lorsque le serveur ne contient aucun jalon, blocage complet du BUS, merci Patrice pour les corrections :)~~ -> crond.php, server.php
  1. ~~Ajouter les références 67201 et 67202 demande de frederic~~ -> MYSQL Table references
  1. ~~Les jalons ne sont pas mises à jour tant que le serveur n'a pas redémaré~~ -> crond.php, server.php