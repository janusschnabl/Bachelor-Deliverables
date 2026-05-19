# Task X: Regex to NFA

The detailed rules of the mandatory assignment are found [here](README.md).

NOTE: ensure that the master branch of your repository is updated with:

- MacOS, Linux: `./update.sh`
- Windows: `update.ps1`

## Goals

The goal of this task is to apply your knowledge about epsilon closures to convert an $\epsilon$-NFA into an equivalent NFA with no epsilon transitions.

## Detailed Description

> **Relevant files in your group's repository:**
>
> RegexToNFA.fs

Your task is to implement the function:

```
let analysis (input: Input) : Output =
    failwith "Module not yet implemented"
```

The above program takes an $\epsilon$-NFA and produces an equivalent NFA in the [dot-language](dot.md), by eliminating all $\epsilon$-transitions using epsilon closures.

### Transformation from $\epsilon$-NFA

For each state $q$ and each symbol $a$, the new transitions are defined as:

$$d'(q, a) = \epsilon\text{-closure}(\ d(\ \epsilon\text{-closure}(q),\ a\ )\ )$$

A state $s$ is accepting if and only if:

$$\epsilon\text{-closure}(s) \cap F \neq \emptyset$$

### Pruning

After the transformation, prune all states that cannot be reached from the initial state of the new automaton through any transitions.

Launch inspectify as usual:

```
# On Windows
inspectify.ps1 --open
# On macOS and Linux
./inspectify.sh --open
```

## Hints

- These 3 concerns can be seperated:
  - Compute epsilon closures
  - Define new transitions
  - Determine new accepting states
- Do pruning after construction

## Feedback & Evaluation

You can evaluate your solution by comparing the result to the ones provided by the `inspectify` tools.
We encourage you to proactively ask for feedback from the TAs and the teacher.
