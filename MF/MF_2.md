# Formal models
## A taste

### Introduction

* What is a formal model
  * a model using a formal model
  * a model is the object that represent a system
  * a model has a goal
    * we can reason on this model
  * a formal language is a language that syntax and semantics has been characterized mathematically
    * example : first order logic, turing machines, ...
    * counterexample : french, english, C++, UML, ...
      * in FL, semantic has to be unique
      * in PL, semantic is to hard to be exprimed by math
  * goal
    * replace meaning by computation
* why do we use formal models
  * standard use for the delimited study of a domain
    * modelisation démarche
  * 4 domains in computer science
    * study foundations of languages and their properties
    * build formal models
    * verify properties of a system
    * implement safe mechanisms of computation
  * needs
    * explicits all assumptions, hypothesis
    * reasoning is based only on rules defined before
      * rules are inference rules

* The lambda-calculus [Church]
  * FL to model the notion of function
  * use of LC to illustrate notion of a FL

### Defining a language

* a language is a set of terms combining symmbols from an alphabet
  * use concat to use string concatenation
  * use of empty sentence
  * *free monoïd*
  * a language is a subset of the monoïd
* computer science focuses on finitely generated languages
  * the set of terms can be described by a finite set of information
* study and classification of languages is formal language theory
  * how do we defined a language
  * recognize a terms *efficiently*
* defining a concrete syntax
  * a concrete syntax is generally defined by a grammar
    * define a sort of base (math speaking)
  * a grammar is defined using BNF/EBNF
    * a set of production rules defining non-terminals as combinations of non-terminals and terminals
  * the concrete syntax focusses on interaction with the user
    * must be readable, efficient, ...
    * must solve the ambiguities, priorities, associativity, ...
* Defining a (n abstract) syntax
  * an abstract syntax describes the essential content of a sentence
  * it aims at being used by any tools manipulating terms
  * It is defined by a signature
* Terms as trees
* Naming
  * we use names to
    * *metavariable* : represent a set of terms (MAJ)
      * macro in lisp ?
    * *variable* : represent an unknown part of a term (min)
  * metavariable are not part of the syntax and used only inside metaterms
    * a metaterm is a set of term
    * useful to manipulate or to describe properties of sets of terms
  * variable are part of the term
    * syntax must be extended
    * a variable may occur several time within a term
    * the meaning of a variable is given by replacing all its occurrences by a term
    * a term T containing x can be viewed as a function from term to term
* variable
  * a term without a variable is a ground term or closed term
  * variables are leafs
* Substitutions
  * the meaning of a term containing a variable depends upon its context of use
* Scoping
  * we need to define that in the syntax by binders
* The syntax of the lambda-calculus
  * contains 3 constructions
    * variable
    * application, constructor of ar 2
    * function or abstraction, binding
* variables in the LC
  * L is a binder
  * free variable : it's a sort of a global variable
  * combinators contain no free variable
* Induction
  * a method of construction (definition) or proof
    * example : recurrence
  * structural induction
    * prove for all constant and variable
    * prove for all constructors and binders
  * well-founded induction
* Substitution on LC
  * defined inductively
    * prevent captures
  * alpha-equivalence
    * freshness condition
* redo LC rewriting

### Giving meanings to syntax

#### Giving meaning

* three way
  * axiomatic semantics
  * denotational semantics
  * operational semantics

#### axiomatic semantics

* defined by systems of equations describing the effect of each syntactic construction to logical assertions
* Gives a macroscopic vision of : consistency, completeness, compositionality
* Hoare triple

#### denotational semantics

* defined by a projection in a known mathematical space
* gives an abstract vision of the meaning
* used to study meta-theory : fixed-point theory, ...

#### operational semantics

* each term reduce to another (smaller) term or is a value
  * when we attain value, calculus is finished
* defined computation rules (rewriting)
* small-step or big-step
* gives a microscopic vision of the meaning
*
