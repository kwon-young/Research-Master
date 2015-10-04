# Connaissance, model and paradigm

this course is oriented IA and machine learning

sujet de tp avec du code, il faut faire !!!!

## meta-heuristique for hard optimisation

Optimisation :

* define a cost function
* how to get the best solution, minimize cost function
* there is constraint

Discret problem :

* routage : ex : voyageur de commerce
  * pbm NP complet
  * combinatory optimisation
  * affectation quadratique : ex placement de composants

Combinatory optimisation :

* S is very large
* s is a solution
* f cost function
  * en fonction du problème, c'est plus ou moins compliqué

Find optimum

* start with a bad, aleatoire solution
* small modification can change cost drastically
* sometimes you find good solution : local minimum
* objective : find the global minimum

difficulties :

* very big pbm : NP complet
  * combinatory explosion

solution : heuristic

* heuristic is bidouille
* guaranty reasonable time
* but doesn't guaranty best solution
* domain specific

so we do meta-heuristic

* no domain specific
* can be applied to main problem with commune property

example of meta-heuristic 

* phyisque : recuit simulé
* biologie : GA, NN
* ...

commune principle

* start with a initial solution
* applied cost function : this is difficult
* make a movement : this is difficult to find
  * the movement need to be in the neighbourhood
* stop criteria
* pro :
  * those algo are very robust
  * there are random
  * directes
  * extension, hybride
* less :
  * approach method
  * slow
  * difficult to tune parameter

* global search : diversification
* local search : intensification

* Method of monte-carlo
  * we do n'importe quoi
* iterative method
  * we start from good solution
* simulated annealing
  * method to make a diamond
  * cycle of heat and freeze
  * criteria of state of energy and cold
  * objectif : convergence without getting stuck in local min
  * strategy : 
    * explorate first
    * then exploit
  * how
  * next solution can be badder
  * but is less badder more we go through the algo
* loi de boltzmann
* probability

Convergence :

* often convergence is guaranted

Research tabous

* add memory
* can't revisited area we have already visited

Colonie de fourmis

tester avec shader

* attraction
* cohesion
* repulsion

## Genetic Algorithm

* optimisation technic
* based from biology
* developed by John Holland in 1970's

* optimisation technic for artificial learning of parameter

* Programmation génétique : Aller voir !

Principle of AG :

* Encode the problem
  * gene
  * X
* Initial population
* evaluation
* selection of parents
* cross-over, mutation


