# Integers

Integers for the [Occam](http://djalbat.com/occam) proof assistant.

This package is somewhat experimental. 
The idea is to define integers as either natural numbers or as natural numbers preceeded by a negative sign.
Put another way, the approach is not to have, say, two constructors for `zero`, one of type `NaturalNumber` and one of type `Integer`:
```
Type NaturalNumber
Constructor zero:NaturalNumber

Type Integer
Constructor zero:Integer
```
Overloading constructors in this manner would mean decorating them in some way under the hood, so to speak.
When the user encounters `zero`, it would be unclear as to whether the term were a natural number or an integer.

Instead, the types themselves are overloaded, specifically:
```
Type NaturalNumber
Constructor zero:NaturalNumber

Type NaturalNumber:Integer
```
Now the term `zero` is both a natural number and an integer, because the  re-declaration of the `NaturalNumber` type ensures that all natural numbers are integers.
Note that since this package depends on the [natural numbers](https://openmathematics.org/#natural-numbers) package, this is indeed a re-declaration.
Re-declarations in order to afford sub-typing are one reason why this package should be regarded as experimental.

To continue, negative integers are then defined axiomatically:
```
Axiom 
  n:NaturalNumber iff -n:Integer

Axiom
  zero=-zero
```
Again this is arguable.
It requires a dependency on [propositional logic](https://openmathematics.org/#propositional-logic) that might otherwise be avoided.
Its advantage is that it is easy to extend expressions to support terms such as `-n`, see the [negatives](https://openmathematics.org/#negatives) package.

A possible, but admittedly extremely ugly, alternative is the following:
```
Constructors NaturalNumber:Integer,-NaturalNumber:Integer
```
This avoids any dependency on propositional logic, it could be argued that it should be possible to define integers without recourse to logic after all.
But it is not immediately obvious how to extend the grammar to support this construction.
So for the moment the re-declaration of types in order to afford sub-typing, together with the axioms, stays.

## Notes

* As of writing, the [Florence vernacular](https://raw.githubusercontent.com/occam-proof-assistant/Parsers/master/es6/florence/bnf.js) does not support sub-typing.
Support could be added by replacing this line...
```
typeDeclaration ::= typeName ;
```
...with the following:
```
typeDeclaration ::= typeName ( ":" typeName )? ;
```

## Contact

* jecs@imperial.ac.uk
* http://djalbat.com
