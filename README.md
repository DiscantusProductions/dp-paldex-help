# DP_Paldex licence help pages

Published at <https://discantusproductions.github.io/dp-paldex-help/>.

**The source of truth is `docs/support/errors/` in the DP_Paldex repo.**
Edit there and republish; editing here creates a second copy that drifts.

## These URLs are permanent

The app prints `ERROR_HELP_BASE` + the error code, and a build already on
somebody's machine cannot be edited. Renaming a page breaks the link for
every copy of the app ever shipped. Add pages; do not rename them.

`every_failure_code_has_a_help_page` in `app/src/licence.rs` fails the
DP_Paldex build if a code exists with no page, so the set stays complete on
its own.
