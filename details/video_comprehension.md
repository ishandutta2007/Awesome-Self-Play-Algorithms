# High-Frame-Rate Video Comprehension

## Overview
High-frame-rate video features massive temporal redundancy. Local attention windows allow networks to process high-resolution video streams.

## Technical Concept
Rather than calculating self-attention between all frames (which is computationally impossible for long videos), a temporal sliding window limits the attention frame by frame to adjacent timestamps.

```mermaid
graph LR
    F1[Frame t-1] <--> F2[Frame t] <--> F3[Frame t+1]
    F2 -.x|Blocked| F_Far[Frame t-100]
```

---
[← Back to README](../README.md)
