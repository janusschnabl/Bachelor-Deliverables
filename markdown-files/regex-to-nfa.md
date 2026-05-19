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

The conversion shall be implemented in three steps:

1. **Compute epsilon closures** — For each state $q$, compute $\epsilon\text{-closure}(q)$: the set of all states reachable from $q$ using only $\epsilon$-transitions (including $q$ itself).
2. **Derive new transitions** — For each state $q$ and each non-$\epsilon$ symbol $a$, compute $d'(q, a)$ as defined above.
3. **Determine accepting states** — Mark a state $s$ as accepting if its $\epsilon$-closure intersects with the set of accepting states $F$.

### Pruning

After the transformation, prune all states that cannot be reached from the initial state through any transitions. This keeps the resulting NFA minimal.

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
