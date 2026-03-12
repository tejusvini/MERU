# MERU Operators

MERU uses a minimal operator system.

All expressions follow the form:

operator[object]

---

# Structural Operators

#   self / value

Example:

#[5]

---

@   observer

Examples:

@[6]
@[]

---

%   mirror

Example:

%[&[#[5]]]

---

&   repeat

Example:

&[#[5]]

---

>   grow

Example:

>[#[8]]

---

<   lookback

Example:

<[#[2]]

---

# Relationship Operators

:   coexistence

Example:

A : B

---

:>  dependency

Example:

A :> B

---

# Logical Operators

?   conditional

Example:

A ? C

---

|   alternative

Example:

A ? C | B
