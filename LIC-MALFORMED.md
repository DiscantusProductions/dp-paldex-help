---
layout: default
title: "The licence file is damaged"
permalink: /LIC-MALFORMED/
---

**Error code: `LIC-MALFORMED`**

## What this means

The file is there and readable, but it is not shaped like a licence any more.
Something changed its contents between us sending it and the app reading it.

## Why it happens

- It was opened in a text editor and saved. Even saving without typing anything
  can change the file.
- It was copied by selecting text on screen and pasting, rather than by copying
  the file. This loses parts of it.
- It came through a chat app, a document editor, or an email client that
  reformatted it.
- The download was interrupted and the file is only part of the way there.
- A zip extraction failed partway.

## What to do

1. Get a **fresh copy** of the original file. Do not reuse the one that failed.
2. Move it as a **file**. Do not open it, do not copy its text, do not paste its
   contents into a new document.
3. If you have to send it to yourself, put it in a zip first — that stops
   well-meaning software from tidying it up.
4. Drop it beside the app's `.exe` and restart the app.

**Do not try to repair it by hand.** A licence is signed; any edit at all,
including one that looks harmless, makes it invalid.

---

## Still stuck?

Open the app's **Settings**, scroll to **Diagnostics**, and press **Save a
report**. That writes a file with everything needed to work out what happened.
It contains no licence key, no signature, no password, and no personal
identifier — it is safe to send. Attach it when you get in touch.
