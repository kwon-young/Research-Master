# Réalité Virtuelle

## Placement adaptatif d'objets

Mondes Virtuels

* exemple : roman
* Images : produite par ordinateur
  * infographie 2D/3D
* Pbm lors de la génération d'image 2D
  * 1 seul point de vue
  * pas d'interaction temps réel
* Definition RV :
  * représentation du monde virtuel
  * un utilisateur
  * signaux pour sentir le monde
  * possibilité d'action pour agir dans le monde virtuel
  * temps réel
* Question
  * Comment représenter les mondes virtuels
  * Comment les faire ressentir à l'utilisateur
  * Comment créer un monde virtuel

### Comment représenter les mondes virtuels

* On reste à la surface
* Nature des mondes virtuels
  * un ensemble d'objets
  * on voit, entend, bousculé … par les objets
  * notion de perception des objets
    * direct
    * indirect
      * oeil
      * source lumineuse
      * surface de réflexion
      * modèle très simple
        * pas d'ombre
        * pas de mirroir
* surface = foorme + aspect
  * aspect = modèle d'éclairement ou texture
  * forme = géométrie dans l'espace | algèbre
    * f(x, y, z) = 0
    * géométrie algorithmique
      * surface est un ensemble de triangle
      * grosse accélération matériel
      * représentation polygonale des objets
* Représentation polygonale
  * un triangle est formé par 3 points
  * utilisation d'un repère pour représenter les points
  * pour représenter un objet, on donne la liste des triangles
  * problème de redondance
  * solution : représentation partagée des maillages (surfaces)
    * tableau de sommets
    * tableau de faces : indices sur des sommets
    * représentation interne des modèles : en mémoire
    * représentation externe des modèles : dans fichier
      * pour plus : alias wavefront obj
* Placement des objets
  * création de primitive géométrique
    * sphere
    * boite
    * ou juxtaposition de primitive
    * caractériser par un nom et des paramètres
    * pour simplifier, on jarte les centres
    * on utilise des primitives canoniques centré à l'origine
      * rayon 1 pour une sphère
      * l=h=p=1 pour une boite
  * génération d'objet à partir de transformation géométrique
    * rotation
    * translation
    * mise à l'échelle
    

### Stirring

## Architecture Cognitive

## Agent conversationnel animé
