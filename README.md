# ECZ-ID Passport Bootstrap

Route a supported machine subject through its free Business Passport Parent gateway and one of seven free ECZ-ID child Passport families without auto-issuing identity or inferring ownership.

**Start without an ECZ-ID account or API key.** ECZ-ID does not charge to install or use this public Action; GitHub Actions runner usage follows your GitHub plan.

## Outcome

Preserve the free Business Passport Parent -> seven free child Passport hierarchy while keeping missing identity neutral and requiring user confirmation before any issuance/publishing.

## Run it now

Create `.github/workflows/eczid.yml`, paste this complete first-run workflow, commit it, then run it from the **Actions** tab.

```yaml
name: ECZ-ID Passport Bootstrap

on:
  workflow_dispatch:

permissions:
  contents: read

jobs:
  eczid:
    runs-on: ubuntu-latest
    steps:
      - name: Check out repository
        uses: actions/checkout@v7

      - uses: EcoCitizenz-Ltd/eczid-passport-bootstrap@v1
        with:
          family: auto
```

### First-run path

1. Add the workflow above.
2. Run it manually with **Run workflow**.
3. Open the job and review the ECZ-ID Job Summary.
4. Use the generated local JSON report and outputs below for your own policy or follow-up automation.
5. If persistent machine identity is useful, [choose the right free ECZ-ID Passport](https://developers.ecocitizenz.com/get-started/free-passport/?utm_source=github&utm_medium=action-readme&utm_campaign=github-actions&utm_content=eczid-passport-bootstrap&ecz_source=github&ecz_surface=eczid-passport-bootstrap&intent=free-passport); identity is optional and does not change the technical result.

## Minimal Action step

Already have a workflow? Add only this step:

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
- The complete first-run example grants only `contents: read`; tighten or extend permissions only when the rest of your workflow genuinely needs more.
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

[Choose the right free Passport →](https://developers.ecocitizenz.com/get-started/free-passport/?utm_source=github&utm_medium=action-readme&utm_campaign=github-actions&utm_content=eczid-passport-bootstrap&ecz_source=github&ecz_surface=eczid-passport-bootstrap&intent=free-passport)

## Works with GitHub, not against it

ECZ-ID complements GitHub-native controls with persistent identity, accountable operator context, declared authority, current state, change and re-checkable evidence. It does not replace CodeQL, secret scanning, dependency review, workflow dependency lockfiles or artifact attestations.

## License

ECZ-ID does not charge to install or use this public Action for its intended purpose. The distributed implementation remains proprietary; see [LICENSE.txt](./LICENSE.txt) for the exact terms.

## Support and security

Use the repository issue tracker only for reproducible product defects that contain no secrets or customer-private evidence. Follow [SECURITY.md](./SECURITY.md) for vulnerability reporting and [SUPPORT.md](./SUPPORT.md) for private/commercial support routes.
