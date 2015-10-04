# Laboratoire Virtuel pour la Biologie

notation :
3 devoirs écrits après chaques paquets de cours

1 présentation pour restitution de papier en fin de semestre, décembre

2 homework

Informatique & Biologie
  Simulation de systèmes physiologiques humains

  1 - Syst multi-agents

Agent : Cycle perception-décision-action
Syst M-A : 
  - auto-organisation
  - émergence
  - robustesse
  - adaptabilité

Autonomie des modèles

Utilisation de la POO particulièrement utile pour implémenter un syst M-A
  - multiples agents avec une seule méthode vivre
  - un ordonnanceur qui boucle sur tous les agents
    - on préfère un ordonn aléatoire à un ordonn séquentielle pour une distri équitable
  - environnement commun, ex : échiquier

  2 - Expérimentation "in virtuo"

Exp in virtuo s'est fait par rencontre :
1997 : Immunologie
1998 : Hématologie
2001 : Cancérologie
2002 : Allergologie/Dermatologie
2004 : Modélisation endothémium

  cf slide p 3
  in vivo
boucle modèle du medecin -> interaction avec patient -> affinage du modèle
  
  in vitro
boucle modèle du medecin -> interaction avec éprouvette -> affinage du modèle

  in silico 
boucle modèle math -> sim in computer -> affinage du modèle //pas d'interaction avec le médecin

  in silico 
boucle modèle math du medecin -> sim in computer -> interaction avec medecin -> affinage du modèle

agent ~= cellule :
  - est dans son env
  - peut percevoir son env

syst M-A ~= syst M-Cellulaire
ex : travaux en immunologie : réponse humorale
cf slide 8 p4
Anti-gène
Macrophage
Cellule Présentant Antigène
Lymphocyte B
Lymphocyte T4 : tymus
Plasmocyte
Anticorps
Apoptose = mort cellulaire programmé

  3 - Mod & sim de syst physiologiques humains

niveau microscopique
agent-cellule/molécule : cel de base ~1 000 000 carte graphique 1 pc
  - comportement : libre de coder comme on veut
  - modèle spatial : disque ou sphère ou avec des ressorts
  - comportement de base :
    - mitose
    - activation
    - internalisation : récepteur disparaisse
    - expression de récepteurs
    - apoptose
  - recepteur codé numériquement, ex : nbr réel
    grosse simplification du réel
agent-situé : localisation x, y, z de l'agent dans un espace
ex : sim coagulation du sang
phénomène en cascade
hémophile de type A ou B
validation d'un modèle scientifique avec des données biologiques
thrombine ?

dans une simulation : très simple de plotter toutes les courbes que l'on veut

test d'hypothèse :
  anti protéine C
  anti protéine C + novoseven
courbe accidenté de génération de thrombine

niveau macroscopique
agent-réaction : Cycle perception-décision-action
au lieu de regarder chaques cellules / on regarde les concentrations
perception : lecture des concentrations
décision : calcul des concentrations pour effectuer des réactions chimiques
           vitesse de réactions
action : modif des concentrations
agent reaction est non-situé, ils sont dans un volume

échantillonage du temps en cycle où chaques agents vienne s'exécuter une fois
approche classique : equation diff
asynchronisme : chaques réactions s'effectue les uns après les autres
                intro de biais : ordre d'exécutn des agents
                on compense les biais par tirages aléatoire
intéret de la démarche : modif du syst en cours d'exécution
courbe lisse car pas de situation spatiale

### Agent interface

Mix between agent situé et agent réaction

we keep agent reaction and add agent interface between them
we cut the space into maille

Classicaly, math speaking :

* diff equat between maille
* variables = concentrations in every maille

point of vue agent :

* agent-interface is used in place of diff equation
* but we activate them in order
* agent-interface try to equilibrate concentration
* if we activate them in order, we introduce a bias
* so we activate them randomly
  * asynchronous phenomena
  * chaotic order

Exemple of coagulation :

* we split a 3D veine into maille
* we compute the 42 reactions in every maille

### Agent interaction

* Mixage de tout ces modèles
* Principe d'autonomie des modèles
  * simulation multi-modèles
  * paradygme systémique
    * syst logique
    * échange informatière entre *organisations*
    * systèmique : 
      * science
      * modelisation d'un sytème
      * interaction ou flux du système
      * état et sous état du système

Modèle agent-interaction

* Phénomène
  * agent interaction
    * agent interface : aspect flux
    * agent reaction : aspect organisation
  * composant : aspect organisation, exemple concentration
  * agent cellule : phénomène particulier
    * peut contenir des composants
    * peut contenir des agents interactions
  * agent organes : idem
* phénomène peut être vu comme un agent interaction particulier
  * peut modifier le niveau supérieur de concentration
* simulateur

Exemple cellule :

* cellule : 
  * Membrane
  * Cytoplasme
  * Noyau
  * agent reaction dans chaques compartiment
  * agent interface avec l'extérieur
* est contenu dans un milieu
  * agent reaction

## Régulatn de syst M-A

traitement d'image à l'aide d'agent

* agent dans une image pour détecter les stries concentration
* calculer le nombre d'anneau dans un otholite
* un agent simple :
  * a un capteur : perception locale des contours
  * deplacement : perception de la continuité
    * a un inertie pour suivre les anneaux et non les discontinuités
  * résultat pas cool
* agent de haut niveau :
  * connait la forme globale de l'otholithe
  * pbl de sur detection, car un agent travaille perpétuellement

source d'inspiration de la biologie :

utilisation des ph des régulation en biologie dans les systèmes de M-A

métaphore biologique
cf réponse humorale

* AIS de régulation
  * stimulant
  * travail à effectuer
  * travail effectué

* exemple d'utilisation d'AIS
  * on met deux agents blanc et noire
  * on répartis des stimulants aléatoirement dans l'image
  * agent se duplique quand il mange
  * agent meure si il ne mange pas
  * récompense quand travail effectué

## Conclusion

* Support de réflexion
  * besoin d'être valider par les biologistes



