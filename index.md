---
layout: default
title: "DP_Paldex licence help"
permalink: /
---

# Licence error codes

If DP_Paldex showed you a code, it is explained here.

Every failure the licence check can report has a short code, and that code
is stable: a version from two years ago prints the same one as today.

- [`LIC-BADSIG`](LIC-BADSIG/) — The licence signature does not check out
- [`LIC-MALFORMED`](LIC-MALFORMED/) — The licence file is damaged
- [`LIC-NOFILE`](LIC-NOFILE/) — No licence file installed
- [`LIC-NOKEY`](LIC-NOKEY/) — This build cannot check licences at all
- [`LIC-PRODUCT`](LIC-PRODUCT/) — This licence is for a different product
- [`LIC-REVOKED`](LIC-REVOKED/) — This licence has been revoked
- [`LIC-TIER`](LIC-TIER/) — The licence names a level this app doesn't recognise
- [`LIC-UNREADABLE`](LIC-UNREADABLE/) — The licence file could not be read
- [`LIC-VERSION`](LIC-VERSION/) — This licence is in a newer format

---

## Nothing here matches what you are seeing?

Open **Settings**, scroll to **Diagnostics**, and press **Save a report**.
That writes a file describing what happened. It contains no licence key, no
signature, no password and no personal identifier, so it is safe to send.
