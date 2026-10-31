# Node security maintenance draft — 1 November 2026

The tracked asdf selector .tool-versions pinned Node 24.9.0, below the patched Node 24.22.1 floor. Update it within the same major. Existing CI/Docker selectors float on supported major/LTS lines; old builds/images still require inspection and rebuilds. Nix derives Node/Electron from the locked nixpkgs input, which was not evaluated here. No actual build/server/desktop runtime version or owned production deployment was measured.

pnpm-workspace.yaml also selects Electron ^40.6.1. That is a separate bundled runtime, unaffected by this host-Node patch. Its exact lock resolution and shipped binaries require inspection; migration to a supported patched Electron major remains unresolved. No Electron compatibility migration is included.

Read AGENTS.md before preparing this patch. Static selector inspection only; required pnpm typecheck and pnpm lint:fix were not executed locally because the large fork was not materialized/installed. Keep this PR in draft pending repository CI and those checks. Do not claim the application is fully remediated or safe to deploy. No production deploy, merge, dependency-audit clearance or Render hosting assumption.

Sources: https://nodejs.org/en/blog/vulnerability/october-2026-security-releases ; https://render.com/docs/advisory-emudhra . Patched floors: 22.23.4 / 24.22.1 / 26.12.1. Verify actual Node/Electron and CA stores inside each released runtime, not just package engines.
