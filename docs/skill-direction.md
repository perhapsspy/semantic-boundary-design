# 스킬 방향

## 목적

- 복합 기능, 포팅, 통합, 리팩터링에서 같은 의미를 여러 representation이 지나갈 때 semantic decision owner를 하나로 정한다.
- raw data, user intent, event, record, route, command, API payload, realtime patch, presentation model, compatibility adapter가 의미를 편의상 다시 결정하지 않게 한다.

## 핵심 방향

- 많은 layer가 데이터를 observe, pass, render할 수는 있지만 meaning을 decide하는 owner는 하나여야 한다.
- capability를 user/domain term으로 먼저 명명한 뒤 representation crossing과 semantic decision을 분리한다.
- owner ledger는 구현보다 먼저 나온다.
- adapter는 기본적으로 translation owner이며, product policy owner가 되려면 명시적 결정이 필요하다.
- guard는 helper 내부 구현이 아니라 owner boundary behavior contract를 보호한다.

## 인접 스킬과의 경계

- `source-owner-audit`는 현재 source owner를 읽기 전용 근거로 찾는다. 이 스킬은 semantic decision 배치와 caller boundary 설계를 맡는다.
- `structure-first`는 current unit의 primary flow와 atom 설계를 맡는다. 이 스킬은 capability-wide semantic owner ledger를 먼저 잡는다.
- `interactive-state-flow`는 route/async/realtime freshness와 stale/pending/presentation owner에 특화된다. 이 스킬은 permission, command grammar, route grammar, lifecycle alias, projection 등 더 넓은 semantic decision을 다룬다.
- `justified-change`는 변경 범위가 정당한지 통제한다. 이 스킬은 어떤 의미 결정을 어느 owner에게 둘지 배치한다.

## 범위 밖

- 특정 저장소, framework, database, product 사례에 고정된 지침.
- source owner를 찾는 read-only audit 자체.
- code shape만 다루는 local refactor.
- async freshness 전용 성능/상태 흐름 설계.
- 변경 범위 승인이나 구현 우선순위 결정.

## 수정 기준

- 반복해서 오해되는 semantic owner 배치 기준만 배포 스킬에 추가한다.
- 특정 사례는 일반 drift smell이나 owner selection rule로 추상화할 수 있을 때만 반영한다.
- 예시가 꼭 필요하면 아주 짧게 넣고, 특정 기술명이나 회사/프로젝트 맥락에 기대지 않는다.
- 한국어 문서는 영문 기본 스킬의 의미를 보존하되 자연스럽고 직접적으로 쓴다.
- 저장소 운영 문서는 패키징과 유지보수 기준을 맡고, 스킬 사용 계약은 배포 스킬 본문에 둔다.
