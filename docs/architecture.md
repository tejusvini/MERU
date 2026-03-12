# MERU Architecture

MERU is designed as a structural pattern analysis system.  
Each component performs a single transformation on the input.

The architecture intentionally separates **structure discovery** from **statistical inference**.

---
The triad system defines the geometric lattice.

The MERU Pattern Language (MPL) does not construct this grid.
It only describes structural relationships within it using
values, positions, and logic operators.

## Processing Pipeline


input sequence
→ quantization
→ triad grid construction
→ sensory feature extraction
→ pattern detection
→ operator representation
→ structural memory


Each stage produces a more structured representation of the input.

---

## Components

### Quantizer

Converts raw input (text, symbols, or tokens) into a discrete sequence.

Responsibilities:

- token segmentation
- symbol normalization
- sequence generation

Output:


[t1, t2, t3, t4, ...]


---

### Triad Grid

Organizes the sequence on a **3×N structural lattice**.


L C R


Where:

- **C (center)** forms the structural spine
- **L and R** hold lateral relationships

All patterns must ultimately resolve back to the center column.

This constraint stabilizes pattern formation.

---

### Sensory Feature Extraction

Extracts structural relationships from the grid.

Typical features:

- repetition
- symmetry
- adjacency
- directional growth

The result is a feature set describing potential patterns.

---

### Pattern Engine

The pattern engine converts detected structures into **MERU Pattern Language (MPL)** expressions.

Examples:


% [#-1]
&2
#> 1


These operator expressions describe the structural behavior of the sequence.

---

### Self Model

The self model accumulates structural knowledge over time.

Responsibilities:

- pattern memory
- frequency tracking
- stability evaluation

Patterns that appear repeatedly become **structural invariants**.

---

## Design Philosophy

MERU is based on several design principles:

1. **Minimal operator set**
2. **Explicit structural representation**
3. **Geometry over statistics**
4. **Stable pattern growth**

The system aims to describe patterns in the simplest possible structural language.
