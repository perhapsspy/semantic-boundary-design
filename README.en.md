# Semantic Boundary Design

[한국어](README.md) | [English](README.en.md)

## Summary

`semantic-boundary-design` helps agents assign one **semantic decision owner** before feature, porting, integration, migration, or refactor work crosses several layers.

When the same meaning moves through records, routes, UI drafts, command inputs, API payloads, realtime patches, presentation models, and compatibility adapters, the skill builds an owner ledger so convenient callers do not reinterpret aliases, statuses, permissions, fallback rules, query grammar, or command payloads.

`Spec:` Agent Skills / SKILL.md | `License:` MIT | `Agents:` Codex, ChatGPT, Agent Skills-compatible tools

## Quick Start

**Install**

```bash
npx skills add perhapsspy/semantic-boundary-design
```

Or copy `skills/semantic-boundary-design` into your agent skills directory.

**Use**

```text
Use $semantic-boundary-design to assign owners for route/query grammar, command payloads, and realtime patch meaning in this migration.

Use $semantic-boundary-design to create an owner ledger for identity aliases and lifecycle status decisions in this refactor.
```

## Use When

- A change crosses UI, route, client state, command, API, storage, realtime, adapter, or presentation layers
- Identity aliases, lifecycle/status, permission, route/query grammar, command payloads, or result/event projection are spreading across callers
- A compatibility adapter starts preserving product policy instead of translating shapes
- Callers use `x || y || z` fallback chains or duplicate lifecycle checks to decide meaning
- Tests freeze helper internals instead of behavior contracts

## More

- Skill details: [English](skills/semantic-boundary-design/SKILL.md) | [한국어](skills/semantic-boundary-design/SKILL.ko.md)
- Skill direction: [docs/skill-direction.md](docs/skill-direction.md)

## Support

[![Buy Me A Coffee](https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png)](https://www.buymeacoffee.com/perhapsspy)

## License

[MIT](LICENSE)
