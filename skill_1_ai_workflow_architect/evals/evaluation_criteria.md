## Scoring Framework

Each output is evaluated on 6 dimensions. Each dimension is scored 0–10.

| Dimension | Weight | Description |
|-----------|--------|-------------|
| Completeness | 25% | All required sections present and populated |
| Practicality | 25% | Architecture is realistic and implementable |
| Adaptability | 20% | Clarification behavior matches input quality |
| Depth | 15% | Tech choices include reasoning, not just names |
| Risk Quality | 10% | Risks are specific, cross-category, with mitigations |
| Structure | 5% | Output is clearly organized and readable |

**Overall Score = weighted average × 10**

---

## Dimension Rubrics

### Completeness (0–10)

| Score | Criteria |
|-------|----------|
| 10 | All 8 output sections present, none empty |
| 7–9 | 6–7 sections present, minor gaps |
| 4–6 | Key sections missing (roadmap or DB schema) |
| 0–3 | Multiple critical sections absent |

### Practicality (0–10)

| Score | Criteria |
|-------|----------|
| 10 | Tech stack appropriate for stated scale, all choices justified |
| 7–9 | Most choices appropriate, 1–2 over/under-engineered |
| 4–6 | Generic stack not tailored to project type |
| 0–3 | Architecture is unrealistic or contradictory |

### Adaptability (0–10)

| Score | Criteria |
|-------|----------|
| 10 | 0–1 questions on detailed input; 3 questions on vague input; hard stop maintained |
| 7–9 | Mostly correct behavior, minor over/under-asking |
| 4–6 | Asked too many or too few questions |
| 0–3 | Generated architecture without sufficient information |

### Depth (0–10)

| Score | Criteria |
|-------|----------|
| 10 | Every tech choice includes why + alternative considered |
| 7–9 | Most choices explained, some alternatives missing |
| 4–6 | Choices listed without reasoning |
| 0–3 | Generic output, no tailoring to project |

### Risk Quality (0–10)

| Score | Criteria |
|-------|----------|
| 10 | 3 risks from different categories, specific impacts, actionable mitigations |
| 7–9 | 3 risks but some from same category or vague mitigations |
| 4–6 | Only technical risks, or generic mitigations |
| 0–3 | Risks not present or irrelevant |

### Structure (0–10)

| Score | Criteria |
|-------|----------|
| 10 | Clear headers, tables where appropriate, easy to scan |
| 7–9 | Mostly structured, minor formatting issues |
| 4–6 | Wall of text, hard to navigate |
| 0–3 | Unstructured output |

---

## Test Results

| Test Case | Completeness | Practicality | Adaptability | Depth | Risk Quality | Structure | Overall |
|-----------|-------------|-------------|-------------|-------|-------------|-----------|---------|
| Tutoring App | 9 | 9 | 10 | 8 | 9 | 9 | **9.1** |
| Designer Marketplace | 10 | 9 | 10 | 9 | 8 | 10 | **9.4** |

---

## Pass Threshold

A skill output is considered passing at **Overall Score ≥ 7.0**.
Both tested outputs passed with scores above 9.0.
Uploading evaluation_criteria.md…]()

