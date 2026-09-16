---
layout: default
title: "No licence file installed"
permalink: /LIC-NOFILE/
---

**Error code: `LIC-NOFILE`**

## What this means

The app looked for your licence file and there wasn't one. This is also the
normal state of a free install, so **if you have not bought anything, nothing is
wrong** — you are seeing the free version, which is the version you have.

If you *have* bought or been given a key, the file has not landed in the right
place yet.

## Why it happens

- The licence file was downloaded but never moved into the app's folder.
- It was extracted somewhere else — a Downloads folder, or a nested folder that
  came out of a zip.
- It was renamed. The app looks for one exact name.
- The app was reinstalled into a different folder and the old licence stayed
  behind with the old copy.

## What to do

1. Find the file you were sent. It ends in `.dppl`.
2. Do **not** rename it. The name has to stay exactly as delivered.
3. Put it in the same folder as the application's `.exe`. The error message in
   the app shows you that exact folder — it is written out in full.
4. Restart the app.

If you are not sure where the app lives: right-click its shortcut, choose
**Open file location**, and drop the `.dppl` file there.

---

## Still stuck?

Open the app's **Settings**, scroll to **Diagnostics**, and press **Save a
report**. That writes a file with everything needed to work out what happened.
It contains no licence key, no signature, no password, and no personal
identifier — it is safe to send. Attach it when you get in touch.
