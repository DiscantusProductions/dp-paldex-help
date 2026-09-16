---
layout: default
title: "The licence file could not be read"
permalink: /LIC-UNREADABLE/
---

**Error code: `LIC-UNREADABLE`**

## What this means

The file is there. The app could not open it.

This is almost never a problem with the licence itself — it is the operating
system refusing access.

## Why it happens

- Windows marked the file as blocked because it came from the internet.
- The app is installed somewhere that needs administrator rights, such as
  `C:\Program Files`, and it is not running with them.
- Antivirus or a controlled-folder-access rule is holding the file.
- Something is a folder where a file should be, usually after a bad extraction.
- The drive it lives on is disconnected, or is a network location that is not
  reachable right now.

## What to do

1. **Unblock it.** Right-click the `.dppl` file → **Properties** → if there is
   an **Unblock** checkbox near the bottom, tick it and press OK. This is the
   fix most of the time.
2. **Try a different folder.** If the app is under `C:\Program Files`, install
   it somewhere in your own user folder instead. It does not need to be there.
3. **Check your antivirus.** Look for the app in its quarantine or blocked list.
4. **Re-copy the file.** If it was extracted from a zip, extract it again rather
   than dragging it out of the archive preview.

---

## Still stuck?

Open the app's **Settings**, scroll to **Diagnostics**, and press **Save a
report**. That writes a file with everything needed to work out what happened.
It contains no licence key, no signature, no password, and no personal
identifier — it is safe to send. Attach it when you get in touch.
