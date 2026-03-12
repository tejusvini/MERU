MERU Pattern Language (MPL) Grammar

This document defines the formal grammar for the MERU Pattern Language (MPL).

MPL is a structural language used to describe relationships between patterns detected by the MERU structural engine.

The language follows a uniform operator-expression syntax that produces deterministic expression trees suitable for machine parsing.

1. Expression Rule

All MPL expressions follow a single structural rule:

operator[object]

Where:

operator is a structural operator.

object is either a value or another expression.

Examples:

#[5]
@[6]
%[#[5]]
%[@[][&[#[5]]]]

Expressions form nested trees.

2. Core Expression Grammar

The MPL grammar can be described using a simplified BNF notation.

EXPR        ::= OPERATOR "[" OBJECT "]"

OBJECT      ::= VALUE
              | EXPR
              | EXPR_LIST
              | EMPTY

EXPR_LIST   ::= EXPR
              | EXPR EXPR_LIST

VALUE       ::= INTEGER

EMPTY       ::= ""

OPERATOR    ::= "@"
              | "%"
              | "&"
              | "#"
              | "<"
              | ">"
3. Structural Operators

The core operator set is intentionally minimal.

Operator	Meaning
@	observer / reference point
%	mirror symmetry
&	repetition
#	value or structural element
<	lookback reference
>	growth / forward relation

Example:

#[5]

Represents a structural element with value 5.

Example:

&[#[5]]

Represents repetition of element 5.

Example:

%[&[#[5]]]

Represents mirror symmetry of the repeated structure.

4. Observer Expressions

The observer operator defines the reference location used for interpreting a structure.

Example:

@[6]

Observer positioned at index 6.

If no position is specified:

@[]

The observer defaults to the structural center detected by the MERU engine.

5. Pattern Definitions

Patterns define reusable structural descriptions.

Syntax:

PTRN(name) = expression

Example:

PTRN(MIRROR) = %[@[][&[#[5]]]]

Patterns represent structural properties rather than specific input sequences.

6. Program Definitions

Programs describe relationships between patterns.

Syntax:

PROG(name) = PROG[ relationships ]

Example:

PROG(SYMMETRY) = PROG[ CENTER :> MIRROR ]

Programs do not represent a single solution.
They represent possible structural explanations.

7. Relationship Operators

Programs combine patterns using relationship operators.

Operator	Meaning
:	coexistence
:>	dependency
?	conditional
|	alternative

Examples:

A : B

Patterns A and B both hold.

A :> B

Pattern B depends on A.

A ? C

Pattern A applies only if condition C holds.

A ? C | B

If C holds use A, otherwise use B.

8. Relationship Chains

Relationships may be chained.

Example:

A : B : C

Example:

A :> B :> C

Chains represent structural dependency graphs.

9. Named and Anonymous Patterns

Programs may reference patterns in two ways.

Named patterns
PTRN(CENTER) = >[#[8]]
PTRN(MIRROR) = %[@[][&[#[5]]]]

PROG(SYMMETRY) = PROG[ CENTER :> MIRROR ]
Anonymous expressions
PROG(SYMMETRY) =
PROG[ >[#[8]] :> %[@[][&[#[5]]]] ]

Both forms are valid.

10. Expression Trees

Every MPL expression produces a deterministic expression tree.

Example:

%[@[][&[#[5]]]]

Tree representation:

mirror
 └ observer
    └ repeat
       └ value(5)

This tree structure allows MPL programs to be executed and analyzed by the MERU engine.

11. Language Design Principles

The MERU Pattern Language follows several guiding principles.

Minimal operator set

Uniform syntax (operator[object])

Machine-first grammar

Structural descriptions rather than statistical inference

Multiple valid interpretations allowed

MERU records all structural patterns that can be detected.
It does not attempt to choose a single correct interpretation.

12. Language Status

MPL is currently experimental and evolving alongside the MERU structural engine.

The grammar defined here represents MPL v0.1.
