# Semantic Boundary Design

[한국어](README.md) | [English](README.en.md)

## 요약

화면, API와 저장소가 같은 ID·상태·권한을 서로 다르게 해석하는 문제를 막습니다. 여러 계층을 지나는 규칙을 어디에서 한 번 결정할지 정해 각 계층이 같은 뜻을 다시 만들지 않게 합니다.

## 빠른 시작

```bash
npx skills add perhapsspy/semantic-boundary-design
```

또는 `skills/semantic-boundary-design`를 에이전트 스킬 디렉터리에 복사합니다.

```text
$semantic-boundary-design 이 상태와 권한 규칙을 어디에서 결정해야 모든 화면과 API가 같게 동작하는지 정리해줘.
```

## 이런 때 사용

- 화면, API, 저장소를 함께 바꾸는 기능이나 migration
- 같은 ID, 상태나 권한 규칙이 여러 파일에서 반복되는 변경
- 호환 코드가 데이터 형식뿐 아니라 제품 동작까지 결정하려는 경우
- `x || y || z` 같은 fallback이나 상태 검사가 여러 호출부에서 늘어나는 경우

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
