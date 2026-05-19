# Task X: Regex to DFA (Direct)

The detailed rules of the mandatory assignment are found [here](README.md).
NOTE: ensure that the master branch of your repository is updated with:

- MacOS, Linux: `./update.sh`
- Windows: `update.ps1`

## Goals

The goal of this task is to combine your knowledge of epsilon closures and subset construction to convert an $\epsilon$-NFA directly into a complete DFA.

## Detailed Description

> **Relevant files in your group's repository:**
>
> RegexToDFADirect.fs

Your task is to implement the function:

```
let analysis (input: Input) : Output =
    failwith "Module not yet implemented"
```

The above program takes an $\epsilon$-NFA and produces a complete DFA in the [dot-language](dot.md), by mimicking the subset construction while accounting for $\epsilon$-transitions.

### Transformation from $\epsilon$-NFA — Subset Construction with Epsilon Closures

Given an $\epsilon$-NFA $A_E = (Q_E, \Sigma, \delta_E, q_{E0}, F_E)$, construct the DFA $A_D = (Q_D, \Sigma, \delta_D, q_{D0}, F_D)$ as follows:

- $Q_D = \mathcal{P}(Q_E)$ — each DFA state is a subset of $\epsilon$-NFA states
- $q_{D0} = \epsilon\text{-closure}(q_{E0})$ — the start state is the epsilon closure of the original start state
- $F_D$ consists of all subsets of $Q_E$ that contain at least one state from $F_E$
- $\delta_D$ is constructed according to:

$$\delta_D(\{q_1, \ldots, q_k\}, a) = \epsilon\text{-closure}(\ \delta_E(q_1, a) \cup \ldots \cup \delta_E(q_k, a)\ )$$

The transition from a DFA state (a set of $\epsilon$-NFA states) on symbol $a$ is the epsilon closure of the union of all transitions from each constituent state on $a$.

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
