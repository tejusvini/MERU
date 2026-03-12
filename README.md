# MERU

**MERU** is a structural pattern engine that detects and generates patterns using a minimal operator language on a geometric lattice.

Unlike statistical models, MERU analyzes sequences by discovering **structural invariants** such as symmetry, repetition, and growth. These structures are represented on a triad grid and expressed through a small set of operators.

The system is designed to explore how patterns emerge, stabilize, and transform across different inputs.

---

## Core Idea

MERU works through a simple pipeline:

```
input sequence
→ quantization
→ triad grid structure
→ sensory feature extraction
→ pattern detection
→ operator representation
```

The result is a compact structural description of the pattern.

---

## Key Components

### Triad Grid

MERU organizes sequences on a **3×N lattice**:

```
L   C   R
```

* **C (center)** forms the spine.
* **L and R** hold symmetric lateral relationships.
* All structures must resolve back to the spine.

This constraint stabilizes pattern growth and prevents uncontrolled branching.

---

### Pattern Operators

Patterns are expressed using a small operator set:

```
@   anchor
%   mirror
&   repeat
#>  grow
#<  shrink
```

These operators form the basis of the **MERU Pattern Language (MPL)**.

---

### MERU Pattern Language (MPL)

MPL is a compact language for describing structural transformations.

Example:

```
% [#-1 #-2]
```

Meaning:

* mirror relationship
* using the previous two elements as reference

This representation allows patterns such as symmetry, sequences, and recursive growth to be expressed as operator formulas.

---

## System Architecture

```
input text
→ quantizer
→ triad structure generator
→ sensory head
→ pattern engine
→ self model
```

Each component performs a single role:

* **Quantizer** – converts raw input into tokens
* **Triad structure** – organizes tokens on the lattice
* **Sensory head** – extracts structural features
* **Pattern engine** – detects patterns and expresses them in MPL
* **Self model** – accumulates structural memory

---

## Playground

An interactive playground allows patterns to be explored visually.

The grid interface lets you:

* input sequences
* visualize the triad structure
* inspect detected pattern operators

```
/playground/meru_grid.html
```

---

## Example

Input:

```
om namah shivaya
shivaya namah om
```

Detected pattern:

```
% [#-1]
```

Meaning:

mirror symmetry around the center.

---

## Philosophy

MERU explores pattern discovery as a **structural problem**, not a statistical one.

The system focuses on:

* geometry
* symmetry
* operator algebra
* recursive structure

---

## Project Status

MERU is an experimental research project exploring structural pattern languages.

Current focus:

* stabilizing the operator set
* developing the MERU Pattern Language
* building an interactive pattern playground
* exploring pattern memory and discovery

---

## Repository Structure

```
meru
│
├─ engine
├─ playground
├─ docs
└─ examples
```

---

## License

Apache License 2.0

---

## Acknowledgment

MERU builds on ideas from geometry, lattice structures, and pattern systems used in mathematics, linguistics, and computer science.
