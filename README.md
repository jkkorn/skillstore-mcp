# skillstore — an MCP server that serves runnable methods

A hosted [Model Context Protocol](https://modelcontextprotocol.io) server. Your coding agent asks it for a
method for the task in front of you, and gets back a step-by-step procedure to run on your own material —
not a chat answer, not a link.

**Endpoint:** `https://skillstore-jk.fly.dev/mcp/library` · streamable HTTP · no account, no key, no
install.

```bash
# Claude Code
claude mcp add --transport http skillstore https://skillstore-jk.fly.dev/mcp/library
```

<details>
<summary>Codex, Cursor, Grok, and anything else that speaks MCP</summary>

Add it wherever your editor keeps MCP servers, as a **streamable HTTP** server with the URL above and no
auth. In Grok: `grok.com/connectors → New Connector → Custom`. Tools are discovered automatically.
</details>

## The four tools

| tool | what it does |
|---|---|
| `find_skill` | the task in plain words → the methods that fit, strongest first |
| `browse_skills` | what is on the shelf, by area |
| `get_skill` | the full runnable procedure for one id |
| `rate_skill` | whether it actually worked. This is the only thing that makes the ranking honest |

## What it says when it has nothing

Most of the value is here rather than in the hits. `find_skill` answers in three bands:

- **strong match** — the library has a method for this
- **possible** — the candidates are returned *with* the caveat, because below the confidence floor the
  right answer is still rank 1 about two thirds of the time
- **nothing here covers this** — no ranked list at all. Not one defining word of your task appears in any
  skill, so anything shown would be a coincidence of wording

That third band exists because the alternative is worse: a landing-page skill returned for a question about
braising lamb, at a respectable-looking score.

## Where it is good, and where it is not

Measured, not claimed. On the maintainer's own real queries the top hit is correct **11 of 11** times in
English, with **0** confident wrong answers. On iOS and React Native tasks — Swift, SwiftUI, Xcode builds,
Swift Testing, keychain, RN bridging — **11 of 15** land on the right skill, but **6 of 20** tasks get a
*confident wrong answer*, mostly where no iOS-specific skill exists and something adjacent wins. An
accessibility question has been answered by a video-processing skill matching on the word "dynamic".

Coverage is deepest in product, growth, ops and writing, and thinner the further you get from those.

## Privacy

- The task text you search with is **never stored**. Counters only: an enum name and a timestamp.
- No account, no key, nothing to sign up for.
- External skills are served from their source repositories under their own licences; where a licence does
  not permit redistribution, you get a link instead of the text.

## The diagnosis

Separately from the connector, there is a one-minute check over the skills already installed on your
machine — how many are written so your agent can't reliably fire them. It changes nothing and stores
nothing: **https://skillstore-jk.fly.dev/diagnose**

## Status

Working and in daily use by its author, with essentially no other users yet. If you try it, the most useful
thing you can do is say what it got wrong.
