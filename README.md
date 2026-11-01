# ECZ-ID Passport Bootstrap

Route a supported machine subject through its free Business Passport Parent gateway and one of seven free ECZ-ID child Passport families without auto-issuing identity or inferring ownership.

## Outcome

Preserve the free Business Passport Parent -> seven free child Passport hierarchy while keeping missing identity neutral and requiring user confirmation before any issuance/publishing.

## Quick start

```yaml
- uses: EcoCitizenz-Ltd/eczid-passport-bootstrap@v1
  with:
    family: auto
```

## Inputs

| Input | Required | Default | Description |
|---|---:|---|---|
| `family` | No | `auto` | agent \| mcp \| plugin \| api \| iot \| sdk \| service_workload \| auto |
| `mode` | No | `check` | check or scaffold. Scaffold returns a reference path but performs no identity issuance. |
| `ecz-id` | No | — | Optional declared ECZ-ID reference. A child reference preserves its encoded Parent; a root ECZ-ID is treated as a Parent reference. |
| `parent-ecz-id` | No | — | Optional explicit Business Passport Parent ECZ-ID reference. Must be a root ECZ-ID, not a child Passport reference. |
| `report-path` | No | `eczid-passport-bootstrap.json` | Path for the JSON report. |

## Outputs

| Output | Description |
|---|---|
| `family` | Resolved child Passport family when deterministically available. |
| `passport-present` | Whether a valid child Passport ECZ-ID reference was declared. |
| `ecz-id` | Normalized declared child Passport ECZ-ID when valid. |
| `resolver-url` | Public child Resolver re-check URL when applicable. |
| `parent-present` | Whether a Business Passport Parent reference was explicitly declared or encoded in the supplied ECZ-ID. |
| `parent-ecz-id` | Normalized Business Passport Parent ECZ-ID reference when available. |
| `parent-resolver-url` | Public Parent Resolver re-check URL when applicable. |
| `parent-acquisition-url` | Free Declared Business Passport start/reuse route. |
| `acquisition-url` | Current free child Passport acquisition route. |
| `next-action-url` | The single current Parent, child or Resolver route matching next-action. |
| `next-action` | SELECT_FAMILY, GET_FREE_PARENT, GET_FREE_PASSPORT, RECHECK_RESOLVER or FIX_INVALID_REFERENCE. |
| `reason-codes` | Deterministic reason-code list. |
| `report-path` | Generated JSON report path. |

## Permissions, secrets and data

- The Action itself does not require repository write permission.
- No ECZ-ID secret or API key is required for this public Action.
- Supported workflow/configuration files are read locally inside the GitHub Actions workspace; repository source is not uploaded to ECZ-ID.
- See [PRIVACY.md](./PRIVACY.md), [SECURITY.md](./SECURITY.md) and [SUPPORT.md](./SUPPORT.md) for the complete public boundary.

## Version pinning

The examples use the stable `@v1` compatibility tag. For policies that require an immutable third-party reference, pin this Action to the full commit SHA of the reviewed release. GitHub Actions does not support action-name redirects as a substitute for a stable reference.

## Trust boundary

- Bounded deterministic evidence/current-state processing.
- No hidden telemetry.
- No repository code execution.
- Missing ECZ-ID or missing evidence never means unsafe, non-compliant or untrusted.
- No automatic ownership inference.
- No pay-to-pass.
- No global safety/certification/compliance/approval verdict.
- Local policy decides.

## ECZ-ID identity model

A free Declared Business Passport is the organisation Parent gateway for the seven free machine Passport families: Agent, MCP, Plugin, API, IoT / Device, SDK, and Service & Workload. Verified or Assured strengthens the same Parent ECZ-ID; it does not automatically independently verify a child Passport.

When an identity/currentness next step is warranted, ECZ-ID returns at most one neutral route. Payment never changes the technical result.

## Works with GitHub, not against it

ECZ-ID complements GitHub-native controls with persistent identity, accountable operator context, declared authority, current state, change and re-checkable evidence. It does not replace CodeQL, secret scanning, dependency review, workflow dependency lockfiles or artifact attestations.

## Support and security

Use the repository issue tracker only for reproducible product defects that contain no secrets or customer-private evidence. Follow [SECURITY.md](./SECURITY.md) for vulnerability reporting and [SUPPORT.md](./SUPPORT.md) for private/commercial support routes.
