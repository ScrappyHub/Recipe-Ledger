# Recipe Ledger Specification

Recipe Ledger defines a deterministic pipeline for compiling experimental or process runs into verifiable claim packages.

The system accepts structured run inputs and produces artifacts that can be independently validated.

---

## Run Components

Each run contains the following components:

### Target Specification

Defines the expected properties or requirements of the experiment.

### Recipe

Defines the procedure used to produce the measured results.

### Measurements

Observed values produced during the run.

### Comparison Results

Evaluation of measured values against the target specification.

---

## Claim Package

A claim package contains the complete record of a run.

This includes:

- target specification
- recipe definition
- measurements
- comparison results
- run metadata

The package can be validated by an independent verifier.

---

## Validation Rules

Verification ensures:

- input schemas are valid
- required measurements exist
- comparison results match the inputs
- artifacts have not been tampered with

If any of these conditions fail, the claim package is rejected.
