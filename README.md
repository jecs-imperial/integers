# Integers

Integers for the [Occam](http://djalbat.com/occam) proof assistant.

## Notes

This package is somewhat experimental. You can view it in the Florence grammar tool but not currently in Occam. In that tool, you need to replace the existing type declaration line...

    typeDeclaration                      ::=   typeName ;

...with the following:

    typeDeclaration                      ::=   typeName ( ":" typeName )? ;

The idea here is that although the `NaturalNumbers` type has already been defined, it can be redefined (essentially) to be a subtype of the `Integer` type. This means that this package can depend on the `natural-numbers` package, which seems the most natural way around (no pun intended).

## Contact

* jecs@imperial.ac.uk
* http://djalbat.com
