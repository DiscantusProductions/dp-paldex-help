---
layout: default
title: "What DP_Paldex records, and what it sends"
permalink: /privacy/
---

# What DP_Paldex records, and what it sends

Short version: **nothing leaves your machine unless you press a button that says
it will.** There is no telemetry, no analytics, no crash reporting that phones
home, and no account.

This page is the long version, because "trust us" is not an answer for a tool
that reads a game's memory and installs a keyboard hook.

---

## The two things that ever touch the network

**1. Checking for updates.** An anonymous request to our public releases page on
GitHub, when you press Check for Updates or when auto-update is on. It sends no
identifier — there is no licence key in it, no machine id, nothing that says
which install is asking.

**2. Activating a licence.** When you type a key and press Activate, that key is
sent to our activation service and a licence file comes back. That is the only
time your key leaves your computer, and it is the only thing sent.

**After that, your licence is checked entirely offline, forever.** The check is
a signature verification against a key compiled into the app. It does not call
home, it does not expire, and it keeps working if our service disappears or we
stop maintaining the project.

---

## Diagnostic reports: yours, and manual

The Settings page has **Copy diagnostics** and **Save diagnostics**. They exist
because "it does not work" is impossible to act on, and asking somebody to find
a dozen log files by hand is worse.

**Both build the same report and neither sends it anywhere.** Copy puts it on
your clipboard; Save writes a text file and tells you where. The report opens
with a note asking you to read it before you share it, and inviting you to edit
out anything you would rather not send.

There is a third button, **Send diagnostic logs**, which posts to our issue
tracker. It needs a GitHub access token, which almost nobody has — without one
it tells you so and you use Copy or Save instead. So in practice every report is
a file you own and decide what to do with.

### What is in a report

- The app version, and when the report was made.
- **Your licence status as one line** — the tier, the licence id, the issue
  date. Never the key, never the signature, never the licence file itself. A
  report you paste into a public forum cannot hand away your entitlement.
- Whatever you typed in the description box.
- Your current settings — overlay sizes, positions, toggles.
- Install status: app and data versions, and which of our mods are loaded.
- **Only if you switch it on:** your Windows version, processor core count and
  memory size, behind the *Include computer info in diagnostics* toggle. Off
  unless you turn it on.
- Tails of **this app's own log files** — what our overlays did, errors they
  hit.
- `UE4SS.log`, the modding framework's log. **This is a shared file**: if you
  run other Palworld mods, their output is in it too.
- The most recent Unreal Engine crash report, **filtered to seven fields** — the
  callstack, the thread stacks, the error message, the crash type and the engine
  version. Unreal writes far more than that into the same file, including
  identifiers for your machine and your Epic account, and none of it is
  included. Field names that were dropped are listed; their values are not.

### What is removed before it is written

- Your Windows account name and your machine name, replaced with placeholders
  like `%USERPROFILE%`.
- Our own install directories.
- GitHub token prefixes, licence file contents, and long runs of hex.

### What is never recorded, anywhere, at all

Not "redacted from reports" — never written in the first place:

- What you type. No keystrokes, no text, ever.
- Window titles of other applications.
- The contents of your save files.
- Hardware identifiers, serial numbers, or a machine fingerprint.
- Your email address, or any account you hold.

---

## The keyboard hook, stated plainly

**DP_Paldex installs a global (low-level) Windows keyboard hook.** It has to:
Palworld takes exclusive control of input, and a normal application hotkey never
arrives while a game is focused. The hook is how pressing your hotkey opens the
overlay at all.

**It records nothing.** It looks at each key long enough to decide whether it is
one of *our* hotkeys, and lets everything else through untouched.

There is an optional diagnostic for hotkeys that will not fire, and it is worth
describing precisely because this is the part people are right to ask about:

- It records a timestamp, **the name of one of our own hotkeys**
  (`"world_tree"`, `"quicksearch"`), and an outcome such as `"armed"` or
  `"rejected: not foreground"`. Never a character, never a key code.
- It is **off unless an environment variable is set**, and there is deliberately
  no switch for it in the interface — a setting is something you can be talked
  into turning on; an environment variable makes "the shipped build records
  nothing" a fact you can check rather than a promise.
- Even when it is on, it records only while Palworld or one of our own overlays
  is the foreground window.

---

## Where things live on your machine

| What | Where |
|---|---|
| Settings, waypoints, your data | `%LOCALAPPDATA%\DP_Paldex` |
| Logs and diagnostic reports | `%TEMP%`, named `dp_paldex_*` |
| Your licence file | Your install directory |

Uninstalling removes the install directory. If you want the logs gone too,
delete the `dp_paldex_*` files in `%TEMP%` — routine ones are capped and swept
automatically, but nothing stops you clearing them yourself.

---

## If you would rather check than trust

The source is not public, so this page is a description rather than something
you can diff. Two things you *can* do:

- **Read a report before sending it.** It is plain text, written for a person,
  and it is the whole of what we would ever see.
- **Watch the network.** Outside an update check and a licence activation, this
  app makes no outbound connections. Any firewall tool will show you that.

Something here wrong, or something you found that this page does not describe?
Say so — a privacy page that quietly drifts from the code is worse than none.
