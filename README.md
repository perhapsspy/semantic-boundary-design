# Semantic Boundary Design

[한국어](README.md) | [English](README.en.md)

## 요약

`semantic-boundary-design`은 여러 계층을 지나는 기능, 포팅, 통합, 리팩터링에서 **의미 결정의 owner**를 하나로 정하게 해주는 스킬입니다.

같은 의미가 record, route, UI draft, command input, API payload, realtime patch, presentation model, compatibility adapter를 지나갈 때 convenient caller마다 alias, status, permission, fallback, query grammar, command payload를 다시 해석하지 않도록 owner ledger를 먼저 잡습니다.

`스펙:` Agent Skills / SKILL.md | `라이선스:` MIT | `에이전트:` Codex, ChatGPT, Agent Skills 호환 도구

## 빠른 시작

**설치**

```bash
npx skills add perhapsspy/semantic-boundary-design
```

혹은 `skills/semantic-boundary-design` 폴더를 에이전트 스킬 디렉터리에 직접 복사합니다.

**바로 사용**

```text
$semantic-boundary-design 를 사용해서 이 migration의 route/query grammar, command payload, realtime patch 의미 owner를 정리해줘.

$semantic-boundary-design 로 이 refactor에서 identity alias와 lifecycle status 결정이 어느 layer에 있어야 하는지 owner ledger를 만들어줘.
```

## 이런 때 사용

- UI, route, client state, command, API, storage, realtime, adapter, presentation을 가로지르는 변경을 시작할 때
- identity alias, lifecycle/status, permission, route/query grammar, command payload, result/event projection이 여러 곳에 흩어질 때
- compatibility adapter가 단순 translation을 넘어 product policy를 보존하려고 할 때
- caller가 `x || y || z` fallback chain이나 중복 lifecycle check로 의미를 다시 결정할 때
- 테스트가 behavior contract가 아니라 helper 내부 구현을 고정할 때

## 더 보기

- 스킬 상세 규칙: [English](skills/semantic-boundary-design/SKILL.md) | [한국어](skills/semantic-boundary-design/SKILL.ko.md)
- 스킬 방향: [docs/skill-direction.md](docs/skill-direction.md)

## 지원

[![Buy Me A Coffee](https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png)](https://www.buymeacoffee.com/perhapsspy)

## 라이선스

[MIT](LICENSE)
