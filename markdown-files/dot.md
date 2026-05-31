# DOT Language

All automata in this assignment are represented using the [DOT language](https://graphviz.org/doc/info/lang.html).
We use a directed graph format with the following structure:

```
digraph Automata {
  rankdir=LR;
  "q0";
  "q1" [isInitial=true];
  "q2";
  "q4" [isAccepting=true];

  "q1" -> "q2" [label="a"];
  "q2" -> "q4" [label="b"];
}
```

## State Attributes

The following attributes may be applied to nodes:

```
isInitial=true
isAccepting=true
```

A state with no attribute is an ordinary non-accepting, non-initial state.

## Transitions

Transitions are directed edges with a label representing a single symbol:

```
"source" -> "target" [label="label"]
```

For the transitions in ε-NFA's you can use the following epsilons: `ε` or `ϵ`

## Notes

- All state names must be quoted strings (e.g. `"q0"`).
- The graph direction is always left-to-right (`rankdir=LR`).
- Multiple edges between the same pair of states are allowed (one per symbol).
