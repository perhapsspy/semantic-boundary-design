# Semantic Boundary Design

[한국어](README.md) | [English](README.en.md)

## Summary

`semantic-boundary-design` prevents screens, APIs, and storage from interpreting the same ID, status, or permission differently. It chooses one place to decide each cross-layer rule so every layer does not recreate the same meaning.

## Quick Start

```bash
npx skills add perhapsspy/semantic-boundary-design
```

Or copy `skills/semantic-boundary-design` into your agent skills directory.

```text
Use $semantic-boundary-design to decide where these status and permission rules should live so every screen and API behaves consistently.
```

## Use When

- A feature or migration changes screens, APIs, and storage together
- The same ID, status, or permission rule is repeated in several files
- Compatibility code is deciding product behavior instead of only translating data
- `x || y || z` fallbacks or lifecycle checks keep spreading across callers

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
