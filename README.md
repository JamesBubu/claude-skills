# claude-skills

JamesBubu 的個人 Claude Code 自訂 skills。

## 兩種格式說明

### `skills/{name}/SKILL.md` — Agent Skill（動態加載）

參考 [learn-claude-code s05](https://github.com/shareAI-lab/learn-claude-code) 的設計模式。
Agent 依據 `description` 欄位判斷「何時自動加載這個 skill」，並透過 `tool_result` 注入。

```
skills/
└── obsidian-note/
    └── SKILL.md     ← YAML frontmatter (name + description trigger) + 技能內容
```

### `commands/{name}.md` — Claude Code Slash Command（手動呼叫）

放在 `~/.claude/commands/` 後，在 Claude Code 中輸入 `/command-name` 直接觸發。

```
commands/
└── obsidian-note.md   ← 直接作為 /obsidian-note 指令的 prompt
```

---

## Skills 清單

| Skill | 觸發方式 | 說明 |
|-------|---------|------|
| `obsidian-note` | 自動（agent 判斷）/ `/obsidian-note` | 將學習筆記、教學計畫存入 Obsidian vault |

---

## 安裝 Slash Commands 到 Claude Code

```bash
git clone https://github.com/JamesBubu/claude-skills ~/Code/claude-skills
cp ~/Code/claude-skills/commands/*.md ~/.claude/commands/
```

---

## 新增 Skill 的流程

1. 在 `skills/{name}/` 新增 `SKILL.md`（含 YAML frontmatter）
2. 若也需要 slash command，在 `commands/{name}.md` 新增對應版本
3. `cp commands/{name}.md ~/.claude/commands/`
4. Commit & push

---

## Obsidian Vault（for obsidian-note skill）

- Root: `/Users/chun-yilin/Documents/Obisidian/vaults/Entrepreneur/Entrepreneur`
- Attachments: `<root>/attachments/`
