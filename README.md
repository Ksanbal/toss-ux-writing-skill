# Toss UX Writing and Dark Pattern Skill for Codex, Claude Code, and OpenCode

Portable skill pack for applying Toss Apps UX writing tone and dark-pattern prevention guidance in AI coding/design agents.

Source docs:

- Toss Apps 다크패턴 방지 정책: https://developers-apps-in-toss.toss.im/design/consumer-ux-guide.html
- Toss Apps UX 라이팅: https://developers-apps-in-toss.toss.im/design/ux-writing.html

This is an unofficial working aid. It summarizes and operationalizes the public Toss developer docs for review and implementation workflows. It does not replace the official Toss documentation, Toss policy review, legal review, or product approval.

## Supported tools

| Tool | Install method | Installed location |
|---|---|---|
| Codex | Local plugin marketplace | `~/.codex/config.toml` + this repo |
| Claude Code | Global skill copy | `~/.claude/skills/toss-ux-writing-and-dark-patterns/SKILL.md` |
| OpenCode | Global skill copy | `~/.config/opencode/skills/toss-ux-writing-and-dark-patterns/SKILL.md` |

## Quick install

```bash
git clone https://github.com/Ksanbal/toss-ux-writing-skill.git ~/.agents/toss-ux-writing-skill
cd ~/.agents/toss-ux-writing-skill
./install.sh
```

Restart Codex, Claude Code, and OpenCode sessions after installation.

## Update on another device

```bash
cd ~/.agents/toss-ux-writing-skill
git pull
./install.sh
```

## Usage

### Codex

```text
Use the toss-ux-writing-and-dark-patterns skill. Review this Korean onboarding flow for Toss UX writing and dark-pattern risks.
```

```text
Use the toss-ux-writing-and-dark-patterns skill. Rewrite these CTA, dialog, and error messages in Toss-like UX writing style.
```

### Claude Code

```text
Use the toss-ux-writing-and-dark-patterns skill. Review the current app flow and suggest copy/interaction fixes before launch.
```

Or one-shot:

```bash
claude -p "Use the toss-ux-writing-and-dark-patterns skill. Review the current product flow for Toss UX writing and dark-pattern risks." --max-turns 5
```

### OpenCode

```text
Use the toss-ux-writing-and-dark-patterns skill. Check this mini app for dark-pattern prevention and Korean UX writing quality.
```

Or one-shot:

```bash
opencode run "Use the toss-ux-writing-and-dark-patterns skill. Review this flow for Toss UX writing and dark-pattern risks."
```

## Manual install

### Codex only

```bash
cd ~/.agents/toss-ux-writing-skill
codex plugin marketplace add "$PWD"
```

If needed, ensure this block exists in `~/.codex/config.toml`:

```toml
[plugins."toss-ux@local-toss-design-skills"]
enabled = true
```

### Claude Code only

```bash
mkdir -p ~/.claude/skills/toss-ux-writing-and-dark-patterns
cp plugins/toss-ux/skills/toss-ux-writing-and-dark-patterns/SKILL.md \
  ~/.claude/skills/toss-ux-writing-and-dark-patterns/SKILL.md
```

### OpenCode only

```bash
mkdir -p ~/.config/opencode/skills/toss-ux-writing-and-dark-patterns
cp plugins/toss-ux/skills/toss-ux-writing-and-dark-patterns/SKILL.md \
  ~/.config/opencode/skills/toss-ux-writing-and-dark-patterns/SKILL.md
```

OpenCode can also discover some Claude-style skills, but the installer copies to OpenCode's explicit global skill directory so it works independently.

## Repository layout

```text
.
├── README.md
├── CONTRIBUTING.md
├── LICENSE
├── install.sh
├── .agents/plugins/marketplace.json
└── plugins/toss-ux/
    ├── .codex-plugin/plugin.json
    └── skills/toss-ux-writing-and-dark-patterns/SKILL.md
```

## Validate

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
assert fm['name'] == 'toss-ux-writing-and-dark-patterns'
assert 'description' in fm and len(fm['description']) <= 1024
print('OK')
PY
```

## What the skill checks

- Entry-blocking bottom sheets and notification prompts
- Back-navigation interception
- Missing exit/decline paths
- Unexpected ads
- Ambiguous CTA labels
- Korean UX writing tone: 해요체, active voice, positive phrasing, casual honorifics, verb-based sentences

## License and attribution

This repository's original scripts and packaging are MIT licensed. Toss documentation and trademarks belong to their respective owners. This project is not affiliated with or endorsed by Toss.
