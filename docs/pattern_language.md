# MERU Pattern Language (MPL)

The MERU Pattern Language (MPL) is a compact notation for describing structural patterns.

Instead of describing procedural steps, MPL describes **relationships between elements**.

---

## Operator Set

MERU currently uses a minimal operator set.


@ anchor
% mirror
& repeat
#> grow
#< shrink


Each operator represents a structural transformation.

---

## Operator Meanings

### Anchor (@)

Marks a structural reference point.

Example:


@1


Meaning: element 1 is the anchor.

---

### Mirror (%)

Represents bilateral symmetry around a center.

Example:


% [#-1]


Meaning:

the previous element appears in mirrored form.

---

### Repeat (&)

Represents repetition of a structural element.

Example:


&2


Meaning:

repeat the element twice.

---

### Grow (#>)

Represents directional growth of a sequence.

Example:


#> 1


Meaning:

extend the structure forward.

---

### Shrink (#<)

Represents contraction of a structure.

Example:


#< 1


Meaning:

reduce the structure by one step.

---

## Pattern Expression

Patterns combine operators and references.

Example:


% [#-1 #-2]


Meaning:

a mirrored relationship using the previous two elements.

---

## Example Pattern

Input:


om namah shivaya
shivaya namah om


Detected structure:


% [#-1]


This describes a mirrored pattern around a central reference.

---

## Goal of MPL

MPL aims to express patterns using the **smallest possible symbolic language**.

Instead of large rule systems, patterns are described using:

- operators
- structural references
- minimal syntax
