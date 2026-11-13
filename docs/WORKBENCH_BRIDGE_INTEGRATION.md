# Workbench bridge — cross-repository integration contract (PR #205)

## Ownership and scope

- **EchoPath-Preconditioning-Lab**: private research/validation authority, native reference runtime, wire contract, and sandbox gateway (PRs #198–204).
- **Preconditioning-Lab-Demo**: public-safe discovery, user-facing demo navigation, synthetic diagnostic fixtures, and eventual hosted Workbench entry point.
- **Isolated hosted runtime**: separately deployed native sandbox service built from reviewed source. Never expose the local-only gateway directly to the internet.

The public repository MUST NOT copy private Lab source, research files, internal fixtures, arbitrary raw native diagnostics, credentials, or production kernel code. This bridge starts with a *public-safe integration contract and launch surface*, not a source mirror.

## Versioned interface

The Lab's Workbench uses `etree.workbench_host_wire/v1` with `requestWorkspace`, `requestPreview`, `applyPreview`, and `requestRevision`. The gateway exposes `GET /api/workbench/status`, `POST /api/workbench/session`, and `POST /api/workbench/dispatch`. These are currently local-only implementation details, **not a public API guarantee**.

The hosted experience should be served from the same HTTPS origin as its gateway (or from a reviewed reverse proxy), using server-held session state, HttpOnly cookies, strict Origin checks, rate limiting, CPU/memory/process limits, timeouts, and sandbox cleanup. GitHub Pages alone cannot run the native C++ process.

## Release gates

1. Lab: review Workbench UI assets and wire payloads for public disclosure; export only approved artifacts.
2. Backend: implement hardened hosted configuration, resource limits, trusted proxy/HTTPS handling, lifecycle and health checks.
3. Demo: provide a dedicated Workbench entry point with a staging link only after a verified URL exists; keep v0–v2 unchanged.
4. Validate browser Open → Preview → Apply → Undo → Redo → Reload, independent sessions, expiry, origin denial, and concurrency.
5. Publish public Workbench launch link after security review and live validation; document measured behavior without production or physics claims.

**Current state:** Public landing integration is staged in this PR. No hosted endpoint is configured and no live native interaction is claimed. Existing v3 bridge replay roadmap remains deferred and independent of this Workbench sandbox track.
