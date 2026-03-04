# claude-skills

JamesBubu 的個人 Claude Code 自訂 skills（slash commands）。

## 安裝方式

```bash
git clone https://github.com/JamesBubu/claude-skills ~/Code/claude-skills

# 將 commands/ 裡的 skill 檔案複製到 Claude Code 的 user-level commands 目錄
cp ~/Code/claude-skills/commands/*.md ~/.claude/commands/
```

之後在 Claude Code 裡直接輸入 `/skill-name` 即可呼叫。

---

## Skills 清單

| 指令 | 檔案 | 說明 |
|------|------|------|
| `/obsidian-note` | `commands/obsidian-note.md` | 將學習筆記、教學計畫、課程重點存入 Obsidian vault |

---

## 新增 Skill 的方式

1. 在 `commands/` 資料夾新增一個 `{skill-name}.md` 檔案
2. 檔案內容即為 Claude 接到指令後要執行的提示（支援 `$ARGUMENTS` 變數）
3. 執行 `cp commands/{skill-name}.md ~/.claude/commands/` 讓 Claude Code 讀到
4. Commit & push 到此 repo

---

## Obsidian Vault 路徑（for obsidian-note skill）

- Root: `/Users/chun-yilin/Documents/Obisidian/vaults/Entrepreneur/Entrepreneur`
- Attachments: `<root>/attachments/`
