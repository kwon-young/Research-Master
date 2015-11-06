# Capteur Virtuels

## Humanoïdes Virtuels

* Environnement statiques
* Animations prédéfinies
  * ligne droite
  * ligne courbe : courbe cubique
* utilisation d'humanoïde virtuel pour remplacer les humains
  * entité réactive, ne fait quelque chose que si on les provoques
  * entité pro-active : a un but à part entière

## Système visuel humain

* chez un humain
  * système visuel prédominant

Eric Maisel :
> la nuit, tous les chats sont gris !!

## Acteurs virtuels autonomes

* acteurs virtuels autonomes
  * il n'y a pas besoin d'avoir autant d'acteur que d'avatar
  * pas d'intervention extérieur pour la décision
  * règles et buts propres
  * réactions à l'environnement
* avatars
  * controlé par les utilisateurs
  * animation temps réel
  * périphériques de saisie complexes

## Acteurs virtuels autonomes perceptifs et interactifs

* réagissent à leur environnement
* comportement propre
* prennent des décisions basées sur :
  * perception de l'environnement : utilisation de capteur
  * mémoire : sauf pour le poisson rouge
  * raisonnement : inférer des décisions, conclusion en fonction de la perception, mémoire de travail, mémoire à long terme
* peut communiquer

## Boucle comportementale

* env.init()
while (true)
  env.update()
  for acteur in acteurs
    acteur.perceive(env)
    acteur.decide()
  for acteur in acteurs
    acteur.act()
  env.draw()

## système visuel des acteurs virtuels autonomes

* approche basée sur un accès à une base de données
  * on stocke dans une base de donnée
  * apparence
  * physique
  * comportement
  * géométrie
* approche basée sur un calcul d'images (vision synthétique)
  * géométrie, apparence, sémantique -> images
  * traitement des images calculées

## procédures géométriques

* mondes virtuels décrits par des bases de données
  * groupes de polygones
  * matériaux
* prises d'informations visuelles
  * applications de procédures de géométrie algo sur ces bases de données

## optimisation géométriques

* utilisation de volumes englobants
* utilisation de structures de données spatiales
  * définines par la structure du modèle
  * calculées
* comparaison
  * grille + simple à construire et à mettre à jour
  * hiérarchie + proche des distributions non uniformes

## perception dans un groupe d'entités autonomes (reynolds 87)

* objectif :
  * déplacement d'un groupe d'entités
    * eviter les collisions dans le groupe
    * garder l'aspect groupé
  * parmi des obstacles
* description des déplacements par un animateur
  * fastidieux
  * résultat peu crédibles
* solution : simuler le comportement des entités
* dynamique des entités
  * intégrer accélération et position
  * paramètres de chaque entité :
    * position
    * vitesse
    * ...

* sterring
  * force séparation
    * som(Pi*P/||Pi*P||²)
    * boyds ne voient pas à l'infini : ex shpere centré sur l'individu
  * force cohésion
    * calcul du centre de gravité des entitées perçues
  * force d'alignement
    * moyenne des vitesses des boyds voisins

* capteur virtuel
  * fonction de
    * la distance
    * la position angulaire relative

## perception des utilisateurs dans un envt virtuel collaboratif

* benford and al : " a spatial model of interaction in large virtual environment"
* perception basée sur un modèle aura, focus, nimbus
* 6 concepts
  * media : vue, son
  * chaque objet est doté de 3 régions (aura, focus, nimbus) par media
  * aura :
    * volume englobant le focus et le nimbus
    * permet d'optimiser les calculs
  * Focus :
    * plus un object B est dans votre focus, plus vous faîtes attention à lui
  * nimbus :
    * plus B est dans le nimbus de A, plus il fait attention à A
* l'attention d'un objet A pour un objet B représente l'importance de cet objet
  * l'attention est quantifiable
  * l'attention est spécifique à chaque média
  * l'attention n'est pas une relation symétrique

* adaptateurs
  * modifier le nimbus (micro, podium, porte voix ...)
* Frontières :
  * plans, séparations :
    * obstructives (mur opaque)
    * non obstructives (fenêtres)
    * conditionnellement obstructives (porte)
    * Transformation (vitres teintées fumées)
    * dépendant du média

## Objectif

* simulation d'un trafic routier
* on peut faire une simulation macroscopique avec des équations
  * physique des fluides
* pas possible pour des trafics routiers situés dans une ville
* interaction avec le trafic
* représentation microscopique du trafic
  * simulation de conducteurs virtuels
    * perceptifs et interactifs

## Principe

* Importance de la prise d'informations visuelles
  * dans le monde réel
  * donc dans la simulation
  * example : origine des accident de voiture : mauvaise prise de connaissance visuel
* Architecture de prise d'informations visuelles
  * Tâches de conduite
    * exploité par le controlleur de perception
  * Actions perceptives
  * Capteur
  * Contrôleur de perception
    * decision de où est-ce que l'on prend l'information
  * Processeur d'actions perceptives
    * scheduleur de commande de perception
  * Utilisation d'une mémoire (pour se souvenir de ce qu'ils ont vu)

## Tâche de conduite

* tache de conduite
  * que faire dans une situation particulière

## Capteur

* Contrôle conducteur centré
* Contrôle par le lieu
* Filtrage sémantique

## Routines de perception

* prise en compte du temps
  * par le processeur d'actions perceptives
    * action percpetives
    * liste d'actions en attente
  * spécification qualitative
    * interprétation selon la situtation

## Prise en compte du temps

* permet de simuler certaines situations eventuellement
accidentogènes
* permet une variété des conducteurs

## Objectifs

* Simulation d'un grand nombre d'agents perceptifs
* Système générique et extensible
* efficacité des calculs de perception

## Filtres

* Structure d'un filtre
* Différents types de filtres
  * filtre basé sur la distance
  * champ de vision
  * collision
  * sur les couleurs
  * type d'objects
  * topologique

## Pipeline de filtres

* pipeline
  * connexion d'un capteur (vue, son) à un comportement
  * a travers plusieurs filtres
* exmple de combinaison de filtre (type + fov)

* 3 type de transmission entre filtres
  * mode transparent
  * mode filtrage
  * mode opaque
* partage de filtres entre pipelines

## Objectifs

* noser : partie de tennis
* kuffner, enrique : navigation dans un envt dynamique

## Principe

* Base de données 3d
  * I
  * P(i)
  * T(i)
  * V(i)
  * R3d(i) : représentation 3d (polygones + matériaux)
* calcul de deux images pour chaque acteur virtuel
  * caméra utilisée :

* images calculées
  * image scène éclairée
  * image en fausse couleur
    * polygone de OBJi : association d'un couleur propre à OBJi
* codage proposé par kuffner
  * pour i -> (i, i, i)
    * image en niveaux de gris

## Avantages - Inconvéniants

* Avantages
  * connaissances des objets perçus par l'acteur virtuel (quoi et où)
  * accès à l'information sémantique (gris = clé d'accès

## Extensions de Enrique

* Id : associés à des types d'objets
* Codage d'informations de déplacements
  * codage statique
  * codage dynamique
    * calcul de trois image
      * reel, statique, dynamique

## Objectifs

* Simulation comportementale de
  * poissons virtuels
  * humanoïde virtuels

## Principe

* Estimation des profondeurs
  * yeux orientables
  * focalisations des yeux

* Distribution non uniforme des cellules photo-réceptrives sur la rétine
  * visions fovéale et périphérique
  * 4 images / oeil (- couteux)
  * Résolution identique sur des surfaces différentes
    * Fréquences d'échantillonnage différentes

# Focalisation de l'attention visuelle

* yeux sont des mauvais capteurs
* champ de vision réduit
* exploration de l'environnement
* stratégie de prise d'informations
  * stratégie ascendantes (informations exogènes)
    * cape rouge pour le taureau
  * stratégie descendantes (tache à accomplir)
    * le regard travail par saccade
    * les points de fixations dépendent de la tâche à accomplir

## Carte de saillance

* saillance :
> qui est en évidence, ressort du contexte et s'impose à l'attention
Petit Robert
* Association à chaque pixel d'une image d'un nombre : sa saillance

* Stratégie ascendante
  * bottom-up
    * on va d'un signal à du sens
  * un événement exogène capturant momentanément l'attention visuelle
  * correspond à la sensibilité de l'oeil aux contrastes
    * luminances
    * couleur
    * mouvements
  * approche en deux temps
    * calculer les saillances de l'image rétinienne
    * chercher le point le plus saillant (point de focalisation)
      * winner take all

* to calculate la carte de saillance
  * combinaison linéaire de résultats de filtre
    * de mouvement
    * couleur
    * orientation

* orientations
  * filtre de gabor
    * filtre fréquential localisé dans l'espace

* Objet : controler un humanoïde virtuel de façon à ce qu'il dirige son regard vers les points les plus saillants

* Données obtenues par le moteur graphique 3d de l'application (image + z-buffer)

* filtrage appliqué aux images chromatiques et de profondeur
  * application de filtres de gabor
  * combinaison de résultat et du z-buffer
* application d'une gaussienne

* modèle simple de saillance
  * possibilité d'extension
* application à la réalité virtuelle
* en 2003 : calcul d'une carte de saillance en 100ms
* objets détectés :
  * signalisation routière, maisons, trottoirs

* asservissement de la tête et des yeux aux points de focalisation
* mais
  * abscence de mémoire
    * fixation d'un même point (le plus saillant)
  * problème de validation
