# claudemetre

A native macOS menubar gauge for your **Claude Code** usage — session (5h), weekly, and
instant burn rate shown as high-visibility OKLab gauges, with configurable alarms and a
process panel (group by session, freeze, kill).

## Download

Grab the latest signed `.app` from **[Releases](../../releases/latest)** → `claudemetre-<version>.zip`.

The app is signed with an Apple Development certificate but **not notarized**, so on first
launch Gatekeeper blocks it with *"Apple could not verify 'claudemetre.app' is free of
malware."* This is expected for a non-notarized app — here's how to open it.

**1. Move `claudemetre.app` to `/Applications`** (drag it there).

**2. Clear the quarantine flag** (most reliable — Terminal):

```sh
xattr -dr com.apple.quarantine /Applications/claudemetre.app
```

Then double-click it normally.

**Or, without Terminal:**
- Double-click the app → you'll see the block → open **System Settings → Privacy &
  Security**, scroll to the message about claudemetre, click **"Open Anyway"**, then confirm.
- (macOS 14 and earlier also support: right-click the app → **Open** → **Open**.)

This is a one-time step per download. It does **not** disable Gatekeeper system-wide.

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
