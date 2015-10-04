# CMP

## Modélisation … UML et ses limites

### UML

#### Généralité

Contexte informatique

* Algorithme
  * recherche
  * pas de méthode
  * imagination
* Programme
  * méthode simple pour appréhender la prog facilement
* Système
  * gros
  * complexe

* Programme
  * boite
  * entrée
  * sortie
  * assimilable à une fonction

* Système
  * pas assimilable à une fonction
  * utiliser plusieurs points de vue
  * pour avoir une vue globale sur le système
  * couverture totale

Modèle d'une application informatique

* application = ensemble d'objets interagissant
  * chaque objet assume une responsabilité
* entité = description d'une séquence d'actions
  * couche métier
  * couche service
* colored UML

Modéliser = idéaliser(simplifier)

* à haut niveau : idéaliser
  * vitesse de calcul infini
  * ...

raffiner petit à petit

Voir à des niveaux d'abstraction différents

* pour simplier le raisonnement
* Conceptuel
* Spécification
* Implantation

Pour construire un modèle

* Observer
* Questionner
  * Traquer ce qui est implicite
    * ce que l'on veut faire et pas faire

Quoi produire ?

* le modèle du système a-t-il un sens
* faut-il construire un modèle unique ?

Modélisation

* chercher l'outil ultime est idiot
* les différents point de vue se relie ou pas
* l'outil ultime est la machine de Turing
  * pas du tout pratique

Que décrire dans un système ?

* il faut répondre aux questions
* simplement
  * dimension structurel
    * qui, où, combien
  * dimension fonctionnel
    * que, quoi, comment
  * dimension temporel
    * quand
  * pourquoi ? question fondamental
* et de nombreuses propriétés non fonctionnelles
  * propriété émergence
  * produit de l'assemblage

Modèles

UML contient beaucoups de *points de variations sémantiques*

### Objet

Polymorphisme = une variable peut avoir plusieurs fonctions, donc plusieurs type

Type D o = new Type R(); 

condition Type R sous-type <: type D

exemple = héritage; implementation

Gains attendus

* Analyse et conception "naturelle"
* Abstraction
* Réutilisation
* raffinement et extensibilité

OOP oversold

* Objet à tous les niveaux : granularité trop fine
* miese "en table" RDB délicate
* héritage compliqué
* disparition des boites noires
* interfaces éclatés : spaghettis

but d'un langage

* imposer des contraintes
  * éviter les goto
  * utiliser les exceptions

Objet spaghettis

* L'interface API d'une classe ne suffit pas à comprendre une classe

pour comprendre un objet

* lire les commentaire

Spécifier

* Décrire complètement, de manière non contradictoire le fonctionnement d'un élément (logiciel)
  * comment l'utiliser
  * ce qu'il fait
  * comment le partager
  * quelles qualités attendre
* assertions
* Object constraint language
* besoins
  * accès à l'état antérieur @pre

#### Encapsulation et contrat

#### UML/OCL



#### polymorphisme et liaison dynamique

#### la relation tout-partie

#### UML/point de variation sémantique
