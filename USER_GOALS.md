# User goals

The purpose of b70-lab is to find a fast, useful local engineering assistant for real software projects, not simply the inference engine with the highest token throughput.

## Primary evaluation criteria

### 1. Codebase comprehension

Can the model understand an existing project, its architecture, responsibilities, dependencies and data flow before proposing changes?

Success means that its explanations and recommendations are grounded in the actual codebase.

### 2. Debugging

Can the model investigate a problem, identify its root cause, implement a targeted fix and verify that the problem is resolved?

Success means evidence-based debugging rather than repeated speculative changes or unnecessary rewrites.

### 3. Results on new features

Can the model turn a requested feature into a working, useful addition to an existing project?

Success means that the feature satisfies the requirements, integrates with the existing architecture and works when tested. Successful compilation alone is not sufficient.

## Evaluation approach

- Prioritize real work on the user's own projects over artificial coding challenges.
- Record concrete outcomes and relevant limitations, including human intervention when needed.
- Keep evaluation lightweight. No elaborate scoring system or extensive benchmark suite is required.
- Treat inference speed, context capacity and resource consumption as supporting metrics, not substitutes for software quality.

## Current focus

Evaluate Inkling 2 Mini through ArcAngel as a daily coding assistant on the Intel Arc Pro B70, using the established UD-Q4_K_XL model, 8-bit KV cache and 256k context configuration.

Use native decoding without MTP or speculative decoding for the current quality trial. Other quantizations and inference optimizations can be investigated separately.

The central question: **Can this model help me understand, debug and extend my own software effectively?**
