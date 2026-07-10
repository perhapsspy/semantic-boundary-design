# Semantic Boundary Design

[한국어](README.md) | [English](README.en.md)

## Summary

`semantic-boundary-design` is an Agent Skill for assigning one semantic decision owner before cross-layer changes drift.

When records, routes, commands, API payloads, realtime patches, presentation models, and adapters handle the same meaning, the skill builds an owner ledger so callers do not reinterpret aliases, statuses, permissions, fallbacks, grammar, or payload rules.

## Quick Start

```bash
npx skills add perhapsspy/semantic-boundary-design
```

Or copy `skills/semantic-boundary-design` into your agent skills directory.

```text
Use $semantic-boundary-design to assign owners for route/query grammar, command payloads, and realtime patch meaning in this migration.
```

## Use When

- A change crosses UI, route, client state, command, API, storage, realtime, adapter, or presentation layers
- Identity aliases, lifecycle/status, permission, route/query grammar, command payloads, or result/event projection are spreading across callers
- A compatibility adapter preserves product policy instead of translating shapes
- Callers add `x || y || z` fallback chains or duplicate lifecycle checks

## Other Skills

- Existing owner discovery: `source-owner-audit`
- Change-boundary and local flow cleanup after owners are clear: `structure-first`
- Pure async freshness/responsiveness issues: `interactive-state-flow`

## More

- Skill: [English](skills/semantic-boundary-design/SKILL.md) | [한국어](skills/semantic-boundary-design/SKILL.ko.md)
- Direction: [docs/skill-direction.md](docs/skill-direction.md)

## Support

[![Buy Me A Coffee](https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png)](https://www.buymeacoffee.com/perhapsspy)

## License

[MIT](LICENSE)
