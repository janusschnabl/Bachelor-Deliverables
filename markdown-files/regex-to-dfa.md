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

Let $A_N = (Q_N, \Sigma, \delta_N, q_{N0}, F_N)$ be an NFA. Construct the DFA $A_D = (Q_D, \Sigma, \delta_D, q_{D0}, F_D)$ as follows:

- $Q_D$ is the set of all subsets of $Q_N$, i.e. $Q_D = \mathcal{P}(Q_N)$
- $q_{D0}$ is the set $\{q_{N0}\}$
- $F_D$ is the collection of subsets of $Q_N$ that contain at least one state from $F_N$
- $\delta_D$ is constructed from $\delta_N$ according to:

$$\delta_D(\{q_1, \ldots, q_k\}, a) = \delta_N(q_1, a) \cup \ldots \cup \delta_N(q_k, a)$$

The transition from a DFA state (a set of NFA states) on symbol $a$ is the union of all transitions from each constituent NFA state on $a$.

### Completeness

The resulting DFA must be **complete**,meaning that every state must have exactly one outgoing transition for every symbol in the alphabet. This means the empty set $\emptyset$ acts as a sink (dead) state, and transitions that would otherwise be undefined must explicitly lead to it.

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
