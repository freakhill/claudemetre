# claudemetre

A native macOS menubar gauge for your **Claude Code** usage — session (5h), weekly, and
instant burn rate shown as high-visibility OKLab gauges, with configurable alarms and a
process panel (group by session, freeze, kill).

## Download

Grab the latest signed `.app` from **[Releases](../../releases/latest)** → `claudemetre-<version>.zip`.

The app is signed with an Apple Development certificate but **not notarized**, so Gatekeeper
will block it on first launch. To open it:

- Right-click `claudemetre.app` → **Open** → **Open**, or
- `xattr -dr com.apple.quarantine /Applications/claudemetre.app`

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
