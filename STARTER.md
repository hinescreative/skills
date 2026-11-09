# A practical starter library

Five task skills, maintained in this repository and linked into the agent's
skill directories. The other examples in this repository are not installed by
this set.

| Skill | Job | Source |
|---|---|---|
| ponytail | Complete coding changes with little added machinery | Existing Hines Creative skill; MIT declaration retained |
| frontend-design | Give a frontend a deliberate visual direction | This repository's Anthropic skill; Apache 2.0 |
| fixing-accessibility | Repair controls, keyboard access and forms | Existing installed skill; included MIT license retained |
| fixing-motion-performance | Improve animation without changing the interaction | Existing installed skill; included MIT license retained |
| better-icons | Search Iconify and retrieve SVGs | Existing installed skill; included MIT license retained |

On Linux, from this checkout:

```bash
bash bin/install-starter
npm install -g better-icons@1.0.4
```

The installer creates individual symlinks under `~/.agents/skills` and
`~/.claude/skills`. Re-running it keeps the same links. It refuses to replace an
existing skill with a different source. An optional first argument selects a
test home directory. Keep this checkout in place: it is the source the links use.

The icon CLI requires Node/npm and internet access. The other four skills have
no executable dependencies. No plugins, hooks, MCP servers, background jobs or
home instruction files are installed by this script.

The November 8 adaptation limits Ponytail's implicit use to the current coding
task, removes invented client history from frontend-design, replaces incomplete
motion examples, and makes the icon CLI a declared setup dependency. This is a
small usable starting set; output from actual work guides later changes.
