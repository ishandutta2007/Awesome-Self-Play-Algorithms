# Asymmetric Causal Sliding Window

## Overview
An autoregressive version of local attention where tokens can only look back at past tokens in the sequence.

## Technical Concept
In causal generation, the model must not look into the future. The sliding window is shifted to the left (past tokens only):
$$\text{keys} \in [i-W, i]$$

```mermaid
graph TD
    T1[Token i-2]
    T2[Token i-1]
    T3[Token i (Target)]
    T4[Token i+1]
    T3 --> T1
    T3 --> T2
    T3 -.x|Causal Mask| T4
```

---
[← Back to README](../README.md)
