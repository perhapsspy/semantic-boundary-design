# Semantic Boundary Design

## 목적

표현 경계를 지나는 동안 의미 결정이 흩어지는 것을 막는다.

같은 의미가 raw data, user intent, event, record, route, command, API payload, realtime patch, presentation model을 지나갈 때 semantic decision마다 owner를 하나만 둔다. 여러 layer가 데이터를 observe, pass, render할 수는 있지만 domain meaning을 decide하는 layer는 하나여야 한다.

## Use / Do Not Use

다음 상황에서 local code shaping 전에 capability-wide design을 잡기 위해 사용한다.

- 변경이 여러 layer나 representation을 지난다.
- 같은 의미에 alias, fallback, derived label, status, permission, lifecycle rule이 있다.
- convenient caller가 의미를 parse, normalize, translate, infer하기 시작한다.
- compatibility, migration, integration 코드가 owner 밖에서 product policy를 보존할 위험이 있다.
- 테스트가 owner boundary의 behavior contract가 아니라 helper 내부 구현을 고정한다.

다음 상황에서는 사용하지 않는다.

- semantic boundary movement가 없는 작은 local edit.
- 현재 source owner를 읽기 전용으로 찾는 일. 이때는 `source-owner-audit`를 먼저 또는 함께 사용한다.
- owner가 이미 명확한 뒤 current unit의 primary flow를 정리하는 일. 이때는 `structure-first`를 사용한다.
- async interaction freshness만 문제인 일. 이때는 `interactive-state-flow`를 사용한다.
- 넓은 변경이 정당한지 판단하는 일. 이때는 `justified-change`를 사용한다.

## 인접 스킬

- `source-owner-audit`는 현재 source owner를 근거로 찾는다. 새 semantic owner를 배치하거나 edit을 승인하지 않는다.
- `structure-first`는 semantic owner가 정해진 뒤 current unit의 readable flow, atom, contract test를 다듬는다.
- `interactive-state-flow`는 route, async, realtime, stale, pending, presentation freshness ownership에 특화된다.
- `justified-change`는 implementation scope를 비례적이고 검증 가능하게 유지한다. semantic rule이 어디에 살아야 하는지는 결정하지 않는다.

## Operating Flow

1. capability를 user/domain term으로 명명한다.
2. representation crossings를 나열한다: source record, read model, UI draft, user intent, route/query state, client command input, API/remote payload, command result, event/realtime patch, presentation model, compatibility adapter.
3. semantic decisions를 식별한다: identity/alias, lifecycle/status, permission/capability, command grammar, route/navigation grammar, freshness/conflict/revision/pending/fallback, projection/presentation, compatibility.
4. decision마다 owner를 하나만 배정한다. 의미를 결정할 context와 authority가 있는 가장 작은 durable owner를 선호한다.
5. caller boundaries를 정의한다: caller는 pass, select, invoke, display, render할 수 있다. owner가 아닌 caller는 interpret, normalize, re-decide, preserve policy를 하지 않는다.
6. 현재 task가 정당화하는 범위만 refactor한다. owner boundary나 verification을 막지 않는 nearby drift smell까지 모두 고치지 않는다.
7. semantic decision이 caller로 새는 경우 실패하는 guard나 test를 추가한다.
8. local code shaping, async freshness, read-only owner discovery, scope control은 해당 concern을 소유한 인접 스킬로 handoff한다.

## Owner Selection Rules

- Schema 또는 field aliases -> record/contract owner.
- User intent shape -> UI surface 또는 command input owner.
- Final command payload -> session/command owner.
- API request parsing -> framework route wrapper가 아니라 application route owner.
- Route 또는 query grammar -> navigation owner.
- Permission 또는 capability -> policy owner.
- Labels와 actions -> surface/view-model owner.
- Result envelope, patch, resync semantics -> application/realtime result owner.
- Stale, pending, fallback, conflict, revision acceptance -> freshness-owning route, session, screen owner.
- Compatibility behavior -> adapter는 shape를 translate한다. 명시적으로 배정되지 않았다면 policy owner가 아니다.

## Drift Smells

- record/contract owner 밖의 `x || y || z` fallback chain.
- 중복된 lifecycle 또는 status check.
- UI code가 record에서 final command payload를 직접 만든다.
- route component가 shared query grammar를 parse/build한다.
- API route wrapper가 business request field를 읽는다.
- realtime 또는 event handler가 lifecycle, permission, product policy를 다시 결정한다.
- revision, conflict, pending, fallback, freshness key가 중복된다.
- adapter가 owner에게 translate하지 않고 product policy를 보존한다.
- test가 owner-boundary behavior가 아니라 helper internals를 assert한다.

## Required Guards

owner boundary를 보호하는 가장 작은 guard를 선택한다.

- alias normalization, command payload shape, route/query grammar, result envelope에 대한 contract test.
- caller가 meaning을 reinterpret하지 않고 pass/render/invoke한다는 boundary test.
- 해당 decision이 owner-owned일 때 stale, fallback, permission, lifecycle, compatibility behavior에 대한 negative case.
- 중복 해석을 표현하기 어렵게 만드는 type 또는 schema constraint.
- semantic decision에 의존하는 user-visible behavior regression test.

helper의 현재 구현만 고정하는 test는 피한다. 유용한 assertion은 meaning이 owner에 의해 한 번만 결정되고 caller가 조용히 다른 meaning을 선택할 수 없다는 것이다.

## Output Contract

plan, review, implementation note에 이 스킬이 유용하면 compact하게 출력한다.

- `Capability:` shaping 대상 user/domain capability
- `Representation Crossings:` 관련 data 또는 control forms
- `Semantic Decisions:` drift될 수 있는 decisions
- `Owner Ledger:` `decision -> owner -> reason`
- `Caller Boundaries:` caller가 할 수 있는 것과 하면 안 되는 것
- `Drift Smells:` 관찰되거나 예상되는 leak
- `Required Guards:` 필요한 tests, schemas, checks
- `Handoffs:` 다른 skills 또는 follow-up owners

## Final Gates

- capability가 user/domain term으로 명명되었는가?
- 관련 representation crossings가 보이는가?
- 각 semantic decision에 owner가 정확히 하나인가?
- caller가 meaning을 decide하지 않고 observe, pass, render, invoke할 수 있는가?
- adapter가 명시적으로 policy ownership을 받지 않은 한 translation으로 제한되는가?
- fallback, freshness, lifecycle, permission, compatibility decision이 검증 가능한 owner에게 있는가?
- refactor scope가 현재 task가 정당화하는 범위로 제한되는가?
- guard가 helper internals가 아니라 owner boundary behavior contract를 검증하는가?
- 인접 스킬로 필요한 handoff가 명시되었는가?
