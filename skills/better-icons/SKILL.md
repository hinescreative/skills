---
name: better-icons
description: Search Iconify collections and retrieve SVG icons with the better-icons CLI. Use when a project needs real icons or existing icon assets need replacement.
---

# Better Icons

<!-- Adapted by Hines Creative, 2026-11-08: explicit CLI prerequisite; no MCP setup. -->

Search and retrieve icons from 200+ libraries via Iconify.

## Prerequisite

The CLI needs Node/npm and internet access to Iconify. Check `command -v better-icons`
before use. During environment setup, install the selected version with
`npm install -g better-icons@1.0.4`. If it is missing during a task, report that
specific dependency; do not silently change the environment or MCP configuration.

## CLI

```bash
# Search icons
better-icons search <query> [--prefix <prefix>] [--limit <n>] [--json]

# Search and download all found icons as SVG files
better-icons search <query> -d [dir] [--color <color>] [--size <px>]

# Get icon SVG (outputs to stdout)
better-icons get <icon-id> [--color <color>] [--size <px>] [--json]

```

## Examples

```bash
better-icons search arrow --limit 10
better-icons search home --json | jq '.icons[0]'
better-icons get lucide:home > icon.svg
better-icons get mdi:home --color '#333' --json

# Batch download all search results
better-icons search arrow -d              # saves to ./icons/
better-icons search check -d ./my-icons   # saves to ./my-icons/
better-icons search star -d -c '#000' -s 24 --limit 64
```

## Icon ID Format

`prefix:name` - e.g., `lucide:home`, `mdi:arrow-right`, `heroicons:check`

## Popular Collections

`lucide`, `mdi`, `heroicons`, `tabler`, `ph`, `ri`, `solar`, `iconamoon`

---

## API

All icons from `https://api.iconify.design`
