---
layout: default
title: "The licence signature does not check out"
permalink: /LIC-BADSIG/
---

**Error code: `LIC-BADSIG`**

## What this means

The file is shaped like a licence, and the signature on it is not one of ours.

Every licence is signed with a key that exists on exactly one machine. The app
checks that signature offline, with no internet connection and no account. If
the check fails, the app will not accept the file — there is no override, and
that is deliberate.

## Why it happens

Ordinary, and far more common:

- **The file was modified.** Opening it in a text editor and saving is enough.
- **It was copied as text** instead of as a file, and something was lost or a
  line wrapped.
- **It is a partial download.**

Less ordinary:

- **It is not a licence for this app.** If it came from somewhere other than the
  official store page, it is not one of ours.

## What to do

1. Get a **fresh copy** from where you originally received it, and move it as a
   file rather than as text.
2. If a fresh, untouched copy still fails, get in touch. Include your licence
   id — the app shows it, and it is not secret.

## If you bought this somewhere unofficial

Keys resold on third-party marketplaces are frequently not real, and there is
nothing we can do to make one work. Your money went to someone who is not us.
Take it up with them, and with your payment provider.

---

## Still stuck?

Open the app's **Settings**, scroll to **Diagnostics**, and press **Save a
report**. That writes a file with everything needed to work out what happened.
It contains no licence key, no signature, no password, and no personal
identifier — it is safe to send. Attach it when you get in touch.
