# claudemetre

A native macOS menubar gauge for your **Claude Code** usage — session (5h), weekly, and
instant burn rate shown as high-visibility OKLab gauges, with configurable alarms and a
process panel (group by session, freeze, kill).

## Download

Grab the latest release from **[Releases](../../releases/latest)** → `claudemetre-<version>.zip`,
unzip it, and drag `claudemetre.app` to `/Applications`. That's it.

The app is signed with a **Developer ID** certificate and **notarized by Apple** (v1.1.4+), so it
opens normally — no Gatekeeper warning, no workarounds.

<details>
<summary>Got "Apple could not verify… is free of malware"?</summary>

That only affects the older, non-notarized **v1.1.3** download. Either grab v1.1.4+ above, or
clear the quarantine flag once:

```sh
xattr -dr com.apple.quarantine /Applications/claudemetre.app
```
</details>

## What it does

- Reads your Claude Code usage **locally** — the OAuth token from the macOS Keychain plus the
  usage endpoint — at a low poll rate, so it costs **zero tokens**. Your token is never sent
  anywhere except `api.anthropic.com`.
- Falls back to a local transcript estimate ("est" mode) when the live endpoint isn't
  available.
- Menubar gauge + click-to-open panel: per-window utilization, instant burn (tok/min), and a
  read-only list of running Claude process trees with freeze/kill controls.

## Requirements

- macOS 13+
- [Claude Code](https://claude.com/claude-code) installed and logged in (otherwise the gauge
  runs in estimated mode).
