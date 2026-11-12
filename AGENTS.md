# Agent guide

Impeccable 4.8.2 is installed in this repository at `.claude/skills/impeccable/` and is the design skill for any frontend work here: designing, redesigning, critiquing, auditing, polishing or animating a surface.

## Load context first

```bash
sh .claude/skills/impeccable/scripts/impeccable context --target <path>
```

It returns the resolved product/design paths and platform for a target. Use `--target apps/www`, `apps/lumen`, `packages/liquikit` or `apps/floweb`; from inside one of those directories the same command without `--target` resolves that project. Follow the directives it prints.

## Where the product truth lives

| Path | Product |
| --- | --- |
| `PRODUCT.md` | LiquiKit, the library and its site/examples; inherited by `apps/*` and `packages/*` |
| `apps/floweb/PRODUCT.md` | Floweb, the bilingual admin workspace being built in this repo |

There is deliberately no `DESIGN.md` yet. Record the incumbent system with the `document` command before redesigning a surface that already has a visual world.

## Hooks

`.claude/settings.local.json` (machine-local, gitignored) runs the design detector on session start, after every `Edit`/`Write`, and on stop; findings come back as hook context. The engine binary is cached in `.claude/skills/impeccable/scripts/bin/` (gitignored); the launcher re-downloads the pinned version when it is missing. Turn the hooks off with the skill's `hooks off` command.

## Detector from a shell

```bash
sh .claude/skills/impeccable/scripts/impeccable detect apps/www/src packages/liquikit/src
```

Static files only run the rules that need no parsed page; scanning the running dev server gives the full check.

## Subagents

`.claude/agents/` ships four: `impeccable-documenter`, `impeccable-asset-producer`, `impeccable-finish-reviewer`, `impeccable-manual-edit-applier`.

## Repository commands

```bash
bun install
bun run dev        # registry, then site :3000 and Lumen :3200
bun run build
bun run typecheck
bun run check      # Biome
```
