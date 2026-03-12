# MERU Pattern Language (MPL)

The MERU Pattern Language (MPL) is a structural language for describing relationships between patterns discovered in data.

MPL does not parse raw input directly. Instead, it operates on structural features produced by the MERU perception pipeline:

raw input  
→ quantizer  
→ triad grid  
→ sensory system  
→ pattern engine  
→ MPL expressions

The language describes **structural relationships**, not raw data.

MERU does not attempt to find a single correct interpretation.  
Multiple valid structural descriptions may exist simultaneously.

---

# Core Syntax Rule

All structural expressions follow a single rule:


operator[object]


This rule applies uniformly across the language.

Examples:


#[5]
@[6]
%[&[#[5]]]

[#[8]]


This structure produces a deterministic expression tree that is easy for machines to parse.

---

# Structural Operators

MERU uses a minimal operator set.

self / value

@ observer
% mirror
& repeat

grow
< lookback


Examples:


#[5]


Represents a structural element with value `5`.


&[#[5]]


Repeat the element `5`.


%[&[#[5]]]


Mirror the repeated structure.


@[6]


Observer positioned at location `6`.

---

# Default Observer

If no observer position is specified:


@[]


The observer defaults to the structural center detected by the system.

---

# Pattern Definitions

Patterns are reusable structural descriptions.

Syntax:


PTRN(name) = expression


Example:


PTRN(MIRROR) = %[@[][&[#[5]]]]


Patterns describe **structural properties** that may hold in the sensory representation.

---

# Program Definitions

Programs describe relationships between patterns.

Syntax:


PROG(name) = PROG[ relationships ]


Example:


PROG(SYMMETRY) = PROG[
CENTER :> MIRROR
]


Programs represent **structural explanations**, not solutions.

Multiple programs may describe the same input.

---

# Relationship Operators

Programs combine patterns using structural relationships.


: coexistence
:> dependency
? conditional
| alternative


Examples:


A : B


Patterns `A` and `B` both hold.


A :> B


Pattern `B` depends on `A`.


A ? C


Pattern `A` only applies if `C` holds.


A ? C | B


If `C` holds use `A`, otherwise use `B`.

---

# Chained Relationships

Relationships may be chained.

Example:


A : B : C


Example:


A :> B :> C


Chains represent structural relationship graphs.

---

# Named and Anonymous Patterns

Programs may reference:

- named patterns
- anonymous expressions

Named pattern example:


PTRN(CENTER) = >[#[8]]
PTRN(MIRROR) = %[@[][&[#[5]]]]

PROG(SYMMETRY) = PROG[
CENTER :> MIRROR
]


Anonymous example:


PROG(SYMMETRY) = PROG[
>[#[8]] :> %[@[][&[#[5]]]]
]


Both forms are valid.

---
Position System

MERU patterns may optionally reference positions in the triad lattice.
The pattern language does not construct the grid; the triad engine provides the coordinate space.

Positions answer the question:

WHERE does the pattern occur?

Patterns may contain:

position + logic
logic only
position only
Origin

The default reference point is the origin.

@

Equivalent to:

ROW 0
SPINE

If no position is specified, MERU assumes the origin.

Row Movement

Rows extend in two directions from the origin.

+row  → north
-row  → south

Movement is expressed using operators:

>n@  move south n rows
<n@  move north n rows

Examples:

>1@
>2@
<1@
<3@
Columns

The triad grid has three columns:

W   S   E

Meaning:

W = west
S = spine
E = east

Column can be attached to a row position.

Examples:

>2.W@
>2.E@
<1.W@

If no column is specified, spine is assumed.

Apex

The lattice has a structural apex.

ROW -2
SPINE only

No lateral nodes exist at this row.

Example reference:

>2@
Position + Logic

Logic may be attached to a position using brackets.

Example:

>2.W@[&[#[5]]]

Meaning:

at row -2 west
repeat value 5

Parser output:

POS(row=-2, col=W)
   └ repeat
      └ value 5
Example Patterns

Repeat pattern at origin

@[&[#[5]]]

Mirror across the spine

%[
>1.W@
>1.E@
]

Repeat pattern two rows south west

>2.W@[&[#[5]]]
# Design Principles

The MERU Pattern Language follows several principles:

1. Minimal operator set  
2. Uniform syntax (`operator[object]`)  
3. Machine-first grammar  
4. Structural descriptions rather than statistical inference  
5. Multiple interpretations allowed  

MERU records all structural patterns that can be detected.  
It does not attempt to choose a single correct interpretation.

---



The language is currently experimental and evolving alongside the MERU structural engine.
