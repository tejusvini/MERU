# MERU Design Principles

MERU is a system for discovering and describing structural patterns.

Unlike conventional statistical models, MERU focuses on **structural invariants** that emerge from relationships within data.

The MERU Pattern Language (MPL) exists to represent these structures in a minimal and machine-readable form.

---

# Structural Recognition, Not Prediction

MERU does not attempt to predict or classify input.

Instead, it detects structural properties that can be described as patterns.

Examples of structural properties include:

- repetition
- symmetry
- growth
- positional relationships
- structural dependencies

These properties are represented using MPL expressions.

---

# Multiple Valid Interpretations

MERU does not assume there is a single correct interpretation of an input.

A structure may have multiple valid descriptions.

Example:


11


Possible interpretations:


#[11]
&[#[1]]


Both descriptions may be recorded.

MERU does not discard alternatives.

---

# Programs Are Structural Descriptions

A `PROG` in MERU represents a **set of patterns that describe a structure**.

Programs do not represent solutions or winning hypotheses.

They represent structural explanations.

Example:


PROG(SYMMETRY) = PROG[
CENTER :> MIRROR
]


This states that mirror symmetry depends on the existence of a center.

---

# Separation of Perception and Structure

MERU operates after the perception pipeline.

The perception system processes raw input:


input
→ quantizer
→ triad grid
→ sensory layer


The pattern engine then constructs MPL expressions describing the detected structures.

The language itself never processes raw data directly.

---

# Minimal Operator System

The language intentionally uses a very small operator set.

self / value

@ observer
% mirror
& repeat

grow
< lookback


All expressions follow a single structural rule:


operator[object]


This produces a consistent tree representation.

---

# Machine-First Syntax

MERU syntax is designed primarily for machines.

Humans interact with the language through tools, visualizations, and documentation.

Consistency and deterministic parsing take priority over brevity.

---

# Structural Relationships

Programs connect patterns using a small set of relationship operators.


: coexistence
:> dependency
? conditional
| alternative


These relationships form graphs describing how patterns relate to each other.

---

# Structural Recording

MERU's goal is to **record as much structure as possible**.

Patterns are not discarded simply because alternative patterns exist.

Structural knowledge accumulates rather than replacing previous interpretations.

---

# Experimental System

MERU is currently an experimental system exploring structural pattern languages and pattern-based computation.

The language and architecture may evolve as the system develops.
