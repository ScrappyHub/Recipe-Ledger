# Recipe Ledger

Recipe Ledger is a deterministic evidence compiler for laboratory and process runs.

It records structured run inputs, measurements, and outcomes and produces a verifiable claim package that can be independently validated. The system is designed to support scientific workflows, engineering experiments, manufacturing tests, and other repeatable processes where results must be provable and reproducible.

Recipe Ledger focuses on three guarantees:

• deterministic processing  
• verifiable output artifacts  
• reproducible validation

The project provides a standalone command pipeline that ingests run data, constructs a structured claim package, and verifies the integrity of that package using deterministic rules.

---

## What Recipe Ledger Does

Recipe Ledger converts experimental or operational runs into structured evidence artifacts.

Each run contains:

- a target specification
- a process recipe
- measurement data
- derived comparison results

From these inputs the system builds a **claim package** that records the run and its outcomes in a format that can be independently verified.

This allows a third party to confirm:

- the run inputs
- the measured results
- the comparison logic
- the resulting claim

without trusting the original environment that produced the run.

---

## Typical Use Cases

Recipe Ledger is designed for environments where experimental results must be reproducible or auditable.

Examples include:

- laboratory experiments
- materials testing
- manufacturing process validation
- scientific instrumentation
- quality assurance runs
- engineering test pipelines

Any workflow that produces measurements against a defined specification can use Recipe Ledger to produce a verifiable artifact.

---

## Core Properties

Recipe Ledger enforces several deterministic behaviors:

### Deterministic Serialization

All run inputs are converted into canonical byte representations before processing.

This prevents platform-dependent variations and ensures identical runs produce identical artifacts.

### Verifiable Claim Packages

The output of a run is a claim package containing:

- run metadata
- target specification
- recipe definition
- measurement evidence
- comparison results

These artifacts can be verified independently using the included verification scripts.

### Reproducible Validation

The repository includes a full validation runner that executes:

- a valid run
- multiple invalid run scenarios

The invalid scenarios intentionally introduce errors such as:

- invalid schema
- tampered results
- missing measurements

The system must reject these invalid cases to demonstrate verification integrity.

---

## Repository Structure


recipe-ledger
├─ scripts/
│ ├─ rl_ingest_lab_run_v1.ps1
│ ├─ rl_build_claimpack_v1.ps1
│ ├─ rl_verify_claimpack_v1.ps1
│ └─ _RUN_recipe_ledger_full_selftest.ps1
│
├─ rgsr/
│ ├─ runs/
│ └─ claimpacks/
│
├─ proofs/
│ ├─ keys/
│ └─ receipts/
│
├─ test_vectors/
│ ├─ positive/
│ └─ negative/
│
└─ docs/


---

## Running the Self Test

Recipe Ledger includes a full validation runner.


powershell -NoProfile -ExecutionPolicy Bypass -File scripts_RUN_recipe_ledger_full_selftest.ps1


The runner performs:

1. ingestion of a valid run
2. construction of a claim package
3. verification of the package
4. execution of several negative validation tests

Successful execution indicates the system is operating correctly.

---

## Verification Key

The repository includes a public verification key located at:


proofs/keys/id_ed25519.pub


This key allows independent verification of generated artifacts.

---

## Design Goals

Recipe Ledger is built with the following priorities:

- deterministic execution
- transparent validation rules
- independent verifiability
- reproducible experiments

The system is intentionally simple and designed to run locally without requiring external infrastructure.

---

## License

TBD
