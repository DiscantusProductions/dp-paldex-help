---
layout: default
title: "Windows warnings when you install DP_Paldex"
permalink: /install/
---

# Windows will warn you the first time. Here is why, and what to do.

DP_Paldex is not code-signed. Windows treats any program it has not seen before
as unknown, so the first time you download and run it you will get at least one
warning. **This is expected.** This page walks through each warning you can
hit, in the order you hit them.

If you would rather not take our word for it, the last section shows you how to
check the file you downloaded is byte-for-byte the one we published.

---

## Why isn't it signed?

A code signing certificate costs about $120 a year, every year. DP_Paldex is a
one-person project and it is not yet earning that reliably. Rather than raise
the price or ship something half-finished to cover a certificate, we would
rather explain the warning honestly and sign once the project can pay for
itself.

**Signing would not remove the first warning anyway.** Microsoft's own
documentation is explicit that a signed app from a new publisher is still
*"flagged as unrecognized until reputation accumulates."* What signing buys is
the publisher name in the prompt instead of "Unknown publisher," and reputation
that carries from one release to the next. Useful, not magic.

---

## 1. Your browser may warn while downloading

Some browsers flag any `.zip` containing executables, especially from a site
they have not seen often. Choose **Keep** / **Download anyway**.

**Only ever download from our official releases page.** If you found this file
anywhere else, delete it. We cannot vouch for a copy we did not publish, and an
unsigned file is exactly what someone would tamper with.

---

## 2. "Windows protected your PC" — the blue box

This is **SmartScreen**, and it is the one nearly everybody sees.

> Windows protected your PC
> Microsoft Defender SmartScreen prevented an unrecognized app from starting.
> Running this app might put your PC at risk.

There is no visible **Run** button. That is deliberate — it is meant to slow
you down.

**What to do:**

1. Click **More info** (small text, under the message).
2. A **Run anyway** button appears. Click it.

That is the whole fix. You will not be asked again for that same file.

### Why it happens

SmartScreen checks two things: whether the publisher is known, and whether this
exact file has been downloaded often enough to be considered safe. Microsoft's
description is *"Checking downloaded files against a list of files that are well
known and downloaded frequently. If the file isn't on that list, Microsoft
Defender SmartScreen shows a warning, advising caution."*

A brand-new release of a small tool is on neither list. **This warning is
Windows telling you it has no opinion, not that it found something wrong.**

### It goes away on its own

Reputation builds automatically as more people download a given release.
There is no form to fill in and no way to speed it up. Newer releases may warn
again while the old one had stopped — that is normal, because reputation
attaches to the specific file.

---

## 3. A tip that avoids most of the per-file prompts

When Windows downloads a `.zip`, it tags it as coming from the internet, and
extracting it copies that tag onto every file inside. Clearing it once on the
zip is tidier than clearing it on each file.

**Before extracting:**

1. Right-click the downloaded `.zip` → **Properties**.
2. At the bottom of the **General** tab, tick **Unblock** if it is there.
3. **OK**, then extract as normal.

If there is no **Unblock** checkbox, there was nothing to clear. Nothing is
wrong.

**Do this only for a file you downloaded from our releases page yourself.** It
is a real safety check and it is worth keeping for everything else.

---

## 4. Windows 11 only: Smart App Control

**If you are on Windows 10, skip this section — Smart App Control does not
exist there.**

On some Windows 11 machines a feature called **Smart App Control** runs
alongside SmartScreen. It is stricter, and the important difference is that
**it has no "Run anyway."** If it blocks DP_Paldex, the app simply will not
start.

Microsoft's description of how it decides: it first asks whether its cloud
service *"can make a confident prediction about its safety,"* and if it cannot,
it checks for a valid signature — an app with no valid signature *"is
considered untrusted"* and is blocked.

### Do you even have it?

Probably not, and there is a quick way to check:

**Start → Windows Security → App & browser control → Smart App Control**

If you do not see a **Smart App Control** section at all, you do not have it and
nothing here applies.

Smart App Control is off on machines that are managed by an employer or school,
that have Developer Mode enabled, that run Windows in S mode, or that have
optional diagnostic data turned off. It generally only turns itself on for a
fresh Windows 11 installation — most people who upgraded from Windows 10 never
get it.

### If it is on and blocking

We will not pretend there is a clean workaround. Your options are:

- **Turn Smart App Control off.** It is your machine and your call, but
  understand it protects you against everything else too, and historically
  turning it off was permanent — a clean reinstall of Windows was the only way
  back. Recent Windows updates have changed that, and it can now be re-enabled
  without reinstalling, but check your own machine before assuming.
- **Wait.** Smart App Control also allows apps its cloud service is confident
  about, so a release that has been downloaded widely can start passing.
- **Skip DP_Paldex for now.** A legitimate choice, and we would rather say so
  than talk you into weakening your machine for an overlay.

This is the honest answer to why signing is on our roadmap at all.

---

## 5. Antivirus, and why the installer asks for an exclusion

DP_Paldex loads a small module into Palworld to read your position for the
GPS and map features. **Loading code into a running game looks, to an
antivirus, exactly like what a cheat or a trojan does** — the behaviour is
identical; only the intent differs, and no scanner can see intent.

The installer adds a Microsoft Defender exclusion for the game's mod folder for
this reason. If you use a third-party antivirus, you may need to add the same
exclusion yourself, for the Palworld folder shown in the installer window.

**If that makes you uncomfortable, that is a reasonable instinct.** An
exclusion is a real hole in a real defence. The next section is how to satisfy
yourself before you make one.

---

## 6. Checking you got the file we actually published

Every release publishes a `manifest.json` next to the installer, and that
manifest contains the installer's SHA-256 hash. You can check your download
against it without trusting us at all.

Open PowerShell in your Downloads folder and run:

```powershell
Get-FileHash .\DP_Paldex_Installer.zip -Algorithm SHA256
```

Compare the `Hash` it prints with the `sha256` value for the installer in
`manifest.json` on the same release page. **If they differ, do not run it.**
Delete it and tell us — a mismatch is either a corrupted download or something
we would very much want to know about.

Two further things are worth knowing, because they run whether you check or
not:

- The app **verifies every update before installing it**. The update manifest
  carries a signature we make offline, and the installer is checked against its
  recorded hash before it is written to disk. A tampered update is rejected,
  not run.
- Your licence is verified **entirely on your own machine**, offline. Nothing
  about your key is sent anywhere after you activate it.

---

## Quick reference

| You are on | SmartScreen | Smart App Control | What to do |
|---|---|---|---|
| Windows 10 | Yes | **Does not exist** | More info → Run anyway |
| Windows 11, upgraded from Windows 10 | Yes | Almost never on | More info → Run anyway |
| Windows 11, clean install | Yes | Possibly on | More info → Run anyway; see §4 if it is blocked outright |
| Any, with third-party antivirus | Varies | — | Also add the exclusion in §5 |

Still stuck? Open an issue from the app's Settings page — the report it builds
already includes what we would otherwise have to ask you for.
