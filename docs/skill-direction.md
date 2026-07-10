# 스킬 방향

배포 계약은 `skills/semantic-boundary-design/SKILL.md`가 소유한다. 이 문서는 그 계약을 언제 확장할지의 기준만 기록한다.

## 목적

- cross-layer 변경에서 semantic decision owner를 하나로 정한다.
- record, intent, event, route, command, payload, patch, presentation, adapter가 같은 의미를 다시 결정하지 않게 한다.

## 유지할 것

- capability를 user/domain term으로 먼저 이름 붙인다.
- representation crossing과 semantic decision을 분리한다.
- owner ledger를 구현보다 먼저 만든다.
- adapter는 기본적으로 translation owner다. policy owner가 되려면 명시적 결정이 필요하다.
- guard는 helper internals가 아니라 owner-boundary behavior를 보호한다.

## 인접 스킬 경계

- `source-owner-audit`: 현재 source owner를 읽기 전용으로 찾는다.
- `structure-first`: owner가 정해진 뒤 current unit의 변경 경계, flow, atom을 다듬는다.
- `interactive-state-flow`: freshness, pending, stale, async presentation behavior에 특화된다. 이 스킬은 freshness가 representation 사이 semantic contract일 때만 다룬다.

## 범위 밖

- 특정 저장소, framework, database, product 사례.
- source owner discovery 자체.
- code shape만 다루는 local refactor.
- async freshness 전용 설계.
- 변경 범위 승인이나 구현 우선순위 결정.

## 수정 기준

- 반복해서 오해되는 owner 배치 기준만 배포 스킬에 추가한다.
- 특정 사례는 일반 drift smell이나 owner selection rule로 추상화될 때만 반영한다.
- 한국어 문서는 영문 기본 스킬의 의미를 보존하되 직접적으로 쓴다.
- 저장소 운영 문서는 패키징과 유지보수 기준만 맡긴다.
