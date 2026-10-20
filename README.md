# ngmind

An agent skill that teaches Angular code to beginners through a dialogue between two voices — **Programmer** and **Angular** — moving from the *why* of the architecture down to each line of code.

Works with Claude Code, Codex, Cursor and any agent that supports [Agent Skills](https://agentskills.io) (`SKILL.md`).

## Why

Most code explanations jump straight to syntax. ngmind starts with the need a piece of code solves, then the design decisions behind it, and only then the implementation — so you learn to *think* the way the code was built, not just read it.

## How it works

ngmind walks through code in **concentric circles**:

1. **App purpose and nearby architecture** — what the feature contributes to the app and how work is split between the piece and its collaborators.
2. **The piece's role** — why it exists and where its responsibility ends.
3. **Internal decisions** — why it needs its properties and methods, grouped by responsibility.
4. **Implementation** — a top-to-bottom, line-by-line reading in small chunks.

Each turn covers **one focus** as a short dialogue:

> **Programmer:** I need the user to be able to prepare an order. The app separates the catalog from order review…
>
> **Angular:** I can connect those pieces through their template bindings: I pass the data to the list and run the bound expression when it emits the selection event…

Then it stops and waits. Say "next" to continue, ask a question, zoom out, or jump straight to specific lines.

Grounded by design: it only states relationships it can verify in your project, marks inferred motives as *possible reasons*, checks your Angular version, and consults [angular.dev](https://angular.dev) when behavior depends on the version. It never edits your code.

## Install

```bash
npx skills add pietrodags/ngmind
```

The CLI detects your installed agents and lets you choose where to install. Useful flags:

```bash
npx skills add pietrodags/ngmind -g             # install globally (user-level)
npx skills add pietrodags/ngmind -a claude-code # target a specific agent
```

### Manual install

Copy this folder into your agent's skills directory, e.g. for Claude Code:

```bash
git clone https://github.com/pietrodags/ngmind ~/.claude/skills/ngmind
```

## Usage

Invoke it explicitly or just ask about Angular code:

```
/ngmind explain src/app/catalog/catalog-page.component.ts
```

```
Explain this component with ngmind: <paste code>
```

```
ngmind, go straight line by line through the ngOnInit of ProductList
```

ngmind replies in the language you write in.

## Files

```
ngmind/
├── SKILL.md            # skill instructions
└── agents/openai.yaml  # Codex UI metadata
```

## License

[MIT](LICENSE) © Pietro D'Agostino
