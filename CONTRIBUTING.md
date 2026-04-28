# Contributing

This repository packages a portable Toss UX writing and dark-pattern prevention skill for Codex, Claude Code, and OpenCode.

## Edit workflow

1. Update `plugins/toss-ux/skills/toss-ux-writing-and-dark-patterns/SKILL.md`.
2. Check the latest Toss official docs:
   - https://developers-apps-in-toss.toss.im/design/consumer-ux-guide.html
   - https://developers-apps-in-toss.toss.im/design/ux-writing.html
3. Validate JSON and frontmatter:

```bash
python3 -m json.tool .agents/plugins/marketplace.json >/dev/null
python3 -m json.tool plugins/toss-ux/.codex-plugin/plugin.json >/dev/null
python3 - <<'PY'
from pathlib import Path
import yaml
p = Path('plugins/toss-ux/skills/toss-ux-writing-and-dark-patterns/SKILL.md')
text = p.read_text()
assert text.startswith('---\n')
end = text.find('\n---\n', 4)
assert end != -1
fm = yaml.safe_load(text[4:end])
assert 'name' in fm and 'description' in fm
assert len(fm['description']) <= 1024
print('OK')
PY
```

4. Run `./install.sh`.
5. Start fresh Codex, Claude Code, and OpenCode sessions and test natural-language invocation:

```text
Use the toss-ux-writing-and-dark-patterns skill. Review this flow.
```

## Writing guidelines

- Keep the skill actionable and concise.
- Prefer checklists, review procedures, and before/after rewrite patterns over long quoted documentation.
- Link to official Toss docs rather than copying large sections.
- Make clear that this is an unofficial aid, not a replacement for Toss review or legal approval.
