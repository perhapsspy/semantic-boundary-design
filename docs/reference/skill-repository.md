# 스킬 저장소

## 현재 규칙

- 이 저장소는 `semantic-boundary-design`라는 독립 스킬 패키지다.
- 기본 README 언어는 한국어이고, 영어 문서는 `README.en.md`에 둔다.
- 설치 가능한 스킬은 `skills/semantic-boundary-design/` 아래에 둔다.
- `SKILL.md`는 영문 기본 스킬이며 frontmatter 메타데이터를 가진다.
- `SKILL.ko.md`는 한국어 페어이며 frontmatter를 넣지 않는다.
- `skills/semantic-boundary-design/agents/openai.yaml`은 OpenAI용 인터페이스 메타데이터를 제공한다.
- 프로젝트 라이선스는 MIT다.
- 저장소 로컬 운영 지침은 `AGENTS.md`에 둔다.
- README는 스킬 저장소 형태를 따른다: 요약, 빠른 시작, 사용 사례, 짧은 지원/라이선스 안내.
- 방향 문서는 `docs/` 아래에 두되, 스킬 사용자가 런타임에 참고해야 하는 내용은 배포 스킬 본문이나 스킬 패키지 내부 참조 문서로만 둔다.

## 범위 경계

- 스킬은 어떤 저장소에서도 독립적으로 쓸 수 있어야 한다.
- 스킬 본문은 독립적으로 유지한다. 다른 스킬과의 경계는 설명할 수 있지만, 특정 저장소나 특정 사례에 의존하지 않는다.
- 저장소 맥락, 패키징, 반복되는 유지보수 필요를 지원하지 않는 추가 파일은 피한다.
