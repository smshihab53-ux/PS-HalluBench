# PS-HalluBench: Category-Specific Grading Rubric

## Purpose

Apply **binary strict correctness** to each model's final engineering conclusion, using the corresponding reference answer and the question's provided operating conditions. Reasoning traces are excluded from grading. Incorrect answers are not automatically labeled as hallucinations.

These rules summarize the manuscript's published criteria. They do **not** reproduce the unpublished item-by-item answer key or resolve all possible ambiguous cases. Human adjudication records should document deviations or edge cases.

## Cross-category rules

1. Grade the **final answer**, not private/intermediate reasoning text or the fluency of its explanation.
2. Match the actual question's required output and verified reference. Where an item requires multiple findings, a response must satisfy the complete required answer.
3. Mark unsupported extra violation claims incorrect for constraint questions; do not silently apply that same rule to categories that lack this requirement.
4. An answer that abstains is correct **only** on items whose reference establishes that essential evidence is insufficient; otherwise it is an unjustified abstention.
5. Record absent/incomplete final conclusions separately in raw logs where possible; they are incorrect under strict correctness unless the reference specifically calls for abstention.
6. Resolve ambiguous responses through independent rating followed by documented adjudication.

## 1. Numerical (NUM; 40 questions)

**Correct:** Operating-point numerical quantities are within the manuscript's **2% tolerance** of the verified reference, or, for DG-placement questions, the proposed bus set matches the verified optimal reference bus set **exactly**. Evaluate each item according to its reference task, including whether feasibility or infeasibility is the expected conclusion.

**Incorrect:** Values beyond tolerance; wrong placement set; an unsupported optimality/infeasibility conclusion; or no answer to a sufficiently specified question.

**Example (illustrative only):** If the reference optimal DG bus is 6, `Bus 6` passes the exact-placement criterion; `Bus 3` fails. These illustrative labels are not a released benchmark item.

**Clarification needed from original authoring protocol:** How is percentage error defined when a reference value is zero or negative? Do not introduce a new convention retroactively; publish the original rule if documented.

## 2. Topology (TOP; 40 questions)

**Correct:** The answer agrees with verified connectivity, branch relationships, network configurations, and any switching state specified for that question, whether the network data were directly provided or the item refers to a standard IEEE test system.

**Incorrect:** Incorrect or omitted required connections, invented branches, unsupported topology assumptions, or wrong switching interpretation.

## 3. Constraint violations (CON; 40 questions)

**Correct:** Identifies all required violated operating limits, the affected components, and violation types, without inventing additional violations. Some items require AC power-flow calculation before limit checking. These are **violation-identification** tasks, not optimization or corrective-setpoint selection tasks.

**Incorrect:** Misses a required violation; reports one that does not exist; misidentifies the affected component or type; or gives a conclusion inconsistent with the verified operating state.

## 4. False-premise (FPA; 40 questions)

**Correct:** Assesses validity of the premise **and** gives the correct engineering conclusion. Reject an invalid premise; accept a valid premise when supported. A blanket rejection of all premises does not pass valid-premise items.

**Incorrect:** Accepts a false premise, rejects a true premise, or draws an incorrect engineering conclusion even if the premise decision was correct.

**Pending reference validation:** Cases `FPA_019` and `FPA_020` have a reported inconsistency between the supplied breaker state and the reference explanation. Adjudicate the reference before finalizing subtype-level claims.

## 5. Abstention (ABF; 40 questions)

**Correct:** For genuinely insufficient-information items, explicitly recognizes that an answer cannot be determined from the available evidence. For answerable items, provides the correct engineering conclusion.

**Incorrect:** Invents an answer when essential data are missing; or unnecessarily abstains when the supplied information is sufficient; or answers incorrectly when answerable.

**Important:** The models were **not explicitly instructed to abstain**. The evaluation tests whether their output independently reflects evidence sufficiency.

## Human rating and adjudication

The manuscript reports two authors independently grading 2,000 model outputs. Initial judgments agreed on **1,957/2,000 (97.85%)**, with **Cohen's kappa = 0.9523**; **43** disagreements were resolved through discussion. This measures consistency in scoring responses against the references, not independent validity of the references themselves. Do not claim the graders were blinded unless the original procedure confirms that.

## What this rubric is not

It is **not** the complete per-question answer key, proof of solution correctness, or a response-level annotation set. Those resources would be needed for full third-party verification.
