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

Résumé

* langage formel
  * un terme est un model
  * syntax
    * abstraite : défini de manière algébrique, un terme est un arble
      * les feuille sont ou bien des variable ou des constantes
      * les noeuds sont des constructeurs ou lieur
      * définition par induction
  * sémantique : donner du sens
    * sémantique axiomatique
    * sémantique dénatotionnel
    * sémantique calculatoire

## Reduction of ^x

Church-Rosser theorem

> Bheta-reduction is confluent on ^x

* a term has at most one normal form
* reduction strategy
  * by value : innermost reduction
  * by name : the outermost reduction

## is ^x a programming language

* in theory, ^x is turing complete
* in practice, not usable by human
* we extend its core with
  * basic datatype (integer, boolean, ...)
  * data structures (pairs, lists, ...)
  * recursion
  * ...

## Church numerals

*Faire les exercices*

## classifying terms of ^x

* some terms have odd comportement
  * only finit reductions, well-behaved
  * have both finite and infinite reductions
  * have only infinite reductions
* we want to get rid of infinite reductions
  * two ways
  * use a stricter syntax (often impractible)
  * we use types and then work on the subset of well-typed terms
* types are names for sets of terms
* => tpes are about classification of terms
  * structurally (on their syntax)
  * and / or behaviorally

## From mathematics to Fortran

* Russel's paradox

## Judgment and inference rule

* we try to link a type to a term
* a *judgement* is a logical assertion
* there exists various forms of judgment
  * term -> other term
  * environment |- term => Value
  * environment |- term : Type
* an *inference rule* is a collection of judgments
  * the *premises* (j1, ..., jn)
  * and the *conclusion*

## Derivation

* a *derivation* (or proof) is a tree of such rules where the leaves are axioms
* this tree can be build
  * from axiom to conclusion using *forward chaining*
    * blind search
  * from conclusion to axioms using *backward chaining*
    * goal directed search in the judgment space
* syntactic reasoning
* inference proof cannot proove that something is not true
* no way to say a judgment is not derivable

## Type systems

* a set of rules
* A *Type Judgment* has-type assertion : gamma |- Term : tau
  * gama being a *typing context* colleecting the types of variables
* a *Type Rule* is an implication between type judgments
  * int + int = int
* type system (TS) is a set of type rules
* *Type Derivation* is a logical deduction based on a TS
* *Type Language*

## Type Checks

* *Type Checking*
* *Typeability* : does my problem is derivable
* type inference (or type reconstruction) algorithm 
* Typeability is a lot harder than type checking

## Properties of the simply typed ^x-calculus

R. Milner in [Mil78]
> well-typed programs cannot "go wrong"

* strong normalization
  * a well-typed term has only finite reduction sequences
  * beta-reduction is strongly normalizing on ^xT
* proof is harder, it is not a direct induction
  * see [Pied02, ch12]
* is omega typeable (omega is infinite reduction)
  * so no, it is not typeable
* ^xT is not turing-complete

## static type checking

* more generally, Halting and Error discovery are undecidable
* to be decidable, a TS must use a safe approximation
* TS must reject some correct (but too complicated) terms

=> STS goes against flexibility and need a compromise
=> To achieve safety, we have to use runtime checks (array bound)

## formal definition of a TS

* the language definition
* type language definition
* set of Forbidden errors
* set of typing rules
* operational semantics of the language
* a proof of TS Soundness relative to semantics stating

*a typed program cannot cause forbidden errors*

* note on semantics of types
  * we haven't precisely stated what is a type
  * if we do not use too complex type relations, it is not necessary
  * usual interpretations of types: sets, ideal, tree
