# Main Benchmark Inference Protocol

## Experimental scope

- **Study:** 200 questions × 10 LLMs = 2,000 model-question pairs, one generation per pair.
- **Categories:** 40 questions each in numerical, topology, constraints, false-premise, and abstention.
- **Environment:** Open-weight models deployed on University of Arkansas HPC NVIDIA A100 GPUs. GPT-4o, GPT-5.1, GPT-5.4 accessed through the OpenAI Responses API.
- **Tool access:** No external tools, code execution, retrieval, or numerical solver access in the **main benchmark**.
- **Scoring target:** Only the model's final answer was scored; reasoning traces were not used to determine correctness.
- **Abstention prompting:** No explicit instruction encouraged models to abstain or challenge question premises. The tests assess whether this behavior emerges unprompted.
- **Sampling:** Local models and GPT-4o used temperature `0.7` and top-p `0.8`. GPT-5.1 and GPT-5.4 used default API sampling settings. One generation per model-question pair.
- **Reasoning:** Qwen3.5 thinking reported as enabled; confirmation against final inference logs is pending. GPT-5.1 and GPT-5.4 reasoning effort `medium`. Other reasoning-specific settings require confirmation from original scripts before publication.
- **Output budget:** Final maximum generation/output budget `16384` tokens per model-question run. The authors report **0 truncated final outputs out of 2,000**. Smaller pilot budgets (~2,000 and ~8,000) produced truncated outputs and were not the source of the reported final aggregate scores.
- **OpenAI reasoning-token accounting:** For the reasoning models, the API output budget includes internal reasoning and visible output tokens.
