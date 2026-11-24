# b70-lab

Intel Arc Pro B70 lab notes from testing various inference engines.

Focus: native single-stream decode speed without MTP/speculation, prompt ingestion speed, and populated-context scaling.

## Layout

- `hardware.json`: shared hardware/environment snapshots.
- `engines/<checkout>/settings.json`: engine identity and named configuration snapshots.
- `engines/<checkout>/results.jsonl`: one JSON object per measurement.

## Record format

Each result references a settings ID. Settings IDs are immutable; add a new one when the configuration changes. Keep engine commit, model and quantization, graph state, flash attention, KV precision, context capacity, batch/microbatch/chunk, compiler/build flags and environment overrides where known.

Results record workload (synthetic or real), phase (prefill or decode), token count, populated context start/end, throughput in tokens/s, and correctness status. Record streaming, elapsed time, VRAM and GPU utilization when available. A null or absent field means unknown, never false or zero. Historical summaries are labelled `historical_summary`; directly reported command/API results are labelled `direct_report`. Approximate values are marked explicitly.

Decode depth buckets use the populated starting context: 0–<10,000; 10,000–<65,536; 65,536–<131,072; 131,072+. Keep exact counts and note when runs cross a bucket. Context capacity is not populated depth. Prefill length is not decode depth. A synthetic START_POS with unfilled KV is not a real populated-context measurement.

Do not conflate custom attention with a GGML flash-attention flag, or synthetic forward-pass throughput with end-to-end generation. Compare matched configurations and retain all baselines. Functional output is not independent numerical verification. Separate estimates from measured results.

Keep the repository small: no model weights, build artifacts, credentials, large logs, or dashboard dependencies. Source changes belong in engine repositories. Append new measurements; do not silently replace old ones.
