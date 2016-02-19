# Introduction #

Pour qu'une référence puisse être ajoutée au Serveur il faut au préalable connaitre et comprendre :
  * l'utilisation
  * le fonctionnement
  * la programmation

# Explications #

Il y a trois possibilités pour ajouter des références :
  1. Me faire parvenir l'équipement... Je m'occupe du reste !
  1. Intégrer soit même l'équipement dans le serveur et les bases de données... A vous de jouer !
  1. Poster une "issue" avec la demande d'ajout de l'équipement, attention il faudra respecter les conditions necessaires pour que la demande aboutisse... on partage le travail !

La meilleur méthode reste la dernière, poster une "issue", mais impérativement avec les indications suivantes :

  * La référence Legrand de l'équipement
  * La documentation en pièce jointe (si celle-ci n'existe plus la scanner)
  * S'il n'y a pas de documentation, il faudra décrire l'appareil très précisemment :
    * A quoi sert-il et comment fonctionne-t-il ?
    * A quoi est-il physiquement relié (Liste des borniers) ?
    * De qu'elles familles provient-il (CPL/RF/IR) ?
    * Est-il emmetteur, recepteur ou les deux ?
  * Renvoyer la liste des commandes IOBL définissant le module :
    * Version, Fonction, Units
    * Description des Units
    * Type de programmation

# Exemple #

Cette exemple décrit les commandes necessaires pour comprendre le fonctionnement d'un inter VMC

Dans l'ordre inverse nous testons :
  1. Le type de l'equipement
  1. La valeur de chaque unit dans chaque état
  1. S'il est possible de programmer un unit

<table border='1'>
<blockquote><tr>
<blockquote><th>trame</th>
<th>direction</th>
<th>Format</th>
<th>type</th>
<th>value</th>
<th>dimension</th>
<th>param</th>
<th>id_legrand</th>
<th>unit</th>
</blockquote></tr>
<tr>
<blockquote><td><b>#1000*0#1815138*56*0##</td></b><td>GET</td>
<td>DIMENSION_REQUEST</td>
<td>CONFIGURATION</td>
<td></td>
<td>MEMORY_DEPTH_INDICATION</td>
<td></td>
<td>113446</td>
<td>2</td>
</blockquote></tr>
<tr>
<blockquote><td><b>1000*66*1815138##</td></b><td>SET</td>
<td>DIMENSION_SET</td>
<td>CONFIGURATION</td>
<td>MEMORY_READ</td>
<td></td>
<td></td>
<td>113446</td>
<td>2</td>
</blockquote></tr>
<tr>
<blockquote><td><b>1000*73*1815136##</td></b><td>GET</td>
<td>DIMENSION_SET</td>
<td>CONFIGURATION</td>
<td>INVALID_ACTION</td>
<td></td>
<td></td>
<td>113446</td>
<td>0</td>
</blockquote></tr>
<tr>
<blockquote><td><b>1000*66*1815137##</td></b><td>SET</td>
<td>DIMENSION_SET</td>
<td>CONFIGURATION</td>
<td>MEMORY_READ</td>
<td></td>
<td></td>
<td>113446</td>
<td>1</td>
</blockquote></tr>
<tr>
<blockquote><td><b>#1000*0#1815138*55*141*102*1*255*255*0##</td></b><td>GET</td>
<td>DIMENSION_REQUEST</td>
<td>CONFIGURATION</td>
<td></td>
<td>UNIT_DESCRIPTION_STATUS</td>
<td>unit_code=141;unit_status=102;other=1*255*255*0</td>
<td>113446</td>
<td>2</td>
</blockquote></tr>
<tr>
<blockquote><td><b>#1000*1815138*55##</td></b><td>SET</td>
<td>DIMENSION_REQUEST</td>
<td>CONFIGURATION</td>
<td></td>
<td>UNIT_DESCRIPTION_REQUEST</td>
<td></td>
<td>113446</td>
<td>2</td>
</blockquote></tr>
<tr>
<blockquote><td><b>#1000*0#1815137*55*19*255##</td></b><td>GET</td>
<td>DIMENSION_REQUEST</td>
<td>CONFIGURATION</td>
<td></td>
<td>UNIT_DESCRIPTION_STATUS</td>
<td>unit_code=19;unit_status=255</td>
<td>113446</td>
<td>1</td>
</blockquote></tr>
<tr>
<blockquote><td><b>#1000*1815137*55##</td></b><td>SET</td>
<td>DIMENSION_REQUEST</td>
<td>CONFIGURATION</td>
<td></td>
<td>UNIT_DESCRIPTION_REQUEST</td>
<td></td>
<td>113446</td>
<td>1</td>
</blockquote></tr>
<tr>
<blockquote><td><b>4*58*0#1815137##</td></b><td>GET</td>
<td>BUS_COMMAND</td>
<td>THERMOREGULATION</td>
<td>HIGH_FAN_SPEED</td>
<td></td>
<td></td>
<td>113446</td>
<td>1</td>
</blockquote></tr>
<tr>
<blockquote><td><b>#1000*0#1815138*55*141*101*0*255*255*0##</td></b><td>GET</td>
<td>DIMENSION_REQUEST</td>
<td>CONFIGURATION</td>
<td></td>
<td>UNIT_DESCRIPTION_STATUS</td>
<td>unit_code=141;unit_status=101;other=0*255*255*0</td>
<td>113446</td>
<td>2</td>
</blockquote></tr>
<tr>
<blockquote><td><b>#1000*1815138*55##</td></b><td>SET</td>
<td>DIMENSION_REQUEST</td>
<td>CONFIGURATION</td>
<td></td>
<td>UNIT_DESCRIPTION_REQUEST</td>
<td></td>
<td>113446</td>
<td>2</td>
</blockquote></tr>
<tr>
<blockquote><td><b>#1000*0#1815137*55*19*255##</td></b><td>GET</td>
<td>DIMENSION_REQUEST</td>
<td>CONFIGURATION</td>
<td></td>
<td>UNIT_DESCRIPTION_STATUS</td>
<td>unit_code=19;unit_status=255</td>
<td>113446</td>
<td>1</td>
</blockquote></tr>
<tr>
<blockquote><td><b>#1000*1815137*55##</td></b><td>SET</td>
<td>DIMENSION_REQUEST</td>
<td>CONFIGURATION</td>
<td></td>
<td>UNIT_DESCRIPTION_REQUEST</td>
<td></td>
<td>113446</td>
<td>1</td>
</blockquote></tr>
<tr>
<blockquote><td><b>4*57*0#1815137##</td></b><td>GET</td>
<td>BUS_COMMAND</td>
<td>THERMOREGULATION</td>
<td>LOW_FAN_SPEED</td>
<td></td>
<td></td>
<td>113446</td>
<td>1</td>
</blockquote></tr>
<tr>
<blockquote><td><b>#1000*0#1815136*51*422993*17*55*2##</td></b><td>GET</td>
<td>DIMENSION_REQUEST</td>
<td>CONFIGURATION</td>
<td></td>
<td>DEVICE_DESCRIPTION_STATUS</td>
<td>reference=67451;version=11;function_code=55;units_count=2</td>
<td>113446</td>
<td>0</td>
</blockquote></tr>
<tr>
<blockquote><td><b>#1000*1815136*51##</td></b><td>SET</td>
<td>DIMENSION_REQUEST</td>
<td>CONFIGURATION</td>
<td></td>
<td>DEVICE_DESCRIPTION_REQUEST</td>
<td></td>
<td>113446</td>
<td>0</td>
</blockquote></tr>
</table>