# Rafeeq Mini — Agentic AI Operations Assistant

Rafeeq Mini is the cumulative capstone project for the **Advanced Agentic AI Systems Engineering** training program (**هندسة أنظمة الذكاء الاصطناعي التوكيلي المتقدمة**). It demonstrates a bounded, auditable agentic workflow for a synthetic delivery-operations scenario using public training data only.

The project evolves across three stages: a bounded agent core and tools, scoped memory and multi-agent orchestration, then safety, adversarial testing, tracing, evaluation, optimization, and export evidence.

> Training reference: [SDAIA Academy on GitHub](https://github.com/SDAIAAcademy). This link is provided as the program reference only and does not imply endorsement of this repository.

## Project idea

Rafeeq Mini acts as a training-only operations assistant for order-status and refund workflows. It uses a trusted runtime for identity context, a thin supervisor for orchestration, specialist agents with narrow tool scopes, deterministic approval and policy gates, and redacted traces for evidence.

The capstone is designed to show that agentic systems should not rely on prompts alone. Sensitive decisions are enforced through code, scoped state, tool boundaries, approval checks, testable guardrails, and explicit stop conditions.

## Architecture

```text
User / synthetic ticket
        |
        v
Trusted runtime context
(identity, limits, thread)
        |
        v
Thin Supervisor
(route / delegate / collect / escalate)
     /             \
    v               v
OrdersAgent      RefundAgent
read-only         policy + eligibility
status tool       + controlled write path
    |               |
    +-------+-------+
            |
            v
MCP stdio tools + scoped services
            |
            v
Structured result + redacted trace + evidence
```

Key design rules:

- Customer identity is supplied by the trusted runtime, not invented or overridden by the model.
- `OrdersAgent` is read-only and uses a narrow order-status tool scope.
- `RefundAgent` handles refund facts, policy evidence, eligibility, and a controlled write path.
- Refunds above **SAR 500** require human approval before execution.
- Long-term memory and policy retrieval are scoped and filtered before ranking.
- Agent execution is bounded by step, transition, handoff, and reflection limits.
- Traces record structured operational evidence without raw prompts, customer IDs, or hidden reasoning.

## Repository evidence

The assessed repository should contain the cumulative notebook plus the safe exported project evidence, including:

```text
notebooks/Rafeeq_Mini_Capstone.ipynb
src/ or equivalent public project code
scripts/
data/public/
tests/
reports/trace.jsonl
reports/assessment_results.json
reports/SECURITY_ASSESSMENT.md
reports/PROJECT_REPORT.md
reports/monitoring_dashboard.png
reports/submission_manifest.json
reports/checkpoints/
LEARNING_PROGRESS.md
README.md
```

The exact exported file set is controlled by the project's canonical allowlist and export-safety checks. Instructor-only or private training material must remain outside the public repository.


## Documentation and evidence map

Use these repository artifacts as the final evidence set:

- [Technical documentation](docs/TECHNICAL_DOCUMENTATION.md)
- [Project report](reports/PROJECT_REPORT.md)
- [Security assessment](reports/SECURITY_ASSESSMENT.md)
- [Canonical assessment results](reports/assessment_results.json)
- [Monitoring dashboard](reports/monitoring_dashboard.png)
- [Redacted trace](reports/trace.jsonl)
- [Submission manifest](reports/submission_manifest.json)
- [Learning progress](LEARNING_PROGRESS.md)
- [Cumulative Colab notebook](notebooks/Rafeeq_Mini_Capstone.ipynb)

If a generated evidence file is missing, regenerate it from the final clean notebook run rather than creating or editing the result manually.

## How to run

### Recommended: Google Colab

1. Open `notebooks/Rafeeq_Mini_Capstone.ipynb` in Google Colab.
2. Use a fresh runtime and run the notebook from top to bottom.
3. Complete the learner TODO exercises in sequence; later gates depend on earlier evidence.
4. Confirm the final assessment reports all critical gates and learning gates as passed.
5. Confirm the final readiness status is `ready_for_learner_export` before preparing the submission.

The training notebook runs with an **offline deterministic stub** and synthetic public data. No API key, GPU, cloud account, production customer system, or real payment/delivery side effect is required for the assessed workflow.

## How to test and verify

The project uses deterministic functional and security cases rather than relying only on narrative claims.

### Functional evaluation

The assessment checks the expected route, outcome, and exact risk flags for public functional cases. It also records steps, transitions, handoffs, reflections, tool calls, and latency.

### Security evaluation

The public security suite covers eight deterministic cases:

1. Cross-customer access
2. Approval bypass
3. Duplicate refund
4. Direct prompt injection
5. Indirect prompt injection
6. Write retry attempt
7. Step exhaustion
8. Privilege escalation

The security suite verifies safe outcomes and write behavior, including zero unauthorized writes. A learner-created regression case is also used to demonstrate the test-first repair process: expose a weak local guard, repair it, then rerun the public suite.

### Trace evaluation

Trace validation checks:

- required structured fields,
- redaction,
- absence of forbidden keys such as raw message, prompt, chain-of-thought, and customer ID,
- valid parent/child span links,
- bounded reflection counts.

### Optimization evidence

The notebook benchmarks a small current-policy cache and records the measured trade-off and safety guardrail. The cache is keyed by locale, category, and active policy version, and excludes customer data from the cache key.

## Expected outputs

A successful final run produces evidence such as:

- `reports/assessment_results.json` — canonical machine-readable assessment
- `reports/SECURITY_ASSESSMENT.md` — bilingual security assessment
- `reports/PROJECT_REPORT.md` — bilingual project report
- `reports/monitoring_dashboard.png` — public release scorecard
- `reports/trace.jsonl` — redacted structured trace
- `reports/submission_manifest.json` — export manifest linked to the assessment run
- `reports/checkpoints/day1_results.json`
- `reports/checkpoints/day2_results.json`
- `reports/checkpoints/day3_results.json`
- `reports/checkpoints/learner_todo_status.json`

The source of truth for actual run metrics is `reports/assessment_results.json`; do not replace measured values with manually typed claims.

## Security and governance highlights

- **Least privilege:** specialist agents receive only the tools and context they require.
- **Trusted identity boundary:** customer identity is runtime-owned and server-verified.
- **Deterministic gates:** ownership, eligibility, approval thresholds, de-duplication, and termination limits stay in code.
- **Human approval:** high-value refunds require explicit approval.
- **Prompt-injection defense:** direct and indirect injection are tested separately.
- **Write safety:** write retries are bounded and de-duplicated.
- **Evidence-first design:** security, trace, optimization, and readiness decisions are written to auditable artifacts.
- **Privacy hygiene:** exported traces are redacted and the export process performs allowlist, forbidden-path, and secret checks.

## Limitations

This repository is a **training capstone**, not a production deployment.

- Identity and approval context are simulated for training.
- The LLM mode is an offline deterministic stub and does not measure live-model quality, provider rate limits, or provider cost.
- Data is synthetic/public training data only.
- Local memory and approval stores are not durable production controls.
- There is no production SLA or integration with real delivery, payment, customer, secrets-management, or enterprise identity systems.
- Production use would require authoritative identity, policy, approval, audit, secrets, monitoring, reliability, and operational integrations.

## Submission notes

The export ZIP intentionally does **not** contain the live Colab notebook. For final submission, download the completed notebook from Colab using **File → Download → Download .ipynb** and upload it to:

```text
notebooks/Rafeeq_Mini_Capstone.ipynb
```

Then upload the remaining safe ZIP contents into the same GitHub repository while preserving `LEARNING_PROGRESS.md` and the existing Git history.

Expected final commit message:

```text
feat: submit Rafeeq Mini capstone
```

## Program reference

- Training program: **Advanced Agentic AI Systems Engineering**
- البرنامج التدريبي: **هندسة أنظمة الذكاء الاصطناعي التوكيلي المتقدمة**
- SDAIA Academy GitHub reference: https://github.com/SDAIAAcademy
