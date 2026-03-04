Save or update learning notes in the Obsidian vault. Use this after creating a teaching plan, explaining a key concept, completing a lesson, or generating any content worth retaining.

## Vault Configuration

- **Root**: `/Users/chun-yilin/Documents/Obisidian/vaults/Entrepreneur/Entrepreneur`
- **Attachments folder**: `<root>/attachments/`
- **Attachment embed syntax**: `![[attachments/filename.ext]]`

## Folder Structure

```
Entrepreneur/
├── Learning/
│   └── {Topic Name}/           ← one folder per course / project
│       ├── 00 學習計畫 - {Topic}.md   ← course overview & teaching plan
│       ├── s01 {Lesson Name}.md       ← individual lesson notes
│       └── ...
├── attachments/                ← ALL images, diagrams, screenshots
└── ...
```

## File Naming

- Course overview / teaching plan → `00 學習計畫 - {Topic}.md`
- Lesson note (following source lesson IDs) → `{sXX} {Lesson Name}.md`
- Session summary → `{YYYY-MM-DD} {Session Topic}.md`

## YAML Frontmatter (required on every new note)

```yaml
---
tags:
  - learning
  - {topic-tag}
created: YYYY-MM-DD
updated: YYYY-MM-DD
source: {url or "in-session"}
status: in-progress | completed
---
```

## Obsidian Formatting Rules

- Internal links → `[[Note Name]]` (no path prefix)
- Embedded files → `![[attachments/filename.ext]]`
- Callout boxes:
  - `> [!info]` for background info
  - `> [!tip]` for key insights
  - `> [!warning]` for gotchas
- Inline `#tags` — use frontmatter tags only, not inline
- Headings: H1 = title, H2 = main sections, H3 = subsections

## Execution Steps

1. Parse `$ARGUMENTS` to determine the topic, lesson ID, and content type.
2. Resolve the target file path under `Learning/{Topic}/`.
3. **Check if file exists** using the Read tool.
   - If **exists**: append new sections or update stale content. Update the `updated:` date.
   - If **not exists**: create with YAML frontmatter + structured content.
4. If any diagrams, screenshots, or images were generated during the session:
   - Save to `<root>/attachments/{descriptive-name}.{ext}`
   - Reference in the note as `![[attachments/{descriptive-name}.{ext}]]`
5. Use `[[wikilinks]]` to cross-reference other relevant notes in the vault.
6. Confirm to the user: file path saved/updated and any attachments created.

## Trigger Examples

- After creating a teaching plan → save as `00 學習計畫 - {Topic}.md`
- After explaining lesson sXX → save/update `sXX {Lesson Name}.md`
- At end of a learning session → append session summary to the relevant lesson note
- When a key concept is explained → add a callout block to the relevant note
