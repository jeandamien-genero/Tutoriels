# Résoudre le Rubik's cube

## Constitution du cube

### Les pièces

* Pièces centrales : fixes et unicolores ;

* Pièces arrêtes : mobiles et bicolores ;

* Pièces coin : mobiles et tricolores ;

### Les faces

* Avant : _front_ (F) ;

* Arrière : _back_ (B) ;

* Haut : _up_ (U) ;

* Bas : _down_ (D) ;

* Droite : _right_ (R) ;

* Gauche : _left_ (L) ;

### Les mouvements 

* F : un quart de tour dans le sens des aiguilles d'une montre ;

* F' : un quart de tour dans le sens inverse des aiguilles d'une montre ;

* X2 : demie tour, peu importe le sens

* R : face de droite vers l'arrière ;

* R' : face de droite vers l'avant ;

* L : face de gauche vers l'avant ;

* L' : face de gauche vers l'arrière ;

## Résolution du cube

### Face blanche

#### Croix blanche

* Faire remonter les arrêtes blanches ;

* Mettre les arrêtes au-dessus du centre qui leur correspond : demi-tour de la face choisie, positionner l'arrête en-dessous du centre recherché, nouveau demi-tour.

#### Coins blancs et première ligne

* Placer le coin recherché en-dessous de sa position et faire  R' D' R D

#### Deuxième ligne

* Mettre la face jaune au-dessus ;

* Choisir une pièce arrête sur le haut qui ne contient pas de jaune ;

* Mettre la couleur de la face avant de cette arrête au-dessus du centre correspondant ;

* 1er cas : la pièce arrête en haut doit basculer à gauche : U' L' U L U F U' F'
 
* 2ème cas : la pièce arrête en haut doit basculer à droite : U R U' R' U' F' U F

* Faire remonter les pièces à placer qui sont sur la deuxième ligne en haut avec  une des deux formules.

* Si une arrête est bien placée mais inversée : R U R' U2 R U2 R' U F' U' F

* Si une ligne de couleur est complète mais que les deux arrêtes doivent être inversée : R2 U2 R2 U2 R2


### Croix jaune

#### Faire la croix

* 1er cas : juste le point jaune : R' U' F' U F R = amène au cas de la barre jaune

* 2e cas : barre jaune : cube avec la barre horizontale : F R U R' U' F'

* 3e cas : j jaune : cube dans le sens du j : R' U' F' U F R

#### Mettre les arrêtes au-dessus du centre qui leur correspond

* 1er cas : deux arrêtes bonnes côte à côte : en mettre une au fond et une à gauche : R U2 R' U' R U' R' U'

* 2e cas : deux bonnes face à face : mettre une bonne devant : R U2 R' U' R U' R' 

* 3e cas : tout est bien placé.


### Bien placer les coins

* Peu importe leur orientation, bien placer les coins

* 1e cas : un coin est bien placé ;

* 2e cas : il faut déplacer trois coins dans le sens des aiguilles d'une montre : placer le bon coin à droite :  L' U R U' L U R' U'

* 3e cas : il faut déplacer trois coins dans le sens inverse des aiguilles d'une montre : placer le coin bien placé à gauche :  R U' L' U R' U' L U 

* 4e cas : aucun coin n'est pas bien placé : L' U R U' L U R' U' : permet de ramener à un des deux cas précédents.

### Terminer le cube 

* 1er cas : deux coins côte à côte sont bien placés : face avec les deux couleurs identiques des coins mal orientés à droite : R U2 R' U' R U' R' L' U2 L U L' U L

* 2e cas : deux coins en diagonal sont bien placés : mettre le jaune à gauche vers soi : F R U2 R' U' R U' R' L' U2 L U L' U L F' 

* 3e cas : trois coins mal orientés avec le jaune à droite : la pièce bien orientée à gauche : R U2 R' U' R U' R' L' U2 L U L' U L : ramène au cas n° 1

* 4e cas : trois coins mal orientés avec le jaune à gauche : le coin bien orienté est en haut à gauche : R U2 R' U' R U' R' L' U2 L U L' U L : ramène au cas n° 1

* 5e cas : aucun coin n'est bien orienté : mettre deux couleurs identiques vers la droite : R U2 R' U' R U' R' L' U2 L U L' U L : ramène au cas n° 1

