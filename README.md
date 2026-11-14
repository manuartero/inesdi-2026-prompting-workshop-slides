# inesdi-2026-prompting-workshop-slides

Slides for Workshop 1 «Prompt engineering estratégico» of INESDI's Master in Applied AI for Business (edition 2609): two live 90-minute sessions on 24/11/2026 and 01/12/2026. The content is in Spanish.

Built with [Slidev](https://sli.dev). The look is a lean take on INESDI's 2026 templates: ink and paper, with the school's yellow as the only accent.

## Commands

```sh
pnpm install
pnpm dev        # session 1 at localhost:3030
pnpm dev:2      # session 2
pnpm export     # both sessions as PDF in exports/ (for the campus)
pnpm build      # both sessions as static sites in dist/
```

## Layout

| Path            | What                                                                                     |
| --------------- | ---------------------------------------------------------------------------------------- |
| `session-1.md`  | Session 1 · structured prompts: headmatter, cover, about me and agenda, then one `src:` import per section |
| `session-1/`    | Session 1 sections, one file each (`01-two-prompts.md` … `06-wrap-up.md`)                 |
| `session-2.md`  | Session 2 · workflows, same shape                                                        |
| `session-2/`    | Session 2 sections (`01-recap.md` … `06-wrap-up.md`)                                     |
| `public/captures/` | Screenshots: the CMS (`cms-*.png`) and the demo results (`s1-*.png`)                  |
| `layouts/`      | INESDI layouts: `cover`, `section`, `default`, `two-cols` (`::left::`/`::right::`), `statement`, `end` |
| `components/`   | Brand: `InesdiWordmark`. Content: `TopicRow`, `PretrainingCompression`, `AttentionArcs`, `ContextWindowZones`, `GriefSpiral` |
| `styles/`       | Brand tokens and helper classes: `ine-card`, `ine-card--accent`, `ine-todo` |

Section slides take a `number` frontmatter field. To add a section, create its file and add a `src:` block to the session file.

The examples use **Peluda**, a fictional pet-food subscription company. Its back office lives in [inesdi-2026-peluda-admin](https://github.com/manuartero/inesdi-2026-peluda-admin).
