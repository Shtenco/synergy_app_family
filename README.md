<!-- SCIENTIFIC-V3-2026:START -->
<img src="assets/readme/scientific-architecture-v3.svg" width="100%" alt="FAMILY APPLICATION / CONSENT MODEL"/>

[Научно-техническое досье V3](docs/SCIENTIFIC_DOSSIER_V3_2026.md) — исследовательские идеи, формализация и эксперименты. Исходный README сохранён полностью.
<!-- SCIENTIFIC-V3-2026:END -->

# ‍‍‍ SYNERGY App Family — verified specification dossier

> **Домен:** Apps / Family Product Architecture  
> **Роль:** семейный application/product узел для совместных household-сценариев без переноса финансовой authority в UI.  
> **Статус:**  **STUB / specification-only** — на проверенном `main` присутствует только `README.md`; executable runtime, tests и evidence artifacts отсутствуют.  
> **Проверено по фактическому root tree:** 29.09.2026.  
> **Архитектурный родитель:** [`synergy_apps`](https://github.com/Shtenco/synergy_apps)

## 1.  Проблема и граница проекта

Этот repository резервирует отдельную ответственность внутри SYNERGY: семейный application/product узел для совместных household-сценариев без переноса финансовой authority в UI.

Ключевой принцип документации здесь — не путать подробно описанную будущую архитектуру с существующей реализацией:

```text
specification != implementation
architecture diagram != runtime integration
roadmap != completed feature
repository name != security/performance proof
```

Пока в `main` нет кода, strongest honest status — **STUB**.

## 2.  Фактическое состояние `main`

```text
synergy_app_family/
└── README.md
```

Не обнаружены в root tree:

- `src/` / `runtime/`;
- `tests/`;
- build/dependency manifest;
- CI workflow;
- persisted evidence;
- release/deployment artifact.

Это фиксируется как отрицательный, но полезный факт maturity audit.

## 3.  Целевой design contract

Будущая реализация должна иметь явную цепочку:

```mermaid
flowchart LR
    I[Typed inputs] --> V[Deterministic validation]
    V --> R[Bounded runtime]
    R --> E[Evidence]
    E --> C[Typed contract]
    C --> D[Downstream authority]
```

Runtime не получает дополнительные полномочия только потому, что находится внутри SYNERGY.

## 4.  Планируемые inputs

- household/member identities and consent state;
- read-only accounting/payment projections;
- family budgets/goals configured by users;
- capability/policy descriptors;
- notification/preferences state;

Каждый input должен иметь version/source/provenance там, где это влияет на воспроизводимость или безопасность.

## 5.  Планируемые outputs

- family-oriented read models;
- typed user intents;
- consent/audit events;
- shared-goal UI projections;
- non-authoritative recommendations;

Output становится federation evidence только после schema validation и, при необходимости, cryptographic/content-addressed binding.

## 6.  Authority boundaries

Обязательное системное правило:

```text
component output != downstream authorization
local state      != global/canonical truth
self-reported success != observed evidence
generated artifact != verified artifact
```

Canonical accounting, settlement, risk, governance, identity или deployment authority остаётся у соответствующего domain owner.

## 7.  Threat / failure model

| Failure mode | Promotion requirement |
|---|---|
| cross-member data leakage | mandatory reject/mitigation evidence before promotion |
| one family member acting outside granted consent | mandatory reject/mitigation evidence before promotion |
| UI balance treated as ledger truth | mandatory reject/mitigation evidence before promotion |
| shared-device session leakage | mandatory reject/mitigation evidence before promotion |
| minor/guardian policy ambiguity | mandatory reject/mitigation evidence before promotion |
| duplicate payment intent | mandatory reject/mitigation evidence before promotion |

Threat model обязан становиться executable через negative tests, а не оставаться только prose.

## 8.  Минимальная test matrix

- [ ] member isolation;
- [ ] consent revoke;
- [ ] role/capability denial;
- [ ] shared-device logout;
- [ ] stale read model;
- [ ] duplicate-submit/idempotency;
- [ ] privacy export/delete workflow;
- [ ] offline reconciliation;

Дополнительно обязательны malformed-input tests, crash/restart behavior и deterministic fixtures для core logic.

## 9.  Evidence model

Strong evidence package будущего runtime должен связывать:

```text
input/event id
input hash/provenance
software commit
configuration/policy version
result/output
test or execution status
artifact hash
timestamp
limitations
```

Без такого bundle README не должен использовать GREEN/E2E wording.

## 10.  Place in SYNERGY

```mermaid
flowchart LR
    SYS[synergy_system] --> P[synergy_apps]
    P --> THIS[synergy_app_family]
    THIS --> E[typed evidence]
    E --> NEXT[downstream canonical authority]
```

Стрелка показывает target architecture, **не runtime dependency**.

## 11.  Reproducibility текущего состояния

Сегодня воспроизводить runtime нечего. Проверяемый факт:

```bash
git clone https://github.com/Shtenco/synergy_app_family.git
cd synergy_app_family
find . -maxdepth 2 -type f
```

Предметный результат текущего `main`: `README.md`.

Когда появится runtime, README обязан заменить этот раздел exact build/test commands и dependency versions.

## 12.  Current vs required repository map

| Surface | Current | Required for CANDIDATE |
|---|---:|---:|
| repository-specific specification |  |  |
| source/runtime |  |  |
| typed schema/contract |  |  |
| unit tests |  |  |
| negative/security tests |  |  |
| CI |  |  |
| evidence artifacts |  |  |
| reproducible build/run |  |  |

## 13.  STUB → CANDIDATE promotion gate

Promotion is allowed only after all of the following exist:

1. executable minimal core;
2. typed input/output schema;
3. deterministic unit tests;
4. at least one negative/failure test per major invariant;
5. pinned dependencies/toolchain;
6. CI command;
7. real repository artifact/evidence;
8. README updated from target tense to implemented tense only for verified pieces.

## 14.  CANDIDATE → E2E_TESTED gate

Requires:

- upstream producer and downstream consumer;
- exact payload binding;
- observed execution;
- persisted evidence;
- verifier;
- no authority bypass;
- reproducible run.

A local unit test is insufficient.

## 15.  Current evidence maturity

```text
Problem/domain definition     
Architecture specification   
Inputs/outputs specification 
Threat/failure model           documented
Executable implementation    
Tests                        
Observed evidence            
E2E                          
Production                   
```

## 16.  Roadmap

1. formalize v1 typed contract;
2. implement smallest executable core;
3. add deterministic fixtures;
4. add failure/security tests;
5. add CI;
6. generate content-addressed evidence;
7. integrate one upstream/downstream pair;
8. run observed federation gate;
9. only then upgrade maturity.

## 17.  Что проект сейчас НЕ утверждает

- что runtime существует;
- что integration уже работает;
- что security/performance claims доказаны;
- что target diagrams соответствуют deployed topology;
- что roadmap items completed;
- что STUB может считаться E2E/production.

## 18.  Federation navigation

- [SYNERGY SYSTEM](https://github.com/Shtenco/synergy_system)
- [Атлас 75 репозиториев](https://github.com/Shtenco/synergy_system/blob/main/docs/SYNERGY_REPOSITORY_ATLAS.md)
- [Documentation quality registry](https://github.com/Shtenco/synergy_system/blob/main/registry/DOCUMENTATION_QUALITY.json)

**Итог:** repository теперь имеет подробный предметный specification dossier, но status сознательно остаётся  STUB до появления кода и evidence.
