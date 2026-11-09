# inesdi-2026-prompting-workshop-slides

Slides for Workshop 1 «Prompt engineering estratégico» of INESDI's Master in Applied AI for Business (edition 2609): two live 90-minute sessions on 24/11/2026 and 01/12/2026. The content is in Spanish.

Built with [Slidev](https://sli.dev). The look follows INESDI's 2026 templates: ink background, yellow band, cyan stripe.

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
| `session-1.md`  | Session 1 · structured prompts                                                           |
| `session-2.md`  | Session 2 · workflows                                                                    |
| `layouts/`      | INESDI layouts: `cover`, `section`, `default`, `two-cols` (`::left::`/`::right::`), `statement`, `end` |
| `components/`   | Brand: `InesdiWordmark`, `BrandStrip`. Content: `TopicRow`, `PretrainingCompression`, `AttentionArcs`, `ContextWindowZones`, `GriefSpiral` |
| `styles/`       | Brand tokens and helper classes: `ine-card`, `ine-card--yellow`, `ine-card--cyan`, `ine-todo` |

Content slides take a `minutes` frontmatter field (e.g. `minutes: 25–50`) that shows as a chip in the corner; section slides take `number` and `minutes`.

The examples use **Peluda**, a fictional pet-food subscription company. Its back office lives in [inesdi-2026-peluda-admin](https://github.com/manuartero/inesdi-2026-peluda-admin).
