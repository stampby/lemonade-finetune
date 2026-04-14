# lemonade-finetune

LoRA fine-tuning pipeline for [Lemonade SDK](https://github.com/lemonade-sdk/lemonade) on AMD Strix Halo.

Bare metal. ROCm/Vulkan. No containers. No cloud. Your hardware, your model.

## What This Does

- **Data prep** — Clean and format transcripts, conversations, and domain knowledge into training-ready datasets
- **LoRA training** — Fine-tune on AMD GPUs using unsloth/axolotl with ROCm
- **GGUF export** — Merge LoRA adapters and convert to GGUF for llama.cpp inference
- **Eval** — Benchmark fine-tuned models against base to prove the improvement

## Hardware Target

- AMD Ryzen AI MAX+ 395 (Strix Halo)
- 128GB unified LPDDR5X
- ROCm 7 / Vulkan — gfx1151
- Inference via Lemonade Server (lemond) at 359 tok/s

## Structure

```
data/           # data prep scripts (not training data)
configs/        # LoRA training configs per base model
scripts/        # train, merge, convert, eval pipelines
eval/           # benchmark harness
```

## Pipeline

```
Raw Data → data/ prep → configs/ LoRA → scripts/ train → scripts/ merge+convert → GGUF → lemond
```

## Status

🚧 Setting up the pipeline. Base model: Qwen3.5-35B-A3B running at 359 tok/s on Vulkan.

---

Designed and built by the architect.

Part of the [halo-ai](https://github.com/stampby) stack.
