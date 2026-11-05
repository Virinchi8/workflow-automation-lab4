# PBL-II Practical Assignment - Camunda 8 Workflow Automation (Labs 1-3)

End-to-end workflow automation with **Camunda 8**: BPMN orchestration, DMN decisions, Java / Spring Boot external
job workers, REST connectors against mock services, Tasklist human tasks, and Operate monitoring with incident recovery.
All data is synthetic - no real payment credentials, secrets or patient data are used anywhere in this repository.

| Lab | Scenario | Process id | Worker / mock API port |
|---|---|---|---|
| [Lab 1](lab1-loan-approval) | Loan approval automation | `loan-approval` | 8081 |
| [Lab 2](lab2-order-processing) | E-commerce order processing and fulfilment | `order-processing` | 8082 |
| [Lab 3](lab3-hospital-triage) | Hospital appointment and patient triage (educational) | `patient-triage` | 8083 |

## Repository layout

```
.
|-- README.md                      this file
|-- docs/
|   |-- SETUP.md                   install and run instructions (Camunda 8 Run, Modeler, Java, Maven)
|   `-- SUBMISSION_CHECKLIST.md    the assignment's common checklist mapped to files in this repo
|-- scripts/run_test_cases.py      starts the documented test cases and collects results from Camunda
|-- lab1-loan-approval/
|-- lab2-order-processing/
`-- lab3-hospital-triage/
    |-- bpmn/  dmn/  forms/        Camunda models (open in Camunda Modeler)
    |-- worker/                    Spring Boot job workers + mock REST API + unit tests
    |-- test-data/test-cases.json  test cases (inputs, expected outcomes)
    |-- docs/                      variables, DMN rules, API examples, test cases, screenshot checklist
    |-- README.md                  how to run the lab
    `-- REPORT.md                  implementation report
```

## Quick start

```bash
# 1. start Camunda 8 locally (see docs/SETUP.md), then:
cd lab1-loan-approval/worker
mvn spring-boot:run            # deploys BPMN + DMN + forms, starts workers and the mock API

# 2. in another terminal, from the repository root
python scripts/run_test_cases.py 1
```

Repeat with `lab2-order-processing` / `lab3-hospital-triage` (each lab uses its own port, so labs can run side by side).

## Before you submit

The code, models and documentation are complete, but the assignment asks for evidence from **your own run**. Still to do:

1. Run each lab and capture the screenshots listed in `labN/docs/screenshots/README.md`.
2. Run `python scripts/run_test_cases.py N --collect` and copy the *Actual outcome* / *Status* into `labN/docs/test-cases.md` (or link `test-results.md`).
3. Put your name and register number in each `labN/REPORT.md` and tick the boxes in `docs/SUBMISSION_CHECKLIST.md`.

## Publishing to GitHub

```bash
git init
git add .
git commit -m "Add PBL-II Camunda 8 labs 1-3"
git branch -M main
git remote add origin https://github.com/<your-user>/<your-repo>.git
git push -u origin main
```

`target/`, IDE files and `runs.json` are excluded by `.gitignore`.
