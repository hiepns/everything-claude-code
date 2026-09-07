# ECC 2.2.1 bug and security patch execution

Status: in progress, 2026-09-07. Ticket: ECC-031.

## Outcome and authority

The user authorized reviewing, repairing, and merging critical bug and security
PRs, followed by publishing ECC 2.2.1. This advances the M0 distribution and
release-evidence contract. ECC retains policy, canonical state, and release
authority. New feature platforms, ECC 3 contracts, and broad refactoring remain
outside this patch.

## Integration sequence

1. Independently review and merge the verified PowerShell security fix #2961.
2. Repair installer ownership and uninstall dry-run data-loss reports #2964 and
   #2952. Exercise install, upgrade, dry-run, and uninstall on disposable roots.
3. Repair hook JSON truncation #2924, Pi/OMP recursive process spawning #2909,
   and project-scoped GateGuard exemptions #2921 without weakening denials.
4. Review manual Claude hook activation #2982 and plugin dependency loading
   #2822. Include complete, verified fixes; document any remaining limitation.
5. Verify memory MCP compatibility and existing heredoc fixes in current source
   and the actual packed artifact. Avoid duplicating already merged repairs.
6. Review the integrated diff, run focused and full tests, lint, coverage,
   security checks, and hosted platform and packed-lifecycle checks.
7. Update release notes to actual merged behavior. Verify exact current main,
   tag/version availability, signing identity, and registry publishing path.
8. Push the verified signed tag, watch the existing staged publication workflow,
   and verify public registry integrity, release, and install lifecycle.

## Working rules

- Independent reviews and fixes use separate worktrees. One integration owner
  serializes merges and checks the final combined result.
- Preserve contributor attribution. Consolidated or superseded PRs are linked
  to the actual merged fix; PR closure alone is not repair evidence.
- Hosted checks must correspond to the source being merged or released. Failed
  checks are diagnosed before a rerun.
- Never run lifecycle tests against real user homes. Never include credentials
  in logs, source, release notes, or dashboard records.
- Keep v2.2.0 immutable and publish only the single tested 2.2.1 artifact through
  the existing release workflow, with registry readback before latest promotion.

## Initial evidence

- Base: e04ea0b9cc8248686edf5ac751cadff550e162b8.
- Current GitHub account: haelyra, repository write permission verified.
- Repository NPM_TOKEN secret is configured; validity still needs publication.
- No remote v2.2.1 tag; registry lookup returns E404 for ecc-universal@2.2.1.
- Registry latest is 2.2.0. No local GPG private signing key or loaded SSH agent
  identity was available in the initial check. Signing remains an open gate.
- #2961 head db88758cbdadf214728d5ea028fa5705453d6ffc is mergeable with hosted
  checks passing; independent review is in progress.

## Completion evidence

Pending integration, hosted validation, signed tag, publication, registry
integrity readback, and clean lifecycle canaries. This document does not claim
that 2.2.1 has shipped.
