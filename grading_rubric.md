# PS-HalluBench: Category-Specific Grading Rubric

## Purpose

Apply **binary strict correctness** to each model's final engineering conclusion using the corresponding reference answer and the question's provided operating conditions. Reasoning traces are excluded from grading. Incorrect answers are not automatically classified as hallucinations.

This rubric summarizes the evaluation criteria described in the PS-HalluBench manuscript. Reference answers are provided separately in `PS_HalluBench_Benchmark_Reference_Answers.txt`.

## Cross-Category Rules

1. Grade the **final answer**, not intermediate reasoning traces or the fluency of its explanation.
2. Compare the response against the question's required output and verified reference answer. Where multiple findings are required, the response must satisfy all required components.
3. For constraint-verification questions, unsupported additional violation claims are incorrect.
4. Abstention is correct only when the reference establishes that essential information is insufficient. Unjustified abstention on answerable questions is incorrect.
5. Missing, incomplete, or incorrect final conclusions are graded as incorrect unless the reference explicitly requires recognition of insufficient information.
6. Ambiguous responses are independently evaluated and resolved through adjudication.

## 1. Numerical Reasoning (NUM; 40 Questions)

**Correct:** Numerical operating-point quantities fall within the manuscript's **2% tolerance** of the verified reference answer. For DG-placement questions, the predicted bus set must exactly match the verified optimal reference bus set.

For questions requiring feasibility assessment, the response must correctly identify whether a feasible solution exists.

**Incorrect:** Numerical values exceeding the accepted tolerance, incorrect DG-placement bus sets, unsupported feasibility or optimality conclusions, or failure to provide the required answer.

**Example:** For a question with reference optimal DG bus 6, the answer `Bus 6` is correct, while `Bus 3` is incorrect.

**Numerical tolerance clarification:** The manuscript specifies a 2% tolerance but does not establish a separate convention for zero-valued or negative reference quantities. Such cases should follow the original evaluation procedure rather than introducing a new tolerance convention retrospectively.

## 2. Network Topology (TOP; 40 Questions)

**Correct:** The response correctly identifies network connectivity, branch relationships, network configurations, and applicable switching states according to the verified reference.

Questions may involve directly supplied network configurations or standard IEEE test systems.

**Incorrect:** Incorrect connections, missing required branches, fabricated connections, unsupported topology assumptions, or incorrect switching-state interpretations.

## 3. Constraint Verification (CON; 40 Questions)

**Correct:** The response identifies all required operating-limit violations, including affected components and violation types, without reporting nonexistent violations.

Questions may require AC power-flow calculations to determine the operating state before checking constraints.

These are **violation-identification tasks**, not optimization or corrective-setpoint selection tasks.

**Incorrect:** Missing a required violation, reporting a nonexistent violation, identifying an incorrect affected component, specifying an incorrect violation type, or reaching a conclusion inconsistent with the verified operating state.

## 4. False-Premise Acceptance (FPA; 40 Questions)

**Correct:** The response correctly assesses the validity of the question's underlying engineering premise and provides the correct engineering conclusion.

For invalid-premise questions, the model must recognize the incorrect assumption rather than accepting it as true.

For valid-premise questions, the model must avoid unjustified rejection and provide the appropriate engineering conclusion.

**Incorrect:** Accepting an invalid premise, rejecting a valid premise, or providing an incorrect engineering conclusion even when the premise is correctly classified.

**Reference verification note:** `FPA_019` and `FPA_020` have been flagged for a possible inconsistency between the specified breaker state and reference explanation. Their original network configurations and reference answers should be checked before treating these items as independently validated.

## 5. Abstention and Evidence Insufficiency (ABS; 40 Questions)

**Correct:** For questions with genuinely insufficient information, the response explicitly recognizes that the requested conclusion cannot be determined from the provided evidence.

For answerable questions, the response must provide the correct engineering conclusion rather than abstaining.

**Incorrect:** Providing unsupported conclusions when essential information is missing, unnecessarily abstaining when sufficient information is available, or providing an incorrect answer to an answerable question.

**Evaluation note:** Abstention performance should be interpreted in the context of the exact system prompt used during inference. Any instructions related to information sufficiency or uncertainty must be disclosed in the accompanying inference protocol.

## Human Rating and Adjudication

Two authors independently evaluated the **2,000 anonymized model responses**, blinded to model identity, using the category-specific criteria.

The manuscript reports:

- **Initial agreement:** 1,957/2,000 responses (97.85%).
- **Cohen's kappa:** 0.9523.
- **Disagreements:** 43 responses, resolved through discussion.

The reported agreement measures consistency between human evaluators when applying the grading criteria. It does not independently establish the validity of every reference answer.

## Reference Answers and Reproducibility

The repository contains the following materials:

- `Benchmark.zip` — benchmark questions.
- `PS_HalluBench_Benchmark_Reference_Answers.txt` — reference answers for the benchmark.
- `System_Prompt` — released system prompt.
- `inference_protocol.md` — inference settings and evaluation methodology.
- `DG40_Questions_Separate_Files.zip` — supplementary DG-placement scenarios.

Researchers evaluating additional models should use the original benchmark questions, corresponding reference answers, and category-specific grading rules.

Differences in system prompts, model configurations, or grading procedures should be documented when comparing results.

## Scope and Limitations

This rubric defines the operational criteria for strict correctness. It does not provide independent mathematical proofs for every reference answer, response-level grading records, or a complete record of adjudication decisions.

Strict correctness measures whether the model's engineering conclusion agrees with the verified reference. It does not establish that every incorrect response was caused by a distinct hallucination mechanism.
