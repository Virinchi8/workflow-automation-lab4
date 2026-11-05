# Workflow Automation Lab 4: Camunda 8 (PBL-II Labs 1-3)

End-to-end workflow automation with **Camunda 8**: BPMN orchestration, DMN decision tables, Java / Spring Boot
external job workers, REST connectors against mock services, Tasklist human tasks, and Operate monitoring with
incident recovery.

All data is synthetic. No real payment credentials, secrets or patient data are used anywhere in this project.

## Labs

| Lab | Scenario | Process id | Worker / mock API port |
|---|---|---|---|
| [Lab 1](lab1-loan-approval) | Loan approval automation | `loan-approval` | 8081 |
| [Lab 2](lab2-order-processing) | E-commerce order processing and fulfilment | `order-processing` | 8082 |
| [Lab 3](lab3-hospital-triage) | Hospital appointment and patient triage (educational only) | `patient-triage` | 8083 |

Each lab contains:

- `bpmn/`, `dmn/`, `forms/`: Camunda models (open in Camunda Modeler)
- `worker/`: Spring Boot job workers, a mock REST API and unit tests
- `test-data/test-cases.json`: test cases with inputs and expected outcomes
- `docs/`: process variables, DMN rules, API examples, test cases
- `README.md` and `REPORT.md`: how to run the lab, and the implementation report

## Tech stack

Camunda 8 (Zeebe, Tasklist, Operate), BPMN 2.0, DMN, Camunda Forms, Java, Spring Boot, Maven, Python (test runner).

## Quick start

```bash
# 1. Start Camunda 8 locally (see docs/SETUP.md), then:
cd lab1-loan-approval/worker
mvn spring-boot:run        # deploys BPMN + DMN + forms, starts workers and the mock API

# 2. In another terminal, from the repository root:
python scripts/run_test_cases.py 1
```

Repeat with `lab2-order-processing` and `lab3-hospital-triage`. Each lab uses its own port, so they can run side by side.
Tasklist and Operate are at `http://localhost:8080/tasklist` and `http://localhost:8080/operate` (login `demo` / `demo`).

Unit tests (no Camunda needed): `cd labN-*/worker && mvn test`

## Notes

- Lab 3 is an educational exercise. Its triage rules are simplified teaching rules, not clinical guidance.
- Setup details are in `docs/SETUP.md`; the assignment checklist is in `docs/SUBMISSION_CHECKLIST.md`.
