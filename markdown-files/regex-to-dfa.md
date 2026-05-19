# Task X: Regex to DFA

The detailed rules of the mandatory assignment are found [here](README.md).
NOTE: ensure that the master branch of your repository is updated with:

- MacOS, Linux: `./update.sh`
- Windows: `update.ps1`

## Goals

The goal of this task is to apply your knowledge about subset construction to convert an NFA into a complete DFA.

## Detailed Description

> **Relevant files in your group's repository:**
>
> RegexToDFA.fs

Your task is to implement the function:

```
let analysis (input: Input) : Output =
    failwith "Module not yet implemented"
```

The above program takes an NFA and produces a complete DFA in the [dot-language](dot.md), using the subset construction algorithm.

### Transformation from NFA — Subset Construction

Let $A_B = (Q_B, \Sigma, \delta_B, q_{B0}, F_B)$ be an NFA. Construct the DFA $A_A = (Q_A, \Sigma, \delta_A, q_{A0}, F_A)$ as follows:

- $Q_A$ is the set of all subsets of $Q_B$, i.e. $Q_A = \mathcal{P}(Q_B)$
- $q_{A0}$ is the set $\{q_{B0}\}$
- $F_A$ is the collection of subsets of $Q_B$ that contain at least one state from $F_B$
- $\delta_A$ is constructed from $\delta_B$ according to:

$$\delta_A(\{q_1, \ldots, q_k\}, a) = \delta_B(q_1, a) \cup \ldots \cup \delta_B(q_k, a)$$

The transition from a DFA state (a set of NFA states) on symbol $a$ is the union of all transitions from each constituent NFA state on $a$.

In representing this automaton we expect you to only output the states reachable from the initial state.

### Completeness

The resulting DFA must be **complete**, meaning that every state must have exactly one outgoing transition for every symbol in the alphabet. This means the empty set $\emptyset$ acts as a sink (dead) state, and transitions that would otherwise be undefined must explicitly lead to it.

Launch inspectify as usual:

```
# On Windows
inspectify.ps1 --open
# On macOS and Linux
./inspectify.sh --open
```

## Hints

## Feedback & Evaluation

You can evaluate your solution by comparing the result to the ones provided by the `inspectify` tools.
We encourage you to proactively ask for feedback from the TAs and the teacher.
