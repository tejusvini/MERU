"""
MERU Pattern Language (MPL) Parser
----------------------------------

Structure of this file:

SECTION 1  : INPUT BLOCK (self-executing example)
SECTION 2  : LOGIC PARSER
SECTION 3  : POSITION PARSER
SECTION 4  : OUTPUT (ASCII + FORMULA)

The parser reads MPL expressions and converts them into an AST.

Supported constructs:

VALUES
#[n]

POSITIONS
@
>n@
<n@
>n.W@
>n.E@

LOGIC
&[ ... ]
%[ ... ]
>[ ... ]
<[ ... ]
?[ ... ]
|[ ... ]
"""


# ============================================================
# AST NODE
# ============================================================

class Node:
    """
    Generic AST node.
    """

    def __init__(self, kind, value=None, children=None):
        self.kind = kind
        self.value = value
        self.children = children or []

    def __repr__(self):
        return f"{self.kind}:{self.value} -> {self.children}"


# ============================================================
# SECTION 2 — LOGIC PARSER
# ============================================================

class MPLParser:

    LOGIC_OPS = set("&%><?|")

    def __init__(self, text):
        self.text = text.replace(" ", "")
        self.i = 0
        self.n = len(self.text)

    # --------------------------------------------------------
    # Entry point
    # --------------------------------------------------------

    def parse(self):
        nodes = []

        while self.i < self.n:
            nodes.append(self._parse_expr())

        return nodes

    # --------------------------------------------------------
    # Expression selector
    # --------------------------------------------------------

    def _parse_expr(self):

        ch = self.text[self.i]

        if ch == "#":
            return self._parse_value()

        if ch in "@<>":
            return self._parse_position()

        if ch in self.LOGIC_OPS:
            return self._parse_logic()

        raise SyntaxError(f"Unexpected character '{ch}' at {self.i}")

    # --------------------------------------------------------
    # LOGIC operator
    # --------------------------------------------------------

    def _parse_logic(self):

        op = self.text[self.i]
        self.i += 1

        if self.text[self.i] != "[":
            raise SyntaxError("Expected '[' after logic operator")

        self.i += 1

        children = []

        while self.text[self.i] != "]":
            children.append(self._parse_expr())

        self.i += 1

        return Node("LOGIC", op, children)


# ============================================================
# SECTION 3 — POSITION PARSER
# ============================================================

    def _parse_position(self):

        # origin
        if self.text[self.i] == "@":
            self.i += 1
            node = Node("POSITION", {"row": 0, "col": "S"})

        else:

            direction = self.text[self.i]
            self.i += 1

            number = ""

            while self.i < self.n and self.text[self.i].isdigit():
                number += self.text[self.i]
                self.i += 1

            if number == "":
                raise SyntaxError("Row movement requires a number")

            row = int(number)

            if direction == ">":
                row = -row
            elif direction == "<":
                row = row
            else:
                raise SyntaxError("Invalid direction operator")

            col = "S"

            if self.i < self.n and self.text[self.i] == ".":
                self.i += 1
                col = self.text[self.i].upper()
                self.i += 1

            if self.text[self.i] != "@":
                raise SyntaxError("Position must end with '@'")

            self.i += 1

            node = Node("POSITION", {"row": row, "col": col})

        # ---------------------------------
        # Attach logic block if present
        # ---------------------------------

        if self.i < self.n and self.text[self.i] == "[":
            self.i += 1

            children = []

            while self.text[self.i] != "]":
                children.append(self._parse_expr())

            self.i += 1

            node.children = children

        return node


# ============================================================
# VALUE PARSER
# ============================================================

    def _parse_value(self):

        if self.text[self.i:self.i+2] != "#[":
            raise SyntaxError("Expected '#['")

        self.i += 2

        number = ""

        while self.text[self.i].isdigit():
            number += self.text[self.i]
            self.i += 1

        if self.text[self.i] != "]":
            raise SyntaxError("Missing closing ']'")

        self.i += 1

        return Node("VALUE", int(number))


# ============================================================
# SECTION 4 — OUTPUT
# ============================================================

def ascii_graph(node, prefix="", is_last=True):

    connector = "└─ " if is_last else "├─ "

    if node.kind == "VALUE":
        label = f"#[{node.value}]"

    elif node.kind == "POSITION":
        r = node.value["row"]
        c = node.value["col"]
        label = f"POS(row={r}, col={c})"

    else:
        label = f"{node.value}"

    print(prefix + connector + label)

    prefix += "   " if is_last else "│  "

    for i, child in enumerate(node.children):

        last = i == len(node.children) - 1

        if isinstance(child, Node):
            ascii_graph(child, prefix, last)


def formula(node):

    if node.kind == "VALUE":
        return f"#[{node.value}]"

    if node.kind == "POSITION":
        r = node.value["row"]
        c = node.value["col"]

        base = f"@({r},{c})"

        if node.children:
            inner = " ".join(formula(c) for c in node.children)
            return f"{base}[{inner}]"

        return base

    if node.kind == "LOGIC":
        inner = " ".join(formula(c) for c in node.children)
        return f"{node.value}[{inner}]"

    return "?"


# ============================================================
# SECTION 1 — INPUT BLOCK (SELF EXECUTING)
# ============================================================

if __name__ == "__main__":

    expr = ">2.W@[&[#[5]]]"

    print("\nINPUT:")
    print(expr)

    parser = MPLParser(expr)

    ast = parser.parse()

    print("\nASCII STRUCTURE:\n")

    for node in ast:
        ascii_graph(node)

    print("\nFORMULA OUTPUT:\n")

    for node in ast:
        print(formula(node))
