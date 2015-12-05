# Large scale tissue morphogenesis simulation on heterogamous systems based on a flexible biomechanical cell model

## Author

* Anne Jeannin-Girardon
* Pascal Ballet
* Vincent Rodin

## Science Domain

* computational biology
* virtual cell
* virtual tissue morphogenesis
* multi-agent systems
* parallel programing
* parallel simulation

## Abstract

Complexity is interesting.
In silico simulation to have a better understanding.
Why complexity ?

#. large amount of cell
#. complex interaction and behavior

Two tools to resolve complexity.

#. virtual cell model
    * mechanical structure
    * main behavior : mitosis, growth ...
    * physical constraints
    * artificial chemistry
    * agent-based formalism
#. opencl simulator
    * parallel simulation

2 experiments to validate the model.

* cellular proliferation
* limb growth

## Introduction

Presentation of tools for:

* simulating biological systems
* complement to *in vivo* and *in vitro* experiments
* better understanding these systems

It's a complex task but advancement in both biology and computer science make things easier.
Allows the simulation of multi-cellular systems.

Multi-cellulars systems:

#. big number of cells
    * cost computer power
#. diversity of cells and behavior
    * specific dedicated alg

Use of multi-core device makes it possible.

Cross-validation between multiple scientific domains : comp sc, math, bio ...

* Cell model : mechanical approach
    * space forces and constraints.
    * internal structure model : internal stability
    * Major impact in cell behavior.
* Cell behavior
    * mitosis
    * motility
    * adhesion
    * cell growth
    * differentiation
    * molecule consumption & production
* dedicated data structure and alg
    * for simulation on multi-core devices

Purpose of this article:

* propose an efficient cell model for intensive simulation of biological cell systems.

Flexible model, many parameters can be user-defined.

* user-defined model
    * include most behavior of a cell, cf up
    * with mechanical properties
    * dedicated structure and alg, relies on OpenCL
* user-defined simulation

## Related works

Many cell-centered models in literature.

* E-Cell : single cell centered with full genome
* ChemCell : single cell centered with chemical reaction within cell
* VirtualCell : detailed cell model for internal cell processes study

Not suited for simulation big cell systems like a fragment of tissue.

Other cell-centered model for modeling tissue is hybrid : discrete cell and continuous behavior.

* Cellular Potts Model (CMP) with multiple extension
* Agent-Based Model (ABM) : originally purely discrete, but complexity of systems force use of continuous elements
    * great liberty in modeling : discrete of cont, ...
    * Cell2Organ : generate complex systems with single cell, multithreaded
    * many other models ...
* simulation software
    * CellSys
    * Flame
    * FlameGPU

Focus of the article.

* ABM
    * high level of description for agent
* continuous env
* discrete cell neighborhoods grid
* artificial chemistry implemented with partial diff equ
* ABM are flexible : add of element is simple
* ABM exploratory aspect : can rerun simulation at will
    * deduce or refine model incrementally
    * explore set of parameters
    * validate hypothesis

Cell structure based on mass/spring systems.
Behavior modeled through agent-based formalism.
Do not model intra-cellular processes.
Simplified cell-cycle.
Use of OpenCL Framework on multi-core CPU or GPU.

## Virtual cell model

#. mechanical part
    * deformable cell model
        * can model cell deformation
        * can model mechanical constraints and influence behvior
        * can model structural stability : impact on behavior
#. basic behavior of biological cells
    * mitosis
    * motility
    * adhesion
    * cell growth
    * differentiation
    * molecule consumption and production

### Cell physics

Physical structure

* mass/spring structure
* $n$ membranes nodes : $N_{i}(0 \leq i < n)$, plus central node C

Connection between nodes : # insert Fig 1 from article

* cytoskeleton : between ns and C
* cortex : ${N_{i} \leftrightarrow N_{(i+2)%n}\}$
* membrane : ${N_{i} \leftrightarrow N_{(i+1)%n}\}$
* simplified representation of a cell
    * allow deformation
        * compression
        * stretching
    * preserve physical integrity

Cells interactions.

* use of Hooke's law : $F = kl$ # Force needed to stretch a spring of a length l is proportional to l
* restoring force : $\vec{F_{l}} = k(l - l_{0})\vec{u} = k\Delta l\vec{u}$
* interact with env and neighbor cells

#### Environmental interactions

Env influence on cell.

* Langevin force : $\vec{F_{l}} = I\vec{u}$
    * model random collision
* repulsion force to keep cell in the env boundaries : $\vec{F_{edges} = k(l - d_{cell,edge})\vec{u}$
* fixation coefficient : $\phi \in [0, 1]$
    * model adherence to the extra-cellular matrix #fluiditer de l'env ?

#### Cell-cell interactions

* adhesive force between cells : $\vec{F_{a}} = k(l - d_{max})\vec{u}$
    * if too close : become repulsion
        * minimal distance between center of cells
    * if too far : break linkage
    * selection of nodes : choose those that are between two centers of cells
* repulsive force if cells too close
    * same node selection mechanism

#### Numerical integration

Use of Euler method for integration.
Cope with drawbacks of the method.

* consider the environment as damped : limit numerical instability
* choose a time step small enough

Advantages.

* fast computation time
* Integration using Newton's law

Add table of system parameters.
System parameters found in literature.

Calculus of the maximum integration step $\Delta t$.
Use of a worst case scenario to calculate an upper bound for $\Delta t$.
Calculate the maximum distance $x_{1}$ an node can move during a $\Delta t$.
Resolve the inequality : $l_{0} \leq x_{1} \leq x_{0}$

### Simplified cell cycle

Biology cell cycle defined by multiple consecutive phase.

* G1 : cell growth
* S : DNA replication
* G2 : cell growth, protein synthesis
* M : division of a cell in two daughter cells
* GO : idle
* Cell Death

Choose a simple model of cell cycle as a state machine.

Include Fig 3 of article

Transition decided by

* size of the cell
* energy
* stochastic process only

### Mitosis

Division of cells by.

* "cutting" cells
* re-position of cells to preserve original cell structure.

* use of division axis
* orientation of the division is up to the user to decide

### Cell growth

Use of a scale factor that defines radius of cells and is calculated relative to the age of the cells.
Age 0, cell has halve the size of and adult cell.
Adult size and growth speed depends on the type of the cell.

We repeat the same equation with a different parameter Td for division process.

### Mechanical stresses evaluation

Evaluation of mechanical stresses.
Allow cell to differentiate, apoptose, specialize, or adapt shape and size.

#### Compression / stretching evaluation

Computing area of cells as triangle (3D, kahan's formula).
Fig. 4 show compression force.

#### Shearing evaluation

Shearing forces computed from couple applied to cells.
Fig. 5 show shearing forces.
Example of multiple layer of tissue moving in opposite directions.

### Molecule consumption and production




