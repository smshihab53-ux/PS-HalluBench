# PS-HalluBench: Category-Specific Grading Rubric

## Purpose

Apply **binary strict correctness** to each model's final engineering answer using the corresponding verified reference. Reasoning traces are excluded from grading. Incorrect answers are not automatically classified as hallucinations.

## General Grading Rules

1. Evaluate only the final answer against the verified reference.
2. All required components of an answer must be correct.
3. Missing, incomplete, or incorrect conclusions are graded as incorrect.
4. Ambiguous responses are resolved through independent human evaluation and discussion.

## 1. Numerical Reasoning (NUM; 40 Questions)

**Correct:** Numerical quantities fall within **2% tolerance** of the verified reference. DG-placement answers must match the exact optimal bus set. Feasibility conclusions must agree with the reference.

**Incorrect:** Values outside tolerance, incorrect DG placements, incorrect feasibility conclusions, or missing answers.

## 2. Network Topology (TOP; 40 Questions)

**Correct:** Network connections, branch relationships, and switching configurations agree with the verified network topology.

**Incorrect:** Incorrect or missing connections, fabricated branches, or unsupported topology assumptions.

## 3. Constraint Verification (CON; 40 Questions)

**Correct:** Identifies all required operating-limit violations, affected components, and violation types without reporting nonexistent violations.

**Incorrect:** Missing violations, falsely reported violations, incorrect components, or incorrect violation types.

## 4. False-Premise Acceptance (FPA; 40 Questions)

**Correct:** Recognizes invalid engineering premises and provides the correct conclusion. Valid premises must be accepted when supported.

**Incorrect:** Accepting false premises, rejecting valid premises, or providing incorrect engineering conclusions.

## 5. Abstention and Evidence Insufficiency (ABS; 40 Questions)

**Correct:** Recognizes when essential information is insufficient to determine an answer. For answerable questions, provides the correct engineering conclusion.

**Incorrect:** Providing unsupported answers when information is insufficient, unnecessarily abstaining, or answering an answerable question incorrectly.
