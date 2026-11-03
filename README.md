# pi-recall

**Pick up where you left off.** Pull the useful parts of earlier [pi](https://pi.dev) conversations into your current one, without pasting raw transcripts.

```
/recall auth refactor
```

## Why

Sometimes you start a new session: the cache expired, the old one got too long, or you're picking up a task from last week. The decisions you made are still in the old session. `pi-recall` finds that session and brings in only what matters.

## Install

```bash
pi install npm:pi-recall
# or
pi install git:github.com/ghodsizadeh/pi-recall
```

## Use it

**`/recall [query]`** opens a picker with the sessions from this project.

| Key | Action |
|---|---|
| type | filter live |
| `↑` `↓` | move |
| `Tab` | select (you can pick several) |
| `Enter` | attach |
| `Esc` | cancel |

Then choose how to attach the sessions:

- **Condensed**: your messages, the assistant's replies and the names of the tools it called. Tool output and thinking are dropped. This step doesn't call a model, so it's instant and the wording is exact.
- **Digest**: one model call turns the selected sessions into a short summary of decisions, current state, files and open items. You can edit the summary before it's attached.

**Or just ask.** The agent has a `recall` tool, so a prompt like this works:

> check how we handled rate limiting in an earlier session and do the same here

## What counts as "this project"

- the git repo you're in, including its subdirectories
- its git worktrees, even ones that live outside the repo folder (`my-app-feature-x/`)

## Good to know

- Search runs over the condensed text, so words that only appeared in tool output won't match.
- Each attached session is capped at about 15k tokens. If a session is longer, the middle is cut, and the agent can still read that part with the tool.
- Everything runs locally. Your sessions are only read, never modified.

## License

MIT
