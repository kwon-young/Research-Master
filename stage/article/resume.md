
# Resume

## DMOS

### State of art problematique

On grammars :
* syntax of grammars too complex
* limited expressiveness
* no context in segmentation

### Concept

Difference in different structured document : *Domain Specific Knowledge*

Generic method to produce recognition system on structured document.
* Using grammatical formalism : *EPF*
    * simple syntax
    * important expressiveness by adding operators :
        * position Operator `AT`
        * Factorisation Operator `##`
        * Save Operators `---> <----`
        * Declaration Operator `DECLARE`
        * Space Reduction Operator `IN ... DO`
* Associated parser
    * automatically produced by compilation
    * contextual segmentation
    * can reject wrong shape

The system has built-in classifiers, but it can be connected to other
classifiers easily.

### Pros

* generic method : save time and energy
* enhance recognition quality
* EPF give more expressiveness
* introduce context in segmentation
* self check result by using *a priori* knowledge to avoid manual proofread


