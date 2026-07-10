# Semantic Boundary Design

[한국어](README.md) | [English](README.en.md)

## 요약

`semantic-boundary-design`은 여러 계층을 지나는 변경에서 의미를 결정할 owner를 하나로 정하게 해주는 Agent Skill입니다.

record, route, command, API payload, realtime patch, presentation model, adapter가 같은 의미를 다룰 때 caller가 alias, status, permission, fallback, grammar, payload 규칙을 다시 해석하지 않도록 owner ledger를 먼저 만듭니다.

## 빠른 시작

```bash
npx skills add perhapsspy/semantic-boundary-design
```

또는 `skills/semantic-boundary-design`를 에이전트 스킬 디렉터리에 복사합니다.

```text
$semantic-boundary-design 로 이 migration의 route/query grammar, command payload, realtime patch owner를 정리해줘.
```

## 이런 때 사용

- UI, route, client state, command, API, storage, realtime, adapter, presentation을 가로지르는 변경
- identity alias, lifecycle/status, permission, route/query grammar, command payload, result/event projection이 흩어지는 변경
- compatibility adapter가 translation을 넘어 product policy를 보존하는 변경
- caller의 `x || y || z` fallback chain이나 중복 lifecycle check가 늘어나는 변경

## 다른 스킬

- 기존 owner 찾기: `source-owner-audit`
- owner가 정해진 뒤 변경 경계와 local flow 정리: `structure-first`
- 순수 async freshness/responsiveness 문제: `interactive-state-flow`

## 더 보기

- 스킬: [English](skills/semantic-boundary-design/SKILL.md) | [한국어](skills/semantic-boundary-design/SKILL.ko.md)
- 방향: [docs/skill-direction.md](docs/skill-direction.md)

## 지원

[![Buy Me A Coffee](https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png)](https://www.buymeacoffee.com/perhapsspy)

## 라이선스

[MIT](LICENSE)
